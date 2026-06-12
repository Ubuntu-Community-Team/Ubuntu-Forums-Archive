---
title: "one home directory, multiple distros"
date: 2006-09-15
forum: General Help
---

### Post by Schalken on 2006-09-15
Since SUSE creates seperate partitions for '/home' (home directories) and '/' (system root), I was wondering if I set Ubuntu to mount SUSE's home partition to '/home', would both distributions be effectively sharing the same home directory?

Would it even work? If I had users with the same name on both operating systems, would both users share the same data and same application settings?

If so, this setup would make installing and testing different distros whenever I like a breeze!

---

### Post by keithweddell on 2006-09-15
Sharing the /home partition works fine.  I've always used different user names on each distro so don't know what would happen if you tried using the same name.  I suspect it would overwrite settings etc at least.

Keith

PS I meant to say back up first!

---

### Post by Schalken on 2006-09-15
What filesystem would you reccommened for the home partition? (obviously one that is readable/writable by both distros, but has to be fast)

---

### Post by keithweddell on 2006-09-15
Don't know really.  I use ext2/ext3 on top of LVM just because it's simple and easy to move around.  I've not really looked into the advantages of different filesystems.  But I'm pretty sure I've read something on this forum so try a search and see what you come up with. 

Keith

PS Try [this]("http://www.ubuntuforums.org/showthread.php?t=149736&highlight=%22fastest+filesystem%22")

---

### Post by Garyu on 2006-09-15
wouldn't it be great if each distro could store distro-specific settings in say /home/garyu/.ubuntu/ and /home/garyu/.suse/ instead of using the same files...

that should not be very difficult to implement actually. also, would make it easier to downgrade if I for example would dist-upgrade to edgy and it wouldn't work as expected. given that very many linux-users try out or even use other distros regularly, this should actually be a high priority for the developers...

---

### Post by David Corrales on 2006-09-15
> **Garyu said:**
> wouldn't it be great if each distro could store distro-specific settings in say /home/garyu/.ubuntu/ and /home/garyu/.suse/ instead of using the same files...

that should not be very difficult to implement actually. also, would make it easier to downgrade if I for example would dist-upgrade to edgy and it wouldn't work as expected. given that very many linux-users try out or even use other distros regularly, this should actually be a high priority for the developers...

This would cause a lot more grief actually. Applications are hardcoded to write stuff to ~/.appname and they would all break (not a good thing lol).
Also, if implemented via some really complex symlink magic, you could end up having to decide which of the folders to use when you're upgrading for example or tons of redundant information.

---

### Post by wkulecz on 2006-09-15
I've done this with Fedora and Knoppix.  It works reasonaably well as long as you insure all you login group IDs match on both systems.  Some distros start at 500, others 1000 or 100 and few installers offer you an option to set it.  Some editing of /etc/passwd and /etc/groups and a bunch of chown -R made it all work.

I gave up on it as if the distros have different library versions stuff I compile in my home directory on one may be broken when run from the other which really is a PITA. So I've settled on a common home directory and different usernames on each distro for my multiboot box.

Using KDE on one (knoppix) and Gnome on the other (FC5) helped a lot in minimizing the desktop environment conflicts.

You could use Gentoo and change the compile time options on everything to get the behaviour you desire and see if your /home/gary/.ubuntu scheme is more trouble than its worth or not.  I suspect its far more hassle that its worth.

--wally.

---

### Post by PriceChild on 2006-09-15
I don't think i would reccomend any of this... Different versions of the programs on each distro may use different versions of config files in your home directory.

It may cause problems...

Pricey

---

