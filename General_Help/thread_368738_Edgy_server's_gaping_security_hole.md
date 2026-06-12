---
title: "Edgy server's gaping security hole"
date: 2007-02-23
forum: General Help
---

### Post by ykhun on 2007-02-23
With physical access to an edgy server, anyone could just reboot the system, go into GRUB and startup in rescue mode. Then set a new password for root and then reboot the box and login as root....

How can this security hole be patched?

I know all the arguments that with physical access, the system's security will be compromised sooner or later. But comeon, it shouldn't be THIS easy!!! I can get into an edgy server in under 5 mins.

I'm about to use a dog cage wtih a BIG lock for the box.

---

### Post by llamakc on 2007-02-23
How is this unique to Edgy?

---

### Post by Tomosaur on 2007-02-23
You could disable the recovery mode and password protect grub, I guess.

---

### Post by llamakc on 2007-02-23
> **Tomosaur said:**
> You could disable the recovery mode and password protect grub, I guess.

So what do you do if I walk up to the box with a livecd, remount wherever your /boot partition is, and comment that out of menu.lst? While I'm at it I could easily tell it to boot into single user mode or pass "init=/bin/sh" instead?

Physical security must come first if you have any concerns.

---

### Post by Tomosaur on 2007-02-23
> **llamakc said:**
> So what do you do if I walk up to the box with a livecd, remount wherever your /boot partition is, and comment that out of menu.lst? While I'm at it I could easily tell it to boot into single user mode or pass "init=/bin/sh" instead?

Physical security must come first if you have any concerns.

There's nothing stopping me taking a sledgehammer to the machine either. There is no reliable defence against physical access to the machine, so it's not worth debating. Just don't let people you don't trust sit at your computer.

---

### Post by ykhun on 2007-02-23
Both of you have your points, but...

I wouldn't be so concern if its physical destruction since the server always have remote backup. We should be more concerned about data thief.

No one can be next to their server all the time. Even if its my desktop, i can't be next to it all the time.

I think we need more constructive discussion in this thread instead of the current tone of "just live with it".

I know windows have a EFS filesystem that encrypts data written on disks based on user accounts, so even if someone physically grab the disk, they will have a hard time trying to decrypt the scrambled data. Thats one solution, but thats window's. Any ideas how we can get some sort of defenses, at the OS level, against physical access?

---

### Post by maxamillion on 2007-02-23
> **ykhun said:**
> With physical access to an edgy server, anyone could just reboot the system, go into GRUB and startup in rescue mode. Then set a new password for root and then reboot the box and login as root....

How can this security hole be patched?

I know all the arguments that with physical access, the system's security will be compromised sooner or later. But comeon, it shouldn't be THIS easy!!! I can get into an edgy server in under 5 mins.

I'm about to use a dog cage wtih a BIG lock for the box.

You give me physical access to ANY server with a Knoppix disk in my hand and it is compromised ... physical access is the compromise at that point.

---

### Post by Tomosaur on 2007-02-23
> **ykhun said:**
> Both of you have your points, but...

I wouldn't be so concern if its physical destruction since the server always have remote backup. We should be more concerned about data thief.

No one can be next to their server all the time. Even if its my desktop, i can't be next to it all the time.

I think we need more constructive discussion in this thread instead of the current tone of "just live with it".

I know windows have a EFS filesystem that encrypts data written on disks based on user accounts, so even if someone physically grab the disk, they will have a hard time trying to decrypt the scrambled data. Thats one solution, but thats window's. Any ideas how we can get some sort of defenses, at the OS level, against physical access?

You can encrypt volumes on linux, too.
[http://www.koeln.ccc.de/archiv/drt/crypto/linux-disk.html](http://www.koeln.ccc.de/archiv/drt/crypto/linux-disk.html)
[http://encryptionhowto.sourceforge.net/Encryption-HOWTO-4.html](http://encryptionhowto.sourceforge.net/Encryption-HOWTO-4.html)

Some more general encryption methods:
[http://www.linuxjournal.com/article/2590](http://www.linuxjournal.com/article/2590)

---

### Post by ykhun on 2007-02-24
I guess i better start hunting around for a steel dog cage and a nice big lock.

---

### Post by nickoli_02 on 2007-02-24
> **ykhun said:**
> I guess i better start hunting around for a steel dog cage and a nice big lock.

That, and never connecting your computer to the internet is pretty much the only way you can ensure your information is completely safe. No matter how high your level of security is, if someone is motivated enough they will find a way to crack your system. If you really want to go that route, go for it ;)

---

### Post by FyreBrand on 2007-02-24
Like it's been said you can't full proof if someone has access but you can do a few things to inhibit that.  I don't work near the servers, but here are a few things we do help secure them:

1. Servers kept in a locked room.
2. There is no booting to optical drives and no attached optical drives can burn data.
3. There is no booting into recovery mode.
4. BIOS and boot loaders are password protected.
5. There are cameras everwhere in that room.
6. There is attached network security devices -- no removing or unplugging a cable from a server or disk array on the rack (or any switch for that matter) without an alarm going off.

Take a few of those steps and physical access won't be your main worry about intrusion.

---

### Post by dcstar on 2007-02-24
> **ykhun said:**
> With physical access to an edgy server, anyone could just reboot the system, go into GRUB and startup in rescue mode. Then set a new password for root and then reboot the box and login as root....

How can this security hole be patched?

I know all the arguments that with physical access, the system's security will be compromised sooner or later. But comeon, it shouldn't be THIS easy!!! I can get into an edgy server in under 5 mins.

I'm about to use a dog cage wtih a BIG lock for the box.

Gee, and here's me thinking that my BIOS password on bootup will force anyone who wants to access my PC to actually open up the case and reset the CMOS or take the drive out.

As well, I believe you can put encrypted passwords in Grub, so that would be another layer to make it more than "5 minutes" to hack into your system.

Your system will be as easy to access as **you** make it.

---

