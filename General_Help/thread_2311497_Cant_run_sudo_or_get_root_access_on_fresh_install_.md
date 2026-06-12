---
title: "Cant run sudo or get root access on fresh install of ANY linux distro, pw wrong!"
date: 2016-01-27
forum: General Help
---

### Post by sharrukin on 2016-01-27
Hi,

Ive seen this issue all over the net, with convoluted or few unclear solutions.  After a fresh successful install of ubuntu (currently running now within virtualbox), mint, or kali linux, cant run sudo or get root access like to change a password or system settings, or run sudo commands.  I know my user, passw I created in installation wizard were 'dev1' and 'easy'   I did all the install steps carefully.  However no matter what I do the password came up as incorrect.  I try switching users and get locked out, the only way into the admin account is through a system restart.  This is super frustrating Ive spent hours upon hours trying to figure this out just being pi$$ed off.  I cant set a new password because the original I made wont work, and I get denied from any settings changes, even though my account is admin.   Any solutions would be great, seeing as all my dev work is at a standstill.  Sigh

---

### Post by buzzingrobot on 2016-01-27
You installed Ubuntu/Mint/Kali, created a user "dev1" during the install with the password "easy"?  Can you log on to an Ubuntu session at all with that combination? 

By default, on Ubuntu and Mint, "sudo dev1 <some command>" should prompt for dev1's password.  Kali is based on Debian, and, as I recall, straight Debian requires a username to be added to sudoers for "sudo" to work, and the "sudo" package may also need to be installed.

How are you "switching users"?  You need to user sudo to create new users in Ubuntu.  You'll also be prompted for it if you use the "Users" panel in System Settings (which you say you can't access).

The root user is locked in Ubuntu/Mint. You can't log in as root or use su to become root.

---

### Post by Dennis N on 2016-01-27
Try Google Search with "ubuntu recover user password". Lots of matches.

---

