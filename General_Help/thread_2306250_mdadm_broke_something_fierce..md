---
title: "mdadm broke something fierce."
date: 2015-12-13
forum: General Help
---

### Post by Roasted on 2015-12-13
Hello friends. I'm posting here today not for a resolution, as we're already past that, but for sake of getting a conversation rolling on a troubling topic. 

I am running Ubuntu 15.10. Ubuntu itself is on an SSD, whereas /home is on two 1TB HDDs in a software RAID mirror with mdadm. This array was set up years ago and has been entirely problem free ever since I set it up. Yesterday I booted up and Ubuntu 15.10 and it went into emergency mode. I hadn't made any changes (at all) to mdadm over the course of yesterday, let alone in the past few months/years. It just worked. In terminal mode, I checked out a few things and noticed that mdadm was giving me a strange output. The most telling thing I noticed was the UUIDs had changed. Overall, my system looked like this:

sda = RAID drive 1
sdb = RAID drive 2
sdc = SSD for /
md0 = RAID mirror for /home

On a hunch I edited fstab to comment out my auto-mount line for my home directory (which would mount as /home). Once I rebooted, it powered up and hit the login screen fine. I couldn't log in though as a home directory didn't exist for my user, so in a TTY I ran cp -R /etc/skel /home/jason and chown'd jason:jason for /home/jason, thereby creating a fresh home directory for myself with myself as the owner/group. Once logged in I dug further and noticed some weirdness. Somehow the UUID for md0 was gone, yet the UUID for sda was listed as the UUID of md0. I couldn't change anything. I couldn't get mdadm to assemble. I couldn't get mdadm to scan. I couldn't fail any of the drives out of the array. I couldn't mount sda or sdb individually. I literally had nothing, nothing whatsoever to go on. I Googled for hours until every single link was purple (indicating I had already been there). In the end, since I had a backup, I choked it up as a fluke and a total loss. I've since rebuilt my drive structure to act in a different fashion (sda for /home, but upon login an rsync job runs to sync everything on sda to sdb -- this is something I've been meaning to do but just haven't had the time to do it). 

I thought this was just a fluke, until I struck up conversation with a friend of mine. He said he had the same exact thing happen. Distro? Ubuntu Gnome 15.10. When? Yesterday. His details? Three drives in RAID 0 using... yep... mdadm. So we're talking about two totally different users on a 15.10 base using mdadm that got mega hosed on the same day. Coincidence? 

Given this, it concerned me to say the very least, and I felt compelled to do something, anything, and decided to make a post here in hopes that somebody might have some sort of idea what happened. As I said, this array was a *total* loss and the only thing that bailed me out was the fact I had a backup on my NAS (my backup runs every time I log in, so it was incredibly recent, fortunately). The buddy in question and I are in the process of getting info together to dig deeper and see what happened in hopes that it may assist developers if we submit a bug report, but in the mean time... does anybody have any idea what could have happened? This sort of loss screams "mega cheap budget hardware RAID card" to me -- not something I'd expect from the tried and true mdadm I've used consistently over so many years.

Any input is greatly appreciated.

PS - For the love of all your precious data, back your stuff up. Now. Seriously. Do it now. ;)

---

### Post by TheFu on 2015-12-16
What do the log files say?
Without that, we don't have any real facts.

For your friend using RAID0 - well, er ... no comment.

---

### Post by Roasted on 2015-12-16
> **TheFu said:**
> What do the log files say?
Without that, we don't have any real facts.

For your friend using RAID0 - well, er ... no comment.

I didn't notice anything in the logs that was mdadm related. All I could articulate was when I powered down the day before, all was well. Powered up, hosed.

Nothing wrong with RAID 0, pending you use it in the appropriate situations with adequate backup solutions for the data in question. I'm relatively certain he utilized RAID 0 just for the OS, however I'm not certain.

---

