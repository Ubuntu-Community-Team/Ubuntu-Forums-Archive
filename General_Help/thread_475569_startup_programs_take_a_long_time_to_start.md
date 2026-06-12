---
title: "startup programs take a long time to start"
date: 2007-06-16
forum: General Help
---

### Post by albesan on 2007-06-16
hello team,

my startup programs take a really long time to kick off, I have added several programs, but just the usual stuff I normally have there and it has always worked fine.
I'm running ubuntustudio with a realtime kernel.
Anybody came across something like this??

any help appreciated, thanks


a.

---

### Post by reader4 on 2007-06-18
I don't have many startup programs, but find that mine are taking a while to start as well.  Most notably, beryl takes a couple of minutes before it starts.  When logging in, I get the usual splash screen which sits on the desktop for quite a while with three (nautilus is the third) icons... when starting an application, the window appears with no decoration... aftera  while, beryl starts, redecorates everything, and the system runs fine.  It's just the startup takes longer than it seems it should.... like it's waiting for something to start, times out and continues.  I'm not even sure how to troubleshoot it.  Any thoughts?

---

### Post by reader4 on 2007-08-21
Does anyone have any thoughts on this?  I have searched for a while and could not find anything to help.  The problem is extremely annoying.  As much as I love Beryl, I use this on a laptop and with the number of times I have to bootup I cannot afford to keep waiting several minutes for a window manager to start.  I can manually start Metacity, but this is beside the point.  What could be taking so long?

No issues when starting from a hibernate/suspend.

---

### Post by reader4 on 2007-08-22
Well, it's not the easiest solution, but it isn't too difficult either.  I found that the problem was in my ~./gnome2/session script.  The hangup was occurring on the command "gnome-wm default0".  Changing "default0" to "beryl-manager" did not help.  What did help was reordering the list, getting rid of the "gnome-wm ..." command and replacing it with "beryl-manager".  The resulting .gnome2/session files reads as:

```
$ more ~/.gnome2/session
[Default]
num_clients=8
0,id=default0
0,Priority=50
0,RestartCommand=beryl-manager
1,id=117f000101000118098425800000049850000
1,RestartStyleHint=2
1,Priority=40
1,Program=gnome-panel
1,CurrentDirectory=/home/********
1,CloneCommand=gnome-panel --sm-config-prefix /gnome-panel-AqCDUy/ 
1,RestartCommand=gnome-panel --sm-config-prefix /gnome-panel-AqCDUy/ --sm-client
-id 117f000101000118098425800000049850000 --screen 0  
2,id=117f000101000118098425800000049850002
2,RestartStyleHint=2
2,Priority=40
2,Program=nautilus
2,CurrentDirectory=/home/********
2,CloneCommand=nautilus --sm-config-prefix /nautilus-FJBR6s/ --load-session /hom
e/********/.nautilus/saved-session-202OTT 
2,RestartCommand=nautilus --sm-config-prefix /nautilus-FJBR6s/ --sm-client-id 11
7f000101000118098425800000049850002 --screen 0 --load-session /home/********/.nauti
lus/saved-session-7CYITT 
3,id=117f000101000118131778600000050540001
,Program=GTKWifi
3,CurrentDirectory=/
3,CloneCommand=GTKWifi --sm-config-prefix /GTKWifi-miP6ht/ 
3,RestartCommand=GTKWifi --sm-config-prefix /GTKWifi-miP6ht/ --sm-client-id 117f
000101000118131778600000050540001 --screen 0 
4,RestartCommand=nm-applet --sm-disable
5,id=117f000101000118098425800000049850001
5,RestartStyleHint=1
5,Priority=40
5,Program=gnome-volume-manager
5,CurrentDirectory=/home/********
5,CloneCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-eTQ
GRs/ 
5,RestartCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-e
TQGRs/ --sm-client-id 117f000101000118098425800000049850001 --screen 0 
6,id=117f000101000118098437700000049850011
6,RestartStyleHint=0
6,Priority=40
6,Program=gnome-power-manager
6,CurrentDirectory=/home/********
6,CloneCommand=gnome-power-manager --sm-config-prefix /gnome-power-manager-5YCj3
s/ 
6,RestartCommand=gnome-power-manager --sm-config-prefix /gnome-power-manager-5YC
j3s/ --sm-client-id 117f000101000118098437700000049850011 --screen 0 
7,id=117f000101000118098437800000049850012
7,RestartStyleHint=2
7,Priority=40
7,Program=gnome-cups-icon
7,CurrentDirectory=/home/********
7,CloneCommand=gnome-cups-icon --sm-config-prefix /gnome-cups-icon-tBFAkw/ 
7,RestartCommand=gnome-cups-icon --sm-config-prefix /gnome-cups-icon-tBFAkw/ --s
m-client-id 117f000101000118098437800000049850012 --screen 0 

```

---

