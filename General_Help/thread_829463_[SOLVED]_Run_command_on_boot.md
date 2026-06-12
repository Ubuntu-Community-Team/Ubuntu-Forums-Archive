---
title: "[SOLVED] Run command on boot"
date: 2008-06-14
forum: General Help
---

### Post by pb_online on 2008-06-14
Hello.

I am using Kubuntu 8.04

I want to run command "sudo aticonfig --set-powerstate=1" on boot.
I tried to put it on etc/rc.local without success.

Any suggestion?

---

### Post by Victormd on 2008-06-14
Go to SYSTEM>PREFERENCES>SESSIONS and you can add it there...

---

### Post by pb_online on 2008-06-14
> **Victormd said:**
> Go to SYSTEM>PREFERENCES>SESSIONS and you can add it there...

I don't see Preferences on System section.

---

### Post by Victormd on 2008-06-14
hummm... just remembered that the menu layout on kubuntu is different from ubuntu...
Can you find anything related to sessions?
On kubuntu you can try to run kcontrol from the terminal

or see if you can find KDE Components>Autostart Applications

---

### Post by pb_online on 2008-06-14
> **Victormd said:**
> hummm... just remembered that the menu layout on kubuntu is different from ubuntu...
Can you find anything related to sessions?
On kubuntu you can try to run kcontrol from the terminal

or see if you can find KDE Components>Autostart Applications

KDE Components > Session Manager
System administration > System Services

I can't do what I want, neither of both sections.

---

### Post by Victormd on 2008-06-14
Ok, after some googling, I think this will do the trick:
[http://www.kubuntu.org/doc/7.10/config-desktop/C/tips.html](http://www.kubuntu.org/doc/7.10/config-desktop/C/tips.html)

Let me know if it works...

---

### Post by unutbu on 2008-06-14
pd_online, when you edited rc.local, did you put

```
sudo aticonfig --set-powerstate=1
```

*before* the "exit 0" line?

Also, since rc.local is run by root, you should write

```
aticonfig --set-powerstate=1
```

---

### Post by spiderbatdad on 2008-06-14
> **pb_online said:**
> Hello.

I am using Kubuntu 8.04

I want to run command "sudo aticonfig --set-powerstate=1" on boot.
I tried to put it on etc/rc.local without success.

Any suggestion?

The system is probably looking for a password. Try removing sudo, make sure it is executable, and change owner to root.

Actually, adding it to startup sessions is the right way to go, but sudo won't work easily. I think better to make the program owned by root, and put it is /usr/sbin

---

### Post by pb_online on 2008-06-14
> **unutbu said:**
> pd_online, when you edited rc.local, did you put

```
sudo aticonfig --set-powerstate=1
```

*before* the "exit 0" line?

Also, since rc.local is run by root, you should write

```
aticonfig --set-powerstate=1
```

Yes, I put it before exit 0.
I tried now without sudo. It didn't work. Why did you put *before* into asterisks?

---

### Post by pb_online on 2008-06-14
> **Victormd said:**
> Ok, after some googling, I think this will do the trick:
[http://www.kubuntu.org/doc/7.10/config-desktop/C/tips.html](http://www.kubuntu.org/doc/7.10/config-desktop/C/tips.html)

Let me know if it works...

There are two ways on the site.
The first didn't work.
About the second, see below...

> **spiderbatdad said:**
> The system is probably looking for a password. Try removing sudo, make sure it is executable, and change owner to root.

Actually, adding it to startup sessions is the right way to go, but sudo won't work easily. I think better to make the program owned by root, and put it is /usr/sbin

Notice that, I don't have the command as a script. I just tried to put the command on etc/rc.local

---

### Post by Mateo on 2008-06-14
don't use the GUI menus.  That runs applications when KDE (or Gnome) starts.  That's not what you want.  You want it starting regardless of whether/when an X session is running.

---

### Post by unutbu on 2008-06-14
Maybe specify the *absolute* path to aticonfig.
(asterisks are a poor man's italics) :)

---

### Post by pb_online on 2008-06-14
I also tried make an executable shell script and put it in usr/sbin without effect. I have to open it manually to work.

---

### Post by unutbu on 2008-06-15
What happens if you put this in your script
```
#!/bin/sh
sleep 15
aticonfig --set-powerstate=1

```
and run the script from rc.local?

Be sure to call the script with an ampersand to it will run in the background (and not hold up your boot for 15 seconds).

---

### Post by pb_online on 2008-06-15
My script's name is aticonf.sh and I wrote on it...

```
#!/bin/sh
aticonfig --set-powerstate=1 
```

I put it on /home/charis/Scripts

and then I wrote in /etc/rc.local ...

```

sh /home/charis/Scripts/aticonf.sh
exit 0 

```

No success. Is there any mistake on this way?

What is that "sleep 15" and where I have to put the & on the command?

---

### Post by unutbu on 2008-06-15
Since the command did not work at boot time, but it seemed to work when you entered it manually, one possibility is that some low level system stuff has to happen before the ATI card is ready for the aticonfig command. Perhaps rc.local is calling the aticonfig command too early. Hence I suggest putting 'sleep 15' in your /home/charis/Scripts/aticonf.sh script like this:

```
#!/bin/sh
sleep 15
aticonfig --set-powerstate=1
```

If you make this change, you will also want to edit rc.local like this:
```

/bin/sh /home/charis/Scripts/aticonf.sh &
exit 0
```

The ampersand (&) runs the aticonf.sh script in the background, allowing rc.local to exit without having to wait 15 seconds. If you didn't put the ampersand there then your bootup routine would take 15 seconds longer -- a real bummer.

I also changed sh to /bin/sh in rc.local as well. I don't know if that is necessary, but it won't hurt.

If the above does not work, I suggest also taking out /bin/sh entirely since it is not necessary: 

```

/home/charis/Scripts/aticonf.sh &
exit 0
```

with aticonf.sh changed to 

```
#!/bin/**bash**
sleep 15
aticonfig --set-powerstate=1
```
(Just in case aticonfig operates differently under bash than dash. This probably won't make a difference, but it wouldn't hurt to try.)

---

### Post by pb_online on 2008-06-15
I tried both ways with no success.

Does it need [COLOR="Red"]sh[/COLOR] /home/charis/Scripts/aticonf.sh ?

---

### Post by unutbu on 2008-06-15
I don't think sh is necessary, though I could be wrong. You've tried it both ways and it still doesn't work, however, so the problem must lie somewhere else.

If you type 

```
man aticonfig
```
does the manual describe any verbose mode or debug mode? Anything that could spit out an error might be helpful.

---

### Post by pb_online on 2008-06-15
No manual entry for aticonfig
See 'man 7 undocumented' for help when manual pages are not available.

---

### Post by unutbu on 2008-06-15
For documentation on aticonfig, try

```
aticonfig --help
```

Try editing your /home/charis/Scripts/aticonf.sh like this:

```
#!/bin/sh
sleep 15
/usr/bin/aticonfig **--effective=now **--set-powerstate=1 

```

and edit rc.local like this:
```

touch /home/charis/aticonf-pre
/home/charis/Scripts/aticonf.sh &
touch /home/charis/aticonf-post
exit 0
```
Then reboot. First, is the powerstate correct? (PS. what command do you use to tell?) Second, if it is not working, what is the result of 

```
ls /home/charis/aticonf-*
```
Do aptconf-pre and aticonf-post exist?

---

### Post by pb_online on 2008-06-16
I read the Documentation...

--effective={now,startup}
        Choose when the requested changes should take effect.
            now:     Immediately.  This change will affect the running X
                     session if applicable.  Only 'set-powerstate' and
                     'overlay-on' are applicable for now.
            startup: On future X server startups.  This change will modify the
                     X server configuration file if applicable.
        The default is 'now,startup', i.e., do both as applicable.
  --nobackup


Maybe
sudo aticonfig --effective=startup --set-powerstate=1
works?

---

### Post by unutbu on 2008-06-16
Try running 

```

cd /etc/X11
sudo cp xorg.conf xorg.conf-20080616
sudo aticonfig --effective=startup --set-powerstate=1
```
from the command line. See if it changes your xorg.conf:

```
cd /etc/X11
diff xorg.conf xorg.conf-20080616
```

If xorg.conf has been altered, edit rc.local by commenting-out the aticonf.sh script:

```

#touch /home/charis/aticonf-pre
#/home/charis/Scripts/aticonf.sh &
#touch /home/charis/aticonf-post
exit 0
```

reboot and see if works.

---

### Post by pb_online on 2008-06-16
When i type sudo aticonfig --effective=startup --set-powerstate=1
I get this...

Warning : Option 'PowerState' is exclusive, other options will be ignored.

What is that mean?

---

### Post by unutbu on 2008-06-16
In xorg.conf you have a section that looks something like
```

Section "Device"
   Identifier "something"
   Driver "radeon"  <-- or maybe Driver "fglrx" or "ati"
   Option "PowerState" "1"
   ...
EndSection
```

This is the section defines your video driver. The Option lines allow you to send extra options to configure the driver.

I don't have any experience with aticonfig, but what it sounds like is if you include 'Option "PowerState" "1"' then all other Options are ignored.

See
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
It may be of general use to you, and it also contains an example xorg.conf with the 'Option "Powerstate" "1"' line in it. 

One thing I find puzzling about that example xorg.conf is if Powerstate "1" is exclusive of all other Options, then why are there so many other Options there. It seems to me they'd all be meaningless...

---

### Post by pb_online on 2008-06-16
sudo nano /etc/X11/xorg.conf

I put Option "PowerState" "1" on the Section "Device"

I restart my pc and the state is in number 2 again.

Damn, nothing works at all :mad:

---

### Post by pb_online on 2008-06-17
Ok I found the solution.

There is a hidden folder in home directory, called ".kde"

I put the script on ~/.kde/Autostart and now it opens on boot :)

Thank you for your time my friend.

---

### Post by unutbu on 2008-06-17
That's great news. Hurray!

---

