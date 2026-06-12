---
title: "Ubuntu 16.04 - Oracle 11g startup issue"
date: 2016-07-16
forum: General Help
---

### Post by iliecristiandorobat on 2016-07-16
[COLOR=#242729][FONT=Arial]Hy, I have installed Ubuntu 16.04 LTS and the database server is starting automatically when machine is opened even I have set to don't. When I was prompted if I want to run Oracle on startup I taped 'no'. The configuration from /etc/default/oracle-xe is:
[/FONT][/COLOR]> [COLOR=#303336]#[/COLOR][COLOR=#303336]This [/COLOR][COLOR=#101094]is[/COLOR][COLOR=#303336] a configuration [/COLOR][COLOR=#101094]file[/COLOR][COLOR=#101094]for[/COLOR][COLOR=#303336] automatic starting [/COLOR][COLOR=#101094]of[/COLOR][COLOR=#303336] the Oracle
[/COLOR][COLOR=#303336]#[/COLOR][COLOR=#101094]Database[/COLOR][COLOR=#101094]and[/COLOR][COLOR=#303336] listener at system startup[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]It [/COLOR][COLOR=#101094]is[/COLOR][COLOR=#303336] generated [/COLOR][COLOR=#101094]By[/COLOR][COLOR=#303336] running
[/COLOR][COLOR=#303336]#[/COLOR][COLOR=#7D2727]'/etc/init.d/oracle-xe configure'[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]Please [/COLOR][COLOR=#101094]use[/COLOR][COLOR=#303336] that method [/COLOR][COLOR=#101094]to[/COLOR][COLOR=#303336] modify this 
[/COLOR][COLOR=#303336]#[/COLOR][COLOR=#101094]file[/COLOR][COLOR=#303336]

[/COLOR][COLOR=#303336]#[/COLOR][COLOR=#303336] ORACLE_DBENABLED[/COLOR][COLOR=#303336]:[/COLOR][COLOR=#7D2727]'true'[/COLOR][COLOR=#303336] means [/COLOR][COLOR=#101094]to[/COLOR][COLOR=#101094]load[/COLOR][COLOR=#303336] the [/COLOR][COLOR=#101094]Database[/COLOR][COLOR=#303336] at system boot[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]
ORACLE_DBENABLED[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#303336]false

[/COLOR][COLOR=#303336]#[/COLOR][COLOR=#303336] LISTENER_PORT[/COLOR][COLOR=#303336]:[/COLOR][COLOR=#101094]Database[/COLOR][COLOR=#303336] listener
LISTENER_PORT[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#7D2727]1521[/COLOR][COLOR=#303336]

[/COLOR][COLOR=#303336]#[/COLOR][COLOR=#303336] HTTP_PORT [/COLOR][COLOR=#303336]:[/COLOR][COLOR=#303336] HTTP port [/COLOR][COLOR=#101094]for[/COLOR][COLOR=#303336] Oracle Application Express
HTTP_PORT[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#7D2727]8090[/COLOR][COLOR=#303336]

[/COLOR][COLOR=#303336]#[/COLOR][COLOR=#303336] Configuration [/COLOR][COLOR=#303336]:[/COLOR][COLOR=#101094]Check[/COLOR][COLOR=#303336] whether configure has been done [/COLOR][COLOR=#101094]or [/COLOR][COLOR=#101094]not[/COLOR][COLOR=#303336]
[/COLOR][COLOR=#303336]CONFIGURE_RUN[/COLOR][COLOR=#303336]=[/COLOR][COLOR=#303336]true[/COLOR][COLOR=#303336]
[/COLOR][COLOR=#242729][FONT=Arial]The configuration from /etc/oratab is:[/FONT][/COLOR]
> [COLOR=#303336]XE[/COLOR][COLOR=#303336]:/[/COLOR][COLOR=#303336]u01[/COLOR][COLOR=#303336]/[/COLOR][COLOR=#303336]app[/COLOR][COLOR=#303336]/[/COLOR][COLOR=#303336]oracle[/COLOR][COLOR=#303336]/[/COLOR][COLOR=#303336]product[/COLOR][COLOR=#303336]/[/COLOR][COLOR=#7D2727]11.2.0[/COLOR][COLOR=#303336]/[/COLOR][COLOR=#303336]xe[/COLOR][COLOR=#303336]:[/COLOR][COLOR=#303336]N[/COLOR]
[COLOR=#242729][FONT=Arial]Even 'ORACLE_DBENABLED=false' the Oracle server is starting with operation system. I can stop it manually, but it is frustrating and if I'm not stopping them, I have to wait 30-40 sec to shut down my computer (even I have ssd, and normally I stay 2, max 3 sec).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]May someone can save me from this hell? :D[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]PS: On Ubuntu 14.04 LTS it was working well with same procedure to install.[/FONT][/COLOR]

---

### Post by iliecristiandorobat on 2016-07-16
I used > sudo systemctl disable oracle-xe.service
and it works.

---

