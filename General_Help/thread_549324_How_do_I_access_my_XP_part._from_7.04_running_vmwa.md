---
title: "How do I access my XP part. from 7.04 running vmware on xp"
date: 2007-09-12
forum: General Help
---

### Post by rhendrix9 on 2007-09-12
I have a Win XPsystem with one HD and 4 partitions.
I also have 7.04 installed with vmware's vmplayer.
How do I access my windows partitions?

---

### Post by dabl on 2007-09-12
You don't, as far as I know, at least not in a direct sense.

VMWare creates a virtual machine entirely WITHIN the Linux system.  The virtual machine has its own virtual (not real) hard drive.

What you CAN do is set up Samba on the Linux host, to see the VMWare Win XP system as another node on the "network" that is entirely on the same platform.  Doing that, when the Win XP system is running in VM Ware, it can see whatever directories in the Linux filesystem that you have marked for sharing.

So, I suppose if you were running ntfs-3g on your Linux system, and had a shared NTFS drive mounted and marked for sharing via Samba, then from within the Win XP VMWare session you would be able to share files with that NTFS drive.  Maybe.    :)

---

### Post by rhendrix9 on 2007-09-12
Well I added this to the vmx file;
sharedFolder.option = "alwaysEnabled"
sharedFolder0.present = "TRUE"
sharedFolder0.enabled = "TRUE"
sharedFolder0.readAccess = "TRUE"
sharedFolder0.writeAccess = "TRUE"
sharedFolder0.hostPath = "C:\"
sharedFolder0.guestName = "drive C"
sharedFolder0.expiration = "never"
sharedFolder.maxNum = "1"
 It seemedd to take it but I can't ffind it in ubuntu.

BTW the host is windows and the guest is ubuntu.

I am modifying it just to look at a folder, where/how in ubuntu do i find a sharded folder.
Uh I'm new to Linux in case u couldn't tell.
Thanks

---

### Post by notwen on 2007-09-12
> **rhendrix9 said:**
> 
I am modifying it just to look at a folder, where/how in ubuntu do i find a sharded folder.
Uh I'm new to Linux in case u couldn't tell.
Thanks

Ubuntu's shared folders can be located by going to System--->Administration--->Shared Folders

You could also try Places--->Network to see any shared folders Windows may be offering.

You should get a prompt when you access Shared Folders, at minimum install SMB(Samba), this will allow your Windows machine and your Ubuntu virtual machine to see each other.

---

### Post by rhendrix9 on 2007-09-12
Well, I tried everything you said, but to no avail...
I can share the linux folder, but that would be futile, the hd is virtual
I just want an are that both systems can access.

Anyone have any other suggestions?

---

### Post by notwen on 2007-09-13
Check out this guide to setting up samba [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server").  This should give you a more detailed idea of what needs to be done.  You'll install Samba on the Ubuntu virtual machine, this should enable it to see a folder which you are sharing on Windows.  I personally only use NFS, so I cannot give you better instructions from experience.  Hope this helps. =]

---

### Post by dabl on 2007-09-13
Concur -- Samba is the way to do it.  I had misunderstood that Linux was the host system -- that's how I have it on my Feisty system.  But, I don't see why Windows couldn't be the host system and you'll still do the same things:

- Set folders on your Windows filesystem to share
- Set up Samba on the Linux guest (I know, it's non-trivial ...), and mark Linux folders to share
- Use Windows networking to find the Samba guest node

Here's some more Samba guidance:  [http://www.penguin.ch/dokuwiki/doku.php/virtual:bridge:smb_conf?s=samba](http://www.penguin.ch/dokuwiki/doku.php/virtual:bridge:smb_conf?s=samba)

:)

---

