---
title: "Windows 8.1 coudnlt boot up through grub after intalling 14.04"
date: 2014-07-14
forum: General Help
---

### Post by iGlobe on 2014-07-14
Hi There... 
I am a complete beginner for the Ubuntu. I am having a boot up problem. Windows 8.1 couldnt boot up via grub after installing 14.04 on my new Lenovo Machine. I followed the instruction given at the site ([http://askubuntu.com/questions/280339/windows-8-wont-boot-via-grub-after-intalling-12-10-with-boot-repair](http://askubuntu.com/questions/280339/windows-8-wont-boot-via-grub-after-intalling-12-10-with-boot-repair)), but then I got an error message. I was informed to send the link below to the email ID at: [email]boot.repair@gmail.com[/email]. Here is the link: [http://paste.ubuntu.com/7791941/](http://paste.ubuntu.com/7791941/)

Could anyone here guide me to fix my problem? Please keep in mind I am an absolute beginner ;)

---

### Post by oldfred on 2014-07-14
It looks like sda5 was your Windows partition but is now your Linux partition. 
Or you erased Windows.
Windows main install is usually just after the system reserved partition which for Windows is an unformatted scratch area for hidden DRM, serial numbers or similar info and is sda4 in your report.

It does look like you did not do the install to entire drive and still have the recovery partition(s). So your one key reinstall with Lenovo may work. But you probably have to remove Ubuntu and create the NTFS partition that it will want to reinstall into.

Did you do a full backup of Windows? And you should also make the vendor recovery set of DVDs as if drive is accidentally erased or drive fails and you have to totally reinstall you need a way to restore Windows. And maintain backups of any data that is important.

See links in my signature if you need more info on backups or making repair flash drive.

---

### Post by iGlobe on 2014-07-14
Yes I have the windows backup... But I thought I can fix it without using backup of windows. May be I was wrong?

---

### Post by oldfred on 2014-07-14
You need to move Ubuntu or totally erase it as I assume at this point you have not reconfigured or added much.

And add a new partition just after sda4. It now will not be sda5, but whatever is next number. I do not think number will matter, but location on drive may. It also will not have same UUID or whateven internal numbers Windows expects so Window repairs will probably be required. You cannot do most of those from Linux and need Windows for that. 
It may be easier to restore backup, but not sure how Lenovo recovery works. Some have posted and it seems like that works well as long as you do not overwrite that partition.

Also see major caution in link in my signature if you decide to reinstall Ubuntu.

---

