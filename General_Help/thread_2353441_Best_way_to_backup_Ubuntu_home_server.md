---
title: "Best way to backup Ubuntu home server"
date: 2017-02-21
forum: General Help
---

### Post by steve130 on 2017-02-21
I have an old PC i've re-purposed into a home server running Ubuntu Server 16.04. I'd like to upgrade to a newer old PC but I don't want to start from scratch setting up all my applications and settings. I keep a full backup from Clonezilla in case something fails, but I can't restore it to a machine with completely different specs, right?  What is the best way to back up my user data, network settings, and applications like Plex Media server so I can restore it to a new machine?

---

### Post by DuckHook on 2017-02-21
It is surprising how versatile Linux is when moving across machines. This is especially so with home servers *provided that you haven't installed any GUI components* on it. The kernel will usually accommodate itself to different mobos and CPUs. If you use the default video drivers, it will also happily load the proper one in the new machine. Ditto with NICs.

I carry around a complete Linux system on a USB stick. It is meant to plug into and boot up on any strange computer that I don't trust, and it does so quite well. It has no Desktop Environment because they can be a lot more finicky, but as a server, you're not running a GUI anyway.

The only thing you have to look out for are the entries in your fstab. These are usually hard coded to a specific HDD via the UUID, and fstab will fail if the new HDD has a different UUID. You can forestall this by changing the fstab entries to /dev/sda&#8230;b&#8230;c&#8230;etc for the move and then back to the new UUIDs once you determine what they are. If you are simply moving all of your disks over in exactly the same configurations, then you don't even need to do that.

Of course, back up first before trying any of this. That ought to go without saying.

---

### Post by bearlake on 2017-02-21
My home server uses Clonezilla for the full backup but I like [luckyBackup]("http://luckybackup.sourceforge.net/manual.html") for data, it's totally great and it's in the repos. ;)

---

### Post by geeksmith on 2017-02-21
I've moved a hard drive with Ubuntu installed from an old computer to a new one several times. It has always worked, with some minor adjustments to network interfaces at times. Overall a very smooth process, especially compared to operating systems that do their best to prevent this sort of thing.

---

### Post by kyknos12 on 2017-02-22
My way
[https://www.youtube.com/watch?v=1Un0vsw6HKY](https://www.youtube.com/watch?v=1Un0vsw6HKY)

---

### Post by Habitual on 2017-02-22
[Simple, Secure Backups for Linux with rsync]("http://rsync.net/resources/howto/rsync.html")

---

### Post by DuckHook on 2017-02-22
> **kyknos12 said:**
> My way…@kyknos

While contributions to the forums are always appreciated, in the case of youtube-type instructions it is customary and just good netiquette to give a brief write-up of what it is that you are suggesting. Not everyone has the patience to sit through a 20+ minute presentation without at least a synopsis summarizing what it is you are asking us to invest our time in.

---

### Post by kyknos12 on 2017-02-23
> **DuckHook said:**
> @kyknos

While contributions to the forums are always appreciated, in the case of youtube-type instructions it is customary and just good netiquette to give a brief write-up of what it is that you are suggesting. Not everyone has the patience to sit through a 20+ minute presentation without at least a synopsis summarizing what it is you are asking us to invest our time in.

if I had not post the video but a litany Article text with explanation,How long will you need someone to sit to read and understand;a video is more understandable

---

### Post by DuckHook on 2017-02-23
> **kyknos12 said:**
> if I had not post the video but a litany Article text with explanation,How long will you need someone to sit to read and understand;a video is more understandableHabitual posted just such a bare link. The link title itself was self-explanatory and I was able to scan the entirety of the content in seconds.

Look. My suggestion was made in the spirit of helping you increase the effectiveness of your advice—from one who has been giving out good advice for a long time. If you wish to continue posting empty two-worded links to 20-plus-minute video with no further clue about what it is that you are advocating, then you are entirely at liberty to do so. Just don't expect a lot of takers.

---

### Post by oldos2er on 2017-02-25
> **kyknos12 said:**
> if I had not post the video but a litany Article text with explanation,How long will you need someone to sit to read and understand;a video is more understandable

One thing that makes the forums worthwhile is that people post helpful information *here,* unlike many sites that are simply link aggregates. Not saying that those are not useful, but that is not what ubuntuforums is about. 

Videos can be useful in technical support, but we're also about community-building.

---

### Post by ian-weisser on 2017-02-26
I understand why the OP doesn't want to start from scratch, but from-scratch can be more robust and maintainable...though admittedly more time consuming and perhaps tedious.

I find that a from-scratch rebuild (sometimes in a VM) every few years makes my servers easier to maintain and, occasionally, restore. And the maintainer's skills are improved, too.
Much better, for example, to learn the details of systemd transition while relaxed.

---

### Post by DuckHook on 2017-02-27
> **ian-weisser said:**
> …Much better, for example, to learn the details of systemd transition while relaxed.…you mean… there ***is*** a way to learn systemd???

I must get me some of your superfood.

---

