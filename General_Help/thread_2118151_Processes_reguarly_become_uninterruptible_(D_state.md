---
title: "Processes reguarly become uninterruptible (D state)"
date: 2013-02-20
forum: General Help
---

### Post by Durr on 2013-02-20
I have a Lenovo Thinkpad X230 with 12.10 on and I'm finding programs either becoming unresponsive or refusing to start up. A look at system monitor or [FONT=Courier New]ps aux[/FONT] shows the process is in uninterruptible I/O and cannot be killed. This has happened with Firefox and Steam so far. I don't think this is an Ubuntu-specific bug as I have had this happen with an old laptop running OpenSUSE however I thought I'd post here anyway as Ubuntu is what I am running now.

Some points of interest:

[LIST]
[*]The laptop is using LUKS/dm-crypt encrption. The entire root partition is encrypted save for /boot.
[*]Root (/) is using btrfs with compression
[*]I am using an SSD (Samsung 840)
[/LIST]
My old laptop had a similar setup and this sort of thing happened every week or so. I suspect one of these three may be to blame but I wouldn't know where to start with investigations. Interestingly on my old laptop Firefox was the only program susceptible but now it looks like everything is fair game to this bug.

This isn't a show-stopping bug but is serious as (as far as I know) any process could freeze up and become uninterruptible, taking any unsaved work with it. I have to restart the laptop to free up the process and be able to use whatever was blocked.

uname -rms:
```
Linux 3.5.0-24-generic x86_64
```

---

### Post by tgalati4 on 2013-02-20
You have what is called a *Triple Threat*.  Also, if you are the only one running this configuration, then you are both an edge case and out-of-luck.

Some questions though:

Why would you encript the operating system? /usr/bin, /var/log, /etc.  I can understand encrypting your user directory (~/) or even a subdirectory, but the entire OS, with the exception of the kernel?

Btrfs is not exactly stable for production use, and then adding compression on top of that?  What was the thinking behind this?

SSD's can have problems (as any disk drive), but the combination of encryption and compression make the trim and housekeeping functions on these drives problematic.

I'm pretty sure we would not have this thread with a spinner hard disk, no compression, ext4 and encryption on a few select subdirectories in your home directory.

What does the following say with respect to disk IO?

```
dmesg | tail -100
```

---

### Post by dcstar on 2013-02-21
> **Durr said:**
> I have a Lenovo Thinkpad X230 with 12.10 on and I'm finding programs either becoming unresponsive or refusing to start up. A look at system monitor or [FONT=Courier New]ps aux[/FONT] shows the process is in uninterruptible I/O and cannot be killed. This has happened with Firefox and Steam so far. I don't think this is an Ubuntu-specific bug as I have had this happen with an old laptop running OpenSUSE however I thought I'd post here anyway as Ubuntu is what I am running now.

Some points of interest:

[LIST]
[*]The laptop is using LUKS/dm-crypt encrption. The entire root partition is encrypted save for /boot.
[*]Root (/) is using btrfs with compression
[*]**I am using an SSD (Samsung 840)**
[/LIST]
.......

One assumes that you have TRIM enabled on all filesystems.

---

### Post by Durr on 2013-02-23
> **tgalati4 said:**
> You have what is called a *Triple Threat*.  Also, if you are the only one running this configuration, then you are both an edge case and out-of-luck.

Some questions though:

Why would you encript the operating system? /usr/bin, /var/log, /etc.  I can understand encrypting your user directory (~/) or even a subdirectory, but the entire OS, with the exception of the kernel?

Btrfs is not exactly stable for production use, and then adding compression on top of that?  What was the thinking behind this?

SSD's can have problems (as any disk drive), but the combination of encryption and compression make the trim and housekeeping functions on these drives problematic.

I'm pretty sure we would not have this thread with a spinner hard disk, no compression, ext4 and encription on a few select subdirectories in your home directory.

What does the following say with respect to disk IO?

```
dmesg | tail -100
```

The entire OS is encrypted because otherwise someone could boot it up or plug the drive into another computer and mess with the OS, for instance install a keylogger. I know it could be possible to embed one within a kernel image but it's one open door closed at least. I really hate the idea of someone being able to boot up my laptop, reset the root password and have their way with it.

As far as I know, TRIM is enabled. Both the [FONT=Courier New]trim[/FONT] and [FONT=Courier New]ssd[/FONT] flags are enabled in /etc/fstab.

Actually, scrap that last line. I thought I had also enabled TRIM in initramfs however it turns out I haven't. So that *could *be the cause of all this I suppose. If it continues then I'll probably go back to ext4 if/when I upgrade to 13.04. If problems persist at that point then at least I'll have a less bespoke set-up and getting help should be easier.

As for I/O messages I don't think I can see anything in dmesg. Are there certain keywords I could use with grep to narrow down the output?

---

### Post by dcstar on 2013-02-24
> **Durr said:**
> 
..........
**As far as I know, TRIM is enabled. Both the [FONT=Courier New]trim[/FONT] and [FONT=Courier New]ssd[/FONT] flags are enabled in /etc/fstab.**

Actually, scrap that last line. I thought I had also enabled TRIM in initramfs however it turns out I haven't. So that *could *be the cause of all this I suppose. If it continues then I'll probably go back to ext4 if/when I upgrade to 13.04. If problems persist at that point then at least I'll have a less bespoke set-up and getting help should be easier.
........

Huh?, AFAIK the only "TRIM" flag in /etc/fstab is called **discard**.

In the other this is supposed to be done:

[https://wiki.archlinux.org/index.php/Dm-crypt_with_LUKS#Discard.2FTRIM_support_for_solid_state_disks_.28SSD.29](https://wiki.archlinux.org/index.php/Dm-crypt_with_LUKS#Discard.2FTRIM_support_for_solid_state_disks_.28SSD.29)

If TRIM is not set on (and working) all devices that do disk writes then SSD performance will eventually go straight into the toilet.

---

### Post by Durr on 2013-02-26
> **dcstar said:**
> Huh?, AFAIK the only "TRIM" flag in /etc/fstab is called **discard**.

In the other this is supposed to be done:

[https://wiki.archlinux.org/index.php/Dm-crypt_with_LUKS#Discard.2FTRIM_support_for_solid_state_disks_.28SSD.29](https://wiki.archlinux.org/index.php/Dm-crypt_with_LUKS#Discard.2FTRIM_support_for_solid_state_disks_.28SSD.29)

If TRIM is not set on (and working) all devices that do disk writes then SSD performance will eventually go straight into the toilet.


Apologies, I meant to say the [FONT=Courier New]discard[/FONT] flag and not [FONT=Courier New]trim[/FONT]. I've also enabled discard in the initramfs image as described in that Arch Linux Wiki page -- I'll watch out for misbehaving processes now that these are enabled and I'll let you know if it happens again in the next few days.

---

### Post by tgalati4 on 2013-02-26
If you are not seeing anything suspicious in dmesg or syslog, then run top and look for IO-Waits (wa).  If anything other than 0, then you may have a problem with your disk.

Regarding security, I wear a tinfoil hat and use a BIOS password and hard disk password.

---

