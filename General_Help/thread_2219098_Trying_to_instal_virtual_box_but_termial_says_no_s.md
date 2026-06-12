---
title: "Trying to instal virtual box but termial says no such dirctory or files"
date: 2014-04-22
forum: General Help
---

### Post by haydenhatfield on 2014-04-22
I have been trying to instal virtual box reccently so i can run windows and ubuntu. But as soon as I put this command sudo dpkg -i VirtualBox-3.2_4.3.10_Ubuntu_raring_i386.debinto terminal i get a respons saying dpkg: error processing VirtualBox-3.2_4.3.10_Ubuntu_raring_i386.deb (--install):

cannot access archive: No such file or directory

Errors were encountered while processing:

I already checked the forums for an answer and all that i got was that i might be running a 32 but program on a 64 bit computer which i am not doing my computer is only 32 but.

Please send me an aswer for how i can fic this problam or what i am doing wrong.

---

### Post by Tristan_Williams on 2014-04-22
First of all, make sure you are in the same directory as VirtualBox-3.2_4.3.10_Ubuntu_raring_i386.deb
If it is located in the ~/Downloads directory, issue the command 'cd ~/Downloads' then try the dpkg -i command.

Other possibility is that it's a bad .deb file. If my above solution doesn't work, try re-downloading the .deb file from a different server.

FYI, you can install 32-bit programs on 64-bit systems with absolutely no problems. It's the other way around that messes things up.

---

