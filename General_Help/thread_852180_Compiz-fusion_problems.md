---
title: "Compiz-fusion problems"
date: 2008-07-07
forum: General Help
---

### Post by painterh on 2008-07-07
Hello;
I am running Ultimate Edition 64bit and have a major problem.  I recently tried to install plugins for additional effects (ie; desktop on a cylinder).  This started a chain of events in which apparently made some bad choices.  The plugins may have not been intended for 64 bit systems.  Anyway, here is where I stand.  I became unable to use desktops effects at all, and reasoned that the best course was to uninstall compiz-fusion and all dependencies and start fresh.  This did not work out well.  For some reason, when I reinstalled compiz-fusion (using synaptic), I was unable to enable plugins because they would uncheck themselves as soon as they were selected.  I first checked my Nvidia driver, and removed and re-installed using Envy first, and when that didn't work I used synaptic.  No sucess.  Currently I have no desktop effects at all.  In fact if I try to enable them in the appearance tab, all I get is a white screen.  I am currently using failsafe mode Gnome to write this, because I made the mistake of trying the command (in terminal) compiz --replace.  Now when I boot up and try to log into Gnome normally, all I get is a white screen (except for "failsafe").  I went through a real headache installing video drivers.  When I finished installing drivers using "Envy" or synaptic, it wouldn't recognize my video card on startup and kept throwing me into "low graphics mode".  I finally found a tutorial of how to install using the latest package from Nvidia website, however, I now have a situation such that if I check for Restricted drivers in use,  It says "no restricted drivers in use on this system".  I am at wits end with this.  I would like to have the nice desktop effects, but I am not going through a complete reinstall to get them.  If anyone has time and expertise to dialog with me about this,I would greatly appreciate it.  It seems for now I am stuck using my system in "failsafe Grome", or th other OS I dual-boot with, (you know That Microsoft product with xp on the end). Thanks in advance for anyones help.

---

### Post by estyles on 2008-07-07
You may have tried this, but when you start Gnome in normal (not failsafe) mode, can you use Alt+Ctrl+F1 to get a terminal window?  If so, then you can log in there, and use "metacity --replace", and you should at least be able to use Gnome normally, although without any visual effects, and troubleshoot your problem further from there.

Other than that, I'm not much help, but consider this a bump.

---

### Post by Tomatz on 2008-07-07
Try this:

```
sudo apt-get remove --purge nvidia*
```

Then
```

sudo apt-get install nvidia-glx-new
```

Reboot

---

### Post by painterh on 2008-07-07
> **Tomatz said:**
> Try this:

```
sudo apt-get remove --purge nvidia*
```

Then
```

sudo apt-get install nvidia-glx-new
```

Reboot

Thanks;  I did that and it did get me back to native resolution on monitor.  I still see no restricted drivers listed in restricted driver manager.  Those are required to enable desktop effects.  I think I have a much more difficult task rebuilding compiz-fusion and advanced desktop effects.  According to synaptic, I have compiz-fusion, plugins and Icon installed, however none of them seem to work.  I don't know what's going on.

---

### Post by Tomatz on 2008-07-07
> **painterh said:**
> Thanks;  I did that and it did get me back to native resolution on monitor.  I still see no restricted drivers listed in restricted driver manager.  Those are required to enable desktop effects.  I think I have a much more difficult task rebuilding compiz-fusion and advanced desktop effects.  According to synaptic, I have compiz-fusion, plugins and Icon installed, however none of them seem to work.  I don't know what's going on.

Check in synaptic to see if **nvidia-glx-new** is installed.

If it is run the following command in a terminal and post the output:

```
compiz --replace
```

---

### Post by painterh on 2008-07-07
> **Tomatz said:**
> Check in synaptic to see if **nvidia-glx-new** is installed.

If it is run the following command in a terminal and post the output:

```
compiz --replace
```

This is what I got

~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by Tomatz on 2008-07-07
Open a terminal and type:

```
sudo nvidia-xconfig
```


**_Reboot_** and run **compiz --replace** again.

;)

---

### Post by painterh on 2008-07-07
I forgot to mention that Nvidia-glx-new is installed and shows such in synaptic.

---

### Post by Tomatz on 2008-07-07
> **Tomatz said:**
> Open a terminal and type:

```
sudo nvidia-xconfig
```


**_Reboot_** and run **compiz --replace** again.

;)

Was sure it would. Just do the above now ;)

---

### Post by painterh on 2008-07-07
when I ran nvidia-xconfig and rebooted, it threw me right back to 600x800 low graphics mode after reboot.   Should I still use the "purge nvidia command and install nvidia-glx-new using apt-get at this point, and reboot?

---

### Post by Tomatz on 2008-07-07
> **painterh said:**
> when I ran nvidia-xconfig and rebooted, it threw me right back to 600x800 low graphics mode after reboot.   Should I still use the "purge nvidia command and install nvidia-glx-new using apt-get at this point, and reboot?

Yeah purge and reinstall and that should get your resolution (drivers) back to normal.

I'm going to bed now as its late in the UK but i'll check back tomorrow ;)

---

### Post by painterh on 2008-07-07
Great.  Thanks for the help.  I happen to have some in-laws that live in Cambridge.  My wifes from Scotland.  Anyway, I'll post tomorrow.  Thanks again.

---

### Post by painterh on 2008-07-07
If anyone else knows why reinstalling drivers would continue to result in com --replace command returning the following, please feel free to post.

harlund@harlund-desktop:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by estyles on 2008-07-07
I'm pretty sure the answer to your problem is somewhere in this thread: [http://ubuntuforums.org/showthread.php?t=596927](http://ubuntuforums.org/showthread.php?t=596927)

---

### Post by Tomatz on 2008-07-08
Try this:


```
sudo apt-get install nvidia-settings
```

Then 

```
sudo nvidia-xconfig
```

**Reboot** Then:

```
gksu nvidia-settings
```

Then **set your screen resolution in nvidia-settings and _save_ (write to xconfig)**

**Ctrl Alt Backspace**

Hope that helps ;)

---

### Post by painterh on 2008-07-08
Well its 6:00 a.m. here and I am going to try a few more things.  I ran the commands exactly as written above and this is what I got.

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

This is what came up when the nvidia-settings app loaded.  I've seen this message.FAR too many times.  I checked in my /etc/X11 folder and noticed that because of all the messing I've done in the last couple days, I now have 39 different xorg.conf files in there.

---

### Post by painterh on 2008-07-09
First I have to say thanks for all the help I received in this forum. As always this has been a great place to get help. Here is where things are today; I completely purged every trace of Nvidia drivers, and Compiz, then I used Envy (which I had never liked very much), to install my Nvidia drivers, and installed compiz using Git.  It took quite a while to download and compile, but I am happy to say that I have Compiz-fusion working and I really like the new effects (ie. deformation/cylinder or sphere).  the only "little" glitches I've noticed is that I can't enable the fusion splash screen, and for some reason, the Emerald title bar for the compiz settings window always seems to be covered by the top panel.  It seems to be the only window that it is affected this way.  But I can live with that, since it has a large close button at the bottom. Again, thanks to all who posted on this topic.

---

