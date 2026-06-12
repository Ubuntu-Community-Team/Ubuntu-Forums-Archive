---
title: "file /boot/vmlinuz-3.5.0-25-generic not found"
date: 2013-03-18
forum: General Help
---

### Post by MourningsEnd on 2013-03-18
Well I was installing JoliOS on my system, but it messed with my main partition.  I came to realize that it was trying to install in my /boot on Xubuntu.  So I went and deleted the files there, but it seems I deleted some Xubuntu as well.

When I try to boot I get: 

"error: file '/boot/vmlinuz-3.5.0-25-generic' not found.

error: you need to load the kernel first."

So I assume I accidentally deleted the kernel?  How would I go about getting that back?

---

### Post by Impavidus on 2013-03-18
Can you still boot an old kernel? If so, you can repair by booting into the old kernel and reinstalling 3.5.0-25. Else you need your live disk.

---

### Post by MourningsEnd on 2013-03-19
How would I boot into an old kernel?

---

### Post by Bashing-om on 2013-03-19
MourningsEnd; Hi!

Boot older kernel: As you have an additional operating system installed, I expect when you boot up you boot first to a grub boot menu (??)
(else hold shift key down as soon as bios screen clears). Depending on the 'buntu version installed is the location of older kernels to boot up. Is there a submenu "older kernels" or some such? All that is needed is to arrow down to the desired kernel and press the enter key. Your system will attempt to boot up with that older kernel.
[INDENT=3]
hth

[/INDENT]

---

### Post by MourningsEnd on 2013-03-20
I can navigate there, but none of the kernels work.  Is there a way to restore them with a CD with Xubuntu on it?  I tried the live version and copying the stuff in /boot/, but it did not work.

Edit: I tried this tutorial: [http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels)

But when I try to ```
apt-get update
``` in chroot I get : 

```
E: Could not open lock file /var/lib/apt/lists/lock - open (2: No such file or directory)

E: Unable to lock the list directory
```

---

### Post by Bashing-om on 2013-03-20
MourningsEnd;

The "Could not open lock file" is generally indicative that another instance of the package manager is open. Insure update manager, software sources synaptic and any other terminal package handlers are closed.

Can't boot any instance of ubuntu, might try this (for mapping):

1. Highlight an old kernel from the Grub 2 menu.
2. Press "e" to open the menu entry for editing.
3. Remove the entire "search" line. Use the Up/Dn cursor to place at the start of the line and hold the DEL key.
4. On the "linux" line, change the part "root=UUID=<long number>" to "root=/dev/sdXY" with X being your Ubuntu drive and Y being your Ubuntu partition. Leave the rest of the line as is.
5. CTRL-x to boot.
if works -> Terminal code: ```
sudo update-grub
```[INDENT=3]
hope that helps

[/INDENT]
[INDENT]
[/INDENT]

---

### Post by MourningsEnd on 2013-03-21
> **Bashing-om said:**
> MourningsEnd;

The "Could not open lock file" is generally indicative that another instance of the package manager is open. Insure update manager, software sources synaptic and any other terminal package handlers are closed.

Can't boot any instance of ubuntu, might try this (for mapping):

1. Highlight an old kernel from the Grub 2 menu.
2. Press "e" to open the menu entry for editing.
3. Remove the entire "search" line. Use the Up/Dn cursor to place at the start of the line and hold the DEL key.
4. On the "linux" line, change the part "root=UUID=<long number>" to "root=/dev/sdXY" with X being your Ubuntu drive and Y being your Ubuntu partition. Leave the rest of the line as is.
5. CTRL-x to boot.
if works -> Terminal code: ```
sudo update-grub
```[INDENT=3]
hope that helps

[/INDENT]
[INDENT]
[/INDENT]


I tried that, and it does not work.  Also, nothing else is open for the lock to occur.

---

### Post by Bashing-om on 2013-03-21
MourningsEnd; Well well well;

As no other instance of the package manager is open -> chroot environment:
Lets rebuild the respective package manager's database then:
```
sudo apt-get clean
sudo rm /var/lib/apt/lists/*
sudo rm /var/lib/apt/lists/partial/*
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```
Maybe this will also install a new kernel. (???)

Get the package manager work'n and then work on grub's booting, ok ?
By the way, that kernel install tutorial is great, will mark it also for a reference.
[INDENT=2]
try'n to help
[/INDENT]

---

### Post by MourningsEnd on 2013-03-22
I keep getting weird ass errors, so I believe I will just format.  The only reason I saught out a solution was for experience.  Thank you for the help though.  ^^

---

### Post by Bashing-om on 2013-03-22
MourningsEnd;

I am glad to be of any assistance and welcome the opportunities to learn more of this facinating operating system.

I agree at this point the fastest way to get back to a stable system is (re)install. Needless to say back up your data prior to wiping the current system.
For a continued learning experience one might (re)install with the same user name and password. I have found many times that system settings and configs are copied across to the new install and nothing is lost. If there are problems then one can wipe the partitions with GParted and do the installation from scratch.

To continue to trouble shoot the present install, might look at how and what is bound in making your current chroot environment. Maybe the required libraries are not available ?
[INDENT=3]I remain open

[/INDENT]

---

