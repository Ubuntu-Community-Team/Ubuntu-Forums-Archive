---
title: "Ubuntu doesn't like my 8800gts"
date: 2007-05-11
forum: General Help
---

### Post by HPCE_Larry on 2007-05-11
I know this has been mentioned before, but the answers given exceed my current understanding of ubuntu. I have the latest dvd version. I boot off that and am presented with a screen that gives the options "Start or Install Ubuntu" "Install in text mode" "Install in OEM mode" "Start in safe graphics mode" and other stuff not related to installing. 

I've tried the first option, but it leads to a graphics error. What do I need to do to make it work?

---

### Post by Loki-uk on 2007-05-11
You need to install in text mode. Once it has booted you might find the screen display is corrupted or you get a black screen, don't worry this is fine. Hit CTRL + ALT + F1 to swicth to a command line then use the command 'dpkg-reconfigure xserver.org' answer all the questions when asked what video card to use select 'vesa' and run through to the end of the questions. Reboot, login and then download the nvidia drivers and follow one of the many threads in this forum to install them.

Loki

---

### Post by m.musashi on 2007-05-11
You can try installing in text mode. The 8800 cards might be too new to have support yet (although that's just a guess). If you can install in text mode you can then try installing the proprietary driver from nvidia (assuming they have one out for the 8800 cards).

EDIT: damn, too slow. Do what Loki-uk said. Those are better instructions anyway.

---

### Post by HPCE_Larry on 2007-05-11
I've installed it, and I rebooted. I reach a screen that tells me to login (text screen, no gui). I type in my username and hit enter. It then tells me to put in my password. I type and nothing apears on the screen. I hit enter and now I can type on the line below the one that asks for the password. I type my password and it says the login is invalid. What do I do?

---

### Post by m.musashi on 2007-05-11
It never shows you the password or any ***. If it works you get a command prompt. If not you get an error. It sounds like you got logged in so you should be good to go. Follow the steps above to get a gui and then install the nvidia driver.

---

### Post by HPCE_Larry on 2007-05-11
I get an error. I don't see any ******'s.

---

### Post by m.musashi on 2007-05-11
Right. When you type your password, it doesn't show anything. Just type it and if it's correct you will get a command prompt. That means you are logged in. You can then do anything you need to. Once logged in, if you type something that is not a valid command you will get an error. That is normal. You just have to type valid linux commands. For example, type
```
sudo dpkg-reconfigure xserver.org
```
The first part, "sudo" says you want to execute the following command as an administrator (called root in Linux). It will ask for your password again. Use the password you chose when you installed. Sometimes sudo won't ask for a password if you just did something with it. It remembers you are acting as root for 15 minutes or so. It will then execute the command. In this case, it will let you reconfigure the display driver (called X). It will ask a bunch of questions and you will have to give the best answer for your hardware. Be sure to choose "vesa" for the graphics driver. It is the most compatible with the most hardware.

When that finishes, type
```
startx
```
That should load the gui. Given how new the 8800 cards are this may or may not work.

---

### Post by sdil on 2007-05-12
I thinks you should use [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by HPCE_Larry on 2007-05-13
@m.musashi: Thanks. I'll try that.

@sdil: That program assumes I have access to a gui. I dont', so it can't really help me.

---

### Post by orb9220 on 2007-05-13
> @sdil: That program assumes I have access to a gui. I dont', so it can't really help me.

Nope it runs from command line or gui.
You can get the commands and paste them in to retrieve and install then run **envy**

But since you are stuck you would have to run a command line browser like lynx or boot up it recovery mode or a liveCD

---

### Post by m.musashi on 2007-05-13
Actually, if you want to try envy you should be able to once you are logged in after booting in text mode. I'm not 100% sure, but I think this will work
```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.3-0ubuntu2_all.deb
sudo dpkg -i envy_0.9.3-0ubuntu2_all.deb
```
This may produce some errors about dependencies. If so, do
```
sudo apt-get install -f
```
and then run it in text mode
```
 sudo envy -t
```

---

### Post by HPCE_Larry on 2007-05-13
Ok I typed in sudo dpkg-reconfigure xserver.org and was told that xserver.org was not installed.  What does that mean, and what should I do?

---

### Post by m.musashi on 2007-05-13
Oops. I think it's supposed to be
```
sudo dpkg-reconfigure xserver-xorg
```
Sorry about that.

---

### Post by HPCE_Larry on 2007-05-14
Ah, that works much better. Still having some trouble. I reach a point where it asks about what bit color to use. I specify 24, and am then brought back to the text world with this error
```

xserver-xorg postinst warning: overwriting possibly customized configuration file; backup in /etc/X11/xorg.conf .20070514160234

```

What does this mean?
BTW, how do I shutdown in text mode with less than a 1 min wait time.

EDIT: lol, nvm. that meant it worked. I now have a giu. New problems are presenting themselves though. My screen runs at 1440x900 and I deffinitally selected that option when installing. However, thats not an option in the change resolutions setting. only the usual 1024x768, 800x600, 640x480 What do I do to add the resolutions?

EDIT2: I downloaded the linux drivers from nvidia. I follow their instructions to type ```
sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
``` I typed that and i got an error.

---

### Post by srt4play on 2007-05-14
That is not an error, just informing you that it overwrote the config file.  Run this:

sudo /etc/init.d/gdm restart
 
and see if you have a gui now.

To shutdown immediately in text mode:

sudo shutdown -h now

---

### Post by HPCE_Larry on 2007-05-14
Thanks, I realized that in a minute. The edits of my post I'll just restate here.

I now have a giu. New problems are presenting themselves though. My screen runs at 1440x900 and I deffinitally selected that option when installing. However, thats not an option in the change resolutions setting. only the usual 1024x768, 800x600, 640x480 What do I do to add the resolutions?

 I downloaded the linux drivers from nvidia. I follow their instructions to type ```
sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
``` I typed that and i got an error.

---

### Post by m.musashi on 2007-05-14
I think you need to prefix that with "sudo" but not 100% sure.

BTW, you might want to give envy a try. I've had good luck with it (on edgy) and it could save you a whole lot of trouble.

---

### Post by HPCE_Larry on 2007-05-14
I downloaded envy but it complains about dependency problems when I try to install it.

---

### Post by m.musashi on 2007-05-14
After you install, type
```
sudo apt-get install -f
```
That should fix the dependencies.

---

### Post by HPCE_Larry on 2007-05-15
Ok I ran envy and get the following bit at the end ```
Errors were encountered while processing:
 nvidia-glx
rm: cannot remove `*.asc': No such file or directory
rm: cannot remove `/usr/share/envy/*.deb': No such file or directory
rm: cannot remove `/usr/share/envy/*.asc': No such file or directory
rm: cannot remove `/usr/share/envy/*.changes': No such file or directory
Traceback (most recent call last):
  File "interface.py", line 20, in <module>
  File "/usr/share/envy/instun/objects.py", line 942, in mainmenu
  File "/usr/share/envy/instun/interfaceclasses.py", line 57, in process
  File "/usr/share/envy/instun/objects.py", line 848, in nvinstconfirm
  File "/usr/share/envy/instun/objects.py", line 149, in nvidiainstall
  File "/usr/share/envy/instun/objects.py", line 126, in nvidiainstall2
  File "/usr/share/envy/instun/classes.py", line 912, in nviconadd
  File "/usr/lib/python2.5/shutil.py", line 80, in copy
    copyfile(src, dst)
  File "/usr/lib/python2.5/shutil.py", line 46, in copyfile
    fsrc = open(src, 'rb')
IOError: [Errno 2] No such file or directory: '/usr/share/envy/nvidia-settings.desktop'

```
So presumably this won't work now? Whats the issue?

---

### Post by HPCE_Larry on 2007-05-15
ok sorry for the double post but I've had an epiphany thats led to a new set of issues. How do I shutdown the xserver? The nvidia drivers say i have to.
I booted in recovery mode which apeared to be what it was asking for. However, it could not find/compile my kernel interface. So they won't work.

My issues with envy (to quote from my last post), are ```
Errors were encountered while processing:
 nvidia-glx
rm: cannot remove `*.asc': No such file or directory
rm: cannot remove `/usr/share/envy/*.deb': No such file or directory
rm: cannot remove `/usr/share/envy/*.asc': No such file or directory
rm: cannot remove `/usr/share/envy/*.changes': No such file or directory
Traceback (most recent call last):
  File "interface.py", line 20, in <module>
  File "/usr/share/envy/instun/objects.py", line 942, in mainmenu
  File "/usr/share/envy/instun/interfaceclasses.py", line 57, in process
  File "/usr/share/envy/instun/objects.py", line 848, in nvinstconfirm
  File "/usr/share/envy/instun/objects.py", line 149, in nvidiainstall
  File "/usr/share/envy/instun/objects.py", line 126, in nvidiainstall2
  File "/usr/share/envy/instun/classes.py", line 912, in nviconadd
  File "/usr/lib/python2.5/shutil.py", line 80, in copy
    copyfile(src, dst)
  File "/usr/lib/python2.5/shutil.py", line 46, in copyfile
    fsrc = open(src, 'rb')
IOError: [Errno 2] No such file or directory: '/usr/share/envy/nvidia-settings.desktop'
``` and so it doesn't work.

My issue with nvidia drivers is a lack of kernel interface. Which can be fixed, and how?

---

### Post by m.musashi on 2007-05-15
Hmmm, I'm not familar with the errors you are getting with envy. You might want to post that as a separate question in order to get more feedback or check [here](http://ubuntuforums.org/showthread.php?t=432056). As for stopping X there is a command but if you are not in a gui it won't matter (i.e. booting recovery mode). Also, the envy site says it's no longer necessary but who knows. Anyway, you can stop it by typing
```
sudo /etc/init.d/gdm stop
```

Another thought is that it's possible you need the development tools installed. I didn't see anything on the envy site saying this but I guess it couldn't hurt. I do know that you need them if you install from the nvidia package. To install them do
```
sudo apt-get install build-essential
```
Hang in there. You are making progress (even if it doesn't feel like it yet) and you will feel quite happy when you finally get this to work. I had a lot of problems when I first switched and fixing them is what taught me most of what I now know.

---

### Post by HPCE_Larry on 2007-05-16
any idea what this kernel interface thing the nvidia drivers are talking about is?


EDIT: YES!!! I reinstalled linux and now everything works.... Envy got the driver, everything looks great. I'm happy. Now to make wine work...

Thanks for all your help everyone, I've learned tons.

---

### Post by m.musashi on 2007-05-16
Glad to hear it worked. I was getting pretty low on ideas :).

---

