---
title: "Problem in running OLSRD in Ubuntu"
date: 2016-10-14
forum: General Help
---

### Post by afz84 on 2016-10-14
Hi everyone,
I installed Olsrd version 0.9.0.3 and when I run Olsrd in the root, I have the following results.

[COLOR=#000000][FONT=&quot][FONT=&quot] --------------------------------------------------------------------------------------------------
 Build date: 2016-10-14 15:19:03 on ubuntu
 [http://www.olsr.org](http://www.olsr.org)


Parsing file: "/etc/olsrd/olsrd.conf"
Link quality fish eye 0
Plugin: olsrd_txtinfo.so.0.1
[/FONT]



[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot] [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Interface Defaultssetting ifs_in_curr_cfg = 0[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        IPv4 broadcast/multicast : AUTO (d)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        Mode           : mesh (d)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        IPv6 multicast           : ff02::6d[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        HELLO emission/validity  : 2.00 (d)/20.00 (d)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        TC emission/validity     : 5.00 (d)/300.00 (d)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        MID emission/validity    : 5.00 (d)/300.00 (d)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        HNA emission/validity    : 5.00 (d)/300.00 (d)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        Autodetect changes       : yes[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        IPv4 broadcast/multicast : AUTO[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        Mode           : mesh[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        IPv6 multicast           : ::[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        HELLO emission/validity  : 0.00/0.00[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        TC emission/validity     : 0.00/0.00[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        MID emission/validity    : 0.00/0.00[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        HNA emission/validity    : 0.00/0.00[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        Autodetect changes       : no[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        IPv4 broadcast/multicast : AUTO[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        Mode           : mesh[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        IPv6 multicast           : ::[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        HELLO emission/validity  : 0.00/0.00[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        TC emission/validity     : 0.00/0.00[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        MID emission/validity    : 0.00/0.00[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        HNA emission/validity    : 0.00/0.00[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        Autodetect changes       : no[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Added 0.0.0.0 to IP deny set[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Added 127.0.0.1 to IP deny set[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot] [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot] ---- Interface configuration ----[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot] [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Checking <OLSRd-Interfac:[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        No such interface![/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Checking <OLSRd-Interfac:[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]        No such interface![/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]No interfaces detected! This might be intentional, but it also might mean that your configuration is fubar.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]I will continue after 5 seconds.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Using 'etx_ff' algorithm for lq calculation.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]---------- LOADING LIBRARY olsrd_txtinfo.so.0.1 ----------[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]OLSRD txtinfo plugin 0.1 by Lorenz Schori[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Checking plugin interface version:  5 - OK[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Trying to fetch plugin init function: OK[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Trying to fetch parameter table and it's size...[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Sending parameters...[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Running plugin_init function...[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]---------- LIBRARY olsrd_txtinfo.so.0.1 LOADED ----------[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot] [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]-- ALL PLUGINS LOADED! --[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot] [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Main address: 0.0.0.0[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot] [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Scheduler started - polling every 50 ms




-----------------------------------------------------------------------------------------------

Could you please let me know how I can configure the interfaces?
Thank you in advance,[/FONT][/COLOR]

---

