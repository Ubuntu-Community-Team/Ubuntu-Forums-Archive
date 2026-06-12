---
title: "How do I restore my system from a TAR backup?"
date: 2007-12-16
forum: General Help
---

### Post by tuproxy on 2007-12-16
I can't login to my linux box but I can SSH into it.  I have made a few TAR backups and want to use one to re-install the OS.  

What I would like to do first is backup my RAID configuration and my SAMBA settings.  Samba is the most important, if the RAID isn't possible, no big deal.  

What file do I need to backup Samba and how do I extract the TAR file over my current OS.  Is there anything special I need to do first?

---

### Post by cmnorton on 2007-12-16
This is most curious. If you can ssh into your system and not login, I'd be wanting to fix that first. If you can ssh, you can get a lot of diagnostic information from ps and /var/log/syslog and /var/log/messages for starters.

When you say recover system from tar, what did you tar? Did you make an image, backup from root, or something else?

---

### Post by tuproxy on 2007-12-16
> **cmnorton said:**
> This is most curious. If you can ssh into your system and not login, I'd be wanting to fix that first. If you can ssh, you can get a lot of diagnostic information from ps and /var/log/syslog and /var/log/messages for starters.

When you say recover system from tar, what did you tar? Did you make an image, backup from root, or something else?

I created a TAR file, of the system, as root when the OS was a fresh install.  I have it saved on the system.  I put the file back into the root dir and extracted it over the corrupt OS.  I used PuTTy to get back into the system and extracted the tar image.

I wish I would have known before as to what files to check.  The system just hung on the GUI with the Ubuntu bar across the screen.  I decided to check my mapped drives and was able to access everything.  

After the extraction, I still had the hanging problem, so I decided to re-install 7.04 instead of running 6.10

Now I'm having a problem with GRUB after the 7.04 install  :(

---

