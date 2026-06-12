---
title: "Update failure"
date: 2015-01-25
forum: General Help
---

### Post by Glen007 on 2015-01-25
Hello all,
I am using Ubuntu 14.04.1 LTS and have been using Ubuntu for a number of years now (albeit on a very newcomer scale) . However, yesterday I performed the usual software update but upon restart the PC failed to boot. I can get into the BIOS and was about to boot up from an old ISO image I have of Ubuntu 13.04. This will delete all of my stored data which is not that ideal. And installing this version alongside the currently installed version isn't really going to fix the problem or would it?
So, is there a workaround where I can somehow retrieve/save the information on my SSD or boot up with another version in order to resurrect the PC?

Thank you.
Regards,   Glen

---

### Post by deadflowr on 2015-01-25
I would first either boot the livecd and run the Try Ubuntu feature, which allows you to do a test run of a live session.
From which I would look to see that the drive didn't bust.

Or I would look into booting into an older kernel, if possible.
(You can usually get the boot menu by pressing the shift key right when the first start-up screen for the machine goes black)
If you can get a boot menu, and it shows some lines like Ubuntu 3.13.0-44 and then a line like Advanced Options click on advanced options and it should list an older kernel entry.
Usually you can pick the top entry, which is the last kernel installed. I would avoid any that say recovery mode, for now; recovery mode can be a little more advanced, so I'd use it as a backup option.

If you're not seeing anything, like the boot menu, then I would go with liveCD option.

With the liveCD option I would start it and then find the app(it's on the disk, as far as I know) called Disks.
Disks should easily tell you if the drive is functioning correctly.

This, of course, would be a starting point, because knowing if the drive is still functional would be key.

And don't worry about anything installing while using the live session(Try Ubuntu) method.
It won't run any installers unless you make it.

Edit: And live sessions run off the system RAM, so it won't write anything to the hard drive.
So it won't do any additional damage to the drive.

---

### Post by Glen007 on 2015-01-25
Hello deadflower,
I have booted up using the Try Ubuntu method as you mentioned.
I am unable to locate the Disks app though. However I can see my folders on the SSD which is showing up in the Devices column. I cannot open them as it states I do not have permission to view. But at least the drive appears to still be functioning at some level.
So from here how would you suggest reinstalling Ubuntu without deleting files?
Thank you for your reply by the way.

---

### Post by mörgæs on 2015-01-25
If you want to back up your files you might need full rights, that is opening the file manager with the *sudo* command first like *sudo nautilus*.

---

### Post by Glen007 on 2015-01-25
One issue is emails. As these are accessed in Evolution in Ubuntu. Most of the files are backed up, just not the latest. 
Is it not possible to reinstall Ubuntu without losing all data?
EDIT: Have used sudo nautilus and all files are intact on the SSD, so it seems to just be a software issue. I am backing up all files now but cannot find the Evolution folder with my emails. Have been searching and of course there are many folders labeled "mail" and "email" etc but none contain what I need my actual emails.
Any idea where the mail folders would be.
Thanks,   Glen

---

### Post by Glen007 on 2015-01-26
Well, I loaded an old backup of Evolution I had saved quite some time ago that worked fine which is of some relief.
I am still running Ubuntu from the DVD in the hope I can find the current folder with emails in it before I reinstall and delete all the data.
I have been searching for ~/.cache/evolution/mail amongst others in Home. Should I be searching for it in another location?
Thank you.   Glen

---

