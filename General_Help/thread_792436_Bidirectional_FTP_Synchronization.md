---
title: "Bidirectional FTP Synchronization"
date: 2008-05-12
forum: General Help
---

### Post by jeffimperial on 2008-05-12
I'm a pretty recent convert to OSS in general and Ubuntu in particuler (OS at least).

With some ~2500 files to be processed each day, the Web designer that I am needs anything that resembles, even distantly, what *_Adobe Version Cue_* does. I've been trying to discover **Subversion** but I find it too partial to developer language. It's so _difficult to set it up_. So I'm looking for something with **[COLOR="Red"]GUI,[/COLOR]** not CLI.

Another difficulty is that I don't have Server Admin rights since I'm allowed to do  that only from the Workstation at the office (We're still in XP there, and I have migrated partially to Ubuntu at home). Hence, **[COLOR="DarkOliveGreen"]I only have FTP access[/COLOR]**, no SFTP or SSH. I want to do a little of the workload at home, but want to do it from Ubuntu to complete my migration.

Oddly enough, the **Server is a Linux machine**. Maybe that's a plus. I can connect to it via Places > Connect to Server... Service Type: FTP (with login). But manually doing the sync is way too much murder.

I have tried using **CrossFTP** and it can be used, but it's way too _cluttered_ with way too much overhead.

Suggestions will be very, very appreciated.

---

### Post by ajopaul on 2008-05-13
am not to sure if i have got wat u need exactly, wget wput ??

---

### Post by jeffimperial on 2008-05-13
> **ajopaul said:**
> am not to sure if i have got wat u need exactly, wget wput ??
Here's a less lengthy description of what I had in mind:

You create pages with Bluefish (which is great by the way) then you save the page and its related files and folders in /home/me/website1. Then I tell _the_program_ to look into that folder and compare it to ftp.website.com/public_html. When _th_program determines two files have different timestamps, it copies the recent version over the old one. And if a file is nonexistent in one end (say the local folder), it copies that file to the other (the remote folder).

---

### Post by p_quarles on 2008-05-13
You should take a look at Unison. It's essentially a bi-directional rsync, and does what it sounds like you're looking for.

---

### Post by jeffimperial on 2008-05-13
> **p_quarles said:**
> You should take a look at Unison. It's essentially a bi-directional rsync, and does what it sounds like you're looking for.
Thanks for the tip. Unfortunately, I don't think it would help me. The Server soes not allow SSH connections; only FTP. But  I'm still not sure. I'm looking at [http://www.micahcarrick.com/11-07-2007/unison-synchronize-ubuntu.html](http://www.micahcarrick.com/11-07-2007/unison-synchronize-ubuntu.html) and as I see it [perhaps I'm mistaken] it says I need the remote computer to talk to my computer via SSH.

---

