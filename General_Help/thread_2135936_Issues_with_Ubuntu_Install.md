---
title: "Issues with Ubuntu Install"
date: 2013-04-15
forum: General Help
---

### Post by Chaori on 2013-04-15
Hi,

For starters I'd like to apologise for my lack of knowledge in Ubuntu/Linux, I've been a Windows man my whole life and now I'm trying to give Ubuntu a go.

I can't seem to get it working on my Revodrive though, after several install attempts at installing it Grub always says unknown filesystem. After Googling and trying suggestions on other forums for a while (such as reinstalling Grub modules, doing a complete format and reinstall, etc) with no success, I decided to try the Windows installer for Ubuntu and installed to a 2nd partition on my Revodrive. This still didn't work, and although it didn't get the Grub error it just hung when trying to boot to the Ubuntu partition. I ended up installing it to my 2nd SSD and it worked, so I'm not sure if Revodrives are simply not supported by Ubuntu or what the go is there.

Booting to the Ubuntu install on my 2nd SSD works, however there are some issues I have inside the OS that are plaguing me. I am using a fairly decent PC (16GB RAM, i7, GTX580) but Ubuntu seems to be running extremely slow (extra emphasis on extremely). When opening and closing programs the effects the OS use are extremely laggy, but once programs are actually open they run fine. Also, a lot of the time the fonts in all programs will become scrambled and blocks of text will become unreadable. After mousing over parts of the scrambled text, some parts will fix themselves and other parts that were working will become scrambled.

I thought it could be a graphics driver issue, so I went to the Nvidia website and downloaded the GTX 500 series driver for Linux x64. When trying to install the driver it takes about 1-2 hours to process the file in Ubuntu and then says the file is missing symbols or characters (don't have the exact error code on me at the moment). Does it sound like the font issues / tearing and the overall slowness are due to my graphics drivers? Am I trying to install the driver the wrong way?

I am sure this must be something simple I'm doing wrong or haven't done since installing, but if anyone could suggest anything I could try for when I get home tonight that would be great. Please let me know if there's any info I can provide to help.

Also, keep in mind I am a complete Linux newb (I work in schools that use Windows Server 2003 / 2008 R2 and Windows 7 on all their staff/student workstations and laptops) so please explain things simply if you are able to help :P.

Thanks in advance, really looking forward to using Ubuntu to its fullest.

[B]Edit: I will add some screenshots when I get home tonight.
Edit#2: After reading up more on OCZ forums about the Revodrive 3 I learned that they don't support Linux at all, and apparently don't intend to. Disappointing.[/B]

---

### Post by Chaori on 2013-04-15
-

---

### Post by cariboo on 2013-04-15
I merged your two threads, please don't create multiple threads on the same subject.

---

### Post by Chaori on 2013-04-15
I wasn't aware I had submitted two, it must have been a form submission issue with Chrome. Thanks, nonetheless.

---

### Post by Chaori on 2013-04-16
Okay, I was doing it wrong. Turns out the issues were the default driver being used by Ubuntu and once I followed the readme for the supported Nvidia driver all is well.

---

