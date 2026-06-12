---
title: "boot failed, No Raided disks?"
date: 2007-06-22
forum: General Help
---

### Post by jamest917 on 2007-06-22
I have downloaded Wubi 3 different times. I'm downloading it my 4th time right now. Every time i install i click reboot now then it shows the boot screen i press enter for Ubuntu. It says like Linux failed and then it says these numbers with "No Raid Disk" or something. I pressed enter a few times to see if i could make it continue. But i had to reboot and select windows uninstall it and reinstall it and this has been a problem where i have been sitting up all night. I'm not good with stuff like this. I even defragmented the c:/ where im installing it. Please help me with this, with something I could understand in a non-techy language so i can understand.

Thanks

---

### Post by ago on 2007-06-23
> **jamest917 said:**
> I have downloaded Wubi 3 different times. I'm downloading it my 4th time right now. Every time i install i click reboot now then it shows the boot screen i press enter for Ubuntu. It says like Linux failed and then it says these numbers with "No Raid Disk" or something. I pressed enter a few times to see if i could make it continue. But i had to reboot and select windows uninstall it and reinstall it and this has been a problem where i have been sitting up all night. I'm not good with stuff like this. I even defragmented the c:/ where im installing it. Please help me with this, with something I could understand in a non-techy language so i can understand.

Thanks

No Raid Disk is not an error message, it's a statement: you have no raid disks.

You may want to edit c:\wubi\boot\grub\menu.lst and delete the words "quiet splash" wherever you see them, then reboot. This will give you a more verbose boot. Then report here any error message exactly as it appears on screen.

---

### Post by jamest917 on 2007-06-23
so if i edit that i won't have anymore problems? ok im reinstalling it and i'll give it a try.

---

### Post by jamest917 on 2007-06-23
hello i reinstalled wubi and quiet splash or w/e. i rebooted the computer selected Ubuntu. Then again "No RAID Disks". Then like a bunch of number and beside it, it says "No disks in drive". It does like like 15 times. Then it pauses it won't do anything for like 30 seconds to like 2 minutes so do i reboot my computer or just leave it like that. I'm on another computer right now. Is this normal what is happening on my computer? Is there some kind of disk that i don't have? Please help me.

Thanks

---

### Post by acowboydave on 2007-06-23
Hello, I had the same problem a few weeks ago, but message lasted for only a second. I have used Wubi test 2, 3, and now the 7.04.01. Are you using the same Feisty download? I had some failures so I downloaded from another mirror. Used free download manager from CNET. Just wanted to be safe. You might have a corrupted Feisty download? Anyways it wont hurt to try a different one. The message no disk in drive sound like it looking for the installation cd, which there is none. Good luck, maybe Ago or CrazyGuy will see your post again,

---

### Post by ago on 2007-06-24
> **jamest917 said:**
> hello i reinstalled wubi and quiet splash or w/e. i rebooted the computer selected Ubuntu. Then again "No RAID Disks". Then like a bunch of number and beside it, it says "No disks in drive". It does like like 15 times. 

I need to know what exactly are the error messages, note that in verbose mode most messages are ok, normally errors appear just before it gets stacked.

---

