---
title: "nfs problem with relocated /home"
date: 2014-04-25
forum: General Help
---

### Post by xeddog on 2014-04-25
I have a small home network that consists of 3 linux machines (Stealth, Intrepid, and G-Man) and one PopcornHour A-210 creatively named Popcorn.   I have set up nfs on the linux machines and use autofs to mount the other linux computers, and fstab to mount the PCH share.  On one of these machines, Stealth, I have moved the /home directory to a separate 1TB disk drive /sdb.  Everything works great with one exception.  None of the other linux machines can mount Stealth's /home.  They all get an error message.  

Intrepid (running Ubuntu 14.04 that I just upgraded from 13.10) produces a dialog box that says "The location could not be displayed", and " "Stealth" could not be found.  Perhaps it has been recently deleted."  I also got these messages when it was still running 13.10.

G-Man (running Mint 16) gets essentially the same message - "The [COLOR="#FF0000"]folder contents[/COLOR] could not be displayed", and also " "Stealth" could not be found.  Perhaps it has been recently deleted."

The interesting thing to me is that Popcorn DOES mount the Stealth /home directory.  The PCH runs an older version of linux with nfs V3, and the uname -a command shows "Linux Popcorn 2.6.22.19-27-4 #46 PREEMPT Mon Jul 8 14:13:12 MYT 2013 mips GNU/Linux"

Can anyone tell me what I can do to fix this??


Thanks,

X

---

### Post by jamesisin on 2014-04-25
Are you saying your /home for all machines is located on a server called Stealth?  So, Stealth has a set of folders called /home/user1 /home/user2 &c.

Are you using static addresses on your network?

How are you calling out these mounts in fstab?

---

### Post by xeddog on 2014-04-25
jamesisin - 

No, only the /home directory for Stealth itself is relocated to the second disk.  All of the other machines have their own "normal" local /home.

All machines do have static ip addresses.

The linux computers all have an fstab entry to mount Popcorn's share, but everything else for mounting the other linux machines directories is done via autofs.  Quite a while ago I tried using fstab entries for these too, but that led to problems when shutting everything down.  The first machine would shutdown and all of the others would hang during shutdown because they couldn't unmount the first machine.  I seem to remember that there was another problem too, but can't remember for sure.  Since Popcorn is the only one that is running 24x7 I don't have the problems during shutdown.

The PCH seems to do it's own thing so I don't know exactly how that is done.

Thanks,

X

---

### Post by jamesisin on 2014-04-25
Have you compared your fstab files between Popcorn and the other machines, see if you are doing anything differently?

---

### Post by SeijiSensei on 2014-04-25
The "cannot be found" messages mean the clients have no method to resolve the name "stealth" to an IP address.  You either need to make entries in the clients hosts files (e.g., /etc/hosts on *nix machines), or set up a DNS server for the local network.  Your router may already provide DNS; check the documentation.

Alternatively use IP addresses in /etc/fstab:
```
10.10.10.10:/home    /home    nfs defaults 0 0
```

There is also the issue of permissions.  Mounts from /etc/fstab take place as the "root" user.  If the server doesn't permit root mounts (often the default), then you need to enable them.  On a regular *nix box running an NFS server, you need to include "no_root_squash" in the options for the share in /etc/exports.  On a proprietary device like a NAS, you need to read the documentation.

---

### Post by xeddog on 2014-04-25
jamesisin -  the fstab entry on the linux machines are identical.   Like this:
"Popcorn:/share	/media/Popcorn 	nfs 	rw,sync,rsize=32768,wsize=32768,vers=3,intr,user,_netdev,exec	0	0"

As for Popcorn, It doesn't have any fstab entries except it's own file systems.



SeijiSensei - All linux machines have hosts files with all of the other systems needed including other linux machines, Popcorn, and even virtual machines that I might create using Virtualbox and bridged network adapters.  Ping commands tell me that all entries are correct because they work.  no_root_squach is already specified in all of the fstab entries as well.  Permissions is one thing I am looking in to, but I have not been able to find anything different between the three linux machines as yet.



But for both of you now, I don't think the problem is with fstab.  The only fstab entry on the linux machines is for Popcorn and they all work.  The problem seems to be with autofs, and even at that it is only when trying to automount Stealth from Intrepid or G-Man.  I don't know if it is coincidence that Stealth is the only one with it's /home relocated, but I don't like coincidences.  If I look at fstab on Intrepid when it has G-Man automounted, there is only Popcorn in fstab, but there is an entry in mtab for G-Man.



Thanks,

X

---

### Post by SeijiSensei on 2014-04-26
> **xeddog said:**
> But for both of you now, I don't think the problem is with fstab.  The only fstab entry on the linux machines is for Popcorn and they all work.

Why aren't you mounting stealth in the same way? Or am I missing something here?

---

### Post by xeddog on 2014-04-27
SeijiSensei - 

I don't use fstab between the three linux machines because it causes problems, or at least caused problems in the past.  One of these problems is a shutdown problem.  If all three machines are up and running, which is the norm, I can shutdown any one of the machines but then the other two will not shut down cleanly because they hang while trying to unmount the first machine.   Another similar problem I had was when all three machines are running, but I decide to reboot one of them.  For example, if I reboot Stealth (which is not a rare occurrence), when it comes back up it all looks good from there, but  Intrepid and G-man are no longer able to access Stealth because the mounts are no longer valid.  That means they have to be unmount/remount Stealth, and that has also been problematic in the past as the umount command has failed on Intrepid and/or G-man.  Even umount -f didn't help.  Nor did restarting the nfs-kernel-server service.  To regain access to Stealth, one or more likely both of the other machines had to be rebooted to reestablish the mount.  

My research on the problem revealed that this was just the way it was using fstab.  There were a few suggestions to make this work better, but none of them did any good.  During my research I saw many references to autofs and initially that seemed to be the solution.  And initially it was.  When I started all this, G-man was running some flavor of Ubuntu, 13.04 I think, Intrepid was running Ubuntu 13.04 too if I remember right, and Stealth was running Ubuntu's prior LTS release 12.04.  At that time all three machines automounted each others / file systems and all was good.  A few days later, I tried to access my home directory on Stealth from one of the other machines, most likely Intrepid, and I noticed that the home directory was not what I expected.  What I got was not my relocated home directory on /sdb, but the original home directory that was on /sda.  The one that wasn't supposed to exist any more.  Installing Mint 16 on G-man, and Ubuntu 13.10 on Intrepid didn't change anything.  But after upgrading Intrepid to 14.04, and Installing a fresh copy of Ubuntu 14.04 on Stealth, I can't get to Stealth at all using autofs.  Not even from G-man which is unchanged.

So that's the history.  If I knew more about linux maybe I could figure this thing out. There are a couple of things, like nfs, that I want.  But other than that I'm just a guy that wants to use the dang thing and not delve into its guts. 

Thanks, and sorry for the long response.

X

---

### Post by steeldriver on 2014-04-27
I'm hazy on the internals of nfs / autofs - although I do run an autofs nfs mount from my netgear NAS to my 12.04 laptop at home. I seem to remember something about an update that sometimes requires an explicit nfsvers=3 in the mount options.

Have you checked the share is visible (via showmount)?

```

showmount -e *remote-host*

```

Can you mount it manually on the command line? if not what error messages do you get? Similarly, are there any mount errors in your dmesg?

---

### Post by xeddog on 2014-04-27
WOOHOO!   I just got it figured out.  My /etc/exports on Stealth was not correct after all.  In the options I had specified fsid=0 instead of fsid=uuid.  As soon as I put in the proper 32 bit uuid and restarted nfs-kernel-server it all works now.  I had tried this before when I had Ubuntu 12.04 installed on Stealth but it didnt work then.  


X

---

