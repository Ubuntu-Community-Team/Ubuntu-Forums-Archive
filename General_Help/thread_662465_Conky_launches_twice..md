---
title: "Conky launches twice."
date: 2008-01-09
forum: General Help
---

### Post by Nem1976 on 2008-01-09
OK I screws something up here. I finished installing ubuntu onto my laptop and I installed conky.

Well I decided to test out the Remember Currently running applications button under the sessions option tab under sessions.  Well now I conky loads twice on boot.  And it ends up creating a window over top the rest of my applications.  If I close both conkys out then relaunch it everything is fine.

I looked at my sessions file and here is what I have.

```

[Default]
0,id=117f000101000119887258700000055270004
0,RestartStyleHint=2
0,Priority=5
0,Program=vino-session
0,CurrentDirectory=/home/nem
0,CloneCommand=vino-session --sm-config-prefix /vino-session-vS7nyU/ 
0,RestartCommand=vino-session --sm-config-prefix /vino-session-vS7nyU/ --sm-client-id 117f000101000119887258700000055270004 --screen 0 
1,id=117f000101000119887258500000055270003
1,RestartStyleHint=0
1,Priority=10
1,CloneCommand=compiz 
1,RestartCommand=compiz --sm-client-id 117f000101000119887258500000055270003 
2,id=117f000101000119887258400000055270000
2,RestartStyleHint=1
2,Priority=40
2,Program=gnome-volume-manager
2,CurrentDirectory=/home/nem
2,CloneCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-YLKPPU/ 
2,RestartCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-YLKPPU/ --sm-client-id 117f000101000119887258400000055270000 --screen 0 
3,id=117f000101000119887258400000055270001
3,RestartStyleHint=2
3,Priority=40
3,Program=gnome-panel
3,CurrentDirectory=/home/nem
3,CloneCommand=gnome-panel --sm-config-prefix /gnome-panel-MeyDMX/ 
3,RestartCommand=gnome-panel --sm-config-prefix /gnome-panel-MeyDMX/ --sm-client-id 117f000101000119887258400000055270001 --screen 0 
4,id=117f000101000119887258400000055270002
4,RestartStyleHint=2
4,Priority=40
4,Program=nautilus
4,CurrentDirectory=/home/nem
4,CloneCommand=nautilus --sm-config-prefix /nautilus-NJMkMU/ 
4,RestartCommand=nautilus --sm-config-prefix /nautilus-NJMkMU/ --sm-client-id 117f000101000119887258400000055270002 --screen 0 
5,id=117f000101000119887258700000055270005
5,RestartStyleHint=1
5,Program=update-notifier
5,CurrentDirectory=/home/nem
5,CloneCommand=update-notifier --sm-config-prefix /update-notifier-jzPNMU/ 
5,RestartCommand=update-notifier --sm-config-prefix /update-notifier-jzPNMU/ --sm-client-id 117f000101000119887258700000055270005 --screen 0 
6,id=117f000101000119887258700000055270006
6,Program=gnome-power-manager
6,CurrentDirectory=/home/nem
6,CloneCommand=gnome-power-manager --sm-config-prefix /gnome-power-manager-kjVYIU/ 
6,RestartCommand=gnome-power-manager --sm-config-prefix /gnome-power-manager-kjVYIU/ --sm-client-id 117f000101000119887258700000055270006 --screen 0 
7,id=117f000101000119887269100000055270009
7,RestartStyleHint=0
7,Program=amarokapp
7,RestartCommand=amarokapp -session 117f000101000119887269100000055270009_1198958932_60223 
8,id=117f000101000119983727500000055510002
8,Program=deskbar-applet
8,CurrentDirectory=/home/nem
8,CloneCommand=deskbar-applet 
8,RestartCommand=deskbar-applet --sm-client-id 117f000101000119983727500000055510002 --screen 0 
9,id=117f000101000119985470700000055510007
9,Program=evolution-exchange-storage
9,CurrentDirectory=/
9,CloneCommand=evolution-exchange-storage 
9,RestartCommand=evolution-exchange-storage --sm-client-id 117f000101000119985470700000055510007 --screen 0 
10,id=117f000101000119985470900000055510008
10,RestartStyleHint=0
10,Program=evolution-alarm-notify
10,CurrentDirectory=/
10,CloneCommand=evolution-alarm-notify 
10,RestartCommand=evolution-alarm-notify --sm-client-id 117f000101000119985470900000055510008 --screen 0 
11,id=117f000101000119985591700000055510012
11,Program=gnome-terminal
11,CurrentDirectory=/home/nem
11,CloneCommand=gnome-terminal 
11,RestartCommand=gnome-terminal --sm-client-id 117f000101000119985591700000055510012 --screen 0 
12,id=117f000101000119985592600000055510013
12,Program=gedit
12,CurrentDirectory=/home/nem/.gnome2
12,CloneCommand=gedit 
12,RestartCommand=gedit --sm-client-id 117f000101000119985592600000055510013 --screen 0 
13,id=117f000101000119966300200000058060002
13,RestartStyleHint=0
13,Program=amarokcollectionscanner
13,RestartCommand=amarokcollectionscanner -session 117f000101000119966300200000058060002_1199663002_898189 
14,RestartCommand=/home/nem/.conky.sh 
15,RestartCommand=conky 
16,RestartCommand=bluetooth-applet 
17,RestartCommand=gnome-at-visual -s 
18,RestartCommand=restricted-manager --check 
19,RestartCommand=xdg-user-dirs-gtk-update 
20,RestartCommand=avant-window-navigator 
21,RestartCommand=gnome-volume-manager --sm-disable 
22,RestartCommand=nm-applet --sm-disable 
23,RestartCommand=/usr/bin/system-config-printer-applet 
num_clients=24
```

The conky.sh is just a script I have that causes conky to wait 20 secs after desktop is loaded to load up.  

I have tried to delete one of the lines and then change the num_clients=x but it ends up still loading conky.

The screenshot is what conky looks like on boot with it creating a window ontop of all others.

---

### Post by dlegend on 2008-01-09
Have you tried logging out and back in, closing out both conky instances, loadnig up a new conky instance, and then clicking the remember current session button?

You could also try removing all instances of conky, saving current session, then on next login launch conky then adding it again and saving one last time.

---

### Post by Nem1976 on 2008-01-09
Yes I tried selecting the button again and it doesn't do any good.  What happens if I just delete the sessions file?  Or recreate a new one for a different account?  Will that work.?

---

### Post by dlegend on 2008-01-09
> **Nem1976 said:**
> Yes I tried selecting the button again and it doesn't do any good.  What happens if I just delete the sessions file?  Or recreate a new one for a different account?  Will that work.?

Starting from scratch never hurts. But please make a backup file just in case (eg. rename it to session-file-name.bak)! Let me know if it works without too much problems. I've never deleted the file before but don't think it'd do anything critical. You can always recover the backup in case of emergency. I think Ubuntu will just generate a new session file.

---

### Post by Nem1976 on 2008-01-09
I will play with it tomorrow morning and see what I can break/fix.  :-P

---

### Post by Nem1976 on 2008-01-10
Ok I backed up the sessions file and rm'ed it an made sure the file was gone then logged out and back in and the file returned.  And all the existing stuff loading is back.  So Conky is still loading twice.  Is there another session file I should be editing?  The one I'm working on is under .gnome2

---

### Post by imoatama on 2008-01-12
There is another session file in /usr/share/gnome/default.session I think. This is what is run by gnome-session when it starts up, and applies to all users. It´s possible though unlikely that you have a line to start conky there as well as in your own session file.

---

### Post by Anduu on 2008-01-13
Having the Save Session Info box checked has caused me nothing but grief since day one...I highly recommend unchecking it.

Make sure anything you want autostarted is in the list then delete your /home/<username>/.gnome2/session file and restart.

---

### Post by Nem1976 on 2008-01-14
Well I found the issue.  Under sessions and the tab current session I found the 2 conkys loading from there.  I deleted both and also unchecked the Automaticlly remember running applications box under the session options tab and everything is working properly now. 

Thanks for all the help in finding this issue.

---

