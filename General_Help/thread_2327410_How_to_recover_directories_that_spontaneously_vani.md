---
title: "How to recover directories that spontaneously vanished?"
date: 2016-06-10
forum: General Help
---

### Post by bc9 on 2016-06-10
OK, please bear with me...


I've got this 1TB external USB hard drive, NTFS formatted, and it's on an old netbook that I leave running 24/7 for P2P filesharing with Transmission. The netbook runs an older version of the Crunchbang Linux distro (now BusenLabs Linux). Anyway, on the 1TB drive I have a top-level directory called "TRANSMISSION_EXTERNAL" under which I have (had) a separate directory for each torrent in order to stay organized. I.e.: inside "TRANSMISSION_EXTERNAL" there'd be a folder for "TORRENT_1" which would contain both the torrent (pointer) file and the file data for that torrent (being shared). I don't use the netbook for anything else: often I don't touch it for weeks at a time and just let Transmission do its thing.


I like to seed old/hard-to-find stuff, so I tend to leave torrents running for a long time. There are (were) a few hundred different torrents running, and thus, a few hundred sub-directories inside of the "TRANSMISSION_EXTERNAL" directory. Until one morning the other week, when I glanced at Transmission to see that it was reporting that hundreds of the running torrents were erroring because it now couldn't locate the relevant directories. I kid you not: about 95% of all the sub-directories inside of "TRANSMISSION_EXTERNAL" had vanished: they were nowhere to be found on the drive: not in Trash, or when viewing hidden files, etc... Only 31 directories remained of the hundreds that were there a day earlier.


I have no idea how or why they disappeared (a bug in Transmission? a gremlin in Crunchbang?) and am unable to find the missing directories (and the files they contain) but I think they're still on the drive because about 197GB of space is unaccounted for, as if stuff had been deleted but the space it used hasn't been freed up for re-use yet. Attached is a screen cap of Properties for the 1TB drive... as you can see, the current contents only account for 54GB of space, but 251GB is being "used" ...there's 197GB worth of stuff someplace that I can't see/find: that should/could be the vanished directories and their files.


[ATTACH=CONFIG]269513[/ATTACH]


In addition to searching the entire drive for known filenames, with Show Hidden Files turned on, I looked inside the ".Trash-1000" sub-directories and they only contain a few recent, manually-deleted files: NONE of the missing directories are in there. Nor are they to be found in the "$RECYCLE.BIN" or "System Volume Information" directories (that show up with Show Hidden Files; please see attached screen cap). 

[ATTACH=CONFIG]269514[/ATTACH]


Can anyone suggest a way that I could locate the 197GB worth of vanished directories that I suspect/hope are still intact somewhere on the drive? Maybe there's a file utility that would help? I've been careful to use the 1TB drive as little as possible to avoid accidentally overwriting the missing data. I've got the drive connected to my main PC now (running Ubuntu 14LTS) and would be *extremely* grateful to anyone who could tell me how to recover/salvage the missing directories if possible. Thanks in advance.

---

### Post by Habitual on 2016-06-10
Crunchbang?

---

### Post by bc9 on 2016-06-10
> **Habitual said:**
> Crunchbang?

#! was short for CrunchBang, a Debian-based Linux distro with a pleasantly minimalist GUI courtesy of Openbox. After the original developer Philip Newborough aka corenominal announced he was retiring in early '15 (from his work on #!), it was taken over and has been maintained/updated by BusenLabs Linux: [https://www.bunsenlabs.org/](https://www.bunsenlabs.org/) There's a brief overview of #! here: [https://en.wikipedia.org/wiki/CrunchBang_Linux](https://en.wikipedia.org/wiki/CrunchBang_Linux)

I chose #! for my ancient netbook (Pentium M from the mid-oughts w/less than half a GB of RAM) because it was just about the only Linux distro I could find at the time that was available not just in a 32-bit version, but also in a 32-bit ***NON*-PAE **version (physical address extension) meaning it can run on old PCs w/CPUs that predate/didn't include the implementation of PAE, like my ancient little netbook. More on PAE here: [https://en.wikipedia.org/wiki/Physical_Address_Extension](https://en.wikipedia.org/wiki/Physical_Address_Extension) According to this page at the BusenLabs site, they still offer/support a non-PAE version: [https://www.bunsenlabs.org/installation.html](https://www.bunsenlabs.org/installation.html) referred to as "bl-Hydrogen-i386+NonPAE.iso" in case anyone wants to amaze themselves that a *really* old PC can run a contemporary OS, along with the current versions of Firefox, OpenOffice, etc... :P

Because P2P filesharing progress is far more limited by the speed of my net connection than by PC specs, it just made sense for me to run Transmission on the smallest, lowest-power-using, quietest little PC I had on hand at the time (the netbook), instead of on my main PC running Ubuntu (which is of modest spec and a decade old btw, but runs so well I've no need of something newer) ...especially since as a P2P machine, it's on 24 hours a day, 7 days a week.

Hope this answers your question re: CrunchBang. ;-) If you were recognizing me instead... yes, I use "Crunchbang" in my username on other forums. ;)

I look forward to someone more learned than I in the ways of Linux suggesting a way to recover my missing directories, as they represent countless hours of P2P effort.

---

### Post by X-RED_Tech on 2016-06-10
NTFS is a no-brainer if you have any Windows 2000 or newer available, even in a virtual machine. The first thing to do is connect it, let Windows recognize the drive and most likely it'll suggest error correction; confirm and let it work. If not, run the error correction tool anyway. That's probably all you need, assuming those are logical errors. It may not be possible to correct physical errors if the drive is failing.

---

### Post by bc9 on 2016-07-11
> **X-RED_Tech said:**
> NTFS is a no-brainer if you have any Windows 2000 or newer available, even in a virtual machine. The first thing to do is connect it, let Windows recognize the drive and most likely it'll suggest error correction; confirm and let it work. If not, run the error correction tool anyway. That's probably all you need, assuming those are logical errors. It may not be possible to correct physical errors if the drive is failing.

Thanks for the reply and sorry for my delayed response... I was offline for a bit.

Per your suggestion I plugged the drive into a Win10 laptop and the drive mounted normally... no dialog suggesting error correction came up. Checking properties for the TRANSMISSION_EXTERNAL and .Trash-1000 folders on the drive show their contents total about 11GB. However, when checking properties for the whole disk itself, it still reports 239GB used... thus, there's still more than 200GB of space missing: the vanished data I'm guessing.

The Win10 laptop is low-end... if it has whatever error correction program that you think I should run manually, just let me know what it's called and I'll give it a try (I'm not that familiar with Windows in general). 

Though it's possible, I don't think the drive is failing or physically defective. Just a feeling on my part. Thanks again for the feedback... any/all help appreciated as I'd still like to salvage the missing data if possible.

[COLOR=#000000][FONT=&quot]*Added later: well, I sort of ran out of patience (and have other, more vital stuff needing my time) so I put the drive back on the netbook and re-started Transmission, even though only about 30 of the hundreds of partially-completed torrents will run now. I know there's a chance that re-starting downloads may overwrite some of the lost data, but I figure completing some of the torrents is better than completing none, and some of the remaining/working 30 are quite rare, so they're worth seeding for as long as possible.*[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]*If anyone can shed some light on how to try to recover the lost data, I'D STILL LOVE TO HEAR ABOUT IT! Thanks!*[/FONT][/COLOR]

---

