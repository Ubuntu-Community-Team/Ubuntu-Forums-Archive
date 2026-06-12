---
title: "Libre Office Base - Can't get ODBC to work connecting to Sqlite3"
date: 2019-11-27
forum: General Help
---

### Post by pizzipie on 2019-11-27
I have posted this problem to OpenOffice/LibreOffice and was told that I should ask for help on this site; Below are Commands and results of the steps I have taken. I don't know where to go next for help.

> 
  	 	 	 	   **USING: 	**[B]Libre Office Version: 6.0.7.3
		Build ID: 1:6.0.7-0ubuntu0.18.04.10[/B]
 
 
 **SITE: **[https://thejeshgn.com/2018/08/23/using- ... l-UnixODBC]("https://thejeshgn.com/2018/08/23/using-sqlite-with-libreoffice-base-on-linux/#Install-UnixODBC")
 
 
 **COMMAND: ****sudo apt-get install sqlite3 libsqlite3-dev**.
 
 
 **RESULT: **Sqlite3 runs fine.

**COMMAND: **./configure && make ( as per instructions in SITE)
rick@rick-Latitude-E6510:~/Desktop/sqlite-driver/sqliteodbc-0.9996$ **./configure && make**

**RESULT:**
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
.
.
.
checking for sqlite3_table_column_metadata in -lsqlite3... no
checking for sqlite3_profile in -lsqlite3... no
checking for sqlite3_strnicmp in -lsqlite3... no
checking for sqlite3_close_v2 in -lsqlite3... no
checking for SQLite4 header and library... no
configure: WARNING: SQLite4 header file and source not found
configure: error: No usable SQLite header/library on this system
rick@rick-Latitude-E6510:~/Desktop/sqlite-driver/sqliteodbc-0.9996$ 

**COMMAND: **make install ( as per instructions in** SITE**)
rick@rick-Latitude-E6510:~/Desktop/sqlite-driver/sqliteodbc-0.9996$ **make install**

**RESULT:**
make: *** No rule to make target 'install'. Stop. 
rick@rick-Latitude-E6510:~/Desktop/sqlite-driver/sqliteodbc-0.9996$ 

  



---

### Post by The Cog on 2019-11-27
There is a package called libsqliteodbc in the Ubuntu repositories. I don't know it that's any help though.

---

