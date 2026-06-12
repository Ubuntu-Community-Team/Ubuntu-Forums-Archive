---
title: "SMB4K problems on 12.04 LTS"
date: 2013-09-14
forum: General Help
---

### Post by pbpersson on 2013-09-14
I installed 12.04 LTS some time ago because it is the "stable, long term support" version of Ubuntu where I thought everything would work perfectly.

There was a problem with SMB4K when I first installed it but I found that I could get to my SMB Windows shares using Dolphin.  Now that has stopped working.  I have to reboot Ubuntu and it will work once, then when I later try to connect it cannot seem to find the Windows machine.

I went back to SMB4K and that also does not work.

The "scan network" feature has never worked, it says "The list of arguments for the "net" command could not be assembled"....whatever that means.  I looked at the details, it says it tried to connect to 127.0.0.1 which is the loopback address.  That's silly, why would it do that?

When I try to manually mount a share it says it could not mount and under the details it says "sudo: no tty present and no askpass program specified".  Here again is another error message that is less than helpful. I wish that developers would think about the end users when they write these error messages.

I checked and I am using version 0.10.10 of SMB4K which is several releases behind.  Isn't the long term support version of Ubuntu always supposed to get the latest bug fixes?

Is there any way to install a more recent version of SMB4K without doing some "build from source" nightmare?  I don't really have tons of time to spend on this so I am just using Windows for now until I can get this Ubuntu machine fixed so it can share data with the network once again.  Any help would be appreciated.


Phil

---

### Post by pbpersson on 2013-09-14
I looked at other Samba clients.  I saw an article about LinNeighborhood where they said it was great.  I could not find that in the repositories.  I installed something called pyNeighborhood which I thought would be even better but it does not work at all.  There are no errors but it cannot find any shares on the network and when I told it to manually mount a share it did nothing.

---

### Post by pbpersson on 2013-09-14
Okay, I read that WebMin had some Samba configuration options and installed that, however apparently the article wanted me to create Samba shares on my Linux machine.  That is not what I wanted, I just want to connect to my Windows shares on the network.  Then I discovered a command line thing called smbclient.  I can connect to the remote Windows machine and can do a "dir" to view all the directories in the share I don't know how to mount.  Then I discovered smbmount.  There was an article that told me how to mount my remote share but it does not work, now I am getting an error message that the directory I created in the /mnt directory does not have an entry in /etc/fstab.  Apparently this article on how to use smbmount is missing a step.  :(

---

### Post by pbpersson on 2013-09-14
It appears there is a good article on this here:  [https://help.ubuntu.com/community/Samba/SambaClientGuide]("https://help.ubuntu.com/community/Samba/SambaClientGuide")

---

### Post by pbpersson on 2013-09-15
Here are the instructions I am using:

```
Now create a directory where you want to mount your share (e.g. /media/samba_share):


sudo mkdir /media/samba_share
Now, using any editor, and add a line to /etc/fstab for your SMB share as follows:


sudo cp /etc/fstab /etc/fstab.bak
gksu gedit /etc/fstab
Add a line for your SMB share:


//myserver_ip_address/myshare  /media/samba_share  cifs  credentials=/etc/samba/user,noexec  0 0
The share will mount automatically when you boot. The "noexec" option prevents executable scripts running from the SMB share.

To mount the share now, without rebooting,


sudo mount /media/samba_share
```

These instructions work **up to a point**.  I can mount the shares but the mounted shares are read only.  There are several articles concerning this on the web but no clear answers.  :confused:

**I give up**, I cannot spend the entire weekend on something that should take one minute. ](*,)

I have lots of other things I need to do, I will just use Windows until someone can tell me what I am doing wrong here. :(

---

### Post by Morbius1 on 2013-09-15
> //myserver_ip_address/myshare  /media/samba_share  cifs  credentials=/etc/samba/user,noexec  0 0
It's not read only - it's only read only to you because it's owned by root. Take possession of the mounted share:

[1] Unmount the share:
```
sudo umount /media/samba_share
```
[2] Change the expression in fstab to this:
> //myserver_ip_address/myshare  /media/samba_share  cifs  credentials=/etc/samba/user,noexec,[COLOR=#0000cd]**uid=1000**[/COLOR]  0 0
[3] Remount the share without a reboot by issuing this command:
```
sudo mount -a
```
See if you can write to the share.

And I'm assuming you are user:1000. To find out run this command:
```
id
```

---

### Post by pbpersson on 2013-09-16
Thank you!  That was wonderfully easy once I knew what to do!  =D>\\:D/

I even rebooted and all my shares are mounted!  Bravo!

So back to my other question - Let's say I install Precise Pangolin and it wants to download 300 updates.  What exactly are those updates and from where do they originate?  I once thought they came from upstream - from all the developers of all the packages so I had the latest and greatest versions of everything.  Apparently this is not the case.  In many cases, new versions of packages (such as SMB4K) probably rely on new libraries which would rely on a new kernel and a new version of Gnome, etc.  What are these 300 updates, are they just little tweaks from Canonical to allow the versions of software released with Precise Pangolin to get along better with each other?

---

