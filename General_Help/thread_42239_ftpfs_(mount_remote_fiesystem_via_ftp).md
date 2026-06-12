---
title: "ftpfs (mount remote fiesystem via ftp)?"
date: 2005-06-16
forum: General Help
---

### Post by bsnram on 2005-06-16
Hi,  Iam looing to mount a remote filesystem with ftp. (similar to mounting with smb). I googled around and found couple of soultions: alex, ftpfs,.  I want to know if anyone has any success with these and what works out of the box with mininal hack.

Thanks for your time
brahma

---

### Post by intangible on 2005-06-17
[QUOTE=bsnram]Hi,  Iam looing to mount a remote filesystem with ftp. (similar to mounting with smb). I googled around and found couple of soultions: alex, ftpfs,.  I want to know if anyone has any success with these and what works out of the box with mininal hack.

Thanks for your time
brahma[/QUOTE]
 If you just want it to be easy to use from Nautilus, try the **Connect to Server** option under the **Places** menu.  If you want it so that.

The easiest way to install ftpfs, so you can do regular filesystem mounts, is to use LUFS (it replaces the old ftpfs).

**sudo apt-get install lufs-source lufs-utils module-assistant**
**man module-assistant** to learn how to use it properly, then use it to install the lufs kernel module.
then:
**sudo lufsmount ftpfs://anonymous:anonymous@ftp.example.com/ /mnt/mountdir**

I've only used it a little bit, but seems to work okay.
Here's some more resource for you: [http://lufs.sourceforge.net/lufs/fs.html](http://lufs.sourceforge.net/lufs/fs.html)

If you need more detailed help, let me know.

---

### Post by robbie1 on 2005-07-09
[QUOTE=intangible]If you just want it to be easy to use from Nautilus, try the **Connect to Server** option under the **Places** menu.  If you want it so that.

The easiest way to install ftpfs, so you can do regular filesystem mounts, is to use LUFS (it replaces the old ftpfs).

**sudo apt-get install lufs-source lufs-utils module-assistant**
**man module-assistant** to learn how to use it properly, then use it to install the lufs kernel module.
then:
**sudo lufsmount ftpfs://anonymous:anonymous@ftp.example.com/ /mnt/mountdir**

I've only used it a little bit, but seems to work okay.
Here's some more resource for you: [http://lufs.sourceforge.net/lufs/fs.html](http://lufs.sourceforge.net/lufs/fs.html)

If you need more detailed help, let me know.[/QUOTE]
 I've done as you suggested above, but it seems to get stuck when I run the lufsmount command (it just sits there). What else can I do? I noticed there is a ftpfs module in module-assistant but it requires a package (ftpfs-src) not in the repos. Help!

---

