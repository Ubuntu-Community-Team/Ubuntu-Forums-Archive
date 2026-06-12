---
title: "Apparent system compromise: any advice?"
date: 2007-11-30
forum: General Help
---

### Post by rh1zome on 2007-11-30
Yesterday Nautilus suddenly started treating all of the text files under my home directory as executable. Rushing to my logs I noticed that my machine had rebooted spontaneously early that morning before I arrived at my desk (unusually for me, I had left my machine running overnight). I presume I had to log in, but this alone wouldn't have set alarm bells ringing, as I often log out before walking away from my machine.

Anyway, I belatedly installed chkrootkit which claimed that my shell history file had been altered (I think that was the message) and that while checking z2 it had been detected that my (non-root) user account (the one I was currently logged in to and using) had been "deleted or never logged from lastlog". A quick bit of Googling seemed to confirm my fears. The majority advice was to disconnect from the network, remove any binaries from within my data folders, back up the data and wipe the partitions - ASAP.

This I promptly did. After reinstalling, I installed the flagged updates and then installed chkrootkit again. This time round, there was no shell history problem, but again it claimed that my user account (the only one on the machine, that had only been created 30 minutes or so previously, and one that I had been using continually since the rebuild) had been "deleted or never logged from lastlog".

I'd only just wiped the partitions. I'd given my account a new, more formidable password (the original wasn't exactly weak), but yet, barely 30 mins after rebuilding, I was seeing this message again from chkrootkit. 

I also rebuilt a laptop which had also failed the chkrootkit test. I deleted and recreated the partitions (as with the desktop, using the Ubuntu installer). With the laptop I didn't bother with the updates, immediately installing chkrootkit. However, it reported the same message as on my desktop: "<currentuser> deleted or never logged from lastlog" (as with the desktop, all other checks were negative).

The only other machine running on my LAN while I reinstalled was my file server (Ubuntu Server 7,10). chkrootkit gives a clean bill of health to this machine, and although I've seen no evidence to suggest that anything is amiss with it, nevertheless, in retrospect I wish I'd shut it down while reinstalling my desktop and laptop, for obvious reasons.

Anyway, this is the situation. What do people think? Any advice? Might this be an issue with chkrootkit, or is it likely that something malicious survived the partition deletions, presumably using the (apparently-fine) file server, or, however unlikely, possibly even my Linksys wireless gateway or Edimax access point (both of which have Linux embedded)?

Footnote: 
- All the machines referred to above are running Ubuntu 7.10.
- My LAN is a wireless one, encrypted using WPA2 (with a looooong passphrase), and containing a Linksys WAG54GS ADSL gateway and an Edimax EG-7209APG wireless access point.
- My backed-up data had not been re-installed before chkrootkit was run on the fresh builds, and so there was no chance of re-infection from that source.

---

### Post by HeavyAl on 2007-11-30
Chkrootkit is known to give false positives under various conditions. I've heard rkhunter makes a good complement to it as it runs overlapping tests.

---

### Post by rh1zome on 2007-11-30
Many thanks HeavyAI. Have installed rkhunter, updated its databases and used it to scan my filesystems. It found some hidden directories and one or two hidden files, although research indicates that what was found is both common and most likely harmless.

It's nice to have some reassurance, although I'm still concerned about what caused the original file permissions changes and subsequent unattended reboot (our electrics here have recently been thoroughly overhauled and the PSU in the machine in question is a recently purchased, high quality Nesteq unit, and really ought to be able to ride any minor current fluctuations.

---

