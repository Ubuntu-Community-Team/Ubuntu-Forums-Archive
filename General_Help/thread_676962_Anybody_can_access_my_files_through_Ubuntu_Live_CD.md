---
title: "Anybody can access my files through Ubuntu Live CD!!!"
date: 2008-01-24
forum: General Help
---

### Post by rahimveron on 2008-01-24
I have set my /home folder's permission like this:
Owner - (Me) Create and Execute
Group - (Me)Create and Execute
Others - None

That should keep my files safe from others, isnt it.
Guess what, its not!!!
I just booted Gutsy Live CD and ran```
gksu nautilus
``` but it didnt asked for any password.
It opens Nautilus window and i can access my /home folder easily :( What type of security is that. Anybody with a Live CD can pop it in my PC and boot and get access to my folders. How? Have i done anything wrong in the Permission settings?
This is really freaking me out. 
Plz Guys help me out. Can it be done?

---

### Post by espressopigeon on 2008-01-24
Yeah, this is a fact of life. 

However, you may be able to set a BIOS password, so that the intruder can't set it to boot from a CD. Of course, since most people probably go into their BIOS like, once a year, the BIOS password tends to be easily forgotten, so set one at your own risk.

---

### Post by az on 2008-01-24
Anyone who can touch your machine and has a screwdriver can be root.  This is not new.

You can encrypt part of your filesystem, if you need to.

---

### Post by rahimveron on 2008-01-24
Thanks guys for clearing my smoky brain :D

---

### Post by heindsight on 2008-01-24
> **rahimveron said:**
> Anybody with a Live CD can pop it in my PC and boot and get access to my folders.

They don't even need a live CD, they can select recovery mode from the GRUB menu, and get root access without a password as well. Changing permissions won't help you, anyone with root access can get to any files on the system regardless of permissions.

What you could do, is configure your BIOS to always boot from the hard drive first, and then set a BIOS password that must be entered before anyone can change the boot order. Additionally you could edit your menu.lst to password protect the recovery mode option. That way you'll have more security at the cost of some convenience.

Keep in mind though, that no computer is secure if someone other than yourself has physical access to it. If someone really wants to get at your data, and they have physical access, they'll find a way. For example, they could take out your hard drive, connect it to another machine...

---

### Post by rahimveron on 2008-01-24
Ok OK Got It. Setting BIOS password is the way to go.

---

### Post by Battie on 2008-01-24
> **heindsight said:**
> They don't even need a live CD, they can select recovery mode from the GRUB menu, and get root access without a password as well. Changing permissions won't help you, anyone with root access can get to any files on the system regardless of permissions.

What you could do, is configure your BIOS to always boot from the hard drive first, and then set a BIOS password that must be entered before anyone can change the boot order. Additionally you could edit your menu.lst to password protect the recovery mode option. That way you'll have more security at the cost of some convenience.

Keep in mind though, that no computer is secure if someone other than yourself has physical access to it. If someone really wants to get at your data, and they have physical access, they'll find a way. For example, they could take out your hard drive, connect it to another machine...

The recovery mode thing concerns me as well.  In past installations I've gone against recommendations and assigned a root password so that I am prompted for it in recovery mode.

Is there any reason why assigning a password like that is really a bad idea?  I hope this question is not off-topic, but it seems related.

Thanks.

---

### Post by Jerry N on 2008-01-24
> **rahimveron said:**
> Ok OK Got It. Setting BIOS password is the way to go.

Anyone with access to your computer and a few minutes of time can eliminate your BIOS password.  Just open the case and set the jumper to clear the BIOS.  Disconnecting the battery for 3 or 4 minutes will do the same thing.  

Jerry

---

### Post by DrMega on 2008-01-24
Is this a legacy from the days when Linux was almost exclusively used as a server OS?

I guess the idea being that if it is a server, then only sufficiently authorised administrators would be allowed anywhere near the physical box.

---

### Post by stchman on 2008-01-24
> **heindsight said:**
> They don't even need a live CD, they can select recovery mode from the GRUB menu, and get root access without a password as well. Changing permissions won't help you, anyone with root access can get to any files on the system regardless of permissions.

What you could do, is configure your BIOS to always boot from the hard drive first, and then set a BIOS password that must be entered before anyone can change the boot order. Additionally you could edit your menu.lst to password protect the recovery mode option. That way you'll have more security at the cost of some convenience.

Keep in mind though, that no computer is secure if someone other than yourself has physical access to it. If someone really wants to get at your data, and they have physical access, they'll find a way. For example, they could take out your hard drive, connect it to another machine...

You can remove the recovery mode option from GRUB to eliminate this possibility.

---

### Post by PeterJS on 2008-01-24
> **DrMega said:**
> Is this a legacy from the days when Linux was almost exclusively used as a server OS?

I guess the idea being that if it is a server, then only sufficiently authorised administrators would be allowed anywhere near the physical box.

It's a fact of reality. There is no OS in the world that can withstand offline probes by somebody that has physical access. If you have physical access you can yank the drives and drop them in a more friendly to you (and hostile to them) environment, wipe the BIOS password as suggested above. The only real thing you can do is encrypt your file system, even then that won't stop people from getting in to your system, it will just make it infeasibly long for them to do so, given determination and a couple decades they will get in.

---

### Post by shad0w_walker on 2008-01-24
Unless your files are encrypted the only thing standing between you and access to them is the OS saying you can't access them.

---

### Post by PeterJS on 2008-01-24
> **shad0w_walker said:**
> Unless your files are encrypted the only thing standing between you and access to them is the OS saying you can't access them.

Yep, and if said OS is offline, like say in a live CD, or the drive is dropped in another machine, then there's nothing in their way.

---

### Post by sisco311 on 2008-01-24
> **stchman said:**
> You can remove the recovery mode option from GRUB to eliminate this possibility.

this makes a little harder but not impossible because you can edit the original boot entry in the grub menu to boot in single mode(recovery mode)

---

### Post by PeterJS on 2008-01-24
> **sisco311 said:**
> this makes a little harder but not impossible because you can edit the original boot entry in the grub menu to boot in single mode(recovery mode)

If you're going to go that route, you could set up a grub password
[http://www.linux.com/articles/53569](http://www.linux.com/articles/53569)
but still that's ultimately susceptible to a liveCD or other offline end around.

---

### Post by sageb1 on 2008-01-24
Removing recovery mode from startup comes with a caveat: store the cd somewhere you know well like in the cd caddy in case your system crashes.

For security, rent a bank deposit box and put all important backups there including start up disks. Installation CDs also go here. 

Backups should fit on a 700MB CD disc and can be GPG'd if need be. Usually though, back up incrementally since if you back up all data each backup will be bigger than the previous. If you only save each backup's new files, you only backup that much more data. If you backup often like once a week, you can end up filling that disk easily than doing it once a month, assuming you create that much data in a month.

Backups of deb's are only necessary to save download time, but this should be done each day and after updates.

You could also create ISO images if need be of less important data and store it on a mail server that offers 5G of email or more. This allows for about 7 700MB ISO images -- each image split and GPG'd with .sigs if need be.

---

