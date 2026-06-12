---
title: "Ubuntu 18.04 LTS - Ideal Configuration for Sharing an External USB Drive"
date: 2019-03-09
forum: General Help
---

### Post by hammmy on 2019-03-09
Hardware: ODROID C1+ (AmLogic S805)
OS: Ubuntu 18.04 LTS with 3.10+ kernel

Over the past several years, I have used this little SoC as a Samba share on my LAN.  Each time I've had cause to fiddle with it (upgrade, change OS, etc.), I've had no end of difficulty whenever I get around to the bit where I share an external drive using Samba.  This time, I'm taking a step back and asking for some help with how I'm conceiving the use of this device and attached drive.
I have a 8TB Western Digital drive in a USB enclosure.  The data on it is organized in four folders on the root: /Audio, /Video, /Data and /Photos.  Ideally I would like to share /Audio and /Video with 755 permissions to whomever is on my LAN (with no credentials), with the entire drive accessible only to sudo-level users.  I visualize accomplishing this with three separate Samba shares: Audio, Video, and the drive's root as the super-secure share. Each time I've waded into this battle with starry-eyed optimism only to be routed into disgraceful 777 nobody:users with a single share for the entire drive.

I learned years back that the FSTAB entry for the drive is key and therefore so is the mount point folder.  I use /media/<username>/WD_8TB.  Where I always end up having to give up the fight is right here: how should I set ownership of this mount point folder in order to do what I want to?

Thank you for reading.

---

### Post by hammmy on 2019-03-09
Pondering a bit, possibly less coherently than what usually passes for cohesion inside my eggspace:

Samba is essentially the only user that needs to own the mount point and attached (NTFS) filesystem.  Samba then distributes (and creates) the content via its own system of users, passwords and shares: an additional abstraction layer.  There aren't any other local users on the ODROID who will be creating content so there's nothing to interfere with Samba ownership.  I would be touching the drive regularly to back it up to another LAN device but I should be able to manage this via the whole-drive Samba share.

So if the above makes logical sense, it would seem that I should mount the drive in FSTAB with CIFS while explicitly calling out the Samba user as owner.  I should do this by calling a credentials file that contains username/password for the Samba user.  I can then lock down the credentials file so it cannot be viewed outside the sudo group (FSTAB is readable by any ol' wandering dogbarber).

This is my plan of attack for today, barring the intervention of actual strategerie from folks who know what they're doing.

---

### Post by hammmy on 2019-03-09
Characteristically I was wrong; there is a local user that needs to create content on the drive: [shh]torrent client[/shh].  Hmm.  Maybe add both users to a specific group?  I could set directory permissions to propagate themselves so Samba maintains ownership over any other incoming content, I reckon.

---

### Post by hammmy on 2019-03-13
I think I have achieved enlightenment.  On an NTFS mount, a user must be assigned as owner or it defaults to whomever mounted it, which is the root user for NTFS.  Alright, so I mount with uid= and gid= and away we go.  I set the mount point folder to 2775 permissions with the same user and group ownership and voila, the 775 looks to be valid (didn't try creation yet).

Now in my Simple Jack existence, the 5 in 2775 should mean I can map the Samba guest account to nobody and bad user to guest and share /Video and /Audio to public=yes.  Instead, life is like a box of chocolates and they're always the horrible raspberry nougats.  What Samba apparently does is check, hurrdurr is this guest user with no credentials the owner of these files that are specifically shared to the public?  Nope!  Well, I'll just spam him with logins and maybe he'll give up.

So...now I remember why I had to set the drive to be mounted as nobody:nogroup the last time I farted around with this.  Otherwise Samba is just going to go full retard.  I suppose I can try force user=currentMountUser in the Samba config for the open shares.  I'll see if that still prompts for login, which I suspect it will, which then means I just abandon the open share concept and curse this whole debacle for a waste of neurons until the next time I futz with this box.  At least I'm writing up the process this time, though (not just here, which has been more of a conversation with the abyss).

---

### Post by hammmy on 2019-03-16
Yep, as I feared forcing user=currentMountUser still required login credentials so I have abandoned the project in favor of secure sign-ins by keepers of the password only; all others are SOL.

I find this a very irritating limitation but no one consulted with my emotions before coding so I too am SOL.  As long as NTFS requires assigning a specific owner at mount and Samba requires the file's owner to match the user, I don't see how this can be worked around.  I would consider going with a different filesystem on the drive but if for hypothetical argument's sake that the house is on fire and I grab the drive and run, do I really want to install Ubuntu before I can access my insurance files?  No; NTFS it remains.

I'll monitor the thread for a few days in hopes that someone shows up and says, hey softskull, here's how you do it.  Otherwise, consider the thread closed.  Thanks and good luck to all!

---

### Post by HermanAB on 2019-03-16
Note that the easiest way to share files with another UNIX/Linux machine is with SCP.  The easiest way to share with a Windows machine is with Anonymous FTP.

Samba is overkill for most situations and it is very error prone.  I gave up with Samba decades ago.  To me, it is a waste of time.

---

