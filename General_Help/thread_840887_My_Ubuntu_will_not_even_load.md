---
title: "My Ubuntu will not even load?"
date: 2008-06-25
forum: General Help
---

### Post by rofl copter on 2008-06-25
Someone on my forums site said that for Linux, i should go to wubi-installer.org and install ubuntu from there. So I did. When I restart my pc, it asks if I would like to run it in either Windows Vista or Ubuntu. I select Ubuntu, and then it says press ESC for menu, I just skip that, and it loads, then this pops up:
```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```
What do I do?

---

### Post by ajmorris on 2008-06-26
I have not run Wubi before... However, when you get to that prompt, login, and run sudo dpkg-reconfigure -phigh xserver-xorg to reconfigure xorg (or you could run sudo xfix) Although... if it was your X that was the issue.. you should get some X errors... Could you post the output of the command sudo dmesg and the contents of /var/log/syslog and /var/log/Xorg.0.log for the logs, you might want to boot some sort of linux live cd, because you cant copy and paste the contents from that file whilst at this prompt. You could also do a remote pastebin if you dont have a live cd, or log in remotely to your box from the pc that you came on the forums from... but these are probably too difficult for you if this is your first time on linux.

You could also consider a dual boot or a Virtual Machine instead of running Wubi...

AJ

---

### Post by urlstevens on 2008-06-30
I was having the same problem/error message and also used the Wubi application to "help" me set up a dual-boot Windows/Ubuntu (heron) system.  Heron worked fine initially, but when I booted into windows then came back to Heron, I started getting the same "busybox" prompt.  

I was finally able to resolve this problem by shutting down Ubuntu, rebooting Windows, and _uninstalling_ Spybot Search & Destroy (my spyware, adware, etc. killer).  I also disabled my virus scanner.  I then shut Windows down and rebooted Heron. . .it loaded up fine, although I still have an ACPI error  (cooling device can't be turned on), which a lot of other people seem to be having.   

I have not looked into the spyware / virus definitions to see if there is some type of ubuntu/linux killer in there, but within Spybot, I did have the “immunize” function activated which apparently blocks registry changes and other “spyware-like” activities.  The partitioning and other changes performed by Wubi may appear spyware/virus/malware-like, but I'll let someone smarter look into that. . .

Bottom line, nuking my Windows-based virus and spyware killers got me back up and running on Ubuntu. . .

---

