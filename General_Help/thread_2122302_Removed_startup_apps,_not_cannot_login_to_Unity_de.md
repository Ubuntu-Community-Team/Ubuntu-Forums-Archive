---
title: "Removed startup apps, not cannot login to Unity desktop"
date: 2013-03-04
forum: General Help
---

### Post by cigtoxdoc on 2013-03-04
I was removing some of the apparently useless (hidden) startup applications.  When I rebooted, I found that I could not log into Unity desktop (even with guest), but I could login to character-based environment after Ctrl-Alt-F1.  So, I know my usernames and passwords are good.  How do I get back to where I was?

John

---

### Post by ManamiVixen on 2013-03-04
What did you remove? Most of the stuff in startup was MANDITORY. Hence why it was hidden. But some, like bluetooth, desktop sharing could be removed.

---

### Post by cigtoxdoc on 2013-03-04
Thank you for your reply.  All my data files are backed up on SpiderOak, but there should be an easier way to recover from this error.  Any ideas?

John

---

### Post by steeldriver on 2013-03-04
what are the exact symptoms? does the lightdm / unity greeter screen start OK but then not let you login? or do you only get a CLI screen?

---

### Post by cigtoxdoc on 2013-03-04
Everthing behaves as normal until you go to log into Unity desktop.  It is rejecting valid passwords.  Password works when I do Ctrl-Alt-F1 and login with user name and password.

John

---

### Post by cigtoxdoc on 2013-03-04
it appears that I could quickly copy the etc/xdg/autostart folder from another similar PC and past it into /etc/xdg/ on the nonworking machine.  I have the folder on  a thumb drive.  There appears no way using UNIX commands to copy the folder from the thumb drive into /etc/xdg/ .

---

### Post by cortman on 2013-03-04
> **cigtoxdoc said:**
> There appears no way using UNIX commands to copy the folder from the thumb drive into /etc/xdg/ .

Come on now, really? :?

You need to mount the flash drive first. Run

```
sudo fdisk -l
```

to see what the computer is calling your flash drive (/dev/sd(a,b,c, etc)(1,2,3, etc). Likely it'll be /dev/sdb1.

Next run

```
sudo mkdir /media/flashdrive
sudo mount /dev/sdb1 /media/flashdrive
```

then navigate to /media/flashdrive, and the contents of the flash drive will be there. You can copy/paste into /etc/xdg, remembering you need to use sudo.

I'm not sure at all if this will fix your original issue but this is how to do what you wanted.

---

### Post by cigtoxdoc on 2013-03-05
Thank you very much for your help.  Yes, the syntax that you gave me work.  Yes, I now have the autostart files from /etc/xdg/autostart files from a similar machine over to /etc/xdg/autostart on problem machine.

However, I can still not get a logon to work on Unity desktop

John

---

### Post by steeldriver on 2013-03-05
Here's another diagnostic you can try - it will tell you whether it's your lightdm / greeter authentication  process that is broken, or a problem starting your default session


1. log in at the virtual terminal (e.g. Ctrl-Alt-F1)

2. kill lightdm if it's still running

```
sudo service lightdm stop
```

3. attempt to start X manually

```
startx
```

If lightdm is broken, you might want to

a. backup the /etc/lightdm/lightdm.conf file

```
sudo cp /etc/lightdm/lightdm.conf /etc/lightdm/lightdm.conf.back
```

b. reconfigure lightdm and the default greeter

```
sudo dpkg-reconfigure lightdm
sudo dpkg-reconfigure unity-greeter
sudo service lightdm start
```

---

### Post by cigtoxdoc on 2013-03-05
Thank you for your help.  I have followed your suggestions, but none of the logins on the Unity desktop work.

What are next steps?

John

---

### Post by steeldriver on 2013-03-05
did startx work? if not, what error messages did it produce?

---

### Post by cigtoxdoc on 2013-03-05
Thank you for your help.

startx gave the following messages
Fatal server error:
Server is already active for display 0
If server is no longer running, remove /tmp/.XO-lock
ddxSigGiveUp: Closing log
Invalid MIT-MAGIC-COOKIE-1 keyInvalid MIT-MAGIC-COOKIE-1 keyxinit:giving up
xinit: unable to connect to X server: Resource temporarily unavailable
xinit: server error

---

### Post by steeldriver on 2013-03-05
and you did stop lightdm first, right? did it really stop? what does

```
ps -ef | grep X
```

say?

---

### Post by grahammechanical on 2013-03-05
> [COLOR=#000000] there should be an easier way to recover from this error.[/COLOR] Why? Why should there be an easy way of doing anything? There are many ways we can break an OS. They are all undocumented. Therefore, the methods for fixing things are also undocumented. An easy answer is to re-install Ubuntu. We are all guessing here. Try this

Use Ctrl+Alt+T to open a terminal and run the command ```
software-center
``` That should load the Ubuntu Software Centre. Search for ubuntu-desktop. Is it still installed? If not install it and shutdown and reboot. You may have removed ubuntu-desktop. Regards.

---

### Post by cigtoxdoc on 2013-03-05
root 2022 1359 0 08:40 tty7 00:00:01 /usr/binX :0 -auth /var/run/lightdm/root:0 -nolisten tcp vt7 -novswitch
john 2441 2331 0 08:47 tty1 00:00:000 grep --color=auto X

BTW, when I did shut down lightdm and run startx, I got a blank screen

Thank you for your help

---

### Post by cortman on 2013-03-05
Apparently that lighdm process didn't get killed properly- it's the first line returned. Kill it with

```
sudo kill -9 process_id
```

What you posted says the process ID is 2022. It's probably changed now, but that's the field you want for the PID.
Then follow steeldriver's instructions.
Good luck.

---

### Post by cigtoxdoc on 2013-03-05
killed process as instructed
startx
screen goes black for a few minutes
then get No protocol specified (multiple times)
then get 

xinit: giving up
xinit: unable to connect to X server: Resource temporarily unavailable

waiting for X server to shut down  ddxSigGiveUp: Closing log
Server terminated successfully (0). Closing log file

xinit: server error
xauth: error on locking authority file /home/john/.Xauthority

---

### Post by steeldriver on 2013-03-05
OK can you check the ownership + permissions on your home dir and ICE / X authority files please? e.g.

```

ls -ld ~
ls -l ~/.{ICE,X}authority

```

Since this appears to affect guest logins it's probably worth checking your available disk space as well

```

df -h

```

---

### Post by cigtoxdoc on 2013-03-05
df -h gave for /dev/sda2 size = 145G, used 96G, avalable 41G Use 71%
udev/dev 1%
tmpfs/run 1%
/run/lock 1%
/run/shm 1%

ls -l ~/.{ICE,X}authority = -rw------- 1 john john 31140 Mar 1 08:53 /home/john/.ICEauthority
                                  = -rw------- 1 root root        0 Mar 5 08:40 /hone/john/.Xauthority

ls -ld ~ = drwxr-xr-x 82 john john 12288 Mar 5 09:39 /home/john

---

### Post by steeldriver on 2013-03-05
OK you need to fix the ownership of your .Xauthority file - either 

```
sudo chown john:john ~/.Xauthority
```

or simply remove it and let the server create a new one next time (doesn't need sudo)

```
rm ~/.Xauthority
```

Then either try startx again or jump right to restarting lightdm if you're feeling lucky

```
sudo service lightdm start
```

---

### Post by cigtoxdoc on 2013-03-05
By following the advice of grahammechanical and reinstalling ubuntu-desktop, things came back almost to working order.  I am still locked out as well as Guest and my secretary's login.  A dummy user I established when problem first occured works.  So, I changed the ownership of .Xauthority as you suggested and we are back in business.  Thank you

---

