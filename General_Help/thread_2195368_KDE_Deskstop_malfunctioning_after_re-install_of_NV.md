---
title: "KDE Deskstop malfunctioning after re-install of NVIDIA drivers"
date: 2013-12-23
forum: General Help
---

### Post by dwlamb on 2013-12-23
I had a challenge with an Nvidia API conflict after installing VMware Player tools.  After doing some research, I found [this]("http://askubuntu.com/questions/145195/nvidia-driver-problem-after-updating-to-12-04"), resolved the issue by purging the driver installed by VMware and installing a new one from the command line.  The gui is back but it is not functioning correctly.  These are the symptoms:


[LIST]
[*]After entering my password, the 4/5 icons of a hard disk, spanner and wrench settings logo, globe and Desktop come up.  The KDE logo does not. 
[*]Normally I have 4 desktops.  Now I am down to one.  If I try to increase the number beyond 1 through Pager settings, the application of the settings is ignored. 
[*]Any software I open is static in one place and stack at 0,0.  Sizes of the windows as last used is intact but all positioning  starts at those coordinates. 
[*]Borders and what not for resizing, moving, minimising or other manipulation of a program window don't exist. 
[*]All closing of programs has to be done clicking Quit through the menu.  Keyboard shortcut of Ctrl+Q will not work and the X button top right does not appear. 
[*]Whereas I can enter my password with no challenge on start-up, using the keyboard is intermittent.  Editors like Kate or Kwrite will take data.  But if I start a software that requires root permissions, the dialog box for the password will not accept input. 
[*]Any software I launch the tab for the program does not appear in the task bar. 
[/LIST]

I do have a backup but it only covers /etc/, /home/, /usr/ and /var/ plus their subdirectories respectively.

Is there a re-install I can deploy to fix this? Any help someone can offer for a solution will be greatly appreciated.

---

### Post by dwlamb on 2013-12-26
I have decided to reformat the drive and start over.

---

### Post by cincibluer6 on 2013-12-26
I find that in cases of graphics issues that once you remove the offending package (and reinstall in your case), it's good to just run the Xreset script in /etc/X11. From a terminal just cd to that directory and sudo sh the script. I'm thinking that something just got a bit wonky with your setup.

So, just food for thought if it happens again. Sad to see that you had to reformat.

---

