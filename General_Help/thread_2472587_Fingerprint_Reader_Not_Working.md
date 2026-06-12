---
title: "Fingerprint Reader Not Working"
date: 2022-03-04
forum: General Help
---

### Post by cobras on 2022-03-04
Hey Folks,

I've searched the threads and can't find one that solves my specific problem.

I've got an ASUS A510Q laptop running Ubuntu 20 on which I've not been able to get the fingerprint reader to work properly.  Originally, I was able to enroll my fingerprint in the Authentication and Login settings and enable Fingerprint Login, but I was never able to actually use it.  My finger print would not log me in.  Login would prompt me for my fingerprint but it would not accept it or it would just fail to read it.

I found a guide that seemed to address my issue:  [https://www.tec4tric.com/linux/enable-fingerprint-login-in-ubuntu](https://www.tec4tric.com/linux/enable-fingerprint-login-in-ubuntu)

Following this guide lead me to where I would need to select Fingerprint authentication at the PAM window, but that option is not present.  I tried selecting Ubuntu authentication, but that did not help.  I've  since gone back and de-selected that, but now I'm in a worst state than when I started.

Now when I go to Settings -> Users the Fingerprint Login option is grayed out (inactive).

How can I fix this?

---

### Post by #&amp;thj^% on 2022-03-04
I just have to ask, you did see this "This tutorial is for this driver &#10145; Elan Microelectronics Corp. ELAN:Fingerprint, specifically the 0c4f device Id."
Check with:
```
lsusb
```
And did you follow it word for word? Referring to this "git clone https://gitlab" if not don't.
Example: If you type "man pam-auth-update" you will learn that it gets the new configuration from /usr/share/pam-configs/
So we need to know before proceeding

---

### Post by cobras on 2022-03-04
> I just have to ask, you did see this "This tutorial is for this driver &#10145;  Elan Microelectronics Corp. ELAN:Fingerprint, specifically the 0c4f  device Id."

I did notice and checked. At the time I thought I had a match, but I just double checked and got the following result:  *Bus 001 Device 003: ID 04f3:0903 Elan Microelectronics Corp.*  I can't swear to it, but I seem to remember the "ELAN:Fingerprint" part was there as well.

> And did you follow it word for word? Referring to this "git clone https://gitlab" if not don't.
Example: If you type "man pam-auth-update" you will learn that it gets the new configuration from /usr/share/pam-configs/

Not sure what you mean here, but I did follow it word for word.

Thanks.

---

### Post by mIk3_08 on 2022-03-05
> **cobras said:**
> I did notice and checked. At the time I thought I had a match, but I just double checked and got the following result:  *Bus 001 Device 003: ID 04f3:0903 Elan Microelectronics Corp.*  I can't swear to it, but I seem to remember the "ELAN:Fingerprint" part was there as well.
Not sure what you mean here, but I did follow it word for word.
Thanks.
Can you please run the command below:
 ```
lsusb
```
And post it to this thread wrap with code so that people in the community that willing to help you will be aware of what fingerprint hardware you have.  regards.

---

### Post by #&amp;thj^% on 2022-03-05
> **cobras said:**
> 
Not sure what you mean here, but I did follow it word for word.

Thanks.

That was what I thought, sorry but I have some bad news though: [https://linux-hardware.org/?id=usb:04f3-0903&page=1](https://linux-hardware.org/?id=usb:04f3-0903&page=1)
I had one in the shop I could never get it to work even went as far as kernel 5.16 and nada.:(

---

### Post by cobras on 2022-03-05
> **mIk3_08 said:**
> 
And post it to this thread wrap with code so that people in the community that willing to help you will be aware of what fingerprint hardware you have.  regards.

```
jorge@rhoxanne:~$ lsusb
Bus 001 Device 005: ID 13d3:5a07 IMC Networks 
Bus 001 Device 004: ID 13d3:3526 IMC Networks 
Bus 001 Device 003: ID 04f3:0903 Elan Microelectronics Corp. 
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. Root Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I'm adding that I seem to remember that before all the changes the line for Bus 001 Device 003 ended with ELAN:Fingerprint.  But I'm not sure.

---

### Post by cobras on 2022-03-05
I was once on an unrelated search and ran into a couple of threads (here or elsewhere) about the fingerprint reader on Asus machines.  The gist seemed to be that Asus machines on Linux just won't accommodate the fingerprint reader, though I seem to recall ONE thread that solved the issue.

At this point I think I'd be happy to just undo what I've done.  My system is not acting right.

---

### Post by #&amp;thj^% on 2022-03-05
> **cobras said:**
> 
At this point I think I'd be happy to just undo what I've done.  My system is not acting right.

I had pointed out that  you will learn that it gets the new configuration from **/usr/share/pam-configs/**
Don't proceed with any actions just yet, I'm running some tests now.
I'll be back.
Paste back this please:
```
cd /usr/share/pam-configs/ && ls && stat *
```

---

### Post by cobras on 2022-03-05
```
jorge@rhoxanne:~$ cd /usr/share/pam-configs/ && ls && stat *
capability  gnome-keyring  mkhomedir  systemd  unix
  File: capability
  Size: 124           Blocks: 8          IO Block: 4096   regular file
Device: 813h/2067d    Inode: 11275981    Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2022-03-04 10:09:24.078271845 -0800
Modify: 2020-02-17 04:44:20.000000000 -0800
Change: 2022-01-27 19:45:38.719038790 -0800
 Birth: -
  File: gnome-keyring
  Size: 152           Blocks: 8          IO Block: 4096   regular file
Device: 813h/2067d    Inode: 11275983    Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2022-03-04 10:09:24.078271845 -0800
Modify: 2020-03-11 02:06:10.000000000 -0700
Change: 2022-01-27 19:45:38.719038790 -0800
 Birth: -
  File: mkhomedir
  Size: 154           Blocks: 8          IO Block: 4096   regular file
Device: 813h/2067d    Inode: 11276439    Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2022-03-04 10:09:24.090271550 -0800
Modify: 2020-08-11 17:15:04.000000000 -0700
Change: 2022-01-27 20:14:55.410749672 -0800
 Birth: -
  File: systemd
  Size: 182           Blocks: 8          IO Block: 4096   regular file
Device: 813h/2067d    Inode: 11275971    Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2022-03-04 10:09:24.106271156 -0800
Modify: 2021-07-01 08:44:19.000000000 -0700
Change: 2022-01-27 20:15:53.614363363 -0800
 Birth: -
  File: unix
  Size: 668           Blocks: 8          IO Block: 4096   regular file
Device: 813h/2067d    Inode: 11276449    Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2022-03-04 10:09:24.106271156 -0800
Modify: 2021-09-16 23:14:18.000000000 -0700
Change: 2022-01-27 20:15:48.085960985 -0800
 Birth: 
```

I'll wait for feedback.

---

### Post by #&amp;thj^% on 2022-03-05
That all looks ok, and there is nothing newly related installed there.
You'll want to undo some of what you did.
Now it gets fun:
```
cd libfprint && git checkout v1.90.5 && cd ..
```
```
sudo nano libfprint/libfprint/drivers/elan.h
```
I'm assuming it's in your home directory, any way remove this line:
```
{.vid = ELAN_VEND_ID, .pid = 0x0c4f, .driver_data = ELAN_ALL_DEV}
```
the line below it should read:
```
{.vid = 0, .pid = 0, .driver_data = 0}
```

Reinstall: >(Providing it was there on your initial install)
```
sudo apt install fprintd libfprint-2-2
```
And I'm not sure why you need this now so:
```
sudo apt remove --autoremove gtk-doc-tools
```
The rest of what I could see from your link isn't going to hurt your system so Ill leave that for you to decide.

---

### Post by cobras on 2022-03-05
```
{.vid = ELAN_VEND_ID, .pid = 0x0c4f, .driver_data = ELAN_ALL_DEV}
```

I had actually already removed this line, but that was all I could think of to undo.  I'll try the rest.

Thank you.

---

### Post by MAFoElffen on 2022-03-05
For Gnome above version 3.38:
[https://itsfoss.com/fingerprint-login-ubuntu/](https://itsfoss.com/fingerprint-login-ubuntu/)

Ubuntu 20.04 is Gnome Version 3.36...

---

### Post by cobras on 2022-03-05
Thanks.  I checked that out before resorting to this forum.  Does not apply to me.

Oh, is your point that I need to upgrade my OS?

---

### Post by cobras on 2022-03-05
> **1fallen said:**
> That all looks ok, and there is nothing newly related installed there.
You'll want to undo some of what you did.
Now it gets fun:
```
cd libfprint && git checkout v1.90.5 && cd ..
```
```
sudo nano libfprint/libfprint/drivers/elan.h
```
I'm assuming it's in your home directory, any way remove this line:
```
{.vid = ELAN_VEND_ID, .pid = 0x0c4f, .driver_data = ELAN_ALL_DEV}
```
the line below it should read:
```
{.vid = 0, .pid = 0, .driver_data = 0}
```

Reinstall: >(Providing it was there on your initial install)
```
sudo apt install fprintd libfprint-2-2
```
And I'm not sure why you need this now so:
```
sudo apt remove --autoremove gtk-doc-tools
```
The rest of what I could see from your link isn't going to hurt your system so Ill leave that for you to decide.

I've taken these steps and my system is a bit more stable.  But now when I try to add a fingerprint there's a message that the fingerprint device is disconnected.  Worse, on boot up I'm prompted for my password but only for a couple of seconds before it starts up without it.

---

### Post by cobras on 2022-03-06
```
sudo apt-get install --reinstall ubuntu-desktop
```

Will this command get me back to square one without loosing all my data?

---

### Post by #&amp;thj^% on 2022-03-07
Sorry I kind of forgot you, but to answer it's worth a shot.

---

### Post by cobras on 2022-03-07
No, that didn't do it.  But I think I figured out why I'm logging in without having to login; the fingerprint reader is not working so my machine is using facial recognition to verify it's me. :P

---

### Post by cobras on 2022-03-08
So I tried upgrading to Ubuntu 21 thinking I'd get a fresh start.

Ubuntu 21 won't let me log in.  Does not recognize my password and will not let me reset the password through the root shell.

Guess I'll stick to Windows.  Thanks for all the help.

---

