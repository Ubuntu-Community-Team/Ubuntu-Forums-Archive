---
title: "Accidentally deleted /usr/sbin contents"
date: 2007-01-02
forum: General Help
---

### Post by Tedi on 2007-01-02
Hi,

I have just deleted the content of /usr/sbin ... I put an extra space before the * :(

Is there any way to recover the content instead of reinstalling Ubuntu?

Thanks in advance!

- Tedi

---

### Post by d3v1ant_0n3 on 2007-01-02
Did you send them to trash or delete the folder? If you sent it to trash, you could open the trash bin and just restore the files back to where they should be?

---

### Post by Tedi on 2007-01-02
I deleted the files from the console with "rm"

---

### Post by riven0 on 2007-01-03
That sounds bad. :( Did you try booting up the liveCD, mounting your hd and copying the /usr/bin file from there?

---

### Post by fokuslee on 2007-01-03
yeah sounds real bad do first reply and maybe open up synaptic and go to edit>fix broken packages
if synaptic don't work maybe try aptitute dist-upgrade? 
GooDLUCK

---

### Post by ~LoKe on 2007-01-03
And it still **works**!?

Yeah, the LiveCD approach is the only solution at this point.

---

### Post by Tedi on 2007-01-03
Well I tried to download de sysv-rc package, uncompress it and get the update-rc, then the install-info ... that way and now I'm just removing and reinstalling the packages I got from /var/lib/dpkg/info/*.list

This seems to work...

---

