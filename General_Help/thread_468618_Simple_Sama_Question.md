---
title: "Simple Sama Question"
date: 2007-06-09
forum: General Help
---

### Post by Turboaaa2001 on 2007-06-09
Ok, I posted something about this in the networking section but no one answered (which is odd since I always get great help here).

Anyway I'm having a problem finding the "smb.conf" file in version 5.01. I'm using the older version because I do not know how to install the newer ones without going through the GUI. And the reason I can't use the GUI is because I have a bad stick of RAM.  It has enough addresses to run the command line and a Samba server but nothing else.

I really need help with this. I'm going coo coo bananas](*,) over it. I looked everywhere including "/etc/Samba/smb.conf" where it's supposed to be, thumbed through my Unix For Dummies Quick Reference 4th Edition, and even pulled out the  1,117 page Red Hat Fedora and Enterprise Linux Bible and prayed over it. So far the Linux Gods nor the Computer Gods have answered my prayers.:x

Please help me. If you could either tell me where to find the "smb.conf" file or how to install 6.06 or later without using the Live-CD GUI I will be very thankful and will offer a pure virgin Athlon XP 3000+ as a sacrifice to the Computer Gods on your behalf....\\:D/

---

### Post by thatcooldude on 2007-06-09
Don't know if you mistyped it here on the forum, but I have the smb.conf file under /etc/samba/smb.conf

If it isn't there, you can always uninstall and reinstall it, and have it regenerate the conf file for you.

sudo apt-get remove samba
sudo apt-get install samba

Should be under /etc/samba/smb.conf

Sorry, that's about all the expertise I have :(

---

### Post by Turboaaa2001 on 2007-06-09
Well any help is better than no help. And besides, you solved my problem.

OMG, I can't believe I forgot to install it!!!! I feel as stupid as a Windows only user....#-o

Well in any case, I thank you and will offer that sacrifice in your honor.[-o<

---

### Post by Turboaaa2001 on 2007-06-09
I do have another question, if someone could tell me how to change the Samba permissions within the "smb.conf"  to allow a Windows PC to access the drive and read/write without logging in?

It's really not that important because I will be trying on my own to figure it out. I have plenty of paper work (Unix for Dummies Quick Feference 4th Edition and the 1,117 page Red Hat Fedora and Enterprise Linux 4 Bible) and I plan on backing up the file and just messing with it.;)

---

