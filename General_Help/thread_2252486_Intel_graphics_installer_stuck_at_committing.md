---
title: "Intel graphics installer stuck at committing"
date: 2014-11-12
forum: General Help
---

### Post by Ankush_Menat on 2014-11-12
Intel released 1.0.7 graphics installer today, I went to 01.org, downloaded deb file and updated my existing installer. While installing drivers it stuck at commiting something (Looks like kernel version :P)
[IMG]http://i.imgur.com/ztE7TKb.png[/IMG]
It was stuck for like 5 minute, laptop fan started running at full speed and laptop was overheating so I pressed ctrl+c and rebooted using sudo poweroff.
Now I tried instlling it agiain and I am getting this error.
[IMG]http://i.imgur.com/3WjI42T.png[/IMG]
Should I force install them?

Intel websites clearly says
> [h=3]Known Issues[/h][COLOR=#333333][FONT=ClearSans-Light]WARNING:[/FONT][/COLOR][COLOR=#333333][FONT=ClearSans-Light] Attempting to "force" package upgrades [/FONT][/COLOR]*may*[COLOR=#333333][FONT=ClearSans-Light] break your OS installation, requiring a re-install or other time-intensive remedies (requiring a high level of expertise). [/FONT][/COLOR]*Do not*[COLOR=#333333][FONT=ClearSans-Light] forcibly upgrade packages![/FONT][/COLOR]

---

### Post by Ankush_Menat on 2014-11-14
Bump? I cant add any new packages due to broken packages? What to do?

forcing broken packeges keeps trying to do something on kernel and it gets stuck in loop.

---

### Post by m8QLJWW on 2014-11-15
Hello,,

I was stuck in the first part of the previous error. Then I tried with [COLOR=#3F4549][FONT=Helvetica Neue]sudo intel-linux-graphics-installer and finally worked for me.

Hope it can help.[/FONT][/COLOR]

---

