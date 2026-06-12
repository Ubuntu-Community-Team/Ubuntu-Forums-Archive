---
title: "GTKpod help, please!"
date: 2005-08-24
forum: General Help
---

### Post by SparkyDawg on 2005-08-24
[B]iTunesDB '/media/RY-RICOS IP/iPod_Control/iTunes/iTunesDB' does not match checksum in extended information file '/media/RY-RICOS IP/iPod_Control/iTunes/iTunesDB.ext'
gtkpod will try to match the information using MD5 checksums. This may take a long time.

No MD5 checksums on individual tracks are available.

To avoid this situation in the future either switch on duplicate detection (will provide MD5 checksums) or avoid using the iPod with programs other than gtkpod.

Extended info will not be used.[/B]

Is the error I get when I try to read the contents of my ipod. It was working fine just a minute ago, but now my IPod has forgotten all the music it had on there, but luckily I can get into the ipod through the device and put all my music on the computer. What do I do to fix this problem? Help would be greatly, greatly appreciated.

---

### Post by 23meg on 2005-08-24
i recommend you rescue your music files via whatever means possible, then erase everything on it, and choose "create ipod's directories" from the file menu to rebuild the file structure. or better, just reformat it with the ipod updater utility in windows or via wine (i heard it works but didn't try myself), upload at least one song via itunes if possible, then enjoy life without appleware.

---

### Post by ACK!! on 2005-08-24
[QUOTE=23meg]i recommend you rescue your music files via whatever means possible, then erase everything on it, and choose "create ipod's directories" from the file menu to rebuild the file structure. or better, just reformat it with the ipod updater utility in windows or via wine (i heard it works but didn't try myself), upload at least one song via itunes if possible, then enjoy life without appleware.[/QUOTE]

The guy's advice is on target.  You should  be able to manually remove the iPod files in fact when I plug in my iPod it mounts automatically as a USB drive.

---

### Post by SparkyDawg on 2005-08-24
[QUOTE=23meg]i recommend you rescue your music files via whatever means possible, then erase everything on it, and choose "create ipod's directories" from the file menu to rebuild the file structure. or better, just reformat it with the ipod updater utility in windows or via wine (i heard it works but didn't try myself), upload at least one song via itunes if possible, then enjoy life without appleware.[/QUOTE]

Okay, how should I erase everything on it, format it?

By the way, thank you very very much.

---

### Post by 23meg on 2005-08-25
you're welcome. i recommend against formatting it via filesystem commands. as i suggested, it's better to do it by downloading the apple updater utility from apple's site, and using its "restore" command to return the ipod to factory state. the windows version of the updater software should run under ubuntu via Wine; if it doesn't you'll need windows to do it. i've had similar problems before and this is the surest solution.

did you upload songs to the same ipod via both itunes and gtkpod repeatedly? i've seen this kind of thing happen when you do that with older versions of both software. if you use linux as your regular operating system i recommend you only use itunes once to transfer a few files (since gtkpod sometimes has trouble building the database on an empty ipod; maybe this is fixed in recent versions though), and use gtkpod only afterwards.

---

### Post by SparkyDawg on 2005-08-27
Thank you so much, you've been a great help.

---

### Post by xaque on 2005-08-29
I'm having some problems with my iPod as well, but the iPod format utility can't detect it, even if I run it under Windows. Will it hurt my iPod if I simply format it through Windows?

---

### Post by WebbyBabe on 2005-08-29
So you mean to tell me that I have to erase everything on my iPod in order to get it to work in Ubuntu with gtkpod?  [-X I mean, I'll do it if I have to, but wow. ](*,)

---

### Post by 23meg on 2005-09-14
right; if nothing else works, try it. did you? and did that help?

---

### Post by rgrig on 2008-02-25
You are joking, right? What do you mean by **nothing else**? The **only** solution proposed in this thread is to format the ipod. That sucks.

---

