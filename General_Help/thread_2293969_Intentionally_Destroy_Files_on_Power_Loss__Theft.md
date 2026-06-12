---
title: "Intentionally Destroy Files on Power Loss / Theft"
date: 2015-09-08
forum: General Help
---

### Post by MinionTech on 2015-09-08
Is there a reliable way to destroy a specific folder on power loss?  I'd like to make sure that sensitive, but easily replaced, data is not accessible if a server is stolen.  These are small desktops being sent to a variety of low-security locations.  Total data size is expected to be larger than total RAM.  Ubuntu Server 14.04 LTS x64.

Any direction or ideas would be appreciated.  Thanks!


--- revision ---


Storing to memory is idea #1 at the moment.  We are currently using encfs, but with up to 500 of these boxes being deployed it could mean an awful lot of accessing and decrypting machines.  Data will be imported on-site, after deployment and is private, but easily replaced.

New questions:

[LIST=1]
[*]With data being larger than RAM, can just enough of the data be stored in a volatile way?  How about scripted encfs setup with a key in tmpfs?  <= New Plan A.
[*]
[*]Can this be done without manual intervention?  Data is imported on-site, after deployment and easily replaced.
[*]
[*]Would we have to go without a swap partition/file to make sure nothing is left behind?
[/LIST]


Your ideas and input are greatly appreciated!


--- revision ---


All data is going in to a mount encrypted at boot, similar to an encrypted swap partition.  Thanks to everyone for their suggestions!

---

### Post by efflandt on 2015-09-08
It would be impossible to delete data upon power loss unless you have a UPS and communication between that and your PC to tell you that AC power has failed before power from the UPS fails. It would also be impossible to destroy a folder if the computer was stolen while not running. Note that /tmp is automatically emptied during boot, but that does not help if someone boots from USB or other external drive or connects the drive to another computer.

So your best bet would be to keep the data on a small encrypted partition. But I have never done that because I have nothing to hide, except passwords, which I keep in a LibreOffice Writer file that is encrypted and requires a password or pass phrase.

---

### Post by tgalati4 on 2015-09-08
You could create a bootup script that looks for a "lock" file--a file that your script produces when a condition is met.  When the lock file is found then delete the folder.  You would need to install *apcupsd* and have your script scan the apcupsd.events file for power loss.

Pseudo code:

1.  grep /var/log/acpupsd.events for power loss (but still running on battery)--you would have to poll this file every 2 minutes (I believe the default acpuspd poll interval).
2.  If power loss, then touch a lock file called /var/log/delete-sensitive-folder.lock.
3.  In a script in /etc/rc.local, put a file existence check for /var/log/delete-sensitive-folder.lock.
4.  If lock file exits, rm -rf /home/users/folders-that-you-want-to-delete
5.  sleep 30 (or however long you think it takes to delete the files), this will delay bootup by this amount of time.
6.  Normally you would delete the lock file to reset it, but since this is a one-shot action, it doesn't really matter.

You would need to figure out a way to hardwire the server to the UPS so that uplugging the UPS keeps the server running on battery.  Otherwise, unplugging the server directly (or cutting the power cord) will cause a hard shutdown, without your script running properly because the lock file doesn't get created.

Some hard disks have a password in firmware, perhaps you could go that route.

---

### Post by patlkli on 2015-09-09
Another idea would be to store your files encrypted on disk using a symmetrical cipher and store the key in volatile memory.

This would require that you can separate the data in parts, so that you can decrypt parts of it into RAM, so that those are also lost on power loss.

And you cannot just access the files, but always have to decrypt them before using them.

However it's probably your best bet (aside from encrypting your whole disk), since the previous ideas here won't save you if the thief knows what he's doing.

---

### Post by XBNCPRk on 2015-09-09
Depending on the usage of the systems (always on vs useage on demand) and their connection speeds, add more ram (its pretty cheap), host the data remotely and copy it into a tmpfs hosted in volatile memory after authenticated startup, or alternatively, just use a well encrypted file system to store it locally.

---

### Post by MinionTech on 2015-09-12
> **tgalati4 said:**
> You could create a bootup script that looks for a "lock" file--a file that your script produces when a condition is met.  When the lock file is found then delete the folder.  You would need to install *apcupsd* and have your script scan the apcupsd.events file for power loss.

Pseudo code:

1.  grep /var/log/acpupsd.events for power loss (but still running on battery)--you would have to poll this file every 2 minutes (I believe the default acpuspd poll interval).
2.  If power loss, then touch a lock file called /var/log/delete-sensitive-folder.lock.
3.  In a script in /etc/rc.local, put a file existence check for /var/log/delete-sensitive-folder.lock.
4.  If lock file exits, rm -rf /home/users/folders-that-you-want-to-delete
5.  sleep 30 (or however long you think it takes to delete the files), this will delay bootup by this amount of time.
6.  Normally you would delete the lock file to reset it, but since this is a one-shot action, it doesn't really matter.

You would need to figure out a way to hardwire the server to the UPS so that uplugging the UPS keeps the server running on battery.  Otherwise, unplugging the server directly (or cutting the power cord) will cause a hard shutdown, without your script running properly because the lock file doesn't get created.

Some hard disks have a password in firmware, perhaps you could go that route.


This is a great idea and added to the current solution, encfs, would be a nice step up!  We're mostly worried about petty theft, so rm on boot fits well.  The step-by-step instructions are appreciated.  Thanks!

---

### Post by MinionTech on 2015-09-12
> **patlkli said:**
> Another idea would be to store your files encrypted on disk using a symmetrical cipher and store the key in volatile memory.

This would require that you can separate the data in parts, so that you can decrypt parts of it into RAM, so that those are also lost on power loss.

And you cannot just access the files, but always have to decrypt them before using them.

However it's probably your best bet (aside from encrypting your whole disk), since the previous ideas here won't save you if the thief knows what he's doing.

Makes sense.  We're using encfs, but since there could be up to 500 boxes it'd be nice not to visit them all on boot.  I'll revise the first question a bit and try to steer the conversation that way.  Thanks!

> **XBNCPRk said:**
> Depending on the usage of the systems (always on vs useage on demand) and their connection speeds, add more ram (its pretty cheap), host the data remotely and copy it into a tmpfs hosted in volatile memory after authenticated startup, or alternatively, just use a well encrypted file system to store it locally.

Volatile memory idea is definitely my favourite answer!  Since data is larger than RAM, is there any way to partially store (stripe?) to RAM, destroying, but not removing everything on power loss?  Thanks!

---

### Post by tgalati4 on 2015-09-13
I have used these instructions for running *firefox* in RAM.  The advantage is that it runs faster than a spinning hard disk.  If you don't perform the synchronization step then the cache disappears when the machine is shut down.  So perhaps you could set up a similar arrangement with your services, so that they disappear when rebooted.

As far as data, you could put the sensitive data on a separate NAS--network attached storage, and take extra precautions to secure the NAS separate from the server.  So if the server gets stolen, the NAS is still secure in another location.  Performance will be slower depending on your network connectivity.  But you could set up caching and ramdisks as explained above so that the client machines will not know the difference between local server storage and the NAS.

---

### Post by HermanAB on 2015-09-13
Yes, there is.  Make a tmpfs (RAM disk).  If you want to be double sure you can encrypt it also to guard against a cryogenic attack.

---

### Post by MinionTech on 2015-09-21
> **tgalati4 said:**
> I have used these instructions for running *firefox* in RAM.  The advantage is that it runs faster than a spinning hard disk.  If you don't perform the synchronization step then the cache disappears when the machine is shut down.  So perhaps you could set up a similar arrangement with your services, so that they disappear when rebooted.

As far as data, you could put the sensitive data on a separate NAS--network attached storage, and take extra precautions to secure the NAS separate from the server.  So if the server gets stolen, the NAS is still secure in another location.  Performance will be slower depending on your network connectivity.  But you could set up caching and ramdisks as explained above so that the client machines will not know the difference between local server storage and the NAS.

> **HermanAB said:**
> Yes, there is.  Make a tmpfs (RAM disk).  If you want to be double sure you can encrypt it also to guard against a cryogenic attack.

Since scheduled db dumps are larger than available RAM, how about striping or using any kind of encryption that doesn't require manual intervention?  Then on power loss remaining data would be junk and cleaned up at boot.  I'm wondering whether encfs could/should be scripted with a random key and make sure that's stored exclusively in RAM.  Next boot we start fresh.  Any opinions or suggestions?  I'm pretty close to marking this thread as solved.  :)

---

### Post by Ettore_Casagrande on 2015-09-21
Can't you just make a single encrypted volume that contains this sensitive information?  Is this information required to boot the device?  If not, you could just SSH in to whichever device lost power (unless it's likely all 500 will lose power simultaneously?), type in the decryption password, and off to the races.  Could even setup the machine to send you a message on boot so you know which one(s) is/are needing attention.

I am sure you could craft a script that zips thru all the machines and mounts that volume, if it's not already mounted.  Actually, since you should be able to connect through a secure channel, you could just schedule that script to run every hour.

---

### Post by HermanAB on 2015-09-22
You could do the same as an encrypted swap partition:  Encrypt the disk partition with a random key kept in RAM.  When power is lost, the key is gone and the data is just 'random noise'.

---

### Post by MinionTech on 2015-09-29
> **Ettore_Casagrande said:**
> Can't you just make a single encrypted volume that contains this sensitive information?  Is this information required to boot the device?  If not, you could just SSH in to whichever device lost power (unless it's likely all 500 will lose power simultaneously?), type in the decryption password, and off to the races.  Could even setup the machine to send you a message on boot so you know which one(s) is/are needing attention.

I am sure you could craft a script that zips thru all the machines and mounts that volume, if it's not already mounted.  Actually, since you should be able to connect through a secure channel, you could just schedule that script to run every hour.

> **HermanAB said:**
> You could do the same as an encrypted swap partition:  Encrypt the disk partition with a random key kept in RAM.  When power is lost, the key is gone and the data is just 'random noise'.

These two suggestions, particularly the part about similar setup to swap encryption, do the trick.  Thanks for your help!  This is getting marked as answered.  :D

---

