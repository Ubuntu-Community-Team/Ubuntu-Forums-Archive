---
title: "Maintenance, Services, System Monitor, Oh My!"
date: 2008-04-17
forum: General Help
---

### Post by AdrianStrays on 2008-04-17
A few little things:

In Windows "ctrl-alt-delete" brings up task manager, how do I make linux bring up System Monitor using the same hotkeys?

I was looking through the services, and I noticed a thing about logging computer activity.  What exactly does Linux log?

Windows takes maintenance, cleaning out temp files, cleaning out the registry, removing unwanted files, defragging and what not.  I know Linux doesn't need defrag, but is there any sort of cleaning up I need to do? From messy installs or prolonged usage?

---

### Post by sekinto on 2008-04-17
> In Windows "ctrl-alt-delete" brings up task manager, how do I make linux bring up System Monitor using the same hotkeys?

Depends on what desktop environment you are using.

> I was looking through the services, and I noticed a thing about logging computer activity.  What exactly does Linux log?

A lot. /var/log contains most of the log files if you want to check them out.

> Windows takes maintenance, cleaning out temp files, cleaning out the registry, removing unwanted files, defragging and what not.  I know Linux doesn't need defrag, but is there any sort of cleaning up I need to do? From messy installs or prolonged usage?

Uninstalling unwanted apps.
Cleaning up personal files.
Clean out /tmp.
Checking disk for errors.

---

### Post by ibuclaw on 2008-04-17
> **AdrianStrays said:**
> A few little things:

In Windows "ctrl-alt-delete" brings up task manager, how do I make linux bring up System Monitor using the same hotkeys?

I was looking through the services, and I noticed a thing about logging computer activity.  What exactly does Linux log?

Windows takes maintenance, cleaning out temp files, cleaning out the registry, removing unwanted files, defragging and what not.  I know Linux doesn't need defrag, but is there any sort of cleaning up I need to do? From messy installs or prolonged usage?

a) You can install a key binder and link the key command to "gnome-system-monitor"
Though I'll doubt you ever need it. You can just click on the Close Button in an Applications window and choose "Force Quit".

b) Logs tell you everything that Linux is doing from the moment the kernel in initiated.
This can help you spot errors or find programs or services that you don't want to start in the startup script.

c) The Linux terminal command
```
 sudo apt-get clean 
```
Is all the cleaning you pretty much have to do.

You could also open synaptic and go into "Status>Not Installed (Residual Config)" and select all the packages displayed to be "Completely Removed"
This removes any excess config files of packages that are no longer installed on your computer.
[[IMG]http://img258.imageshack.us/img258/8167/screenshotsynapticpackamb7.th.png[/IMG]](http://img258.imageshack.us/my.php?image=screenshotsynapticpackamb7.png)


To fix any broken installs
```
 sudo apt-get install -f 
```

Other than that, you can't really do much else. There is no registry in Linux.
And because of the way the filesystem scatters the files across the hard drive, it is very unlikely that fragmentations will occur.

Regards
Iain

[EDIT]
A kind fellow Ubuntuer has also made an App called QuickStart.
It can do all sorts of things such as Backup precious content, Install Common Codecs/Apps and House Cleaning all for you.
It's a great tool for people new to Ubuntu who still have the Windows craving to go always round looking for something to fix. (When there is really nothing to do but **use** your computer)
Anyway, here is the thread with the file on.
[http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)

Enjoy!

---

### Post by AdrianStrays on 2008-04-17
> Though I'll doubt you ever need it. You can just click on the Close Button in an Applications window and choose "Force Quit".


Eh, firefox has a weird habit of being running yet having no window.  Normally I force it out using Task Manager, but now on Ubuntu I ended up unconsciouslly logging out when I press ctrl-alt-delete.  Very annoying, but thanks for the tip!

> QuickStart
I downloaded this, but I didn't see anything in regards to cleaning up installations, I assume I still need to do that manually? What about programs not installed via Synapatic. 

I also have an additional question, in regards to firewalls and virus scanners.  I was under the impression Ubuntu has a built in firewall, is that true?  Is there any reviews of it online? Can I replace it?

Do I need a virus scanner?

---

### Post by AdrianStrays on 2008-04-18
Bump

---

### Post by Sonicgoo on 2008-04-20
I used the info in this thread to help do some clean up on my computer. So I thought I would help out by answering. 

> 
Eh, firefox has a weird habit of being running yet having no window. Normally I force it out using Task Manager, but now on Ubuntu I ended up unconsciouslly logging out when I press ctrl-alt-delete. Very annoying, but thanks for the tip!

There is a graphical **system monitor** under System Administration, I don't think that there is a hotkey for it but I'm sure that you could assign one.

I'm not exactly sure how to add the shortcut but you can find it here

[https://help.ubuntu.com/community/MappingWindowsKey?highlight=%28shortcuts%29](https://help.ubuntu.com/community/MappingWindowsKey?highlight=%28shortcuts%29) 

> 
I also have an additional question, in regards to firewalls and virus scanners. I was under the impression Ubuntu has a built in firewall, is that true? Is there any reviews of it online? Can I replace it?

Ubuntu is a closed system but it does not automatically have a firewall, so if your not already behind some kind of firewall router etc. you may want to set one up. 

[https://help.ubuntu.com/community/Firestarter?highlight=%28firewall%29](https://help.ubuntu.com/community/Firestarter?highlight=%28firewall%29)

Check out the security guides for further information

[https://help.ubuntu.com/community/Security?highlight=%28firewall%29](https://help.ubuntu.com/community/Security?highlight=%28firewall%29)

> Do I need a virus scanner? 

There aren't any know virus's for Ubuntu that I am aware of so the only reason that you would need virus software is to protect windows users from emails. 

The package that you are trying to install open up synaptic and search for it there then check it for install.

p.s. most of the questions that you are asking are in the documentation and already posted in the forums, please search for the answer before asking, thanks.

---

### Post by le singe on 2008-07-14
I know it's been a few months since you posted this, but I was wondering the same exact thing.  In Ubuntu Hardy if you right click the panel, and go to Add to Panel...

a Force Quit item should turn up.  I haven't tried it out, but it might be what you're looking for to deal with nonresponsive programs, if you're still looking.

---

