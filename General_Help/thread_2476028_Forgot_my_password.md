---
title: "Forgot my password"
date: 2022-06-15
forum: General Help
---

### Post by sundaresh on 2022-06-15
I forgot my user login password. How do I change it from grub.

---

### Post by sundaresh on 2022-06-15
Problem solved.

---

### Post by sundaresh on 2022-06-15
Sorry. The problem is not solved. How do I change the user password.

---

### Post by sundaresh on 2022-06-15
Problem not solved

---

### Post by coffeecat on 2022-06-15
@sundaresh, I've merged the orphan post you accidentally made into your thread.

A little more detail would help others to help you. What version and flavour of Ubuntu are you using? What did you do which made you think that you had solved the problem, but which had not?

---

### Post by sundaresh on 2022-06-15
Hirusite hippo

---

### Post by sundaresh on 2022-06-15
I went to grub but it did not work. It asked for root password and just enter did not work.

---

### Post by Rex Bouwense on 2022-06-15
This has worked for me.  First, you have to reboot into recovery mode. 
If you have a single-boot (Ubuntu is the only operating system on your computer), to get the boot menu to show, you have to hold down the Shift key during bootup. 
If you have a dual-boot (Ubuntu is installed next to Windows, another Linux operating system, or Mac OS X; and you choose at boot time which operating system to boot into), the boot menu should appear without the need to hold down the Shift key. 
From the boot menu, select recovery mode, which is usually the second boot option. 

After you select recovery mode and wait for all the boot-up processes to finish, you'll be presented with a few options. In this case, you want the Drop to root shell prompt option so press the Down arrow to get to that option, and then press Enter to select it.
The root account is the ultimate administrator and can do anything to the Ubuntu installation (including erase it), so please be careful with what commands you enter in the root terminal. 


To reset the password, type
 
passwd username

where username is the username you want to reset.

You'll then be prompted for a new password. When you type the password you will get no visual response acknowledging your typing.  Your password is still being accepted. Just type the password and hit Enter when you're done. You'll be prompted to retype the password. Do so and hit Enter again. 
Now the password should be reset. Type 
exit

to return to the recovery menu.

 After you get back to the recovery menu, select resume normal boot, and use Ubuntu as you normally would&#8212;only this time, you actually know the password!

---

### Post by pantazi on 2022-06-15
Not wishing to hijack this thread, but does your instruction mean that no Ubuntu desktop or laptop is safe if lost or stolen?

---

### Post by pbear42 on 2022-06-15
pantazi: That's correct.  Anyone with physical access to the machine can change the password (if they know how).  You can foreclose the easy procedure described by RB by setting a root password (not enabled by default), but the machine would remain vulnerable to anyone who knows how to boot a live session (which is more people than know how to reset the password).  The only way to secure a computer is encryption.  Second best would be to enable the BIOS/UEFI password.

Bouwense: I realize it's widely believed, but the file system isn't mounted read-only in the root shell.  Give it a try.  There's no need to remount.  Hasn't been since at least 16.04.

sundarash: If you mean you tried RB's procedure and were required to enter a root password, that means you set one.  If that's what you mean, your best alternative is to use chroot in a live session.  If not known, determine location of root partition, e.g., with [COLOR=#ff0000]sudo blkid[/COLOR].  Mount root partition (modify sda2 if appropriate): [COLOR=#ff0000]sudo mount /dev/sda2 /mnt[/COLOR].  Invoke chroot: [COLOR=#ff0000]sudo chroot /mnt[/COLOR].  Reset password: [COLOR=#ff0000]passwd sundarash[/COLOR] (or whatever the actual username).  Enter password when prompted (twice).  While you're at it, you might as well reset the root password: [COLOR=#ff0000]passwd root[/COLOR] (use the same password, entering it twice).  Exit chroot: [COLOR=#ff0000]exit[/COLOR].  Unmount: [COLOR=#ff0000]sudo umount /mnt[/COLOR].  Shutdown live session and boot main system.

---

### Post by Hreinsi on 2022-06-15
reinstall

---

### Post by grahammechanical on 2022-06-15
> o reset the password, type
passwd username
where username is the username you want to reset.


I take that to mean that the thief needs to know the username of the owner of the machine. If the machine is set to automatically log in then anyone can use the machine to a limited extent. Any command that needs the administrator (sudo) password will not be processed without that password.

Of course, there is nothing to stop the thief or finder from installing a new OS and making the machine their own or selling it on.

Regards

---

### Post by pbear42 on 2022-06-15
> **grahammechanical said:**
> ... the thief needs to know the username of the owner of the machine. 

That's not difficult to figure out, but we are getting a bit off-topic.  The main thing on this point, and I'm sure you agree, is that a login password isn't meaningful security.

---

### Post by pantazi on 2022-06-16
pbear42, thank you for the clarification. I am concerned that the concise answer to the OP's question is now open to all and sundry but perhaps I am naive in believing that a strong password is desirable. The slightly off-topic replies really deserve a separate thread as it is an important topic.

---

### Post by TenPlus1 on 2022-06-16
While it's possible to change a user password if lost, even in windows machines, encrypting your hard-drive will make sure files are kept safe.

---

### Post by web-user on 2022-06-18
If you system is not encrypted, you always can use the chroot+passwd trick. In the other case it is impossible to recover your system...

---

### Post by TheFu on 2022-06-20
> **pantazi said:**
> Not wishing to hijack this thread, but does your instruction mean that no Ubuntu desktop or laptop is safe if lost or stolen?

No computer is safe if lost or stolen.

The data on it, if encrypted using modern encryption tools, will be safe with a few assumptions. The main assumption is that the computer needs to be powered off and the partitions/storage unmounted. This is called "storage at rest" and applies to all computers and devices.

The risks aren't ubuntu, linux, unix specific. MS-Windows, OSX, BSD, WOPR, and any portable storage each have the same requirements for data security.

A login password **is** part of system security.  Think of the alternative.  Anyone with a flash drive can walk by, plug in the drive, have it automatically run stuff (with malware) that uses the automatic  mount and  driver install features most desktops have setup by default, then completely pwn the system. Takes 15 seconds.  But with a password, they have to either reboot or have a method to get passed the password prompt.

Almost all devices will allow an OS to be booted from flash storage.  Then we can run whatever OS we like and if that OS has software that can access the internal storage, we have full access to it ... if it isn't encrypted.  The flash drive we all create to install our Ubuntu Desktop OSes is perfect for this - just choose "Try Ubuntu" instead of installing.  Then access to the local storage however you like.  There are Window tools that will overwrite the Windows password ... and there are techniques covered 1000x on the web to change any user's password on Linux using this method with a chroot.  Any web search will find those articles.  

There are multiple other ways of changing a user's password on Linux ... using the Recovery mode from Grub and dropping to a root shell will let anyone change a password on the system.  That's probably the easiest.  But the chroot and grub methods may work too. Just depends on whether the system was setup with a grub password to prevent changes.

But ... if the entire OS is encrypted, none of those methods will likely work, at least not without know the decryption key.

---

