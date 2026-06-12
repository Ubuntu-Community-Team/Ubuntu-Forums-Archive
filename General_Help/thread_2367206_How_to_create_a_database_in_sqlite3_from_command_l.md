---
title: "How to create a database in sqlite3 from command line"
date: 2017-07-27
forum: General Help
---

### Post by mohapatrasandeep60 on 2017-07-27
From the command line sqlite3 gives output:
  SQLite version 3.11.0 2016-02-15 17:29:24
Enter ".help" for usage hints.
Connected to a transient in-memory database.
Use ".open FILENAME" to reopen on a persistent database.
sqlite>   tried to quit after that using command sqlite> sqlite3&gt; .quit    ...> 
  it does not quit but  gives output sqlite> sqlite3&gt; .quit    ...>  
  Then I come back to command prompt with ctrl+D
  Then to create Database I entered command sqlite3 TheftSiren.db
  sqlite3 TheftSiren.db
SQLite version 3.11.0 2016-02-15 17:29:24
Enter ".help" for usage hints.
sqlite>  I used ctrl+D again to come to command prompt
  To see if db i created I tried command
  sqlite3&gt; .databases
[1] 2601
SQLite version 3.11.0 2016-02-15 17:29:24
Enter ".help" for usage hints.
Connected to a transient in-memory database.
Use ".open FILENAME" to reopen on a persistent database.
gt: error: neither tool nor script specified; option -help lists possible tools

[1]+  Stopped                 sqlite3
.databases: command not found  it also failed
  can someone tell what i the right way of handling these?

---

