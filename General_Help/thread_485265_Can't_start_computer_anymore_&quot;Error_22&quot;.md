---
title: "Can't start computer anymore &quot;Error 22&quot;"
date: 2007-06-26
forum: General Help
---

### Post by Kivamaki on 2007-06-26
I have Linux installed on my computer, but I didn't want it anymore because I didn't use it (Couldn't get internet connection). So I put in the LIVE cd so I could use the partition software. I opened that up and found the Linux partition and just clicked "Delete". So I think restarted the computer and I get this message:

> Gnome is starting, please wait...
Error 22

And nothing happens after that. What can I do..I just want to go into my Windows.

---

### Post by qamelian on 2007-06-26
You'll need to boot from a Windows boot disk or you Windows installation CD. You need to boot to the recovery console (CD) or to a command prompt (boot disk) and run fixmbr to replace the master boot record with the standard Windows only MBR.

---

### Post by Kivamaki on 2007-06-26
I don't have a windows boot disk, but I did manage to get back into windows.

Using the Live CD, I used the partition manager and right clicked my old Linux parition and clicked "New" and changed it from "ext3" to "unformated" and it allowed me to boot back into windows.

Now what I can I do to completely wipe out the Linux partition and merge it back into my Main drive.

---

### Post by LaRoza on 2007-06-26
If you need to restore the MBR for Windows, use the Super Grub Disk, it is very helpful.

See my sig.

---

### Post by Kivamaki on 2007-06-26
> **LaRoza said:**
> If you need to restore the MBR for Windows, use the Super Grub Disk, it is very helpful.

See my sig.

What? I don't know what MBR is, sorry.

---

### Post by merlinus on 2007-06-26
MBR = Master Boot Record.  It is used by windows.

As the OP said, SuperGrub will help you with the problem.

-merlin

---

