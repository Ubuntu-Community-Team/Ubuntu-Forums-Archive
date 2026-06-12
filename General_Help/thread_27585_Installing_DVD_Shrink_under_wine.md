---
title: "Installing DVD Shrink under wine"
date: 2005-04-16
forum: General Help
---

### Post by JDay on 2005-04-16
I'm trying to install the latest version of DVD Shrink with wine, from the backports repository. I had this working fine, previously, but I recently reformatted and now have the folloing problem: The installer runs fine until the point where it begins to actually install files, and I get the error "Access violation at address 77EC0DDB. Write of address 00730075." Any ideas?

---

### Post by bored2k on 2005-04-16
[http://ubuntuforums.org/showthread.php?t=27369&highlight=decrypter+thoggen](http://ubuntuforums.org/showthread.php?t=27369&highlight=decrypter+thoggen)
These guys might give you a hand.

---

### Post by shakin on 2005-04-16
[QUOTE=JDay]I'm trying to install the latest version of DVD Shrink with wine, from the backports repository. I had this working fine, previously, but I recently reformatted and now have the folloing problem: The installer runs fine until the point where it begins to actually install files, and I get the error "Access violation at address 77EC0DDB. Write of address 00730075." Any ideas?[/QUOTE]

If you follow my how-to about installing DVD Decrypter it walks you through installing the latest Wine from the official Wine repository as well as using winetools to configure it. I still haven't been able to get DVD Shrink to see my DVD drive.

---

### Post by Dromio on 2005-04-16
[QUOTE=bored2k][http://ubuntuforums.org/showthread.php?t=27369&highlight=decrypter+thoggen](http://ubuntuforums.org/showthread.php?t=27369&highlight=decrypter+thoggen)
These guys might give you a hand.[/QUOTE]
 I'm afraid I can't help anymore than to say that I have DVD Shrink 3.2 running under wine from winehq's repository.  

Did you install "Windows Installer" from winetools?  I did install most of the basic things offered by winetools before I installed DVD Shrink.

---

### Post by JDay on 2005-04-17
Thanks for that guide. I needed to install something with winetools but it worked fine after that. And it can read directly from the drive after I enabled ide-scsi, which I couldn't do before. I'm very happy right now. :)

---

### Post by TripHammer on 2005-04-28
[QUOTE=JDay]I'm trying to install the latest version of DVD Shrink with wine, from the backports repository. I had this working fine, previously, but I recently reformatted and now have the folloing problem: The installer runs fine until the point where it begins to actually install files, and I get the error "Access violation at address 77EC0DDB. Write of address 00730075." Any ideas?[/QUOTE]

I have been having the same problem under Hoary.  The problem seems to be with the installation only.  I just copied "DVD Shrink 3.2.exe" folder in "program files\DVD Shrink" from my windows machine to "~/.wine/drive_c/Program Files/DVD Shrink" and things run fine.

---

