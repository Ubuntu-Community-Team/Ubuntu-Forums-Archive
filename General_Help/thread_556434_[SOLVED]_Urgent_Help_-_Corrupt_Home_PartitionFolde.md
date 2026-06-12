---
title: "[SOLVED] Urgent Help - Corrupt Home Partition/Folder?"
date: 2007-09-21
forum: General Help
---

### Post by Scruffynerf on 2007-09-21
Urgent Help required please (typing this from windows partitions)..

Apologies for the long post, but wanted to include as much info as possible.

A combination of a bad bug and updating the system seems to have hosed my home partition, located on a separate hard drive, containing amongst other things photos of my 8 month old son.

After recently updating *something* (can't remember what) and rebooting I was presented with an unusual error on boot.

The error was:
```
Your $HOME/.dmrc file has incorrect permissions and is being ignored. 
This prevents the default session and language from being saved. 
File sould [sic] be owned by user and have 644 permissions
```

So I googled it, and located Ubuntu Bug report #27281. Read for a bit and ended up doing this:
```
sudo chowned scruffy /home
sudo chmod 755 /home
sudo chmod 644 /home/.dmrc
```
(at least that seems to be what I did. Reboot

All good for a while. Some more updates come through, and I download them and some games via synaptic.

Simultaneously open Firefox.

After ~30 seconds, screen turns white, and everything stops - mouse, clock, disk activity... everything. Control+Alt+Backspace (to restart the GDM) does nothing. Keyboard appears to be frozen out as well.

After waiting for 5 mins (just in case) I manually reboot the machine (power cycle). Ubuntu reboots, and my desktop comes up. Odd that it **did not fsck**. More oddly, it auto-opened 2 applications that I was not using - gedit the sources.list and azureus (installed, but not run in a week or so)

Close the apps, open synaptic, it errors out, wanting me to 
```
sudo dkpg --configure -a
```
which I do.
Re-open synaptic and begin to re-install the software originally started.

GDM restarts by itself.

White screen of death appears (WSOD).

Boot back into windows, and as I can read ext filesystems in windows I begin wanting to backup stuff.

Now it gets weird. I can mount my home partition to a windows drive.
I can see the usual folders that appear, even the folder for my username.
In my username folder, I can see all the .application folders, and most of the .application config files. I can successfully copy over my conky settings, and my thunderbird email profile, as well as my firefox bookmarks.

HOWEVER, the important stuff was all located in a folder underneath the username/Desktop folder.

Which is just plain gone. It's not there. It's not flaming anywhere. There were movies, cd collections, and most importantly, photo's of my son in there.

Eeek. 

What I've tried:

Via the windows partition, I've manually combed through everything. It's not there.
I've booted into a Helix Forensic LiveCD and ran Recovery. Nada.
From same LiveCD, I've run Autopsy, however that thinks that I am running BSD. Nope.

I'm currently running Photorec 6.8 across the drive, and that's found a whole lot of garbage, but not my photos.

Is there anything else that I can try? Are there ext3 filesystem undelete tools that will run from XP at all?

---

### Post by Scruffynerf on 2007-09-21
Bump - please help

---

### Post by nick_h on 2007-09-21
First of all before doing anything else I would make a backup of the partition by booting from a recovery CD and using dd to make a copy.

It might be worth running fsck.  You can use the -f option to force a check.

I don't know of any ext3 recovery tools but I am not a linux expert.  Perhaps someone else could suggest a recovery tool.

---

### Post by phidia on 2007-09-21
What nick_h said and take a look at [systemrecovery cd]("http://www.sysresccd.org/Main_Page") you can also search freshmeat.net for recovery applications, but unfortunately this points up that backing up is a necessary discipline.

---

### Post by dabl on 2007-09-21
> **Scruffynerf said:**
> 

After waiting for 5 mins (just in case) I manually reboot the machine (power cycle). 

It's a painful story, and of course no one can tell what "updating *something*" might actually be.

However, here's a tip for future "lockups" or "freezes" -- which are terms that probably should stay in the Windows World where they originated.

IT IS NOT NECESSARY OR ADVISABLE TO PRESS THE POWER SWITCH TO RESTART!

Instead, remember this"

"_R_aising _S_kinny _E_lephants _I_s _U_tterly _B_oring"

Use the Alt-SysRq key combination, followed by letters r, s, e, i, u, b, and your system will be recovered sufficiently that you can issue the ```
sudo shutdown now -r
``` command, to give it a graceful shutdown without filesystem damage.

On your /home partition, if it were me, I would use a Knoppix live CD to check it out, and see if I could copy those precious files off somewhere safe.  :)

---

### Post by Scruffynerf on 2007-09-22
Update: Many thanks for the responses.

Dabl: thanks for the info, however a non-functioning keyboard is non-functioning whatever key combination is hit.

Interesting though.

Update:

I've been able to locate copies of most of the pics - from old backups (why my other half created a new folder and not let me know is beyond me), from my fledgling website, and from the computers of friends that we emailed to.

In the end, I gave up and did a full format and re-install of Feisty with a new home partition (also re-formatted).

What had seemed to happen though was strange. The partition turned out to be reasonably healthy (considering). I was able to retrieve a lot of things from the /.application folders - all my emails, bookmarks files etc intact.

What was lost was any and all data held in folders on the desktop. Actually it was the Desktop itself that was toasted. Anything below the desktop in the folder tree was fine, anything above was gone.

Anyway, must dash, still installing software.  If anyone can hazard a guess as to what actually happened I'd be interested.

cheers

Scruffy

---

