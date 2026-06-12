---
title: "How do I reset the password in WSL2 in Ubuntu 20.4LTS?"
date: 2021-07-18
forum: General Help
---

### Post by tangara on 2021-07-18
I was following a video that said : 

Change to the root user after logging in:

    sudo su - # I found out we can do sudo -s

So, here's where I am stuck:

tangara@DESKTOP-SB41UI7:~$ sudo -s
[sudo] password for tangara:

Now, it seems the root user is me tangara.

But, I have forgotten my password.

How do I reset it ?

I am on Windows 10 system.

Hope someone can help me out on this.

Tks a million

---

### Post by TheFu on 2021-07-18
I don't know anything about WSL2.
Setting any root password is not the Ubuntu way.  In general, Ubuntu's root account doesn't have any password.  
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) 
The **passwd** command can set the password for any user, however.

But WSL2 is from Microsoft and they can do whatever they want, as we've learned over the decades.

There is only 1 userid named "root".  Your userid is ****not**** root on ubuntu. It may be able to elevate privilege for a short time using sudo, but that isn't the same as "being root."

---

### Post by dragonfly41 on 2021-07-18
> [COLOR=#000000]But WSL2 is from Microsoft and they can do whatever they want, as we've learned over the decades.[/COLOR][COLOR=#000000]

Be aware that if you are introduced to Windows 11, from what I read. Microsoft forces secure boot on always.
Unlike today where it is optional.
The conclusion I draw is that Windows 11 and Ubuntu cannot coexist in dual-boot mode, other than using the native Ubuntu offered by WSL2 which is not dual-boot.  I have bookmarked that little nugget of information.

[/COLOR]

---

### Post by TheFu on 2021-07-18
> **dragonfly41 said:**
> Be aware that if you are introduced to Windows 11, from what I read. Microsoft forces secure boot on always. 

Ouch. Happy to be using virtual machines for Windows instead.

---

### Post by tangara on 2021-07-19
sorry guys, I managed to install the things I need in ubuntu system but now how do I make it change back to tangara@destop with the $ ?

---

### Post by QIII on 2021-07-19
Type 

```
exit
```

---

### Post by CatKiller on 2021-07-19
> **dragonfly41 said:**
> Microsoft forces secure boot on always.
Unlike today where it is optional.
The conclusion I draw is that Windows 11 and Ubuntu cannot coexist in dual-boot mode, other than using the native Ubuntu offered by WSL2 which is not dual-boot.

Ubuntu works fine with Secure Boot. The only caveat is that if you're using kernel modules that aren't signed by Canonical (VirtualBox and the Nvidia driver being prime candidates) then you need to sign them yourself and tell your UEFI to trust your signature.

---

### Post by dragonfly41 on 2021-07-19
To close on this point about secure boot I [searched further and found this thread]("https://www.reddit.com/r/linuxquestions/comments/o7igt9/can_i_dual_boot_linux_with_windows_11/") which indicates that I can use ReFIND as signed boot loader which is ideal for my own usage (I use ReFIND today in dual boot).

---

