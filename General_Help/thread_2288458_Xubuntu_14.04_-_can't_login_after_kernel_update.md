---
title: "Xubuntu 14.04 - can't login after kernel update"
date: 2015-07-27
forum: General Help
---

### Post by sorceror171 on 2015-07-27
Updated a Xubuntu 14.04 x86_64 installation to kernel 3.13.0-58-generic, and now I can't log in anymore. I am ***_absolutely _*** using the correct password, but I nevertheless get "Incorrect password, please try again".

The specific sequence was:

1. Had some updates installed late last week, didn't bother with restarting then.
2. Today, hit the "restart now".
3. After reboot, successfully logged in and saw more updates available.
4. Ran update, only saw kernel packages available, updated and rebooted.
5. Tried to log in at screen, failed. Tried to log in via SSH, failed.

This is a real problem, because it's got an encrypted home directory and I don't have the key. I can log in as a guest, but that's it. Has anyone else run into this problem? I'd try downgrading the kernel but there's only one user on the system...

---

### Post by monkeybrain20122 on 2015-07-27
Can you log in by booting into the previous kernel? When booted up keep pressing the shift key until the boot menu appears , then go to advanced options or something like that and choose the previous kernel to boot. If that works, just delete the new kernel (image + headers totally 4 files) from synaptic. To prevent the kernel from updating, in synaptic search for the kernel you are now using (image and headers, totally 4 files) right click and choose pin packages. Now there are two things to keep in mind
1) you don't want to pin the kernels indefinitely because at some point in the future you may want a security updates. So wait a month or so and unpin the packages and see if it upgrade to something newer than the bad kernel
2) This works only if you upgrade with synaptic. If you run sudo apt-get upgrade from the terminal the pin would not be respected.

Now go file a bug report. [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

P.S. I always hate it that Ubuntu doesn't show the menu at boot up, it is an instance of sacrificing functionality for appearance IMO. To change this behaviour, from the terminal
```
gksudo gedit /etc/default/grub
```
Then place a # in front of the line 
> GRUB_HIDDEN_TIMEOUT=0
 

Then save and run
```
sudo update-grub
```

---

### Post by sorceror171 on 2015-07-27
I'd rebooted once, but another reboot seems to have fixed the problem. I'm logged in now, and you'd better believe I'm backing up the encryption key.

I'll keep an eye on it, but I may have to chalk this up to 'one of those things'.

---

