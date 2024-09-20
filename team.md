#### Create table team(tid, country, totalmatch, win,loss). Insert 8 team detail. Create trigger to verify totalmatch is not 0. export data into csv file. Read file using reader object and print record with winning %age.


```python
import sqlite3 as sq
```


```python
con=sq.connect("D:/23BCA296/sqlite-tools-win-x64-3460000/team.db")
```


```python
cur=con.cursor()
```


```python
q="create table team(tid, country, totalmatch, win,loss)"
```


```python
cur.execute(q)
```




    <sqlite3.Cursor at 0x2aef0d422c0>




```python
con.commit
```




    <function Connection.commit()>




```python
con.close
```




    <function Connection.close()>



### insert record


```python
cur=con.cursor()
```


```python
cur.execute("insert into team values(1, 'USA', 10, 7, 3)")
```




    <sqlite3.Cursor at 0x2aef0d41340>




```python
cur.execute("insert into team values(2, 'Canada', 12, 8, 4)")
```




    <sqlite3.Cursor at 0x2aef0d41340>




```python
cur.execute("insert into team values(3, 'Mexico', 11, 6, 5)")
```




    <sqlite3.Cursor at 0x2aef0d41340>




```python
cur.execute("insert into team values(4, 'Brazil', 13, 9, 4)")
```




    <sqlite3.Cursor at 0x2aef0d41340>




```python
cur.execute("insert into team values(5, 'Argentina', 10, 5, 5)")
```




    <sqlite3.Cursor at 0x2aef0d41340>




```python
cur.execute("insert into team values(6, 'Germany', 12, 8, 4)")
```




    <sqlite3.Cursor at 0x2aef0d41340>




```python
cur.execute("insert into team values(7, 'France', 11, 7, 4)")
```




    <sqlite3.Cursor at 0x2aef0d41340>




```python
cur.execute("insert into team values(8, 'Italy', 10, 6, 4)")
```




    <sqlite3.Cursor at 0x2aef0d41340>




```python
con.commit()
```

### create trigger


```python
cur.execute("create trigger verify_totalmatch BEFORE INSERT  ON team\
           begin\
                 select case\
                 when new.totalmatch = 0 THEN\
                 raise(abort,'Total matches cannot be 0')\
                 end;\
                 end;\
        ")
```




    <sqlite3.Cursor at 0x2aef0d41340>



### reading csv file


```python
from csv import reader
```


```python
read_obj=open("D:/23BCA296/sqlite-tools-win-x64-3460000/csv/team3.csv","r")
```


```python
csv_reader=reader(read_obj)
```


```python
for row in read_obj:
    print(row)
```

    tid,country,totalmatch,win,loss
    
    1,USA,10,7,3
    
    2,Canada,12,8,4
    
    3,Mexico,11,6,5
    
    4,Brazil,13,9,4
    
    5,Argentina,10,5,5
    
    6,Germany,12,8,4
    
    7,France,11,7,4
    
    8,Italy,10,6,4
    
    


```python

```


```python

```
