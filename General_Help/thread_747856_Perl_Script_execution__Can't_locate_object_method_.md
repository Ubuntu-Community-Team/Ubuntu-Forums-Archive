---
title: "Perl Script execution : Can't locate object method &quot;session&quot; via package &quot;Net::SNMP&quot;"
date: 2008-04-07
forum: General Help
---

### Post by anujmehta on 2008-04-07
Hi 

I am trying to execute a perl script and getting following warnings and error message.
Do let me know where I am going wrong.

Subroutine AUTOLOAD redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 48.
Subroutine setMib redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 125.
Subroutine initMib redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 136.
Subroutine addMibDirs redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 153.
Subroutine addMibFiles redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 162.
Subroutine loadModules redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 172.
Subroutine unloadModules redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 183.
Subroutine translateObj redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 189.
Subroutine getType redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 218.
Subroutine mapEnum redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 226.
Subroutine strip_session_params redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 258.
Subroutine snmp_get redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 272.
Subroutine snmp_getnext redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 284.
Subroutine snmp_set redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 296.
Subroutine snmp_trap redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 308.
Subroutine MainLoop redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 320.
Subroutine finish redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 328.
Subroutine reply_cb redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 332.
Subroutine select_info redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 340.
Subroutine check_timeout redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 354.
Subroutine _tie redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 370.
Subroutine split_vars redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 384.
Subroutine new redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 417.
Subroutine update redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 557.
Subroutine set redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 595.
Subroutine get redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 620.
Subroutine gettable redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 647.
Subroutine _gettable_do_it redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 776.
Subroutine _gettable_end_routine redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 887.
Subroutine fget redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 917.
Subroutine getnext redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 947.
Subroutine fgetnext redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 970.
Subroutine getbulk redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1000.
Subroutine bulkwalk redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1025.
Subroutine trap redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1072.
Subroutine inform redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1123.
Subroutine new redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1164.
Subroutine new redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1183.
Subroutine tag redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1190.
Subroutine iid redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1194.
Subroutine val redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1198.
Subroutine type redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1202.
Subroutine name redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1206.
Subroutine fmt redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1214.
Subroutine new redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1226.
Subroutine TIESCALAR redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1248.
Subroutine FETCH redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1250.
Subroutine STORE redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1252.
Subroutine DELETE redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1259.
Subroutine TIESCALAR redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1267.
Subroutine FETCH redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1269.
Subroutine STORE redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1271.
Subroutine DELETE redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1276.
Subroutine TIESCALAR redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1284.
Subroutine FETCH redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1286.
Subroutine STORE redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1288.
Subroutine DELETE redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1290.
Subroutine TIEHASH redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1294.
Subroutine FETCH redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1298.
Subroutine STORE redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1308.
Subroutine DELETE redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1312.
Subroutine FIRSTKEY redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1316.
Subroutine NEXTKEY redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1320.
Subroutine EXISTS redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1324.
Subroutine CLEAR redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1325.
Subroutine STORE redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1360.
Subroutine DELETE redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1364.
Subroutine FIRSTKEY redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1368.
Subroutine NEXTKEY redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1369.
Subroutine EXISTS redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1370.
Subroutine CLEAR redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1371.
Subroutine TIESCALAR redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1381.
Subroutine FETCH redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1383.
Subroutine STORE redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1385.
Subroutine DELETE redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1387.
Subroutine TIESCALAR redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1391.
Subroutine FETCH redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1393.
Subroutine STORE redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1395.
Subroutine DELETE redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1400.
Subroutine TIESCALAR redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1407.
Subroutine FETCH redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1409.
Subroutine STORE redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1411.
Subroutine DELETE redefined at /usr/local/lib/perl/5.8.8/SNMP.pm line 1413.
[B][SIZE="4"]Can't locate object method "session" via package "Net::SNMP" (perhaps you forgot to load "Net::SNMP"?) at /opt/abc/scriptmib.pl line 170.
[/SIZE][/B]root@Echelon:/usr/local/lib/perl/5.8.8#

---

