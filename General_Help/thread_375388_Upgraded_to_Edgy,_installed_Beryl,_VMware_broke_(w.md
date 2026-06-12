---
title: "Upgraded to Edgy, installed Beryl, VMware broke (worked the first time)"
date: 2007-03-03
forum: General Help
---

### Post by rainwalker on 2007-03-03
I upgraded to Edgy from Dapper about a week ago and immediately installed Beryl. It's all working fine, except for VMware. It was working earlier today, because I had started it out of curiosity (a friend had told me that upgrading broke it) and to my surprise, it worked! It did tell me, though, that a new version is out (version 1.0.2) and gave me a link to the VMware site. I downloaded the update, and was in the process of running the install script when it told me that it had to compile a working kernel for VMware to work. Oddly, it said that my kernel was compiled with version 4.0.2 or something like that and that the version set to be used was 4.1.3 (I think, I know that the first numbers were 4.0 and 4.1, I'm sort of guessing on the third numbers) and that using the newer version might cause VMware to crash. So I went through the whole process of changing the softlinks for gcc, and it still ended up using 4.0.3 instead of 4.0.2, but I went ahead and compiled the kernel with 4.0.3 anyway. It seemed to work, but I had to install the header files, which I didn't feel like doing, so I aborted the install script and closed the terminal. 
That was earlier today, and I just got home and tried to start VMware, but all that happens is the little "Starting VMware Server Console" message appears in the task bar, but then it disappears and VMware never starts.
Any ideas as to what might be going wrong?

---

### Post by PilotJLR on 2007-03-03
Aborting the install script was bad... it doesn't want to compile a kernel module just for giggles.  :-)

Since edgy has a newer kernel, you need to run the install script again... that's it. beryl should have nothing to do with it.

So install the kernel headers and gcc with:
```

sudo apt-get update
sudo apt-get install linux-headers-`uname -r` gcc build-essential

```

And then re-run the install script, so that it may build the required kernel module.

---

### Post by rainwalker on 2007-03-03
I ran ```
sudo apt-get install linux-headers-2.6.15-27-386 gcc build-essential
``` and got this:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.15-27-386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.15-27-386 has no installation candidate

What does this mean?

---

### Post by PilotJLR on 2007-03-03
Did the "sudo apt-get update" work? I'm not sure why you would get this error if the "apt-get update" is done just prior to the install command.

Also - consider rebooting into the -generic kernel instead of -386... -generic on Edgy is best for most computers.

---

### Post by rainwalker on 2007-03-03
It all worked.

I don't know how to boot into the kernels you're taling about, or even what kernel I've booted into right now

---

### Post by PilotJLR on 2007-03-03
Just to verify, are you typing in "sudo apt-get install linux-headers-`uname -r`" verbatim? Cause it's important the `uname -r` is in there...

If you did do that, then reboot and you'll see several kernel choices in the GRUB bootloader. Choose the newest kernel with the -generic suffix. For most computers, this is the best choice with Edgy. We can make it the default later, if this work okay.
Once you do that, rerun the 2 commands I posted earlier.

---

### Post by rainwalker on 2007-03-03
I put '2.6.15-27-386' intead of 'uname -r', because that's what it gives me when I enter it in a terminal. Am I supposed to just leave it?

---

### Post by PilotJLR on 2007-03-04
> **rainwalker said:**
> I put '2.6.15-27-386' intead of 'uname -r', because that's what it gives me when I enter it in a terminal. Am I supposed to just leave it?

No, that should be okay...

Since edgy is on the 2.6.17-11 kernel now, you can choose to either manually find and install the headers for the kernel you have now, or upgrade to the current one.
**I would recommend upgrading... with "sudo apt-get dist-upgrade".** Lots of updates will be applied, then reboot into the 2.6.17-11-generic kernel, and THEN install the kernel headers.

---

### Post by rainwalker on 2007-03-04
How do I check what kernel I'm running? Because I'm running Edgy and from what I can understand it doesn't look like I'm running the 2.6.17-11 kernel.

---

### Post by PilotJLR on 2007-03-04
"uname -r" tells you what kernel you are running...

This is the reason you need a dist-upgrade, so that you WILL have the current kernel.

---

### Post by rainwalker on 2007-03-04
I used the "official" upgrade method, with the update manager command and all that. Why didn't it upgrade the kernel then?

---

### Post by PilotJLR on 2007-03-04
I have no idea... I would have thought that it did.
I know this is a silly question, but after doing the upgrade, did you reboot and verify the newest kernel was selected in GRUB?

Regardless, I've already posted the commands to fix it.

---

### Post by rainwalker on 2007-03-04
No, I didn't I just booted up after it upgraded.

---

### Post by rainwalker on 2007-03-04
I've decided to just uninstall VMware, because I don't actually use it. Do you know how to un install it?

---

### Post by PilotJLR on 2007-03-06
I've actually never uninstalled it... as far as I know, you would need to just remove the vmware binaries... there are a few config files, but they are really small.


Did the commands I posted a few days ago not update your kernel?  (the dist-upgrade)

---

### Post by rainwalker on 2007-03-06
> I would recommend upgrading... with "sudo apt-get dist-upgrade". Lots of updates will be applied, then reboot into the 2.6.17-11-generic kernel, and THEN install the kernel headers.
I read that using apt-get can cause  alot of errors, are you sure that it's safe to do this?

---

### Post by PilotJLR on 2007-03-07
Apt-get and deb files are the basis for the entire OS's package management system... if this was inherently dangerous, then it wouldn't be worth turning on the computer!

There is, of course, always a possibility of a problem when you change kernels or packages... but it's unlikely.

So saying that apt-get is "full of errors" is flat out false.

If you do this, then reboot, it is likely you will be okay:
```

sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by rainwalker on 2007-03-07
I get
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by PilotJLR on 2007-03-07
Wow  ;-)

Please post /etc/apt/sources.list

---

