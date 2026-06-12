---
title: "If one moves their encrypted Harddrive with the OS to another computer"
date: 2018-06-19
forum: General Help
---

### Post by tuddungoggo on 2018-06-19
Hello,

This may be a very stupid question (especially for a CS graduate). I have never done this before, but if I was to move an encrypted Drive from one computer to another, there should be no drawbacks right? I am just curious. Again, you can laugh at me if you want lol (haha this guy has a CS degree and does not even know).

---

### Post by oldfred on 2018-06-19
Yes, but.

Is hardware similar? If changing to new hardware and not same drivers you may have issues booting old drive.

If booting another drive, is it also LVM with encryption? If not it may not have the LVM tools required to mount it, nor the encryption tools needed to load it. You can add those.

       Mount LVM - duckhook
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372) 
            Recover files on encrypted drive
[https://ubuntuforums.org/showthread.php?t=2382995](https://ubuntuforums.org/showthread.php?t=2382995)
[https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line](https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line)

---

