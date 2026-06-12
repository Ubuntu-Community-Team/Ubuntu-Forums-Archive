---
title: "LC-3 Simulator problem.. Compiling issue?"
date: 2008-03-07
forum: General Help
---

### Post by Longhorn Engineer on 2008-03-07
Hello, I am trying to install LC-3 on my laptop and I am running into some problems.

[http://users.ece.utexas.edu/~patt/06f.306/software.html](http://users.ece.utexas.edu/~patt/06f.306/software.html)

I get to the part where I run /make to compile the simulator but i run into these errors.

parker@parker-eee:~/lc3tools$ sudo make
[sudo] password for parker:
/usr/bin/gcc -c -g -Wall  -DINSTALL_DIR="\"/home/parker/lc3tools\"" -DMAP_LOCATION_TO_SYMBOL -o lc3sim.o lc3sim.c
lc3sim.c:143: warning: pointer targets in initialization differ in signedness
lc3sim.c:144: warning: pointer targets in initialization differ in signedness
lc3sim.c:145: warning: pointer targets in initialization differ in signedness
lc3sim.c:146: warning: pointer targets in initialization differ in signedness
lc3sim.c:147: warning: pointer targets in initialization differ in signedness
lc3sim.c:148: warning: pointer targets in initialization differ in signedness
lc3sim.c:149: warning: pointer targets in initialization differ in signedness
lc3sim.c:150: warning: pointer targets in initialization differ in signedness
lc3sim.c:151: warning: pointer targets in initialization differ in signedness
lc3sim.c:152: warning: pointer targets in initialization differ in signedness
lc3sim.c:153: warning: pointer targets in initialization differ in signedness
lc3sim.c:154: warning: pointer targets in initialization differ in signedness
lc3sim.c:155: warning: pointer targets in initialization differ in signedness
lc3sim.c:156: warning: pointer targets in initialization differ in signedness
lc3sim.c:157: warning: pointer targets in initialization differ in signedness
lc3sim.c:158: warning: pointer targets in initialization differ in signedness
lc3sim.c:162: error: static declaration of ‘lc3_register’ follows non-static declaration
lc3sim.h:109: error: previous declaration of ‘lc3_register’ was here
lc3sim.c: In function ‘command_loop’:
lc3sim.c:364: warning: pointer targets in assignment differ in signedness
lc3sim.c:380: warning: pointer targets in passing argument 1 of ‘sscanf’ differ in signedness
lc3sim.c:386: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
lc3sim.c:400: warning: pointer targets in passing argument 1 of ‘strncasecmp’ differ in signedness
lc3sim.c:400: warning: pointer targets in passing argument 2 of ‘strncasecmp’ differ in signedness
lc3sim.c:411: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
lc3sim.c:411: warning: pointer targets in passing argument 2 of ‘strcpy’ differ in signedness
lc3sim.c:412: warning: pointer targets in passing argument 1 of ‘strcat’ differ in signedness
lc3sim.c:413: warning: pointer targets in passing argument 1 of ‘strdup’ differ in signedness
lc3sim.c:413: warning: pointer targets in assignment differ in signedness
lc3sim.c: In function ‘main’:
lc3sim.c:461: warning: pointer targets in passing argument 1 of ‘cmd_execute’ differ in signedness
lc3sim.c:465: warning: pointer targets in passing argument 1 of ‘cmd_file’ differ in signedness
lc3sim.c: In function ‘read_obj_file’:
lc3sim.c:549: warning: pointer targets in passing argument 1 of ‘fopen’ differ in signedness
lc3sim.c: In function ‘read_sym_file’:
lc3sim.c:577: warning: pointer targets in passing argument 1 of ‘fopen’ differ in signedness
lc3sim.c:579: warning: pointer targets in passing argument 1 of ‘fgets’ differ in signedness
lc3sim.c:581: warning: pointer targets in passing argument 1 of ‘sscanf’ differ in signedness
lc3sim.c:582: warning: pointer targets in passing argument 1 of ‘strcmp’ differ in signedness
lc3sim.c:586: warning: pointer targets in passing argument 1 of ‘sscanf’ differ in signedness
lc3sim.c:588: warning: pointer targets in passing argument 1 of ‘add_symbol’ differ in signedness
lc3sim.c: In function ‘init_machine’:
lc3sim.c:620: warning: pointer targets in passing argument 1 of ‘read_obj_file’ differ in signedness
lc3sim.c:623: warning: pointer targets in passing argument 1 of ‘read_sym_file’ differ in signedness
lc3sim.c: In function ‘cmd_break’:
lc3sim.c:993: warning: pointer targets in passing argument 1 of ‘sscanf’ differ in signedness
lc3sim.c:996: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
lc3sim.c:997: warning: pointer targets in passing argument 1 of ‘strncasecmp’ differ in signedness
lc3sim.c:1007: warning: pointer targets in passing argument 1 of ‘strncasecmp’ differ in signedness
lc3sim.c:1008: warning: pointer targets in passing argument 1 of ‘strcasecmp’ differ in signedness
lc3sim.c:1019: warning: pointer targets in passing argument 1 of ‘strncasecmp’ differ in signedness
lc3sim.c: In function ‘cmd_execute’:
lc3sim.c:1103: warning: pointer targets in passing argument 1 of ‘fopen’ differ in signedness
lc3sim.c: In function ‘cmd_file’:
lc3sim.c:1146: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
lc3sim.c:1154: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
lc3sim.c:1154: warning: pointer targets in passing argument 2 of ‘strcpy’ differ in signedness
lc3sim.c:1155: warning: pointer targets in passing argument 1 of ‘strrchr’ differ in signedness
lc3sim.c:1155: warning: pointer targets in assignment differ in signedness
lc3sim.c:1157: warning: pointer targets in passing argument 1 of ‘strcat’ differ in signedness
lc3sim.c:1159: warning: pointer targets in passing argument 1 of ‘strcasecmp’ differ in signedness
lc3sim.c:1166: warning: pointer targets in passing argument 1 of ‘strcasecmp’ differ in signedness
lc3sim.c:1174: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
lc3sim.c:1182: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
lc3sim.c: In function ‘parse_address’:
lc3sim.c:1262: warning: pointer targets in passing argument 1 of ‘find_symbol’ differ in signedness
lc3sim.c:1265: warning: pointer targets in assignment differ in signedness
lc3sim.c:1267: warning: pointer targets in assignment differ in signedness
lc3sim.c:1269: warning: pointer targets in assignment differ in signedness
lc3sim.c:1270: warning: pointer targets in passing argument 1 of ‘sscanf’ differ in signedness
lc3sim.c:1270: warning: pointer targets in passing argument 2 of ‘sscanf’ differ in signedness
lc3sim.c: In function ‘parse_range’:
lc3sim.c:1286: warning: pointer targets in passing argument 1 of ‘sscanf’ differ in signedness
lc3sim.c:1302: warning: pointer targets in passing argument 1 of ‘strcasecmp’ differ in signedness
lc3sim.c: In function ‘cmd_option’:
lc3sim.c:1393: warning: pointer targets in passing argument 1 of ‘sscanf’ differ in signedness
lc3sim.c:1395: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
lc3sim.c:1396: warning: pointer targets in passing argument 1 of ‘strcasecmp’ differ in signedness
lc3sim.c:1398: warning: pointer targets in passing argument 1 of ‘strcasecmp’ differ in signedness
lc3sim.c:1404: warning: pointer targets in passing argument 1 of ‘strncasecmp’ differ in signedness
lc3sim.c:1411: warning: pointer targets in passing argument 1 of ‘strncasecmp’ differ in signedness
lc3sim.c:1419: warning: pointer targets in passing argument 1 of ‘strncasecmp’ differ in signedness
lc3sim.c:1429: warning: pointer targets in passing argument 1 of ‘strncasecmp’ differ in signedness
lc3sim.c: In function ‘cmd_register’:
lc3sim.c:1505: warning: pointer targets in initialization differ in signedness
lc3sim.c:1505: warning: pointer targets in initialization differ in signedness
lc3sim.c:1505: warning: pointer targets in initialization differ in signedness
lc3sim.c:1505: warning: pointer targets in initialization differ in signedness
lc3sim.c:1505: warning: pointer targets in initialization differ in signedness
lc3sim.c:1505: warning: pointer targets in initialization differ in signedness
lc3sim.c:1505: warning: pointer targets in initialization differ in signedness
lc3sim.c:1505: warning: pointer targets in initialization differ in signedness
lc3sim.c:1506: warning: pointer targets in initialization differ in signedness
lc3sim.c:1506: warning: pointer targets in initialization differ in signedness
lc3sim.c:1506: warning: pointer targets in initialization differ in signedness
lc3sim.c:1507: warning: pointer targets in initialization differ in signedness
lc3sim.c:1509: warning: pointer targets in initialization differ in signedness
lc3sim.c:1509: warning: pointer targets in initialization differ in signedness
lc3sim.c:1509: warning: pointer targets in initialization differ in signedness
lc3sim.c:1510: warning: pointer targets in initialization differ in signedness
lc3sim.c:1515: warning: pointer targets in passing argument 1 of ‘sscanf’ differ in signedness
lc3sim.c:1529: warning: pointer targets in passing argument 1 of ‘strcasecmp’ differ in signedness
lc3sim.c:1529: warning: pointer targets in passing argument 2 of ‘strcasecmp’ differ in signedness
lc3sim.c:1535: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
lc3sim.c:1537: warning: pointer targets in passing argument 1 of ‘strncasecmp’ differ in signedness
lc3sim.c:1537: warning: pointer targets in passing argument 2 of ‘strncasecmp’ differ in signedness
lc3sim.c: In function ‘cmd_translate’:
lc3sim.c:1592: warning: pointer targets in passing argument 1 of ‘sscanf’ differ in signedness
make: *** [lc3sim.o] Error 1

I made sure that I had build-essentials, wish, and flex. (in readme)

I decided to continue with the installation and tried to open the simulator window with

 lc3sim-tk &

and it spits out

parker@parker-eee:~/lc3tools$ lc3sim-tk &
[1] 5521
parker@parker-eee:~/lc3tools$ bash: lc3sim-tk: command not found

I tried searching for the warnings but I couldn't find anything helpful. 

Any insight before I install XP on my laptop so I can do my homework? :confused:

---

