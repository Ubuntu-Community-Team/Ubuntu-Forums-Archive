---
title: "Evolution &amp; gmail (imap) folder sync issues"
date: 2019-07-08
forum: General Help
---

### Post by Jonners59 on 2019-07-08
In the past week, I have started having issues with Evolution.  I use 5 email accounts in Evolution, all google hosted, and all synchronised with calendar and contacts etc.  I have used this configuration since 2008 when I first moved to Ubuntu.  HOWEVER:  About a week or so ago, I found that in synchronising, and when trying to open certain folders or move messages to certain folders, I'd get an error message saying that it can't be done as the folder does not exist.  It does, I have used it (them) for some time.  They exist in other apps and online via browser, but Evolution is having problems.  I have also noted that it has created it's own folders, that do not exist, again, I can not remove them as they do not exist.

It started in only one account and has spread to another account, so not all as yet.

I have deleted the two accounts and recreated them but get exactly the same problem.

I have attached 2 screenshots.
A genuine folder that can not be accessed or used: [ATTACH=CONFIG]283578[/ATTACH]  Note all sub folders do not show either
A false folder Evolution has created: [ATTACH=CONFIG]283580[/ATTACH]  

Latest Ubuntu (Linux PC 5.0.0-20-generic #21-Ubuntu SMP Mon Jun 24 09:32:09 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux) and Evolution version 3.32.1-32

---

### Post by Jonners59 on 2019-07-09
Images attached rather than inline.

Observation is that this affects folders/Labels that have a "&" in them.  Only fix so far seems to be to remove "&" from name and replace with "+".  Not a good fix, as there could be many and "&" used to work.

---

### Post by Jonners59 on 2019-07-09
[COLOR=#000000][FONT=&quot]These are folders I have created.  I have subsequently noticed that this is ANY folder where I have used a "&" in the name.  So I have fixed it for me by simply (via a browser) replacing folders in my google account that have a "&" with a "+" and then trying to create a new folder with the new name in Evolution, which it eventually rejects and changes the old automatically.  This is NOT a good solution:[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][INDENT]a. If there are a lot of folders it can take a long time[/FONT][/COLOR][/INDENT]
[COLOR=#000000][FONT=&quot][INDENT]b. It is a backward step, as it was an allowed character in the past.[/FONT][/COLOR][/INDENT]
[COLOR=#000000][FONT=&quot]c. It makes filling difficult when using, for instance, the name of a company and that company spells its name with a "&". Then it may become difficult to find.

[/FONT][/COLOR]Seems this is a known bug

[COLOR=#3C3C3C][FONT=monospace]The fix for it was added into [/FONT][/COLOR][COLOR=#3C3C3C][FONT=monospace]evolution-data-server 3.32.3+. When updated it (and restart[/FONT][/COLOR]
[COLOR=#3C3C3C][FONT=monospace]Evolution), it should start working properly.[/FONT][/COLOR]
[COLOR=#3C3C3C][FONT=monospace]       [/FONT][/COLOR]
[https://gitlab.gnome.org/GNOME/evolution-data-server/issues/116](https://gitlab.gnome.org/GNOME/evolution-data-server/issues/116)

---

