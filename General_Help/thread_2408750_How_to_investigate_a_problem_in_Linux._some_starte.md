---
title: "How to investigate a problem in Linux. some starter tips needed, multiple questions?"
date: 2018-12-22
forum: General Help
---

### Post by saleb on 2018-12-22
I am a fresh Linux user. After almost two decades in the Windows environment, I switched to Linux a few days ago. I have used Linux in various other systems like LAMP VM or Raspberry Pi Ubuntu Mate, but never had it as software on the main machine. 

I am still learning about the users and groups, that is something that I should fully understand, as I want to make a clear system in which some similar functions administers the same account but not my main account. If there is some excellent resource that I can use to gain a deeper understanding, please share the link.

Also, I need a resource for understanding a debugging process in Linux. 

I have here some annoying situation. The system freezes up occasionally. I just lose keyboard and mouse and it stays there. In that state Caps lock does not change state, Alt+Tab, Ctrl+Alt+F1, Ctrl+Alt+F2, Ctrl+Alt+Del od nothing, but on one such occasion I had a video playing in Totem video app, the video continued without a hiccup. The only thing I could do was a hardware reset. 
So, how does one investigate such a problem? I assume some driver made a problem, probably somewhere is some log of activities, maybe even a crash report, something that does the same function as event type warning and critical, minidump, bsod code and task manager in Windows. I can ask to help me investigate, tell me what to type and which results to send here, but I am more interested to understand that whole process while solving this specific issue. 

There is also an annoyance connected to the user password. I understand, probably deeper than other windows users, the concept of user and password. I would not want to disable sudo password requests, just some of them. The system is set up to boot into my account without a password, that's cool. but then if it goes into sleep/lock mode, when you touch the mouse it asks for a password. Also, when starting Chrome, which has my account with all its passwords it asks for the Linux users password. These two instances I would like to disable, all the other sudo password requests should stay (we do not want that someone tries out rm -r * without the password request). 

Also, I need to understand how all the installation possibilities work. Is there a reason why some applications get installed in one way, and others in other? Is there a way to know how to install something without following the tutorial for that specific app. By now I have encountered at least three methods. There is a snap way that seems simple and elegant. Then there is a dpkg -i file.deb. Then there is unpacking of an archive. A repository installation (apt or apt-get install). And at the end there is a download source, type a ./configuration and make option that seems most archaic. 

Most annoying from all is packed archive. I have found a resource telling that, you should unpack and place the folder at an appropriate location (!?) How would I know what is appropriate? Should such a file go to /home, as visible or as .name, should it go in some folder outside /home. Some things ended up in /opt/ some other, who knows. What goes where?

How does one clean after himself? Should I write down how I installed something to uninstall it in the same way? I learned that things installed with apt-get install get removed with apt-get purge, but what happens with all the dependencies? I have also learned that make, cleans after itself if it was unsuccessful in whatever it tried to do. But, what happens with tar.gz, dpkg and snap installed items? 

That's all for now, I hope. Sorry for the long post, I just feel a bit overwhelmed at the moment. I remember how much time I needed to understand WinXp administration and bug tracking and I know that one cannot learn all of that in a weekend, but some general directions or articles/clips that could help further would be much appreciated at the moment. Thank you

---

### Post by CatKiller on 2018-12-22
Always install software from the repositories. Don't use a different method.

---

### Post by oldfred on 2018-12-22
Usually best to ask one unique question per thread and then have good title, so those who may know answer will respond. Many just review titles. Plus then others searching forum for answers can easily find [Solved] threads on a specific topic.

I think this is the setting I use, but I am using gnome-panel/fallback/flashback, so may not be same?
gsettings set org.gnome.desktop.screensaver lock-enabled false

What brand/model system?
What video card/chip?
Often video issues or overheating can cause unknown lockups. 

Is system up-to-date? Or UEFI/BIOS latest version from vendor. If SSD firmware most current version?

New users should only use repository for new software until more familiar with Linux. I prefer to use Synaptic as it gives more details. I almost never use Software Center.
sudo apt install synaptic

If software not found, you may want to consider other equivalent software as just about everything you could want in is repository.
But if wanting other software use a ppa, then .deb and auto install from that. 
I do not think I have ever compiled anything myself.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by saleb on 2018-12-22
> **oldfred said:**
> Usually best to ask one unique question per thread and then have good title, so those who may know answer will respond. Many just review titles. Plus then others searching forum for answers can easily find [Solved] threads on a specific topic.


Yes, I know, but it seemed to me as a new member kind of pointless to open three or five new threads. I am still a bit overwhelmed by all of this so I am not focused on one single thing.  
I actually started the thread about the freezing problem, and then all of the other things popped into my mind. I will follow the guidelines next time. 

gsetting seems to work. While researching what that code does I found a sweet little tool called dconf-editor which can help me understand what else there is (no I will not toggle randomly all the exposure settings, but it will be interesting to see what is available).

The machine is self-assembled. Asus X370-F, Ryzen 7, 16gb memory, Samsung 840Evo SSD, older Geforce GTX660 graphic, multiple ntfs hard drives. 

Overheating is not the problem, all the temperatures are in 50C range. I actually do not know the temperature now with Linux (I haven't yet time to play with and configure lmsensors). Right now it popped in my mind, I have to find something that shows the hard drive health and smart data. At the moment that is also not the priority. 

Graphics driver installed is the one available through apt-get, nVidia X Server, driver version 390.77, NV-Control version 1.29. Someone somewhere suggested this as a proper driver for Ubuntu 18.04 and discouraged the use of the newest nVIdia driver. Current nVidia driver version is 410.78 and is packed in a file with .run extension. 

It should be everything up to date. I really do not know about the SSD firmware. 
Another question about hardware is there something like the device manager, where I can see if all the drivers are installed and hardware works as it should? Does it happen that the system installs a wrong driver for something?

I have used Serviio network streaming solution in windows so I wanted their software here too. Their install instructions included sources and make, but there were some errors so I abandoned the idea and installed Emby .deb through dpkg which now works flawlessly. 

I have installed Synaptic, it opens some catalog-like graphic environment.

---

### Post by QIII on 2018-12-22
Please open five separate threads.  It will be much less overwhelming, not to mention less confusing for you and everyone interested in helping, if you were to get help for each issue individually.

---

### Post by CatKiller on 2018-12-22
> **saleb said:**
> I actually started the thread about the freezing problem, and then all of the other things popped into my mind. I will follow the guidelines next time. 

Your symptoms are a classic X/window manager hang. X controls the display, keyboard and mouse. The window manager controls the position and decoration of the windows. The application itself controls the contents of the window. I think; the division is something like that. Anyway, the inputs from the mouse and keyboard aren't getting through past either X or the window manager, but the application itself is still happily painting into the window that it's been given. Tricky to pin down exactly because the design of X is a bajillion years old, and Nvidia tend to do their own thing rather than what everyone else does. The implementation of X's replacement has been an uphill struggle.

[snip some stuff]

> Graphics driver installed is the one available through apt-get, nVidia X Server, driver version 390.77, NV-Control version 1.29. Someone somewhere suggested this as a proper driver for Ubuntu 18.04 and discouraged the use of the newest nVIdia driver. Current nVidia driver version is 410.78 and is packed in a file with .run extension.

Essentially, never ever run that. There is an ex-Windows user inclination to go, "oh, I'll just download a random thing off the Internet and run it." That isn't the way things work here. I suspect that file has been deliberately left as a pain in the **** to use specifically to discourage people from doing that.

The package manager is the way to install things. There are PPAs that you can incorporate into the package manager if you really, *really* need the latest version of some software.

> Another question about hardware is there something like the device manager, where I can see if all the drivers are installed and hardware works as it should? Does it happen that the system installs a wrong driver for something?

Only if you do it yourself by mucking around.

There are plenty of applications that will prettify the *display* of system information, but nothing for changing it. The drivers themselves are included in the kernel, or as kernel modules. It *is* possible to play around with the settings, but it's fairly arcane and you're very likely to simply break it.

The Device Manager was the thing I missed most in my first couple of months of using Linux.

> I have installed Synaptic, it opens some catalog-like graphic environment.

Synaptic shows all the packages that are available in the repositories you're using. It's useful to install things through that so that you develop a feel for how packages and dependencies and the like actually work. The App Store-like front ends obfuscate a lot of that detail, and don't include everything.

It sounds like you were a Windows Power User. Honestly, they have the hardest time getting over the hump, because they were comfortable fiddling with things in Windows and Linux seems so alien and weird. Once you really grasp that Linux is different to Windows, it all starts to fit together. You seem to be doing well so far; just keep asking questions.

---

### Post by oldfred on 2018-12-22
NVidia has a series of drivers. As a set of models gets older and cannot support new features a driver is frozen, only security updates. But a newer model driver installed with an older card may not work.
And with nVidia drivers, installing a new driver does not auto uninstall old driver, you must manually purge old driver before installing new driver. Do not install .run driver from nVidia. If you get a new nVidia card purge old driver, and add ppa to get newest drivers that are pre-configured to work with Ubuntu.

You might want to add a kernel ppa, to get newer kernels than are in default 18.04.
       Gigabyte B450 Ryzen needs kernel & mesa drivers
[https://ubuntuforums.org/showthread.php?t=2408247](https://ubuntuforums.org/showthread.php?t=2408247)
Asus B350M-A needs newer kernel that 18.04 default
[https://ubuntuforums.org/showthread.php?t=2391892](https://ubuntuforums.org/showthread.php?t=2391892)
[https://ubuntuforums.org/showthread.php?t=2390660&p=13799816#post13799816](https://ubuntuforums.org/showthread.php?t=2390660&p=13799816#post13799816)

---

### Post by saleb on 2018-12-23
> **CatKiller said:**
> Your symptoms are a classic X/window manager hang. X controls the display, keyboard and mouse. The window manager controls the position and decoration of the windows. The application itself controls the contents of the window. I think; the division is something like that. Anyway, the inputs from the mouse and keyboard aren't getting through past either X or the window manager, but the application itself is still happily painting into the window that it's been given. Tricky to pin down exactly because the design of X is a bajillion years old, and Nvidia tend to do their own thing rather than what everyone else does. The implementation of X's replacement has been an uphill struggle.



Just one follow up question on this matter, and then I'll close this thread. Assuming you are right, then I should be able to setup ssh and access from outside with telnet, restart X and everything would continue to work, right? 

It seems that systemctl restart display-manager should do the trick. 

On the other matter. Yes, I am a kind of a power user for WinXP and W7. When new hardware arrived and forced me to W10, I was less power user and more ](*,) user, so something needed to change. This was the best thing I could think of.

---

### Post by vidtek on 2018-12-23
Saleb-

You are definitely on the right track, coming here to ask the questions, there is a wealth of people here with in-depth knowledge of the system.  For instance, Oldfred is the guru of booting issues, grub and partitioning problems.

I have tried many different flavours of linux over the years, starting with Red Hat in 1996 and always come back to Ubuntu.  Catkiller is right, Device Manager is the one piece of Windows I still occasionally miss.  There is no direct equivalent, although settings manager in KDE comes the closest in my opinion.  

It is *very* easy to break a system in linux messing about with stuff you only 1/2 (1/4?) understand, all of us still do that on regular occasions.  After repeated installations after breaking stuff, I discovered a cli (command-line-interface) application fsarchiver.  It is in the repositories and it has saved my bacon on many occasions.  There is also a graphical version qt5-fsarchiver.
With this you can take a snapshot of your system and home partitions and restore them as they were before you borked it.  
I personally use Kubuntu because I love the eye candy and the usefulness of many of its facilities, multiple desktops on multiple activities to separate out the various things I do at any one time.  It also has kdeconnect for easy connections to your smartphones and tablets, plus the wonderful settings manager.  With other systems you will have to use the cli and various commands such as dmesg, which shows you your hardware in very detailed form.
As a hint, you can use this form of the command to limit the massive amount of output dmesg gives you: 
dmesg | grep saa  
is one I use to check my tuner cards, this command will search dmesg for anything with saa in the output.
dmesg | grep usb   
will just give information on your usb ports and their assignments.
dmesg is a very powerful tool in your linux arsenal.
Another useful utility is Double Commander, a dual-pane xtree style file manager in the repositories that can be run as root.  Be careful what you do when running it as root, it is very easy to stuff up!

The best of luck to you, keep coming back here and we will all do our utmost to assist you.
Tony.

---

### Post by Impavidus on 2018-12-23
> **saleb said:**
> 
The machine is self-assembled. Asus X370-F, Ryzen 7, 16gb memory, Samsung 840Evo SSD, older Geforce GTX660 graphic, multiple ntfs hard drives. 

NTFS-formatted hard drives in a Linux-only system are a bad idea. Linux can read and write NTFS partitions, but cannot fix them if they are broken. I suggest you only use a Linux-native format, like ext4.

---

### Post by CatKiller on 2018-12-23
> **saleb said:**
> Just one follow up question on this matter, and then I'll close this thread. Assuming you are right, then I should be able to setup ssh and access from outside with telnet, restart X and everything would continue to work, right? 

In principle, yes, but don't use telnet. There is minimal overhead from using SSH. You can even use SSH from a phone if you don't have a second computer handy. Depending on exactly where in the stack the problem is, you might still be able to use Ctrl-Alt-F2 to get to a TTY to give it a kick, too.

---

### Post by saleb on 2018-12-23
@vidtek
I have enjoyed reading your message. My previous contacts with Linux included snapshots. I was in Windows, Linux was in VM, before each installation or configuration there was a snapshot. Whenever something goes wrong the vm is returned to the previous state and another approach tried, but it's more challenging when Linux is the main system. The approach with the fisarchiver is a nice solution and I will familiarize myself with it. When I first started a few days ago I found some representation of task manager called Stacer, that was the moment when I realized that there is no Device Manager. 
Thanks for the dmesg, I did not know of it, the only similar command that I knew of is lshw, and those other ls commands, but of that one, I did not know for that one. 

@Impavidus:
I know that any mismatch between so different technologies is bad in the long run, but this is one of the things that cannot be changed at the moment. The ntfs drives are all over 80% full data drives. I have about a month available to familiarize myself with the basics of Linux which would include virtual Windows inside Linux in contrast to the other way around that was until now. If I choose Linux, gradually transfer all data into Linux format and implement something like Snapraid, but if get forced to go back to Windows it is better that data disks remain ntfs for now.

Thank you all

---

