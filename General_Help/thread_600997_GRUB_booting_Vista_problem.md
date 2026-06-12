---
title: "GRUB booting Vista problem"
date: 2007-11-02
forum: General Help
---

### Post by TuxTwig on 2007-11-02
This may seem familiar but this actually has little to do with the actual booting itself. I installed Ubuntu, checked my partitions (the Vista partition is intact), and changed my menu.lst file to include Vista in the boot menu itself. GRUB gives me the option to boot, but when I select Windows Vista, a black screen pops up for a little while (around a minute), then my Vista loading screen comes up (the one with the green loader bar), then pure blackness again, there is no Windows logon screen after this. I wonder if this has anything to do with Ubuntu affecting it because I can properly boot Vista. Being a newbie to Ubuntu myself, I would appreciate any posts posted. :)

---

### Post by lyndaj70 on 2007-11-02
I think the Vista boot loader is PART of the Vista boot process (not something you can skirt)

---

### Post by TuxTwig on 2007-11-02
I've heard of other people booting Vista from GRUB before, and I'm pretty sure it can run without the Windows bootloader. I don't think the Vista bootloader can run Ubuntu..how'd you set up your desktop?

Link to Gparted Scan screenie: [http://ubuntuforums.org/attachment.php?attachmentid=48648&d=1193872410](http://ubuntuforums.org/attachment.php?attachmentid=48648&d=1193872410)

And this is what I've put in the menu.lst file: 

      title Windows Vista Ultimate
      rootnoverify (hd0,0)
      makeactive
      chainloader +1
      boot

Oh and, how do you get rid of GRUB and rerun the Vista bootloader. I can't use the Vista DVD because mine is OEM.

---

### Post by TuxTwig on 2007-11-02
Please guys, I need all the help I can get. :)

---

### Post by TuxTwig on 2007-11-02
Guys, how do I get rid of GRUB and use the Windows Bootloader again?

---

### Post by LaRoza on 2007-11-02
> **TuxTwig said:**
> Guys, how do I get rid of GRUB and use the Windows Bootloader again?

Super Grub Disk, in my sig.

---

### Post by TuxTwig on 2007-11-02
Thank you, I'll try using this to see if I can boot Vista. :)

---

### Post by TuxTwig on 2007-11-02
I booted SGD from a DVD and i used Fix boot of Windows and activate partition. Blank black screen. One minute later, Vista loader screen, and after that, nothing. And my keyboard and mouse stop working at that point. (I have a G15 which glows when there's power), I really don't know what to do now. HELP.

---

### Post by TuxTwig on 2007-11-03
I know how to boot Vista with GRUB, has anyone had any problems doing this? Any problems similar to mine? :) Feel free to offer advice/guidance!

---

### Post by TuxTwig on 2007-11-03
Someone please post!

---

### Post by Jose Catre-Vandis on 2007-11-03
Again, what was your installation route forVista and Ubuntu, did you do any moving about of partitions? Was there a boot entry for Vista following Ubuntu install (there should have been one by default, Ubuntu finds other OS when it installs GRUB) What is your hard drive set up, are you running OS on separate hard drives? If so you may need to map Vista in your menu.lst entry to get it going.

---

### Post by TuxTwig on 2007-11-03
Thanks for posting Jose but GRUb already recognizes Vista in the boot menu. The problem is that vista won't boot. (Just the Vista loading screen runs). As I've posted before, the screenshot of Gparted. [http://ubuntuforums.org/attachment.php?attachmentid=48648&d=1193872410](http://ubuntuforums.org/attachment.php?attachmentid=48648&d=1193872410)

---

### Post by TuxTwig on 2007-11-04
Posts please!

---

### Post by froy02 on 2007-11-04
You need to supply more information . Did you install ubuntu on a second drive or on the same drive that vista is loaded on.  From there we could advise you om what amy be the problem.

When somebody or something   tampers with the drive that vista is loaded on, it will try to repair itself.   The reason for the long boot process is that maybe you did not leave enough room for vista to work with.  It would eventually finish but  it would take a very long time.    

Too many scenerios for possible cause but you are not supplying enough info.
  SUPPLY MORE INFO.!!!!!!!!!!!!!!

---

### Post by TuxTwig on 2007-11-04
I have one hard drive. It's around 250GB in size. It's formatted into 2 partitions. One contains Vista and the other has Linux installed. Each of the two partitions are around 120GB in size. If you want to see my partitions, I posted a screenshot of my Gparted scan.

---

### Post by TuxTwig on 2007-11-04
What sort of information do you wnat me to supply? Please post. :)

---

### Post by TuxTwig on 2007-11-04
What sort of info do you want me to post?

---

### Post by alwaysbutter on 2007-11-12
any progress?

---

