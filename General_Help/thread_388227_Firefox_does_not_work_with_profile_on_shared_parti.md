---
title: "Firefox does not work with profile on shared partition"
date: 2007-03-19
forum: General Help
---

### Post by jadabra on 2007-03-19
Hi,

I'm rather new to Linux, hope this is in the right category.

I want to use my Firefox profile from XP in Ubuntu 6.10, so I stored it on a FAT32 partition (hda6). I made that partition readable/writable from within Ubuntu etc, then edited the Firefox profiles.ini file to load my profile from the FAT partition.

When I start up Firefox, it seems to load the profile, my bookmarks are all there etc.
But then it does not load any website, the RSS bookmarks stay empty too.

As soon as I change the profiles.ini back to point to a profiles folder on the Ubuntu partition, Firefox starts (without my bookmarks of course) and websites load again.

Does anyone know why that happens and how I could change it?

Could the reason be that the FAT32 partition is writable for me (user) but not for Firefox?

Any help very much appreciated, thanks!

---

### Post by praxis22 on 2007-03-19
Easy way to test would be to run firefox as root:

sudo firefox

That way if it's a permissions issue you'll find out. It could just be that you need to chown the files to belong to your user ID

---

### Post by jadabra on 2007-03-19
Thanks, but running Firefox as root did not work either. I tried (as root) to use chown on /media/hda6 (my FAT32 partition) and the files in it, but got back "operation not permitted".

Other ideas?

---

### Post by praxis22 on 2007-03-19
Ah, right. Yes, sorry, you can't chown a file on a FAT32 file system. Not the same at all.

You could try putting a symbolic link from your profiles folder to your FAT32 partiton, that might work. 

In essence:

Move your current profiles folder to something else (mv ./profie profile.bak) etc.
Then put in a link, (ln -s /FAT32/profile ./profile) Or something like that.

If you can see the file with ls and they are readable, etc. with a text editor, then it should work fine. it may help if you do actually write to them first, even if it's just saving the file back out unchanged. That may sort out your permissions.

That way when firefox looks in your profiles folder it should be transsported automagically to the file on your FAT partition. At least in theory :)

EDIT: Failing that you could try to maually mount the FAT32 partition as live mount, rather than an automount under /media. I have mine mounted on /FAT

To do this you create /FAT with: sudo mkdir /FAT
Edit /etc/fstab to add your file system, (in your case /dev/hda6) and then do: mount -a (or reboot if that makes you more comfortable)

This should then make your filesystem available at boot. It will even be fsck'ed in the event of problems.

---

### Post by jadabra on 2007-03-19
Thanks a lot for your help. I got it working in the meantime by putting symlinks to SOME of the Win-Firefox configuration files in my Ubuntu Firefox Profile, following this German How-To:

[http://chris-b-online.de/blog/2006/09/23/ein-firefox-profil-fuer-windows-uns-linux/](http://chris-b-online.de/blog/2006/09/23/ein-firefox-profil-fuer-windows-uns-linux/)

Using the entire Profile from Win-Firefox apparently did not work because some absolute Windows paths are stored in some other config files.

Interestingly enough, there are English How-tos out there that describe the way I tried at first (just changing the path in profiles.ini both under Win and Linux), and it seems to work for them.

Again, thanks.

---

