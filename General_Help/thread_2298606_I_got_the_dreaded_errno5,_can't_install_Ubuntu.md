---
title: "I got the dreaded errno5, can't install Ubuntu"
date: 2015-10-12
forum: General Help
---

### Post by Ihateerrno5 on 2015-10-12
I can't get back to my old OS(which was windows 10), so I can't try wubi installer

What do I do? How do I fix it? Please help.

I'm using a CD/DVD install.

---

### Post by ian-weisser on 2015-10-12
Your next step is to read [http://askubuntu.com/questions/65830/errno-5-input-output-error-when-trying-to-install](http://askubuntu.com/questions/65830/errno-5-input-output-error-when-trying-to-install)
and figure out which of those many possible causes is the one that affects you.

You shouldn't try WUBI anyway - it's long unsupported, and incompatible with Windows 10.

How you get back to Windows 10 depends upon exactly what you did to boot the CD. Please tell us each step.

---

### Post by QIII on 2015-10-12
I think your intention may be the first question to resolve.

Did you intend to get rid of Win10?  If not, the very first thing you need to do is be sure any important files can be recovered and preserved.  The second thing to do is figure out how to get back to or restore Windows.

---

### Post by Ihateerrno5 on 2015-10-12
I intended to get rid of windows 10 and go to Ubuntu. I burned the ISO to my DVD using imgburn, and loaded it through there. Then when it asked me if I wanted to try Ubuntu live or install, I clicked install Ubuntu and delete everything else. At around 50% it stopped working and errno5 popped up. Now I can't get back to windows side at all and can only boot through disk.

---

### Post by QIII on 2015-10-12
The most likely causes are a bad burn or bad sectors on the hard drive.  There is also an outside chance that the Windows partition is in an inconsistent state, but Ubiquity should handle that..

Will the OS run from the "Try Ubuntu" selection?

---

### Post by QDR06VV9 on 2015-10-12
I have seen an install iso from 14.04 and 15.04 **Fail **when using the** install **only method.
Use instead the **Try Ubuntu **then use the installer from the desktop.

---

### Post by Ihateerrno5 on 2015-10-12
> **QIII said:**
> The most likely causes are a bad burn or bad sectors on the hard drive.  There is also an outside chance that the Windows partition is in an inconsistent state, but Ubiquity should handle that..

Will the OS run from the "Try Ubuntu" selection?
Yes, it will run from the Try Ubuntu selection.
> **runrickus said:**
> I have seen an install iso from 14.04 and 15.04 **Fail **when using the** install **only method.
Use instead the **Try Ubuntu **then use the installer from the desktop.
I tried to do that but still got an error.

---

### Post by QDR06VV9 on 2015-10-12
Sorry to hear that.
Sounds like you have everything backed-up form windows that you wanted.
If that is the case you may need to re-download the iso again and check the md5sum hash for integrity.(I know I seldom do this myself)
and Try again. Then if that fails download a copy of gparted 
[http://distrowatch.com/table.php?distribution=gparted](http://distrowatch.com/table.php?distribution=gparted) 
And burn that to a disk or USB Drive and see if reformatting will get you sorted out. (Using ext2 or ext4)


Best Regards

---

### Post by Ihateerrno5 on 2015-10-12
> **runrickus said:**
> Sorry to hear that.
Sounds like you have everything backed-up form windows that you wanted.
If that is the case you may need to re-download the iso again and check the [FONT=Consolas][COLOR=#111111]md5sum hash for integrity.(I know I seldom do this myself)
and Try again. Then if that fails download a copy of gparted 
[/COLOR][/FONT]http://distrowatch.com/table.php?distribution=gparted  And burn that to a disk or USB Drive
 and see if reformatting will get you sorted out. (Using ext2 or ext4)
Best Regards

Yeah, I'm going to try installing from a USB drive. I've redownloaded the ISO from the Ubuntu website so I'll burn it again. Hope it works this time.

---

### Post by QIII on 2015-10-12
Make sure to check the hash on the downloaded iso.  

Edit:  I see you are going to try from USB.  Good!  Much faster!

---

### Post by kurt18947 on 2015-10-13
> **runrickus said:**
> I have seen an install iso from 14.04 and 15.04 **Fail **when using the** install **only method.
Use instead the **Try Ubuntu **then use the installer from the desktop.

That's what I do as well. I also make sure there's a network connection before starting the install. I know the install should work without a network connection but I seem to recall that in rare instances it doesn't - or didn't at one time. I don't recall any details and that may be an inaccurate recollection on my part. I just know know I've had good luck installing from a live session with a network connection. Step one of the trouble shooting flowchart I'm familiar with is that if it works don't mess with it. I try to obey that dictate :p.

---

### Post by whaleyj on 2015-10-14
I've  had the same problem for days - several different versions from 12.10 to 15.04 with many USB sticks and burned DVDs and I just figured it out.

When you do the install, click on "something else" do you hd partitioning as normal. At the bottom of this dialogue box is a place to specify devise for boot loader you need to pick the same partion as your root mount point. For example mine was defaulting to sda when I changed it to sda5 it worked fine. Sda1-3 is winows sda4 was swap. My guess is that since there was no free space on the disk (by free I mean unpartitioned) the error was generated because there was no space for the boot loader.

---

