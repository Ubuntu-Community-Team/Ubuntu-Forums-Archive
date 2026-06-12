---
title: "Switching to Debian"
date: 2007-02-19
forum: General Help
---

### Post by benndamann33 on 2007-02-19
Hi all, so I want to switch to debian completely from ubuntu edgy, but I'd prefer not losing all of my documents. I heard in recovery mode you could mnt your home directory seperately, then remove ubuntu and install debian and copy files over, such that you don't lose your documents. Is this possible? If so, could someone please tell me how to or direct me to the proper post? Thank you!
Ben

---

### Post by benndamann33 on 2007-02-19
seriously, can you please help

---

### Post by Chake99 on 2007-02-19
Couldn't you just install Debian on a different partition and then copy your home files over?

---

### Post by SeanTater on 2007-02-19
I use Debian also, but I leave room for Ubuntu by partitioning my Hard Drive into one large partition for data, and two 15 GB partitions for OS's. This way, if there is a crash, I may need to reinstall and reconfigure my programs, but I never *have* to backup my data just to switch OS's. This has made "distro surfing" much easier.

In your case you should find a CD or a DVD you can write all your backups to, or another computer to which you can transfer them. If you think you need it, you could tar.gz it but you should consider using the command line for it, as most archivers are too buggy to handle thousands of files.

I have not tried it personally, but I think it is an unwise decision to backup your home folder (as in, even the configuration directories) for your move to Debian. You can back them up, but you should only restore the documents and data you use, not the configuration. Conflicting application versions could become quite a hassle.

One thing to note: Debian is not for the faint of heart. It's not really made with the newbie in mind. (Get used to the terminal)
If you like KDE, install it. Gnome is default and there's not much you can do about it.

---

### Post by tribaal on 2007-02-19
Just make sure you backup your data real good.

I'm using Debian Sid now, it's pretty nice, although there is much less difference from Ubuntu than what I expected.

Hope you'll like it.

- trib'

---

### Post by MetalMusicAddict on 2007-02-19
> **tribaal said:**
> I'm using Debian Sid now, it's pretty nice, although there is much less difference from Ubuntu than what I expected.

Ill second this. The only glaring difference I saw was Upstart. It easily boots up 10 seconds faster.

I dont see much point in using Sid if your already a Ubuntu user. Etch is a different story.

To quote a Debian user I know:
> Ubuntu is out-of-the-box what I would have after a week of tweaking Debian.

Ive seen others agree with this.

---

### Post by benndamann33 on 2007-02-19
yeah I pretty much solely use the terminal and I have debian at work, I installed ubuntu becuase it looked flashy but it's just crashy. Anyway, how exactly do you have your system set up such that you can easily switch distros, like you just have a /data mounted and save everything important there?
Ben

---

### Post by r4ik on 2007-02-19
You could pick a daily build Etch net install image and use the "installgui" boot option.
If you're connection is able to.
If the terminal is not you're best friend try "Hakix"

Good luck !

---

### Post by benndamann33 on 2007-02-19
the terminal is fine, and I will be using etch, but do you think I should just back up my data on a cd first? thanks
Ben

---

### Post by r4ik on 2007-02-19
Always backup important data first.

---

