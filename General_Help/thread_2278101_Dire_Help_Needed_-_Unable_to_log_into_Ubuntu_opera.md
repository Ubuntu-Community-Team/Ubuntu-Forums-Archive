---
title: "Dire Help Needed - Unable to log into Ubuntu operating system, at all"
date: 2015-05-13
forum: General Help
---

### Post by elvis6 on 2015-05-13
The problem started when I was using Synaptic Manager. My goal was to remove some previous system updates that I did not want.
In the process of this, I must have inadvertently checked the wrong box(es), and in the status box, I could see it installing some things I did not want installed, so I hit "cancel". I assumed this would cut off everything. But then the status box, showed that it was removing a whole bunch of things that I did not want to be removed, so I had a "novice moment", and literally reached for the plug, and unplugged the machine completely, out of desperation.

So, apparently I did some damage to necessary system files, either while in Synaptic Manager, or due to my "sudden forced crash" of the PC, by unplugging it during that process, because now I am completely unable to log into the system.

When I reboot or start the PC, I get to the login page, I type in my password, and then the screen flashes. as if it's going to log me in, but then it goes back to the log in page. There's no message about an incorrect password, and no error message at all. It's like it just refreshes back to the log-in screen. So I tried to log in as a Guest. And I get the same response.

Somehow, I must have inadvertently deleted some necessary system files.
I do not want to have to do a complete re-install because I will lose a lot of important, unsaved data.

When I reboot, there is an option to into recovery mode.
When I go there, the options I have are 
- Clean
- Repair Broken Packages
- Run in failsafe graphic mode
- Check all file systems
- Update grub bootloader
- Enable networking
- Drop to root shell prompt
- System Summary

Will any of those options help ?

Thanks in advance

---

### Post by elvis6 on 2015-05-13
Update on my attempts to resolve this ^

I randomly tried a couple of those options in recovery mode, and it was unable to complete them due to the following error messages :

- could not resolve security.ubuntu.com
- could not resolve archive.ubuntu.com
- problem activating swap: host/ubuntu/disk fsckfrom util-linux 2.20.1 skipping - it appears to have holes 
- could not write bytes : broken pipe
- try the following apt-get update or --fix-missing

I havn't tried the last suggestion, because I'm not sure how to open up a command line to try it from where I'm at.
Please, someone tell me there's a way that I can update any missing or damaged files, without having to log in normally, since I'm uunable to do that.

---

### Post by cariboo on 2015-05-14
When starting in recovery mode, you must enable networking first before running Repair Broken Packages.

---

### Post by elvis6 on 2015-05-14
> **cariboo said:**
> When starting in recovery mode, you must enable networking first before running Repair Broken Packages.

Thank you very much for the response and the tip.
I went ahead and enabled networking, and then went through the recovery mode again, and selected "repair broken packages".

It seemed to complete the task with no noticeable issues, and at the end, before exiting recovery mode, it stated "Some graphic drivers require a full graphical boot and so will fail when resuming from recovery. If that is the case, simply reboot from login screen and then perform a standard boot"

So, when I got back to the login screen, I was still having the exact same problem.
Based on the above message, I clicked restart from the there, and when it rebooted back to the login screen, I was once again having the same issue of not being able to log into the operating system.

Did I misunderstand the above message about rebooting ? Is it more then just a basic re-start ?
Or is there another step in recovery mode menu that I can take, to fully recover from this ?

---

### Post by elvis6 on 2015-05-14
So, now besides Repairing Broken Packages, I've also run the options for "check all file systems" and "Clean" and "Update Grub Bootloader"
So, the only options I havn't tried in Recovery Mode is "run in failsafe graphic mode" or "drop to root shell prompt"
What else can I do ?
I originally used WUBI to install a dual OS on the PC. Is there a way to use a "Repair" option on that install file ?
Or is there any other way to get updates I need to restore the system ?

---

### Post by elvis6 on 2015-05-14
If none of the above options is possible, is it possible to back up my data (files and internet bookmarks) without being able to log in ?

---

### Post by cariboo on 2015-05-14
It looks like you have a graphics driver problem, what make model graphics card do you have, and have you tried installing a proprietary driver?

---

### Post by elvis6 on 2015-05-14
> **cariboo said:**
> It looks like you have a graphics driver problem, what make model graphics card do you have, and have you tried installing a proprietary driver?

The graphics card is an Intel(R) 82945G Express Chipset Family.
Since I have dual OS, I can get into Windows, and I have no issues there, so if there was a graphics card problem, wouldn't it also create problems with the other OS ?
I havn't tried the proprietary driver option. I'm not sure where to start with that

---

### Post by QIII on 2015-05-14
Not the card, but the *driver.  *

Drivers are used by the OS and are different between the two.  Two OSes don't share drivers.  Having a driver installed on one OS has no effect on the other.

That said, the Intel driver should already be rolled into the kernel except for some rare cases.

---

### Post by elvis6 on 2015-05-14
> **QIII said:**
> Not the card, but the *driver.  *

Drivers are used by the OS and are different between the two.  Two OSes don't share drivers.  Having a driver installed on one OS has no effect on the other.

That said, the Intel driver should already be rolled into the kernel except for some rare cases.

I understand.
I honestly don't know what graphics driver it is, especially since I cannot sign into my Ubuntu system.
Is there a way I can determine that from the "Recovery Menu" ?
Also, how would I install a proprietary driver from the Recovery Menu ?
I did a search and it looks like I go to "root shell prompt", is that correct ?

---

### Post by sandyd on 2015-05-14
What edition of Ubuntu are you using?

Try:

For Ubuntu:
```

sudo apt-get install ubuntu-desktop
```

For Lubuntu:
```

sudo apt-get install lubuntu-desktop
```

For Xubuntu:
```

sudo apt-get install xubuntu-desktop
```

For Kubuntu:
```

sudo apt-get install kubuntu-desktop
```

---

### Post by Geoffrey_Arndt on 2015-05-14
Also, use your windows system to download a live Linux distro.  If you go to "distrowatch.com", you can find several.   I think the "Porteus" distro is fast and easy to setup your own custom iso from their website.   That iso can then be burned to either a CD or a USB Flash-stick.   

After doing that, you can boot into your PC using the Live Linux OS (Porteus) or (Partition Magic) etc.   This allows you to use the file manager program to mount and access your file system that you had in Ubuntu (unless the file system is totally hosed or the hardware is damaged).

You wrote you used "Wubi" to setup a psuedo-dual-boot.   As info, Wubi is no longer supported or recommended.   SO . . what that means is you should thing about doing a normal full dual-boot using an Ubuntu 14.04.2 iso (or any other linux or buntu flavor that you want).   Ask if needing more info . . .

---

### Post by elvis6 on 2015-05-16
> **sandyd said:**
> What edition of Ubuntu are you using?

Try:


For Xubuntu:
```

sudo apt-get install xubuntu-desktop
```



I appreciate this, as well as all the other suggestions everyone has made.
I would like to try this one first, because it seems the simplest, and I am extreme novice.
I am using Xubuntu.
But my question is, how do I get into the command terminal to type the commands you suggested, from the Recovery Menu ?

---

### Post by deadflowr on 2015-05-16
> **elvis6 said:**
> I appreciate this, as well as all the other suggestions everyone has made.
I would like to try this one first, because it seems the simplest, and I am extreme novice.
I am using Xubuntu.
But my question is, how do I get into the command terminal to type the commands you suggested, from the Recovery Menu ?

Follow the advice of enabling Networking after which you then enter the Root Shell and run the command, but exclude sudo, since you will already be root.
so instead of
```
sudo apt-get install xubuntu-desktop
```
just do
```
apt-get install xubuntu-desktop
```
simple as that.

You need to enable Networking to grab the packages, and also, by enabling networking first, the root shell will be rest to read/write; otherwise it would be set as read-only and read-only mode would mean that anything you tried, such as installing new packages, would fail.

Simply clicking on the Networking option should be all you need to do, it should set itself automatically.
If it hangs there, then something is most probably wrong.
If it returns to the recovery mode menu, then networking should now be up and running.

Hope this helps

---

### Post by elvis6 on 2015-05-17
> **sandyd said:**
> What edition of Ubuntu are you using?

For Xubuntu:
```

sudo apt-get install xubuntu-desktop
```


> **deadflowr said:**
> Follow the advice of enabling Networking after which you then enter the Root Shell and run the command, but exclude sudo, since you will already be root.

Thank you very much.
And can I just clairfy one more thing, before I move on.
I just want to make sure that the above option is more like a "repair" rather than  "re-install" and that I will not lose or write over any unsaved data/files that are not backed up ?
Is that correct ?

---

### Post by deadflowr on 2015-05-17
Removing or installing packages never touches any of the existing files in a user's personal folder.

---

### Post by sandyd on 2015-05-18
> **elvis6 said:**
> Thank you very much.
And can I just clairfy one more thing, before I move on.
I just want to make sure that the above option is more like a "repair" rather than  "re-install" and that I will not lose or write over any unsaved data/files that are not backed up ?
Is that correct ?

By default, when you install Ubuntu (or most [recognized ubuntu flavours]("http://www.ubuntu.com/about/about-ubuntu/flavours") I would guess), the system comes with what is called a metapackage.

The metapackage depends on a number of packages that are supposed to be installed on the Ubuntu/Ubuntu Flavour by default (that is, on a clean installation). 

If you wanted to, you could install Ubuntu Server, and then install one of the metapackages listed above, and it will install all the packages that the distro DVD should be installing on your computer had you installed from the DVD instead of from metapackage [SUP][1][/SUP]

By reinstalling this metapackage, it is *possible* that it reinstalls what is missing, or gets your system back into a usable state. Most of the time, this is the fastest way back to a usable system.

[1] This excludes "setting-based" things such as the plymouth splash image, whether GDM/LightDM/SDDM is used. Settings are not modified by packages, and if modifications to a package configuration file are required, apt-get will ask you what you want.

---

### Post by elvis6 on 2015-05-18
> **deadflowr said:**
> Removing or installing packages never touches any of the existing files in a user's personal folder.

> **sandyd said:**
> By default, when you install Ubuntu (or most [recognized ubuntu flavours]("http://www.ubuntu.com/about/about-ubuntu/flavours") I would guess), the system comes with what is called a metapackage.
The metapackage depends on a number of packages that are supposed to be installed on the Ubuntu/Ubuntu Flavour by default (that is, on a clean installation). 
If you wanted to, you could install Ubuntu Server, and then install one of the metapackages listed above, and it will install all the packages that the distro DVD should be installing on your computer had you installed from the DVD instead of from metapackage [SUP][1][/SUP]
By reinstalling this metapackage, it is *possible* that it reinstalls what is missing, or gets your system back into a usable state. Most of the time, this is the fastest way back to a usable system.


It worked !
The system is back up and running normally. Other than my desktop missing a few icons, everything seems to be the way it was before.
I am so very, very grateful for all the assistance.
I admire and appreciate the helpfulness, friendliness, and patience that all of you have.
Thanks so much !

---

