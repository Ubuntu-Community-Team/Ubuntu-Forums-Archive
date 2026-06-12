---
title: "[SOLVED] 13.04 reboot, system logs into an account, no password!"
date: 2013-06-15
forum: General Help
---

### Post by ladasky on 2013-06-15
Hello everyone,

When I first installed 13.04, I had the problem with my system not shutting down correctly that many other users had.  I tried _[these suggestions]("http://ubuntuforums.org/showthread.php?t=2141890&page=2&p=12680281#post12680281")_.  They may have helped. On the first reboot and subsequent shutdown, it appeared that nothing had changed.  But on the second reboot, after I tried a manual shutdown from the terminal, *sudo shutdown -h now*, all shutdowns proceeded correctly after that -- including from the GUI.

While I've apparently fixed the shutdown problem, I have a second problem which persists. Initially, I thought the two problems were a single, connected problem.  Maybe not.

I have two user accounts on my system, the primary account and a second account without administrator privileges.  My system skips the login screen when it boots, and jumps straight into my secondary account!  I don't need to supply a password or anything!  If I log out of that account and then try to log back in, then I need my password.  But not when I first turn the system on.

This would be a rather significant security hole for anyone with a laptop.  Although my machine is not portable, and safe in my home, I would still like to fix this problem.  

Here is my current configuration:

[LIST]
[*]Gigabyte GA-MA78-US2H motherboard, 8 GB RAM, AMD x6 1100T CPU
[*]Ubuntu 13.04 OS, 64-bit
[*]NVidia 460 family GPU card
[*]Ubuntu's recommended NVidia driver, version 310.44 
[*]Western Digital Caviar Black 640 GB hard drive, LVM partitions for boot, root, and home, on top of gpt
[/LIST]

Any suggestions?  Thanks!

---

### Post by ladasky on 2013-06-17
I've waited two days before bumping this thread.  I was hoping that an automatic software update might fix the problem.  No luck so far.  My system continues to jump straight onto the desktop of my secondary account when I boot, bypassing the login screen and thus, the password.  

Before I install 13.04 on my laptop, I want to make sure that I know how to keep this rather significant security problem from happening.

Any suggestions?  Thanks.

---

### Post by Cheesemill on 2013-06-17
Go to Settings > User accounts and make sure that automatic login is switched off.

---

### Post by ladasky on 2013-06-17
:redface: I don't know how automatic login was selected for that account, I must have had a stray click with my mouse?  Problem solved, thank you Cheesemill!

---

