---
title: "'can't read superblock' and now drive is not even recognised"
date: 2022-10-18
forum: General Help
---

### Post by doctorlock on 2022-10-18
Hi all :)
I'm fairly new to Ubuntu and have been using it on a secondary PC to run a minecraft server with. I had a secondary SSD with the server's saves on it, until yesterday when it started saying that the superblock could not be read. I tried to restart the PC after trying a few different things recomended online, but nothing had worked. Now the drive won't even show up on the disk manager, and when plugging into my windows main PC, my PC just boots to a black screen without anything else happening. 

I am pretty sure the drive is lost. I just want to know if there's any way to get the data off it as it's really important to me, I have a backup but its fairly outdated (I know regular backups are incredibly important, this has been a great lesson in that).
Thanks :)

---

### Post by dragonfly41 on 2022-10-18
I can suggest using (or creating) a LiveUSB in a flash drive.
Use it in "Try Ubuntu" mode, not "Install" mode.
Ensure that testdisk tool is installed.
Research the guides/manuals/blogs for using testdisk on your failed drive.
Ensure that you have a good working drive into which you can *save* any recovered files.
Then apply testdisk to your failed drive to try to save recovered files into a good working drive.

---

### Post by HermanAB on 2022-10-18
Buy the exact same drive on Ebay and swap the controller card.

---

### Post by dragonfly41 on 2022-10-18
Expanding on above tip .. from @HermanAB

[https://www.instructables.com/Successful-Hard-Drive-Controller-Replacement/](https://www.instructables.com/Successful-Hard-Drive-Controller-Replacement/)

---

### Post by ActionParsnip on 2022-10-18
Please review your backups if the data  is "important"

---

### Post by Autodave on 2022-10-18
99% of the time, the super block error means that the HD is toast.  You *may* be able to reformat it and use it again, but do NOT trust it.

---

