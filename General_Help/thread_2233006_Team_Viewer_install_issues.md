---
title: "Team Viewer install issues"
date: 2014-07-05
forum: General Help
---

### Post by Edward_Collinson on 2014-07-05
Hey, I have been trying to install Teamviewer to my server running ubuntu server 14.04 LTS
and I am having some issues installing it :(

The problem I am having is where I install the program and it says:
```

[FONT=Menlo]edward@home:~$ sudo dpkg -i teamviewer_linux_x64.deb[/FONT]
[FONT=Menlo]Selecting previously unselected package teamviewer.[/FONT]
[FONT=Menlo](Reading database ... 347393 files and directories currently installed.)[/FONT]
[FONT=Menlo]Preparing to unpack teamviewer_linux_x64.deb ...[/FONT]
[FONT=Menlo]Unpacking teamviewer (9.0.27891) ...[/FONT]
[FONT=Menlo]dpkg: dependency problems prevent configuration of teamviewer:[/FONT]
[FONT=Menlo] teamviewer depends on lib32asound2; however:[/FONT]
[FONT=Menlo]  Package lib32asound2 is not installed.[/FONT]
[FONT=Menlo] teamviewer depends on ia32-libs; however:[/FONT]
[FONT=Menlo]  Package ia32-libs is not installed.[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]dpkg: error processing package teamviewer (--install):[/FONT]
[FONT=Menlo] dependency problems - leaving unconfigured[/FONT]
[FONT=Menlo]Errors were encountered while processing:[/FONT]
[FONT=Menlo] teamviewer
[/FONT]
```[FONT=Menlo][FONT=Verdana]

and on the website it tells me to do this command: [/FONT][/FONT]

[LIST]
[*]sudo apt-get install -f
[/LIST]
&#8203;To fill in missing dependancies, but when I run that command it deletes team viewer :(

So... I need some help :P

Thanks for reading :)

~Ed

---

### Post by claracc on 2014-07-06
I have found this thread: [http://askubuntu.com/questions/453157/how-to-install-teamviewer-on-14-04](http://askubuntu.com/questions/453157/how-to-install-teamviewer-on-14-04) . 

The problem (as it is commneted in the thread)  seems to be the teamviewer software selected, you have to install the 32 bits one to avoid dependency problems.

---

### Post by Edward_Collinson on 2014-07-07
ok thanks

---

### Post by Z80A on 2014-07-07
...and also documented by TeamViewer:

[http://www.teamviewer.com/en/help/363-How-do-I-install-TeamViewer-on-my-Linux-distribution.aspx#multiarch](http://www.teamviewer.com/en/help/363-How-do-I-install-TeamViewer-on-my-Linux-distribution.aspx#multiarch)

---

