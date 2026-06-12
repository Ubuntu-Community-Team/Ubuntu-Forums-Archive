---
title: "[SOLVED] PLEASE HELP: Ubtuntu won't start after updates"
date: 2007-11-16
forum: General Help
---

### Post by navneeth on 2007-11-16
I have searched some of the most recent threads in this forum, and no one seems to have posted about it, yet. 

There were a bunch of updates today for GNOME (16.11.2007) - updated and installed all of them. I had to restart the computer for some reason, and when I did, the light brown screen came with the mouse pointer in the middle and it stayed that way. I tried rebooting a few times, but it's no help. (I don't know what to do after I enter recovery mode.) I can move the mouse pointer around. 

Also, when I try to access Ubuntu's Desktop with the short cut placed in XP's Desktop, I get a message that says "The drive or network that Ubuntu Desktop.Ink refers to is unavailable.Make sure the disk is properly inserted or the network resource is available, and then try again."


On a sort of related note, there is this kernel update (2.22.14 - something to do with restricted driver managers?) that won't install, and it's been bugging me for a few days. Error (1).

I'm typing this from a semi-good installation of XP, and I want to get back to Ubuntu as soon as possible. 

Any help will be appreciated.

---

### Post by navneeth on 2007-11-16
BUMPING

I don't want to do yet another reinstall.

---

### Post by d_demchuk on 2007-11-17
I've had exactly the same problem as you--no solutions have yet been posted. Updates failed, reboot, light brown screen, mouse cursor, nothing else.

I've been posting my questions alongside the update issues under the topic "Re: Error:no apt upgrade possible...403 forbidden error" -- where I see you've also posted just recently. 

Let's hope we hear something soon!

David in Toronto

---

### Post by mahasmb on 2007-11-17
I have the exact same problem as well!

I thought it was my xorg.conf file that was messed up so I tried to switch to a backed up version but it didn't work. My computer's rendered completely useless now...

---

### Post by navneeth on 2007-11-17
Well, my most important files are actually stored in an NTFS partition in my Windows installation. I used the SystemRescue LiveCD to move a few left over in Ubuntu to Windows. (Phew!) I think I may have to delete the whole Ubuntu partition and reinstall Gutsy. :( :(

Just when I thought I had completed the smoothest of upgrades...

---

### Post by conjur3r on 2007-11-17
By chance, did you all install your display drivers manually?  I had to reinstall the nvidia drivers as you do after a kernel update.

When the display seems to be frozen, you can switch to another terminal (CTL ATL F1...) and go from there.

---

### Post by DevilInPgh on 2007-11-17
I'm having the same problems, except after the 403 went into effect.  GNOME seems to be really broken, and when I try to do an aptitude upgrade in Xfce (which seems to be working, as opposed to GNOME), the call freezes at "Building dependency tree... 50%".  The IRC chat was no help at all, actually more of a big frustration in how first they didn't listen to what I was saying, then was absolutely clueless on what my problems were, thinking I wanted to end the command rather than fix what is wrong.

EDIT: KDE is also working.  So my main complaints are with GNOME and aptitude.

---

### Post by navneeth on 2007-11-17
> **conjur3r said:**
> By chance, did you all install your display drivers manually?  I had to reinstall the nvidia drivers as you do after a kernel update.


I don't think it had anything to do with those things, because I don't use a nvidia card. The kernel update has been refusing to install for a few days, but the current problem happened only after a GNOME update (games and stuff). I can't even enter the GNOME desktop, so I'm not sure if I can switch to KDE or XFCE.

---

### Post by Macros42 on 2007-11-17
I just had a problem where X wouldn't start after the updates. Reinstalling the Nvidia driver sorted it out.

On another note - some of the updates won't download:

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.24-2ubuntu1.3_i386.deb
  403 Forbidden


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.24-2ubuntu1.3_i386.deb
  403 Forbidden


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.24-2ubuntu1.3_i386.deb
  403 Forbidden
```

---

### Post by navneeth on 2007-11-17
> **conjur3r said:**
> When the display seems to be frozen, you can switch to another terminal (CTL ATL F1...) and go from there.

Thank you, thank you, and thank you! :)

I was able to get into the terminal. I did a "apt-get install -f," and about 27 updates GNOME were installed. (I thought they had already been installed.) That didn't do the trick. It was only after a dist-upgrade did my Desktop finally show up after nearly a day. Actually, I was a little apprehensive about doing the upgrade, since I saw the letters smb there. But then I realised that the people at Ubuntu had "blocked" the most recent updates, so I assumed that ones I was seeing must be the "good" updates. 

Man, what a relief!

---

### Post by d_demchuk on 2007-11-17
Okay, since it's early and I'm not that bright--what exactly do I do? I switch to a new terminal window and I type...?

---

### Post by navneeth on 2007-11-17
> **d_demchuk said:**
> Okay, since it's early and I'm not that bright--what exactly do I do? I switch to a new terminal window and I type...?

[B]I won't take the risk of recommending you exactly the steps I took, unless you are in the same situation as I was. 

The Ubuntu bar loaded and I was stuck on a pale brown screen with the mouse pointer.
[/B]

 If that's your case, then hit Ctrl+Alt+F1. After a few things are done, you'll be asked for your username and password. If those are provided correctly, you'll be taken to your usual shell, <username>@<hostname>:~$, except that you will not be in a graphical environment. 

Now make sure if any thing has not be installed properly with
```
sudo apt-get install -f
```

Once that has been done, do 

```
sudo apt-get update
```

and

```
sudo apt-get dist-upgrade
```.

Let it download and install the updates. 

Restart the computer and cross your fingers. ;)

BTW, to restart you can use this...

```
sudo shutdown -r now
```

---

### Post by d_demchuk on 2007-11-17
Hi Naveeth--thanks! I ended up at exactly the same place you did, with exactly the same screen colour and mouse pointer. I will give this a try!

David in Toronto

---

### Post by kekvfoste on 2007-11-17
I got the same error this morning.  When I manually ftp'd to the site I noticed the permissions were not set on the file I was trying to download.  A administrator of the server needs to set the permissions to 644 but I'm not sure who to contact.

---

### Post by d_demchuk on 2007-11-17
Thanks, Navneeth--your instructions worked perfectly! (I should hang onto them in the event that something else like this happens...)

Cheers,

David in Toronto

---

### Post by navneeth on 2007-11-17
Glad to help. :)

---

### Post by PC_load_letter on 2007-11-17
I haven't read all the replies yet, but I just wanted to report that my Feisty X-server will not start after installing the latest updates. The error log file says something about nvida.ko file (I don't know what the heck is it) or directory is missing. 
I am using the nvidia unsupported drivers that I installed long time ago. Feisty has been rock solid and never gave me any problems that I opted to hold on and wait before upgrading to Gusty.

[B]Rant Warning:

I find it APPALLING at this day and age that a mere update would ruin an existing solid working configuration like this. This is UNBELIEVABLE! I'm really pissed off right now. 

End of rant.[/B]

---

### Post by uberMongo on 2007-11-17
I'm having the same problem. Only instead of a brown screen with mouse cursor on it I get the "username@hostname:~$" thinggy (did you notice that I'm a noob?).
I also get an error saying that "nvidia.ko" cannot be found at "/lib/modules/2.6.20-16-generic/volatile"
I tried to copy the file from "/lib/modules/2.6.20-16-generic/kernel/drivers/video" than I restarted x and everything came up. But as soon as I restart the machine the file simply disapears again and I'm back at the begining.
I tried installing the nvidia drivers and configure them, but nothing seems to work.

Has I said at the begining I'm a noob at this, can someone please help?

---

### Post by uberMongo on 2007-11-17
after searching the forum I've managed to re-install the drivers and the files don't disapear anymore. But now when I restart I get this:
> kinit: name_to_det_t(/dev/disk/by-uuid/c86e9576-076b-4f0c-ba8e-11ed8999f275) = sda2(8,2)
kinit: trying to resume from /dev/disk/by-uuid/c86e9576-076b-4f0c-ba8e-11ed8999f275
kinit: No resume image, doing normal boot...


I also ge a blue screen with a gray box in it with the following text:

> Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?


when I choose "yes" I get a log saying that the NVIDIA driver component version doesn't match with the NVIDIA kernel module's version.
The driver version component is 100.14.19

I'm running Feisty Fawn. My graphic card is a XFX GeForce 7950 GT.

---

### Post by conjur3r on 2007-11-17
People with nvidia driver issues or nvidia.ko problems, reinstall your drivers!  Reboot and you'll be fine again.  You need to do this everytime your kernel version updates.

Note, this is the price you pay for using manufacturer drivers.  If you had used the Ubuntu supplied drivers, you would not have this problem.  That said, it's not hard to reinstall the drivers - I do it too :)

---

### Post by PC_load_letter on 2007-11-17
> **conjur3r said:**
> People with nvidia driver issues or nvidia.ko problems, reinstall your drivers!  Reboot and you'll be fine again.  You need to do this everytime your kernel version updates.

Note, this is the price you pay for using manufacturer drivers.  If you had used the Ubuntu supplied drivers, you would not have this problem.  That said, it's not hard to reinstall the drivers - I do it too :)

WHAT!!!? So yesterday's updates included a kernel upgrade? Are you sure about this? Because I intentionally do not want to upgrade to Gutsy right now. Or was the kernel upgrade cramped into the many updates. If this is the case, isn't the Ubuntu user entitled to a freakin' message that mentions such a dramatic change? It's like XP upgrading to Vista without letting me know. 

Maybe the majority of the people here are Linux experts, but I'm pretty sure there are many users like myself. I don't have the time to keep this high level of maintenance. I thought I had every thing figured out and optimized when I installed Feisty. Apparently I have to spend half my life installing and uninstalling drivers. 
And regarding the comment about the Nvidia driver, well, maybe if the supplied driver had worked I wouldn't have had to install the manufacturer's.

---

### Post by mahasmb on 2007-11-17
> **navneeth said:**
> Thank you, thank you, and thank you! :)

I was able to get into the terminal. I did a "apt-get install -f," and about 27 updates GNOME were installed. (I thought they had already been installed.) That didn't do the trick. It was only after a dist-upgrade did my Desktop finally show up after nearly a day. Actually, I was a little apprehensive about doing the upgrade, since I saw the letters smb there. But then I realised that the people at Ubuntu had "blocked" the most recent updates, so I assumed that ones I was seeing must be the "good" updates. 

Man, what a relief!

This won't work for me. It tries to download some updates, but my internet doesn't connect unless I use WICD. I can't connect to the internet using the terminal.

---

### Post by jtreach on 2007-11-18
The kernel must have updated at least 4 times since I started using ubuntu and this is the first time it has broken my computer, even though I'm using nvidia drivers. I greatly appreciate all the work everyone has done making a great and free operating system, but PC_load_letter does have a point when he rants, any professional OS should not break after installing updates even if you are using restricted drivers (a warning would have been nice).

That aside I still haven't got it working, x still moans about the apparently missing nvidia.ko file. I have no command line on the latest kernel version (I do on the older versions) and I wouldn't have the faintest idea how to reinstall the nvidia drivers even if I did (No matter how simple it might be to regular terminal user).

Can someone pretty please with a cherry on top, give me an exact set of instructions for reinstalling the nvidia drivers? (Do I need to get the terminal working on the latest kernel version first)

Thank you in advance for any help. :)

---

### Post by uberMongo on 2007-11-18
> **conjur3r said:**
> People with nvidia driver issues or nvidia.ko problems, reinstall your drivers!  Reboot and you'll be fine again.  You need to do this everytime your kernel version updates.

Note, this is the price you pay for using manufacturer drivers.  If you had used the Ubuntu supplied drivers, you would not have this problem.  That said, it's not hard to reinstall the drivers - I do it too :)

That's fine by me, but the problem is that the drivers that come with Ubuntu don't work with my graphics card. I don't have a problem if I have to reinstall them every time a kernel update comes out, but I'd like to be warned about it. It's really bad when you do an update and after you reboot your X server refuses to startup. So I think a little warning would be very cool.

Anyway I managed to solve my problem using Envy, just type:
> envy -t
Don't ask me how to install envy from the command line, I don't know how to do that.

---

### Post by Macros42 on 2007-11-18
> **uberMongo said:**
> Don't ask me how to install envy from the command line, I don't know how to do that.


"sudo apt-get install envy" should do it.

---

### Post by jtreach on 2007-11-18
Yeah, I fixed mine using envy now. :D

---

