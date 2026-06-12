---
title: "unixODBC and FreeTDS Issue"
date: 2008-04-18
forum: General Help
---

### Post by Chad.S on 2008-04-18
Here is my situation:

I'm using WINE to get a windows application running that we use at work. I'm running Ubuntu 7.10. The application requires that I make a connection to our MS SQL server that's hosting the database for said application. To make a long story short, I need to use unixODBC/FreeTDS to make the connection in Wine instead of the native odbc.

This has proved to be a major headache. I initially used ODBCConfig to create the system DSN and set the needed settings. The following is what my config files look like (I put in fake username/passwords/hosts for security reasons):

**/etc/freetds.conf**
-------------------------
[Global]
TDS Version = 8.0
debug level = 10

[HEAT]
host = computer.domainname.com
port = 1433
tds version = 8.0
uid = user
pwd = password
-------------------------

**/etc/odbc.ini**
-------------------------
[HEAT]
Description	= MSSQL
Driver		= MSSQL
Servername	= computer.domainname.com
Database	= heat
UID		= user
PWD		= password
Port		= 1433
-------------------------

**/etc/odbcinst.ini**
-------------------------
[MSSQL]
Description	= Microsoft SQL Driver
Driver		= /usr/lib/odbc/libtdsodbc.so
Driver64	= /usr/lib/odbc
Setup		= /usr/lib/odbc/libtdsS.so
Setup64		= /usr/lib/odbc
UsageCount	= 1
CPTimeout	= 
CPReuse		= 
-------------------------

However, when testing the DSN with the visql command, I get the following response...

[S1000][unixODBC][FreeTDS][SQL Server]Unable to connect to data source
[ISQL]ERROR: Could not SQLConnect

The following is what my tdsdump.log file shows from it trying to connect...

**/tmp/tdsdump.log (computer name edited by me for security reasons)**
-------------------------
12:41:30.866969 Starting log file for FreeTDS 0.63
	on 2008-04-18 12:41:30 with debug level 99.
12:41:30.867039 names for ISO-8859-1: ISO-8859-1
12:41:30.867055 names for UTF-8: UTF-8
12:41:30.867066 names for UCS-2LE: UCS-2LE
12:41:30.867076 names for UCS-2BE: UCS-2BE
12:41:30.867086 iconv to convert client-side data to the "UTF-8" character set
12:41:30.867112 tds_iconv_info_init: converting "UTF-8"->"UCS-2LE"
12:41:30.867129 IP address pointer is NULL
12:41:30.867142 Server computer.domainname.com not found!
12:41:30.867152 tds_free_all_results()
-------------------------

What worries me is the "IP address pointer is NULL" line and then the note that it cannot find the computer name. I can ping that name and DNS resolves it fine. I've also tried hardcoding the IP address and that hasn't helped.

However, I think the root cause is that it isn't reading my configuration files correctly. I was able to find documentation on the evironment variables that can override parts of the freetds.conf. So, I added the following lines to my ~/.profile to utilize some of the variables
[B]
~/.profile snippet...[/B]
-------------------------
TDSVER="8.0";export TDSVER
TDSPORT="1433";export TDSPORT
TDSHOST="computername.domainname.com";export TDSHOST
ODBCINI="/etc/odbc.ini";export ODBCINI
FREETDS="/etc/freetds.conf";export FREETDS
-------------------------

When I have this set, I get the following message when trying the visql command...

[S1000][unixODBC][FreeTDS][SQL Server]Unable to connect to data source
[28000][unixODBC][FreeTDS][SQL Server]Login incorrect.
[][unixODBC][FreeTDS][SQL Server]Login failed for user ''. The user is not associated with a trusted SQL Server connection.
[ISQL]ERROR: Could not SQLConnect

The following is what my tdsdump.log file shows from it trying to connect...
[B]
/tmp/tdsdump.log (computer name edited by me for security reasons)[/B]
-------------------------
14:28:32.565391 Starting log file for FreeTDS 0.63
	on 2008-04-18 14:28:32 with debug level 99.
14:28:32.565500 names for ISO-8859-1: ISO-8859-1
14:28:32.565525 names for UTF-8: UTF-8
14:28:32.565545 names for UCS-2LE: UCS-2LE
14:28:32.565563 names for UCS-2BE: UCS-2BE
14:28:32.565581 iconv to convert client-side data to the "UTF-8" character set
14:28:32.565626 tds_iconv_info_init: converting "UTF-8"->"UCS-2LE"
14:28:32.565676 tds_iconv_info_init: converting "ISO-8859-1"->"UCS-2LE"
14:28:32.565713 Connecting to 172.17.2.84 port 1433, TDS 8.0.
14:28:32.673264 tds_put_string converting 13 bytes of "ubuntu-laptop"
14:28:32.673318 tds_put_string wrote 26 bytes
14:28:32.673341 tds_put_string wrote 0 bytes
14:28:32.673362 tds_put_string wrote 0 bytes
14:28:32.673382 tds_put_string converting 24 bytes of "computer.domainame.com"
14:28:32.673403 tds_put_string wrote 48 bytes
14:28:32.673422 tds_put_string wrote 0 bytes
14:28:32.673440 tds_put_string converting 10 bytes of "us_english"
14:28:32.673461 tds_put_string wrote 20 bytes
14:28:32.673480 tds_put_string converting 4 bytes of "heat"
14:28:32.673500 tds_put_string wrote 8 bytes
14:28:32.673622 tds_process_login_tokens()
14:28:32.675272 Received header
0000 04 01 00 e4 00 3c 01 00-                        |.....<..|

14:28:32.675310 Received packet
0000 aa d0 00 14 48 00 00 01-0e 5a 00 4c 00 6f 00 67 |....H... .Z.L.o.g|
0010 00 69 00 6e 00 20 00 66-00 61 00 69 00 6c 00 65 |.i.n. .f .a.i.l.e|
0020 00 64 00 20 00 66 00 6f-00 72 00 20 00 75 00 73 |.d. .f.o .r. .u.s|
0030 00 65 00 72 00 20 00 27-00 27 00 2e 00 20 00 54 |.e.r. .' .'... .T|
0040 00 68 00 65 00 20 00 75-00 73 00 65 00 72 00 20 |.h.e. .u .s.e.r. |
0050 00 69 00 73 00 20 00 6e-00 6f 00 74 00 20 00 61 |.i.s. .n .o.t. .a|
0060 00 73 00 73 00 6f 00 63-00 69 00 61 00 74 00 65 |.s.s.o.c .i.a.t.e|
0070 00 64 00 20 00 77 00 69-00 74 00 68 00 20 00 61 |.d. .w.i .t.h. .a|
0080 00 20 00 74 00 72 00 75-00 73 00 74 00 65 00 64 |. .t.r.u .s.t.e.d|
0090 00 20 00 53 00 51 00 4c-00 20 00 53 00 65 00 72 |. .S.Q.L . .S.e.r|
00a0 00 76 00 65 00 72 00 20-00 63 00 6f 00 6e 00 6e |.v.e.r.  .c.o.n.n|
00b0 00 65 00 63 00 74 00 69-00 6f 00 6e 00 2e 00 08 |.e.c.t.i .o.n....|
00c0 53 00 52 00 53 00 30 00-31 00 4a 00 4f 00 57 00 |s.e.r.v. e.r.0..|
00d0 00 01 00 fd 02 00 00 00-00 00 00 00             |........ ....|

14:28:32.675456 looking for login token, got  aa(ERROR)
14:28:32.675481 tds_process_default_tokens() marker is aa(ERROR)
14:28:32.675510 tds_get_string: reading 180 from wire to give 90 to client.
14:28:32.675548 tds_get_string: reading 16 from wire to give 8 to client.
14:28:32.675586 looking for login token, got  fd(DONE)
14:28:32.675607 tds_process_default_tokens() marker is fd(DONE)
14:28:32.675627 tds_process_end: more_results = 0
		was_cancelled = 0
		error = 1
		done_count_valid = 0
14:28:32.675647 tds_process_end() state set to TDS_IDLE
14:28:32.675665 leaving tds_process_login_tokens() returning 0
14:28:32.675713 tds_client_msg: #20014: "Login incorrect.".  Connection state is now 2.  
14:28:32.675737 tds_free_all_results()
-------------------------

So it seems to take the enviornment variables and doesn't even read my configuration files, since it isn't using my username/pass specified in the odbc.ini file. I can even modify the isql command to include my username and password and then it connects fine, showing...

+---------------------------------------+
| Connected!                            
|                                       
| sql-statement                         
| help [tablename]                      
| quit                                  
|                                       
+---------------------------------------+
SQL>

So how can I get it to read the configuration files correctly? It seems to be at least reading the freetds.conf file, otherwise it wouldn't be recognizing my name of my DSN. Is there something wrong with my odbc.ini that I'm overlooking?

Any insight would be appreciated.

---

