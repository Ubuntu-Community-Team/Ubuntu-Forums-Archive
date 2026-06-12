---
title: "NTDLR Problem"
date: 2007-08-19
forum: General Help
---

### Post by Dimax on 2007-08-19
After I completed the installation of Wubi and restarted, my system reports that NTDLR is missing. I couldn't boot into either OS.  I tried a few methods from [www.computerhope.com/issues/ch000465.htm](www.computerhope.com/issues/ch000465.htm). I suspected that it is the corrupted ntldr and/or ntdetect.com file. But so far I can't copy over the files from CD because it will give me a Access has been denied whenever I try copying anything. Please help!

BTW, the title is suppose to be **NTLDR** Problem.

---

### Post by clive_pearce on 2007-08-19
From the link you posted, did you go to the recovery console & try fixboot & fixmbr?

---

### Post by Dimax on 2007-08-19
Yes, I did try running fixmbr and fixboot. They also don't work.

---

### Post by ago on 2007-08-19
chkdsk /f

---

### Post by Dimax on 2007-08-19
Tried that and it still fails(Did it for all 32 partitions).

---

### Post by ago on 2007-08-19
Did you try with the official Windows CD version?

---

### Post by Steve1961 on 2007-08-19
If ntdlr exists you need to set the attributes before you can copy a new version over it.  Go back into the recovery console and do this before copying over the files:

attrib -s -h -r ntldr
attrib -s -h -r ntdetect.com

---

### Post by Dimax on 2007-08-19
@ago
Yes, I'm using the official Windows XP installation disk.

@steve[U]
The console says The system cannot find the file or directory specified.[/U] < Ignore this, remind me not to mess with the HD letters.

BTW, where is the ntldr and ntdetect.com files located?(In the windows directory)

---

### Post by Steve1961 on 2007-08-20
> **Dimax said:**
> @ago
Yes, I'm using the official Windows XP installation disk.

@steve[U]
The console says The system cannot find the file or directory specified.[/U] < Ignore this, remind me not to mess with the HD letters.

BTW, where is the ntldr and ntdetect.com files located?(In the windows directory)

They should both be in C:\

---

### Post by neodorian on 2007-08-20
I've got the same issue but unfortunately, the computer in question is a tablet pc with no CD drive so I'm kinda stuck.

---

### Post by Dimax on 2007-08-20
@steve
In just C:\ or C:\WINDOWS?Because I couldn't place it in C:\.

---

### Post by clive_pearce on 2007-08-24
I googled & found this, 

[http://support.microsoft.com/kb/315233/](http://support.microsoft.com/kb/315233/)

Quote

Copy the Ntldr and Ntdetect.com files from the I386 folder on the Windows XP CD-ROM to the root folder of your boot drive. The boot drive is typically drive C

---

### Post by Steve1961 on 2007-08-24
> **Dimax said:**
> @steve
In just C:\ or C:\WINDOWS?Because I couldn't place it in C:\.

Just C:\, which is the root directory

---

