---
title: "Messed up groups... lost sound playback."
date: 2007-05-16
forum: General Help
---

### Post by jonathanku on 2007-05-16
Hoping someone can help here. I've got Feisty AMD64 installed. AMD64 x2 3800, 2GB, Asus M2N4-sli mobo.

Got almost everything working perfectly (sound, screen etc.) and was just creating a couple of symbolic links and changing group ownership (so that two users can share one directory), when I used a command that removed me from all groups apart from jonathan (my primary group) and kerr (a group I created for group-ownership of the shared directory).

Had to boot in recovery mode to a prompt, add me to admin and do something within visudo. Anyway, got the power of **sudo** back, and added myself to all groups again, however, my sound playback has become a casualty of all this. The volume icon has a red cross over it, and double clicking to open the mixer results in two error dialogues:

> "No volume control GStreamer plugins and/or devices found."
and...
> "The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured.

You can remove the volume controle from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."  [close]

This had also previously been a problem with the secondary account I had set up (before I screwed up the groups for us) - but sound was find in my account.

Not sure where to start with the debugging - any help appreciated.

---

### Post by zvacet on 2007-05-16
I think your doing with visudo messed up your system.You changed etc/sudoers file and now you need to know what do you want it to look like to be able to make changes or ask for help.

---

### Post by jonathanku on 2007-05-17
No, I just checked. I changed nothing in sudoers. I now remember - that was just one thing I was looking at when reading someone else's instructions. What I did was add myself to the admin group after booting into recovery mode.

Any other suggestions?
Thanks.
JK

---

### Post by jonathanku on 2007-05-20
Done a bit more digging - looks like I can't access my CDROM drive either.

I notice that when I double click "Audio Disc" in the file-browser it tells me I don't have permissions for that either:> "cdda:///dev/hdc" is not a valid location.
Please check the spelling and try again.
So I looked at /dev/hdc, and it has permissions 660 with "cdrom" as group ownership:> brw-rw---- 1 root cdrom 22, 0 2007-05-20 18:57 hdc
Trouble is, there isn't a cdrom group in **System -> Administration -> Users and Groups** ...!

Should I just create that group and add myself to it? (how?)

---

### Post by jonathanku on 2007-05-21
For anyone reading - I also found under user permissions that no users had a check next to audio devices / CDROM and a host of other things. So I changed that, but there is still no evidence that sound will work again... nor can I access CDROM.

I feel a re-install coming on :-(

---

### Post by jonathanku on 2007-05-22
:o **OK - WHO TURN OFF MY SOUND IN THE BIOS!?!**

Turned it back on. Problem solved. :D

p.s. found this after re-installing Ubuntu. At least CDROM drive also works again.

---

