---
title: "Timeout is not working"
date: 2021-06-25
forum: General Help
---

### Post by netwizard.x1 on 2021-06-25
Hello,

I use Ubuntu Server 20.04 LTS and I would like to configure a session timeout for inactive users (root and normal users). I added a fole to /etc/profile.d. In order to test the timeout I set the time to 20 sec. Unfortunately root and all users I tested will not be logged out.

```
[COLOR=#000000][FONT=&amp]ls -alh[/FONT][/COLOR]total 20K
drwxr-xr-x  [COLOR=#40A070]2[/COLOR] root root [COLOR=#40A070]4[/COLOR].0K Jun [COLOR=#40A070]21[/COLOR] [COLOR=#40A070]21[/COLOR]:43 .
drwxr-xr-x [COLOR=#40A070]81[/COLOR] root root [COLOR=#40A070]4[/COLOR].0K Jun [COLOR=#40A070]20[/COLOR] [COLOR=#40A070]10[/COLOR]:38 ..
-rw-r--r--  [COLOR=#40A070]1[/COLOR] root root   [COLOR=#40A070]96[/COLOR] Dec  [COLOR=#40A070]5[/COLOR]  [COLOR=#40A070]2019[/COLOR] [COLOR=#40A070]01[/COLOR]-locale-fix.sh
-rw r--r--  [COLOR=#40A070]1[/COLOR] root root   [COLOR=#40A070]37[/COLOR] Jun [COLOR=#40A070]21[/COLOR] [COLOR=#40A070]21[/COLOR]:43 [COLOR=#40A070]02[/COLOR]-timeout.sh 
[COLOR=#000000][FONT=&amp]-rw-r--r--  [/FONT][/COLOR][COLOR=#40A070][FONT=&amp]1[/FONT][/COLOR][COLOR=#000000][FONT=&amp] root root  [/FONT][/COLOR][COLOR=#40A070][FONT=&amp]833[/FONT][/COLOR][COLOR=#000000][FONT=&amp] Mar [/FONT][/COLOR][COLOR=#40A070][FONT=&amp]26[/FONT][/COLOR][COLOR=#40A070][FONT=&amp]16[/FONT][/COLOR][COLOR=#000000][FONT=&amp]:49 apps-bin-path.sh[/FONT][/COLOR]
```

```
[COLOR=#000000][FONT=&amp]cat [/FONT][/COLOR][COLOR=#40A070][FONT=&amp]02[/FONT][/COLOR][COLOR=#000000][FONT=&amp]-timeout.sh 
[/FONT][/COLOR][COLOR=#BB60D5]TMOUT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#40A070]20[/COLOR]
[COLOR=#007020]readonly[/COLOR] TMOUT 
[COLOR=#007020][FONT=&amp]export[/FONT][/COLOR][COLOR=#000000][FONT=&amp] TMOUT[/FONT][/COLOR]
```

Does anyone have an idea what could be the reason. 
I additionally tested 700 as file writes but ever this action didn't help.

---

