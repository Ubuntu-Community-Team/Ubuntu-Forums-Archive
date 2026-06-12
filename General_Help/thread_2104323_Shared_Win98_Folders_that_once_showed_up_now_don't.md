---
title: "Shared Win98 Folders that once showed up now don't show - nothing changed"
date: 2013-01-12
forum: General Help
---

### Post by 777funk on 2013-01-12
I haven't changed any of the permissions on my 98 box on the samba network but I notice that many of the folders under a shared folder are no longer showing. 

For a hypothetical example to make this simple, picture this:    
 
      ** My Documents....** should contain My Pictures, My Music, My Videos... etc. Sharing the parent directory should show the contained folders over the network.

On the Ubuntu machine, _**only**_ "My Music" shows up (no trace of My Pics or My Vids) even though they are also contents of the shared parent folder (My Documents). 

So what's the deal with this? This is on a 12.04 dual boot desktop by the way. On the Windows half of the boot, I can see my 98 box's shared folders (all of them) just fine. What's up with these sub folders not showing under Ubuntu?

---

### Post by 777funk on 2013-01-13
Any ideas?

---

### Post by 777funk on 2013-01-14
anyone?

---

### Post by tgalati4 on 2013-01-14
In Windows, Right-Click on the folders that are not showing and check the Sharing status.  Mark as "Share" if they are not already marked.  Then check the share over the network from another machine.

---

### Post by 777funk on 2013-01-14
> **tgalati4 said:**
> In Windows, Right-Click on the folders that are not showing and check the Sharing status.  Mark as "Share" if they are not already marked.  Then check the share over the network from another machine.

They're already shared status and show up in any windows machines (or windows boot on my dual boot). Just not showing ALL the shared folders in Ubuntu. Not sure why.

---

### Post by tgalati4 on 2013-01-14
Could be a bad file name in one of the Windows directories that is clobbering the enumeration.  You might have to reboot the Win98 machine, because, well, it often requires rebooting to fix things.

Look in /var/log/auth.log and see if there are any errors in network authentication that could be causing an issue.  Also check /var/log/samba for errors.  Post any that you don't understand.

---

### Post by 777funk on 2013-01-17
> **tgalati4 said:**
> Could be a bad file name in one of the Windows directories that is clobbering the enumeration.  You might have to reboot the Win98 machine, because, well, it often requires rebooting to fix things.

Look in /var/log/auth.log and see if there are any errors in network authentication that could be causing an issue.  Also check /var/log/samba for errors.  Post any that you don't understand.

Thanks for the ideas!

I found two things in that file that may look to be errors but not sure. Here those are:

> Jan 14 21:22:04 NickUbuntu gnome-screensaver-dialog: pam_smbpass(gnome-screensaver:auth): Cannot access samba password database, not running as root.and 

> Jan 13 09:37:58 NickUbuntu gnome-screensaver-dialog: pam_smbpass(gnome-screensaver:auth): Cannot access samba password database, not running as root.Only the second appears to be Samba related.

ALSO: just tried to get onto the network with my other ubuntu machine and it sees the files/folders just fine. So just the 12.04 is not seeing the folders for some reason.

---

### Post by 777funk on 2013-01-18
any more ideas to look into?

---

### Post by 777funk on 2013-01-21
Is there a way to reset or delete and re-install the network settings?

Seems like something strange is going on with this install.

---

### Post by 777funk on 2013-01-22
Any ideas on how to restore my network back to factory settings? Maybe that would fix the problem on this 12.04 install?

---

