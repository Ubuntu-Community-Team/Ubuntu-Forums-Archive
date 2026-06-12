---
title: "ubuntu 13.04 from usb"
date: 2013-06-17
forum: General Help
---

### Post by enezx on 2013-06-17
I just installed/burned ubuntu 13.04 on my usb stick.
I restarted my pc and from the boot menu selected my usb stick. 

Now when you load ubuntu from a usb it gives you a welcome screen asking whether "to install" or "try ubuntu without installing" right?
It didn't give me that page, instead it directly asked for a username and password. How will I know the username and password when I am using it for the first time.

By the way I already have windows 7 and ubuntu 12.04 installed on my pc. Does that affect?

---

### Post by Cheesemill on 2013-06-17
Did you check the [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") of your downloaded iso file?

The only time I have ever seen the Live CD ask for a password is when booting from a corrupt download.

---

### Post by enezx on 2013-06-17
The md5sum is correct.
Any other advice?

---

### Post by sudodus on 2013-06-17
What about the next step after downloading:

- How did you create the USB live drive?
- What was on the drive before?
- Did you wipe it or format it?

- What tool did you use to create it? Startup Disk Creator or Unetbootin or ...

-o-

Maybe you can try cloning it with dd instead of using the same installing tool once again. I have made a guiding tool (a shell-script) that makes it safe. The advantage with the dd method is that it has a high success rate, particularly if you connect only one USB storage device.

See this link[ Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by sanderj on 2013-06-17
> **enezx said:**
> I just installed/burned ubuntu 13.04 on my usb stick.


Can you explain what you did? How did you install or burn Ubuntu on your usb stick?

---

### Post by grahammechanical on 2013-06-17
It is possible that you installed Ubuntu onto that USB memory stick just as if it was a USB hard drive. Perhaps you did not create a Ubuntu USB live disk.

Regards.

---

### Post by sanderj on 2013-06-17
> **grahammechanical said:**
> It is possible that you installed Ubuntu onto that USB memory stick just as if it was a USB hard drive. Perhaps you did not create a Ubuntu USB live disk.

Regards.

Exactly ... that would explain all.

---

### Post by enezx on 2013-06-18
I used startup disk to create the live disk. 
Anyways I fixed it - First I installed the .iso file again but it did not work the second time either. But after that I installed the 32-bit version (I was installing the 64-bit previously). Now it worked. How does 64-bit or 32-bit affect?

---

### Post by sanderj on 2013-06-18
> **enezx said:**
> How does 64-bit or 32-bit affect?

Not at all.

---

### Post by sudodus on 2013-06-18
> **enezx said:**
> I used startup disk to create the live disk. 
Anyways I fixed it - First I installed the .iso file again but it did not work the second time either. But after that I installed the 32-bit version (I was installing the 64-bit previously). Now it worked. How does 64-bit or 32-bit affect?

It make a huge difference for a computer that can only run 32-bit systems. Newer computers can usually run both 32-bit and 64-bit systems, and in most cases you should notice no difference. If you have less than 3-4 GB RAM, it might be be an advantage to run a 32-bit system, because the 64-bit version uses more memory for the same tasks. If you have more RAM, the 64-bit system is more efficient.

There are also some issues with lacking multimedia codecs in 64-bit systems, but such differences are decreasing all the time.

*Edit*: Only the 64-bit versions of Ubuntu can run in UEFI.

---

