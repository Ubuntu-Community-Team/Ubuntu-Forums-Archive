---
title: "Some questions about installing Windows XP alongside Windows 10 and Ubuntu"
date: 2015-11-24
forum: General Help
---

### Post by JCAPER on 2015-11-24
Hi guys, I'm sorry if I am posting in the wrong category.

So I have a laptop who already has installed Ubuntu and Windows 10. Both are working together nicely with grub (I believe it's grub2).

I found some old CDs with some games, some of which only run on Windows XP. I'm feeling nostalgic so I thought why the hell not installing Windows XP instead of using a virtual machine. However, Windows XP is quite old and I'm not sure if there will be complications, so I want to ask if someone can give me some tips or heads up, or maybe dissuade me from installing Windows XP in case it's just a major headache. Like I said, this is just me feeling a bit nostalgic, so I'll just use a virtual machine if installing it alongside the other 2 OS's is too much trouble.

My laptop is an Asus n56vz with a 500 gb HDD. Roughly, 470 gb are for Windows 10 and the rest are for Ubuntu partitions, my plan is to take at least 30 gb from Windows 10 and give it to Windows XP.

Is there anything I should know about, or can I just go ahead and install Windows XP without worries? If the pc then boots automatically to Windows XP, is there a way to fix grub from Windows XP or will I need to download Ubuntu again and fix it via flash drive (by this I mean trying ubuntu without installing and use the commands to fix the grub)? 

Btw, will grub detect Windows xp?

---

### Post by grahammechanical on 2015-11-24
If you want to expose that machine to malicious attacks, then go ahead. Windows XP is not supported any more. Is this not true? You might also find that XP does not come with the drivers for that hardware.

[http://www.bbc.co.uk/news/technology-25758308](http://www.bbc.co.uk/news/technology-25758308)

[http://www.v3.co.uk/v3-uk/news/2417794/windows-xp-even-more-insecure-as-microsoft-ends-anti-virus-support](http://www.v3.co.uk/v3-uk/news/2417794/windows-xp-even-more-insecure-as-microsoft-ends-anti-virus-support)

Do it in a virtual machine. Let the crooks be nostalgic for the good old days when there was an OS that had so many users who had so little idea about computer security that easy profits were had.

---

### Post by yancek on 2015-11-24
In addition to xp being unsupported and insecure, if you were to install it you would not be able to boot windows 10 from xp and any windows install will overwrite the current MBR.  You would manually need to configure the boot files on xp to boot any thing  else so you would have to be very familiar with the windows boot files.  You might also have serious problems if you are using UEFI with Ubuntu and windows 10.  Better off using virtualbox or some other virtual software.

---

### Post by JCAPER on 2015-11-24
> **grahammechanical said:**
> If you want to expose that machine to malicious attacks, then go ahead. Windows XP is not supported any more. Is this not true? You might also find that XP does not come with the drivers for that hardware.

[http://www.bbc.co.uk/news/technology-25758308](http://www.bbc.co.uk/news/technology-25758308)

[http://www.v3.co.uk/v3-uk/news/2417794/windows-xp-even-more-insecure-as-microsoft-ends-anti-virus-support](http://www.v3.co.uk/v3-uk/news/2417794/windows-xp-even-more-insecure-as-microsoft-ends-anti-virus-support)

Do it in a virtual machine. Let the crooks be nostalgic for the good old days when there was an OS that had so many users who had so little idea about computer security that easy profits were had.
I'm not going to use it for browsing the internet nor for anything else really. Just for playing old games I found in the attic.

Thanks for the warning, but I am already aware of the situation. Your reply was unnecessary at best...

---

### Post by JCAPER on 2015-11-24
> **yancek said:**
> In addition to xp being unsupported and insecure, if you were to install it you would not be able to boot windows 10 from xp and any windows install will overwrite the current MBR.  You would manually need to configure the boot files on xp to boot any thing  else so you would have to be very familiar with the windows boot files.  You might also have serious problems if you are using UEFI with Ubuntu and windows 10.  Better off using virtualbox or some other virtual software.
Thanks for the reply.
I checked some other threads and videos and indeed, installing XP now that I already have Windows 10 and Ubuntu would be a pain.

I'm going to use the virtual box, but something tells me it's going to screw up the game graphics...

Anyway, thanks.

---

### Post by oldos2er on 2015-11-24
We don't support installing operating systems from other vendors that are no longer maintained.

Closed.

---

