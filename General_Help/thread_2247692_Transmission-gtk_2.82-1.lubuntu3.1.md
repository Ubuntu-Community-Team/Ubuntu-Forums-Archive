---
title: "Transmission-gtk 2.82-1.lubuntu3.1"
date: 2014-10-09
forum: General Help
---

### Post by imconfused2 on 2014-10-09
I am running Transmission 2.82-1.lubuntu3.1 under Linux Mint 17 which is based on Ubuntu.  Transmission-gtk does normal file transfer when first started after a while it gets me the message that the peer ID does not match (a torrent site where I could check my connectivity).  Then the transfer degenerates to terrible or non existent.  By restarting after deleting the settings.json file it goes back to normal.   One of the changes in Transmission Version 2.83 is "Fix 2.82 bug that didn't retain peers between sessions".  Could this fix be put into the version in the repository?  I think that the bug is the reason i am not getting good consistent file transfer with transmission-gtk.

---

### Post by QIII on 2014-10-10
Hello!

Typically, I would move a thread about Mint into ***Other Operating Systems & Projects***.  However, this may be something that will be of interest to a wider audience since it is from an Ubuntu repo.

In any case ...  This is a forum populated by volunteer Ubuntu users.  None of us here has any control over what, bug fixes or otherwise, gets put into the repos.  Although the spectre of a a lone Canonical employee may drift through here from time to time, they don't hang out here as a rule.  So requests like your are lost here.

---

### Post by ian-weisser on 2014-10-10
> **imconfused2 said:**
>  Could this fix be put into the version in the repository? 

Perhaps. But perhaps not.
Updating software to a later release depends upon a few factors.

There are two ways to do it, since Ubuntu is not a rolling release:

- Stable Release Update: [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)
- Backport: [https://wiki.ubuntu.com/UbuntuBackports](https://wiki.ubuntu.com/UbuntuBackports)

I use Transmission 2.82 occasionally, and have not had the problem you describe.
So the bug may not be as widespread as you expect (insufficient for an SRU), 
or you may have a different issue completely...like ISP throttling.

---

### Post by imconfused2 on 2014-10-11
I ended up updating to Transmission 2.84.  Unfortunately this did not help.  I also use Ktorrent and Deluge. Both of these are a little better but far from good.  I am seriously thinking that this may not be related to the client at all.  The ISP throttling or ISP interference with the torrent protocols in some other way is getting to look more and more like the cause of all my problems.  Sorry about posting on this forum but the files are from the Ubuntu repository.

---

### Post by ian-weisser on 2014-10-11
I think you're quite right to post here.
You cannot know the source of the problem when you begin the journey.
If you discover anything else, do let us know.

Er, remember to uninstall any versions of Transmission that are not from the official Mint repositories (like 2.84) before you upgrade to the next version of Mint (or the next version of Transmission). Non-Mint software may be incompatible with Mint's package manager, and that may break the next upgrade.

---

### Post by Rob Sayer on 2014-10-12
I've had Mint installed on this netbook a couple of times ... I distro/DE hopped a bit before 14.04 came out for hardware support reasons.  I can't blame you for posting here.  Mint support is *awful*.  

I ended up searching here and on askubuntu for mint problems because AFAIK they don't even have people there who understood the problem.  They seemed *particularly* clueless when it came to communications issues.  Mint support is as bad as Ubuntu's is good.  I think Mint would be fine for experienced users but I couldn't recommend it to linux noobs.

The problem with using ubuntu for mint problems is that the kernel versions used *are* not the same.  The mint kernel is pretty much always months older.  So you can't guarantee a ubuntu solution will work, and novices can't tell when this is more likely.

And I definitely would never use the Ubuntu repos for a mint install, for reasons mentioned in post #5.

My recommendation would be to install ubuntu 14.04 in whatever DE version suits you and your hardware and get decent tech support.

BTW I use transmission and have never had any problems.  I suspect you may have another problem as well.

---

