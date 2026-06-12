---
title: "[SOLVED] Authorize Me!"
date: 2008-05-15
forum: General Help
---

### Post by CrusaderAD on 2008-05-15
Hello... I've got a few problems here. I'm not 100% new to Ubuntu but I am still considered a Windows Convert. I recently upgraded to 8.04 Hardy. The problems I'm having are the following:

1. I can't share folders on the network, I get this message:
'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

2. I can't add/edit users under user settings. Everything is grayed out and the unlock button hangs and eventually gives me "Can not Authenticate"

3. I tried the "Manage System Configurations" but when I go to apply anything (I click grant) it doesn't do anything.

Any help is appreciated. Thanks!

---

### Post by Monicker on 2008-05-15
The first issue is related to a known but, check the Samba Shares section at this link: [http://ubuntuforums.org/showthread.php?t=773851]("http://ubuntuforums.org/showthread.php?t=773851")

Its possible you may also be suffering from the "unable to resolve host" issue mentioned at the same link. To verify, open a terminal and try to execute a command using sudo: sudo ifconfig -a

---

### Post by CrusaderAD on 2008-06-20
Solved it. You can just add the folder you want to share by editing the /etc/samba/smb.conf file. Even if when you try to do it via GUI and it denies you.

---

