---
title: "Endless login screen loop after changing to xdm then back to gdm ..."
date: 2014-06-11
forum: General Help
---

### Post by Bucky Ball on 2014-06-11
Hi all,

As the title suggests. What led to this was me changing login managers on my main squeeze, rock solid 12.04 LTS mini install with xfce last night, and I wish I hadn't!

I was using GDM as the login manager and thought I'd try something lighter. I opened Synaptics and ticked to uninstall GDM and install XDM, then hit apply. During the install/removal of the login managers a splash popped up asking which I would like as my default login manager. Naturally, I chose XDM. All finished and I rebooted, but I got as far as the Edubuntu splash (am using Edubuntu artwork) with the five dots filling and emptying again, and that's where it stayed. 

So, I hit CTL+ALT+F1 and got to a tty, logged in, uninstalled XDM and installed GDM. Reboot. Now I'm getting to the normal login screen, but when I put my password in, goes to black, thinks for awhile, then ... back to the login screen ... forever! 

I have researched the issue, but nothing's worked so far. Tried these things, running from recovery and dropping to root. 

* sudo chown username:username .Xauthority

This reports that can't find .Xauthority, no such file.

* sudo visudo

This brings up the visude file, but not sure what to change in there, if anything. Nothing looks untoward, but then, I am no expert with that file.

* sudo dpkg-reconfigure gdm

All good. Takes me back to the cursor and no complaints. So I exit, restart, but no diff. Back to the login screen forever.

My guess is that when I confirmed I wanted to use XDM as my login manager right at the get go in Synaptics, I have changed something perhaps, but frankly, at a dead-end and, naturally, need this to work. 

Please note well: I have done NOTHING other than attempt to change the login manager and this machine was working faultlessly less than twelve hours ago (and has been for an age ... well, not quite that long, but it is my fully stable install, which is why I need it back). This is probably (possibly) a simple fix, but I'm just not seeing it. 

Thanks in advance for any help and here's hoping we can remedy this pronto! :-k ;)

PS: Another clue, perhaps, is that when I try to update when running the recovery boot, can't get online. Can't update or install anything there. So seems as if I have lost permission on that and a few other things no doubt. A wild guess and stab in the dark, really ...

---

### Post by Bashing-om on 2014-06-11
Bucky Ball; Hello My friend ;

.Xauthotity should be re-created upon reboot, but that file must exit. Else, we will have to create it...
Is that variable set ?
```

sysop@1310mini:~$ echo $XAUTHORITY
/home/sysop/.Xauthority
sysop@1310mini:~$

```
Also check .ICEauthotity:
```

sysop@1310mini:~$ ls -la .ICEauthority
-rw------- 1 sysop sysop 13366 Jun 11 10:17 .ICEauthority
sysop@1310mini:~$

```

Might 'consider' resetting xfce4 desktop to the defaults and see what results (??).

Hope
[INDENT][INDENT][INDENT]it ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-06-11
Hi Bashing-om and thanks for jumping in. ;)

'echo $XAUTHORITY' comes up with a blank. A sign! 'ls -la .ICEauthority' reports pretty much the same as yours; I have the correct date, but the time is about an hour and a half ago.

PS: ... and yes, I just edited my first post but will repeat here: I am using 12.04 LTS mini install with xfce. Slick and speeeedy.

---

### Post by Bashing-om on 2014-06-11
Bucky Ball; Hey hey !

At least we have something to point at.

Have a look here:
[http://ubuntuforums.org/showthread.php?t=2151518&highlight=xauthority](http://ubuntuforums.org/showthread.php?t=2151518&highlight=xauthority)
and see if the same solution applies in your case.

Else:creating a new .Xauthority file !
I am now past full cognitive functionality, but will devote my attention to it in the AM.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-06-11
Thanks for the suggestion.

Booted into recovery and dropped to shell. Wouldn't let me do it, 'cannot move ... etc. etc.' So tried booting to the endless login screen and CTL+ALT+F2 for a tty, logged in there no problem, and tried it there. No complaints. Restart to login screen, password in, thinking time, back to login. So, no change. 

Another clue is that when attempting to login with the GDM login manager, endless loop. When I drop to a tty, login no issue. I can even:
```

sudo startxfce4
```

... from there, but it makes like I am using the system for the first time ...

The commands I used are from the link provided:

```
mv  ~/.bashrc  ~/.bashrc.old
mv  ~/.profile  ~/.profile.old
mv  ~/.bash_logout  ~/.bash_logout.old
cp -v /etc/skel/.[bp]* ~/
```

---

### Post by Bashing-om on 2014-06-12
Bucky Ball; Yuk !

OK,
> 
[color=red]sudo[/color] startxfce4
 I have been told is a no no // everything for starting the GUI is in your /home.
check .Xauthority and .ICEauthority again.

And we are still with out the $XAUTHORITY variable set ?
```

sysop@1310mini:~$ echo $XAUTHORITY
/home/sysop/.Xauthority
sysop@1310mini:~$ 

```

And I too will do some homework.

[INDENT][INDENT]gotta be a cause,
[INDENT][INDENT][INDENT]reason will see us through
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-06-12
Yep, I only used the startxfce4 command once. Am dropping to tty from the login screen to issue commands. Using 14.04 to post so will reboot to 12.04 and check the check .Xauthority and .ICEauthority again and report back.

* Update: No change with the output of the XAUTHORITY and .ICEauthority. The former gives nothing and takes me back to the cursor, the latter shows the same output as reported previously. Hmm. :-k

---

### Post by Bucky Ball on 2014-06-12
:-\" I'm baaa-aaack.

Currently typing from the 12.04 mini install and seems to be back to its rock-solid self. Phew.

I just logged in fine then restarted and fine again, but I'll use the machine for awhile to see if anything else shows up and reboot it a few more times later before marking my thread as solved. 

The solution was as simple as this: I did a bit more sniffing around online and as a consequence had the idea to log into the 14.04 install, navigate to the .Xauthority file and see if there was anything in it. Opened in Leafpad and nope. In Thunar size shows as 0 bytes. Same with .ICEauthority. So I opened Thunar from a terminal as root (gksudo thunar), navigated to the .Xauthority and .ICEauthority files in the 12.04 install, deleted both and restarted. 

Booted 12.04, entered password at the login screen and voila! Appears to be fixed (but will use the machine for awhile to certify). Happy days! ;)

Thanks for your ideas and help, as always.

---

### Post by Bashing-om on 2014-06-12
Bucky Ball; Good deal !

The variable $XAUTHORITY not set was a miss-direction on my part. That variable is not set until the GUI is started .. per my tests on my working xfce install. That variable does not exist outside of the GUI interface. So noted for future reference.

The things in this Operating System I continue to learn; looking forward to any occasion to learn more.

It is it is,
[INDENT][INDENT][INDENT]all in the process[/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-06-14
Well, it's been over twenty four hours and everything's been fine, so I'm calling this 'solved'. Cheers. ;)

---

