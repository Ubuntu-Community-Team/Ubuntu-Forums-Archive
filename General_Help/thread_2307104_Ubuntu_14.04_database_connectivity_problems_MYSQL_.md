---
title: "Ubuntu 14.04 database connectivity problems MYSQL -Driver's SQLAllocHandle on SQL_HAN"
date: 2015-12-22
forum: General Help
---

### Post by vivienneanthony on 2015-12-22
Hello

I recently installed Ubuntu 14.04 and I am having trouble getting database connectivity. Previously I had 12.04 and it worked fine but now  it doesn't work. I'm not sure of whats the problem 

A simple test gives me this results.

vivienne@vivienne-System-Product-Name:/usr/local/etc$ isql -v xxxx xxxxxx   xxxxxx
[IM004][unixODBC][Driver Manager]Driver's SQLAllocHandle on SQL_HANDLE_HENV failed
[ISQL]ERROR: Could not SQLConnect

I removed unixodbc and unixodbc-bin. Then built the unix driver from the source and did a sudo make install. I'm not sure of what the problem is.

Help is appreciated a lot.

Vivienne 

```


odbcinst.ini

[MySQL]
Driver=/usr/local/lib/libodbc.so
UsageCount=1

[ODBCMySql]
Driver=/usr/lib/x86_64-linux-gnu/odbc/libmyodbc.so
UsageCount=2


.odbc.ini

[HangarsDSN]
Description=Hangars Database
Driver=MySQL
Server=db.host.sk
Port=3306
User=xxxx
Password=xxxx
Database=xxxx


odbc info
--------
vivienne@vivienne-System-Product-Name:/usr/local/etc$ odbc_config --odbcinstini
/usr/local/etc/odbcinst.ini
vivienne@vivienne-System-Product-Name:/usr/local/etc$ odbc_config --odbcini
/usr/local/etc/odbc.ini
vivienne@vivienne-System-Product-Name:/usr/local/etc$ odbc_config --libs
-L/usr/local/lib -lodbc
vivienne@vivienne-System-Product-Name:/usr/local/etc$ odbc_config --longodbcversion
3.52                                                                                                    
vivienne@vivienne-System-Product-Name:/usr/local/etc$ odbc_config --odbcversion
3                                                                                                       
vivienne@vivienne-System-Product-Name:/usr/local/etc$ unixodbc                                          
unixodbc: command not found                                                                             
vivienne@vivienne-System-Product-Name:/usr/local/etc$ unixODBC 
    Dec 21 23:40 libodbccr.la
      Dec 21 23:40 libodbccr.so -> libodbccr.so.2.0.0
      Dec 21 23:40 libodbccr.so.2 -> libodbccr.so.2.0.0
  Dec 21 23:40 libodbccr.so.2.0.0
     Dec 21 23:40 libodbcinst.la
     Dec 21 23:40 libodbcinst.so -> libodbcinst.so.2.0.0
       Dec 21 23:40 libodbcinst.so.2 -> libodbcinst.so.2.0.0
   Dec 21 23:40 libodbcinst.so.2.0.0
      Dec 21 23:40 libodbc.la
       Dec 21 23:40 libodbc.so -> libodbc.so.2.0.0
       Dec 21 23:40 libodbc.so.2 -> libodbc.so.2.0.0
 Dec 21 23:40 libodbc.so.2.0.0



```

---

