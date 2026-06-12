---
title: "vmware-server &amp; guests on a NAS"
date: 2007-06-02
forum: General Help
---

### Post by D0ubleStakked on 2007-06-02
Hi,
  Here's my setup:

  Host Server Specs:
    IBM eSeries xServer 225
       Intel Xeon 1.??? - I forget off the top of my head
      8GB RAM
      140GB in RAID 5 

   Ubuntu Server 7.04 + Ubuntu Desktop + linux-kernel-bigiron

   VMWare Server


  So here's what's unique:   The VMware guests are on a separate NAS server and the two servers are connected by a Gigabit switch.  Both servers have gigabit NICs.  The Ubuntu host sees the NAS through a samba mount.  I have added the following to my /etc/rc.d/rc.local
   *mount -t cifs -o username=name,password=passwd //ip_address/Share /mnt/Share *

  I have verified that this samba mount is established correctly when the Ubunut host server boots up

  I have 2 guests:   1 is Fedora Core 5 and 1 is Windows 2000 Server
 (I actually have many more, but they're aren't involved yet)

  Turning on the Fedora Core 5 guest, everything works great.
  Turning on the Windows 2000 Server, **Ubuntu completely locks up on me after about 2 minutes, and I have to reboot the server**.


   Other reserarch:
   Using Fedora Core 6 as the host, both of my guests turn on successfully and run smoothly.  The problem I have with Fedora is that when I turn on more than 3 guests at the same time, the server slows to a crawl. 
  
   Using Windows 2003 Enterprise Server, I can run 7 guests simultaneously without breaking a sweat.  I don't have the $$ to buy Enterprise Server from Microsoft.

    My next steps:
    Try moving the 2 guests locally onto the host server to see if the samba mount, the NICs, or the gigabit switch are the culprit.

   The final design must have the guests on the NAS server, though.  I have 2 other identical servers, and I am trying to roll out a VMWare Server "farm" to my development & test staff.  In total, we'll have ~15 guests running at the same time across these 3 servers, so I need to run **at least 5 guests at the same time**.  With the 8GB RAM and the hyperthreaded Xeon processor in each, I do not expect my server specs to be a problem.  

  I'm curious to explore Fedora Core 7 to see if it works any better, but a good friend of mine has had fantastic success with Ubuntu and strongly recommended it.  I'm not sold on either one, I just don't have the budget for Windows, so I've got to find a solution.

Thanks to anyone who can offer some guidance.
-Brian

---

### Post by handband2 on 2007-06-02
I'm wondering if your Samba settings are correct.  Check to see if your settings are correct. 

Here is a good site to see if you have read/write access for the virtual machine folder:  [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server")

---

### Post by veloce on 2007-06-03
Is your windows vm set for multiple cpu by any chance?  While it (theoretically) works, it can make things slow to less than a crawl - looks like a lockup.

---

### Post by D0ubleStakked on 2007-06-04
I moved the windows 2000 server guest to the local file system on my Ubuntu host, and I encountered the same problem.

The windows 2000 server guest made it further in booting, and I see the windows login screen in the VM Server Console.  Unfortunately, my Ubuntu host is still locked up, and I can't do anything with the keyboard or the mouse.

I will look more into Samba to see if I have it installed & configured correctly.

-Brian

---

### Post by handband2 on 2007-06-04
D0ubleStakked,

Do the files have the correct permissions (owner:group)?  

Also, what Guest Operating System did you choose when creating the windows 2000 virtual machine?  You can check this by looking at your .vmx file and look under guestOS.

---

### Post by D0ubleStakked on 2007-06-04
I have verified that I have the correct permissions set on my Samba mount

I imported the guest VM from MS Virtual Server using the **windows** version of the server console.

We're currently going through a migration from Microsoft Virtual Server 2005 to VMWare.
We have 1 windows vmware server running that we are using to convert all of our Virtual Server guests to VMware guests.
Once the VMware guests are created, we post them up on the NAS server and load them into the linux-based VMware server.

Once we're done with all migration from Virtual Server to VMWare, that windows server will be converted into a linux-based VMWare server

-Brian

---

### Post by handband2 on 2007-06-04
D0ubleStakked,

Have you tried mounting your samba shares through /etc/fstab?

//ipaddress/Share /mnt/Share smb defaults 0 0

---

### Post by veloce on 2007-06-04
> **handband2 said:**
> D0ubleStakked,

Do the files have the correct permissions (owner:group)?  

Also, what Guest Operating System did you choose when creating the windows 2000 virtual machine?  You can check this by looking at your .vmx file and look under guestOS.

Also: at least one of the files that make up the vm needs to be "executable".  This may be an issue on the samba share.  Try chmod 777 on all the files that make up the local copy to see if that allows it to run.  If it does, then you are going to need to find how to set something on a samba share as executable - I seem to remember it is something to do with setting it as system or hidden.

---

