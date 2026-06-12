---
title: "Hoo boy -- waited too long to upgrade"
date: 2012-11-16
forum: General Help
---

### Post by Rocket J Squirrel on 2012-11-16
All right, all right, I should have done this sooner. I decided this evening to go from Ubuntu 10.10 to 11.04, and then to 12.04. But Upgrade Manager discovered that the upgrade packages have been taken offline. 404s is all it found. 

Drat. 

Is now my only option to do a new install of 12.04, overwriting all my stuff?

---

### Post by cwsnyder on 2012-11-16
Been sleeping long, Rip Van Winkle?  10.10 Maverick Meerkat was dropped from support in April, 7 months ago.

If you have a separate /home partition, you won't lose anything but the actual installation of any packages not included in the new release when you upgrade from either USB or CD/DVD.  Otherwise, now is the time to backup your old /home folder and begin again.

---

### Post by snowpine on 2012-11-16
A new install is not your only option (but it is a very good option!) you can also try this:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

I wouldn't go through all that hassle, personally, I'd just do a fresh install (maybe as a dual boot so I could switch back and for for a while until I was sure the new system was set up just as I like).

---

### Post by Rocket J Squirrel on 2012-11-16
> **cwsnyder said:**
> Been sleeping long, Rip Van Winkle?  10.10 Maverick Meerkat was dropped from support in April, 7 months ago.

Yeah, yeah. 

> **cwsnyder said:**
> If you have a separate /home partition, you won't lose anything but the actual installation of any packages not included in the new release when you upgrade from either USB or CD/DVD.  Otherwise, now is the time to backup your old /home folder and begin again.

Nah, no separate /home partition. I'll back the darn thing up on some external HD, bite the bullet, and do a fresh install of 12.04.

So lemme ax you a question: once I got the new OS installed, do I just copy over the new /home folder with the backed-up one?

I guess I'm concerned that there may be User issues, etc.

---

### Post by wildmanne39 on 2012-11-16
Hi, as long as you just copy your personal files and not any system setting or system files you will be fine.
Thanks

---

### Post by Rocket J Squirrel on 2012-11-16
> **Wild Man said:**
> Hi, as long as you just copy your personal files and not any system setting or system files you will be fine.
Thanks

Hey, thanks. Does this mean that everything in the /home folder, and its subdirectories, are okay to overwrite what the new install puts into place?

---

### Post by wildmanne39 on 2012-11-16
Hi, probably not everything, there are hidden files which can cause issues it did for me a few months ago.

When you are in your home folder hit ctrl+H and see what hidden files are there.
Thanks

---

### Post by Rocket J Squirrel on 2012-11-16
> **Wild Man said:**
> Hi, probably not everything, there are hidden files which can cause issues it did for me a few months ago.

When you are in your home folder hit ctrl+H and see what hidden files are there.
Thanks

Good information. So things that are NOT in hidden (.) folders are okay to overwrite. But if it's in a .hidden folder or .file, no overwriting.

(Hm, this might take some thinking.)

---

### Post by wildmanne39 on 2012-11-16
It is best to just look closely, I would not copy old template folder to your new system either.

---

### Post by kostkon on 2012-11-16
> **Rocket J Squirrel said:**
> All right, all right, I should have done this sooner. I decided this evening to go from Ubuntu 10.10 to 11.04, and then to 12.04. But Upgrade Manager discovered that the upgrade packages have been taken offline. 404s is all it found. 

Drat. 

Is now my only option to do a new install of 12.04, overwriting all my stuff?
EDIT: Sorry, I thought you had 10.04...

---

### Post by Rocket J Squirrel on 2012-11-16
> **Wild Man said:**
> It is best to just look closely, I would not copy old template folder to your new system either.

No worries there: my template folder is empty.

(I don't even know what that folder does for a living.)

---

### Post by 3rdalbum on 2012-11-17
Hang on a sec, people are giving you confusing information.

Ubuntu 12.04's installer also has an "Upgrade" option. What this does is:

1. Make a note of what packages you have installed
2. Do a fresh install of Ubuntu
3. Install the latest versions of the packages you had installed
4. Preserve your /home directory and all personal files and settings it contains - even if it's not on a separate partition.

So, no need to back everything up (although it's a good convenient time to do so), just use the Upgrade option and you'll end up with a clean install AND not lose any data.

The only settings you may lose are system-wide settings - for instance, your smb.conf, blacklist.conf, X11.conf, stuff like that.

---

### Post by Wim Sturkenboom on 2012-11-17
> **3rdalbum said:**
> 
Ubuntu 12.04's installer also has an "Upgrade" option
Does that work from 10.10 to 12.04? I have always been under the impression that one has to do all upgrades, so 10.10 -> 11.04 -> 11.10 -> 12.04. This also applies to LTS version, except for the fact that one only has to upgrade to 'in-between' LTS versions; so 6.06 -> 8.04 -> 10.04 -> 12.04.

---

### Post by matt_symes on 2012-11-17
Hi

> **snowpine said:**
> A new install is not your only option (but it is a very good option!) you can also try this:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

I wouldn't go through all that hassle, personally, I'd just do a fresh install (maybe as a dual boot so I could switch back and for for a while until I was sure the new system was set up just as I like).

Interestingly enough, the site [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) does not currently contain the Natty repo's, as i was also thinking of suggesting this method as an upgrade option.

[http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/)

I'm sure Natty will be added soon though so, OP, if you want to wait....

@OP. 

Bear in mind that there have been a HUGE number of changes between 10.10 and 12.04 including, but certainly not limited to, the move to gtk3 and the Unity interface.

This may make any upgrade more problematic than usual. The usual caveats apply, if you do decide on the upgrade option, such as disabling third party repos.

I don't think you can upgrade from 10.10 -> 12.04 using the CD in one step.

Kind regards

---

### Post by Rocket J Squirrel on 2012-11-17
Thanks, all, for taking a look at this.

I'm probably going to backup and restore /home after doing a fresh install of 12.04

I understand from the above that I should restrict this to non-hidden files and folders. 

So, can someone provide a command line method to copy all /home stuff to an external drive, but only non-hidden stuff?

---

### Post by dino99 on 2012-11-17
From the repo:

[HTML]Déjà Dup is a simple backup tool. It hides the complexity of backing up the
Right Way (encrypted, off-site, and regular) and uses duplicity as the
backend.

Features:
 * Support for local, remote, or cloud backup locations, such as Amazon S3,
   Rackspace Cloud Files, and Ubuntu One
 * Securely encrypts and compresses your data
 * Incrementally backs up, letting you restore from any particular backup
 * Schedules regular backups
 * Integrates well into your GNOME desktop[/HTML]

but if you understand what you are doing, you will not format your /home partition (said "partition" as you might have, not /home folder) and only format / to install the new release.

---

### Post by Rocket J Squirrel on 2012-11-17
> **dino99 said:**
> but if you understand what you are doing, you will not format your /home partition (said "partition" as you might have, not /home folder) and only format / to install the new release.

From this I gather that some use a separate partition for /home.

Of course, the key phrase is "[...]  if you understand what you are doing [...]" 

I have Deja Dup installed and it's presently running. I see it is backing up hidden folders and files in /home, and advice above said that I probably don't want to restore those on top of the hidden files/folders that the new install of 12.04 will put in place. I'll look around and see how to specify "not hidden" files for restore.

---

### Post by cwsnyder on 2012-11-18
@Rocket J Squirrel: You may want to take your chances in restoring the .mozilla  folder if you use Thunderbird, or other hidden file which contains your old mail folders, otherwise you will lose them.

What I would recommend on 'hidden' files and folders is to backup the **new** files and folders as well and restore the old hidden files, then judiciously repair the old files in place from settings in the **new** files after you see what is broken.  That is one reason to keep your backups at least for a month or so while you make sure everything is stable.

---

### Post by Rocket J Squirrel on 2012-11-19
cwsnyder: thanks -- perfectly sensible suggestion. Another "hidden" folder here is used by Liferea, the rss reader I use. For that, the easy solution is to export the feedlist and import it later. 

Thunderbird is a bit clunkier, I'll restore the old profile. Chrome, export the bookmarks.

---

