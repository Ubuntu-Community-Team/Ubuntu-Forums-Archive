---
title: "Syncing save games to server"
date: 2020-06-22
forum: General Help
---

### Post by Eragon615 on 2020-06-22
I've got a bunch of devices in my house that I game on, and all of them access the games and save data to an Ubuntu 20.04 server. It works wonderfully for anything constantly on my home network. The trouble comes for mobile devices, such as my laptop and phone, that I leave the house with. 

Ideally, I should be able to do something to target all of a file type (.sav for instance) and it would check if the server file or local file is newer, then sync the newest version. I've heard of rsync, but I've never used this before and I'm having difficulty understanding how to make that work, if it can.

Any suggestions? It'd be nice not manually moving files every thing I decide play something on my PC that I played on my phone last, especially since it means using scp on a phone keyboard.

---

### Post by TheFu on 2020-06-23
Rsync needs an ssh connection + rsync on both sides of the connection to work.  I've only used it to push music onto Android, never the other way around.  I don't consider android to be any "system of record", so nothing gets left there of any import.  When I get home from a trip, I'll USB connect the devices and grab photos to be placed into my photo management system. Any photos on any Android device that aren't in the DCIM/ directory have been pulled from my photo management system.

As for backups, I use adb to backup android stuff, but I'm passed the time when I'm loading and unloading apps. 

```
adb backup [-f <file>] [-apk|-noapk] [-obb|-noobb] [-shared|-noshared] [-all] [-system|-nosystem] [<packages...>]
``` The adb manpage as all the details.  It isn't a versioned backup. We get a ZIP file. Keep a few of those and don't get any media, then it won't be large at all.
There's an **adb restore** command.

Two of my Android devices aren't connected to google and I don't trust android enough to allow texting or email on those devices.  I do hook in with some **nextcloud** clients, but none of that data is important. I certainly would back it up off android. Nextcloud is the "system of record."

Basically, I have specific "systems of record" for different sorts of files.  Any other copies are, by definition, unimportant.  I'm willing to delete those other places at any time or have the device lost/stolen without fear.  I've had an unlocked Android phone stolen while overseas on the 2nd day of a 3 week trip.  That taught me some valuable lessons.

---

