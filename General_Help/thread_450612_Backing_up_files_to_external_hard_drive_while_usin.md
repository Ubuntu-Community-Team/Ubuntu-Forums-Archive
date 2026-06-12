---
title: "Backing up files to external hard drive while using Wubi install"
date: 2007-05-21
forum: General Help
---

### Post by hummingbird59 on 2007-05-21
Here's a question:  I am using Wubi Feisty version from approximately first of May.  I used Open Office in Windoz and have a data file there.  I can access and modify these files in Linux thanks to Wubi (WOW!):D  When I save changes, the changes are made in my windows file.  Good so far.  I like to backup these data files weekly and I was doing that using a 60GB Maxtor One Touch.  Linux sees this drive and I can read files on it, but I can't write to it.  I looked around the forums and found that I needed NTFS config so I installed that via Synaptic.  When I ran that, it showed only one drive, an SDA drive and I was not sure that it was referencing the Maxtor so I did not do anything.  Then, I realized NTFS is already incorporated within Wubi.  So, I uninstalled what I downloaded so as not to mess up wubi.   I'm a complete newbie as far as NTFS and every time I read the how to guide for it, I'm left scratching my head.  Anyway, how do I get write permission to my Maxtor under Wubi without confusing it or me?  Any help or ideas are GREAT!  Thanks in advance!

---

### Post by ago on 2007-05-21
WIth wubi you will basically get 2 drives for ntfs, the default one is read-only, the ntfs-3g is read write. If you do not specify otherwise the read-only one is used (except for the drive hosting the wubi folder which is always accessed via ntfs-3g). ntfs-config allows, among other things, to use ntfs-3g as default driver, therefore when the disk appears in the file browser the access is r/w. If you want to learn how to that manually that is a good chance to learn a few Linux commands and concepts, otherwise use the graphical configuration tool.

---

### Post by hummingbird59 on 2007-05-21
Thanks for the quick reply!  So, forgive a really lame question but how do I access the GUI and could you walk me through it step by step.  When I installed NTFS it was under system tools, but since I uninstalled after realizing I already had it "somewhere", I'm not sure how to find the "pre-installed" version.  I know this is really simple and I am slow but more detail please:D:  Thank you so much for WUBI!:D:D:D

---

### Post by ago on 2007-05-21
sudo apt-get install ntfs-config
sudo ntfs-config

---

### Post by hummingbird59 on 2007-05-21
Thank you Ago!  I'll keep working on it!:)

---

### Post by hummingbird59 on 2007-05-21
When I open ntfs config, it only sees my internal drive, even though my external is mounted and viewable.  Here is my fstab result:



Also, the system has frozen twice today when I tried to access the external hd.  I had to force quit and restart the computer.  Any idea what is happening?  Thanks!:confused:

---

### Post by ago on 2007-05-22
> **hummingbird59 said:**
> 
Maybe ntfs-config does not handle removable hd (never tried that). The way around it is to add a line to fstab

ntfs-3g /dev/(your partition like hda1 or sda1) /media/(mount point) users,uid=(your user id),locale=en_US.utf8 0 0

> Also, the system has frozen twice today when I tried to access the external hd.  I had to force quit and restart the computer.  Any idea what is happening?  Thanks!:confused:
Not really unless you provide more detailed info, next time though try to press ctrl+alt+F2 to get a console, and if you can't see [http://www.developertutorials.com/tutorials/linux/magic-sysrq-050503/page1.html](http://www.developertutorials.com/tutorials/linux/magic-sysrq-050503/page1.html)

see the general forum for more info on ntfs-3g

---

### Post by hummingbird59 on 2007-05-22
Thanks for the info.  I'll try it and see what happens.  BTW, when I get ready to move to a "real" partition, is there going to be a "fool-proof" (read easy for even me) way to do that, ie an automated stable script maybe?  Anyway, just wondering  because I am going to try to work out all my issues and switch completely.  Thanks again!

Edit:  As far as issues, I only have a couple: this backup thng which may be resolved by going to a real partition???, a printer issue re photos and a cd burning problem that seems to be common with others at the moment.

---

