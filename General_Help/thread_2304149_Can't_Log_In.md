---
title: "Can't Log In"
date: 2015-11-24
forum: General Help
---

### Post by erik-zoltan on 2015-11-24
When I start up my system it comes to a login prompt. I enter my username and password, the screen flashes blank, then it comes back to the same login prompt. I can repeat this any number of times and get no further.  

I try hitting Ctrl-Alt-F2 and I can log in with no problems at a console prompt. However can't get into Unity and not sure what to even look at, to troubleshoot this issue. 

I recently upgraded to Wily and had no problems.  I have a fairly simple Ubuntu Wily Werewolf 64 bit system.

Thanks,
Erik

---

### Post by QDR06VV9 on 2015-11-24
see if you are in this mess
[http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop)
Down to the green arrow thread.

---

### Post by erik-zoltan on 2015-11-24
I tried all those steps and it doesn't help. However I can report the contents of my ~/.xsession-errors file, which might offer clues.

```
Xlib:  extension "GLX" missing on display ":0".Xlib:  extension "GLX" missing on display ":0".
openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: no-pinentry-gnome3 main process (4777) terminated with status 1
upstart: upstart-event-bridge main process (4812) terminated with status 1
upstart: upstart-event-bridge main process ended, respawning
upstart: upstart-event-bridge main process (4822) terminated with status 1
upstart: upstart-event-bridge main process ended, respawning
upstart: upstart-event-bridge main process (4832) terminated with status 1
upstart: upstart-event-bridge main process ended, respawning
upstart: upstart-event-bridge main process (4840) terminated with status 1
upstart: upstart-event-bridge main process ended, respawning
upstart: upstart-event-bridge main process (4853) terminated with status 1
upstart: upstart-event-bridge main process ended, respawning
upstart: upstart-event-bridge main process (4862) terminated with status 1
upstart: upstart-event-bridge main process ended, respawning
upstart: upstart-event-bridge main process (4872) terminated with status 1
upstart: upstart-event-bridge main process ended, respawning
upstart: upstart-event-bridge main process (4880) terminated with status 1
upstart: upstart-event-bridge main process ended, respawning
upstart: upstart-event-bridge main process (4886) terminated with status 1
upstart: upstart-event-bridge main process ended, respawning
upstart: upstart-event-bridge main process (4894) terminated with status 1
upstart: upstart-event-bridge main process ended, respawning
upstart: upstart-event-bridge main process (4905) terminated with status 1
upstart: upstart-event-bridge respawning too fast, stopped
upstart: gnome-session (Unity) main process (4961) terminated with status 1
upstart: unity-settings-daemon main process (4955) killed by TERM signal
upstart: Disconnected from notified D-Bus bus
upstart: logrotate main process (4784) killed by TERM signal
upstart: hud main process (4953) killed by TERM signal
upstart: unity-panel-service main process (4966) killed by TERM signal
upstart: unity7 main process (4963) killed by SEGV signal
```
Obviously things are going wrong, any thoughts on how to fix?

---

### Post by QDR06VV9 on 2015-11-24
Did you try with

```
sudo [COLOR=#111111][FONT=Consolas]dpkg-reconfigure lightdm[/FONT][/COLOR]
```

If not post back the errors of this
```
*sudo start lightdm*
```
Not sure I am going to be of much help here but maybe someone else can jump in.

---

### Post by erik-zoltan on 2015-11-24
The dpkg-reconfigure simply exits and does nothing. However I do get an error on starting lightdm. 

```
$ sudo dpkg-reconfigure lightdm
$ sudo start lightdm
start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
$
```

Thanks,
Erik

---

### Post by QDR06VV9 on 2015-11-24
Post back the return of
```
apt-cache policy [COLOR=#000000]upstart-sysv[/COLOR]
```

---

### Post by erik-zoltan on 2015-11-24
Here it is...
```
$ apt-cache policy upstart-sysv
upstart-sysv:
  Installed: (none)
  Candidate: 1.13.2-0ubuntu16
  Version table:
     1.13.2-0ubuntu16 0
        500 http://us.archive.ubuntu.com/ubuntu/ wily/main amd64 Packages
```

---

### Post by QDR06VV9 on 2015-11-24
Ah Ha!
Now I see.
Post back if any errors from
```
sudo systemctl start lightdm 
```
You may have to restart to see if and any changes occur.

---

### Post by erik-zoltan on 2015-11-24
No errors. It just comes back to the $.

---

### Post by QDR06VV9 on 2015-11-24
Think you can get back to your session if you log out and back in again?

---

### Post by erik-zoltan on 2015-11-24
I rebooted and - like before - I get to the purple Ubutu login screen where it asks me for a password. I enter the password and the screen flashes black, then immediately dumps me back out to the login screen again. So I can't really log out of that. I can pull up a console session with ctrl-alt-F2 and enter commands there still.

---

### Post by QDR06VV9 on 2015-11-24
What confuses me is that it is trying to start upstart for the init and it is not installed.
What changes have you made in the system lately?

---

### Post by erik-zoltan on 2015-11-24
I can't log out of Unity because I can't get past the login screen. I did try rebooting and still the same issue, and still no errors from systemctl start lightdm

---

### Post by QDR06VV9 on 2015-11-24
Baby steps here, Lets see if we can get this thing to login proper
Just to be sure we are on the same page here are you using these commands in tty2  by way of key combo of "Ctrl + Alt + F2"
Then to get back to Graphical Session using Key Combo "Alt + F7"
```
sudo systemctl restart lightdm 
```
We still have a few more tricks we can try.

---

### Post by erik-zoltan on 2015-11-24
Very grateful for your help.

So I type the following from the Ctrl-Alt-F2 console.

$ sudo systemctl restart lightdm

Up comes the login screen and I give it my password as usual. It flashes black for an instant, then dumps me back out to lightdm once again. 

When I go back to the Ctrl-Alt-F2 console again, here is what i see.

```
$ sudo systemctl restart lightdm
$
```

Just as before.

Thanks,
Erik

---

### Post by QDR06VV9 on 2015-11-24
It is not going to play nice today.
Well if you don't mind lets see if another DM will work(Stranger things have happened) 
**EDIT This may pull-in more stuff(Packages) than you wanted though!**


```
sudo apt-get install gdm
```


Then we will nudge it to use GDM
```
sudo systemctl disable lightdm
sudo systemctl enable gdm

```

And Again reboot.


To revert the changes 
```
sudo apt-get remove gdm
```

and return to lightdm


```
sudo systemctl disable gdm
sudo systemctl enable lightdm

```
Fingers Crossed
I'm going to be away from my computer for about an hour or so.

---

### Post by erik-zoltan on 2015-11-24
Well, gdm worked even worse than lightdm. It kept flashing the screen over and over every few seconds.  

I had to back out the changes.  

Then on a hunch I tried the following.

```
$ sudo apt-get remove lightdm ubuntu-desktop
$ sudo apt-get install lightdm ubuntu-desktop
$ sudo reboot
```

Then it came back to the lightdm version with the same original problem as before. (Can't log in with lightdm but at least it doesn't go into an infinite login loop.) 

After installing and removing gdm, I am getting an error message when I try to enable lightdm.

```
$ sudo systemctl enable lightdm
Synchronizing state of lightdm.service with SysV init with /lib/systemd/systemd-sysv-install...
Executing /lib/systemd/systemd-sysv-install enable lightdm
The unit files have no [Install] section. They are not meant to be enabled using systemctl.
Possible reasons for having this kind of units are:
1) A unit may be statically enabled by being symlinked from another unit's
   .wants/ or .requires/ directory.
2) A unit's purpose may be to act as a helper for some other unit which has
   a requirement dependency on it.
3) A unit may be started when needed via activation (socket, path, timer,
   D-Bus, udev, scripted systemctl call, ...).
$
```

---

### Post by QDR06VV9 on 2015-11-24
Did you by chance upgrade from trusty (14.04) To Wily (15.10)?

---

### Post by erik-zoltan on 2015-11-24
This is a pretty new machine. I upgraded from 15.04 (vivid) to 15.10 (wily).

---

### Post by QDR06VV9 on 2015-11-24
Yeah I was not worried about the machine, as much as the conflicts that are preventing a normal login!
With Vivid we still had upstart in the system and I think some [COLOR=#000000]symlink's are broke..(I'm strongly leaning this way)
But one more shot here.
[/COLOR]This won't hurt anything but lets try upstart then once just to check. You will need to install it and use it in your advanced menu in Grub.
```
sudo apt-get install upstart-sysv
```
Now reboot and at the **grub menu** choose advanced and navigate down to the entry something **like upstart** and hit enter.

---

### Post by erik-zoltan on 2015-11-25
Interestingly, that didn't help, but then it did.

I noticed my system getting worse and worse as I tried steps to fix it. So after installing upstart-sysv didn't help, I used a 15.10 installation CD to just go ahead and reinstall the system. I came up with a new system that had all my files but none of my software, which seems like a good deal at this point. And I could log in just fine, but I couldn't get a unity side bar or a title bar, and my windows didn't have title bars or resize controls etc.  

So because there were still upstart errors in .xsession-errors, I tried the following command at the terminal.

$ sudo apt-get install upstart-sysv

And now the system works just fine. A couple apps to reinstall but no big deal and I feel like it was a good trade off.

Thanks!!!
Erik

---

### Post by QDR06VV9 on 2015-11-25
Hey that's great to get back to a working system.Ya-Hoo!.:D
Systemd is kind of a puzzle for me, on Ubuntu anyway.
I find it interesting that you still had to have [COLOR=#000000]upstart-sysv in there?
But Hey if your happy then I am Also.[/COLOR];)
I wish I would of had a better outcome for you though.:(
Thanks for your reply.
Kind Regards

---

