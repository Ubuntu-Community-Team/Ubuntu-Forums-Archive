---
title: "877GB of Log Files (2 files) Cannot Be Deleted"
date: 2017-05-04
forum: General Help
---

### Post by Kerry Lange on 2017-05-04
I have a drive accidentally overwritten with a new file system and I used TestDisk to try recovering some files I need. While using TestDisk, the program created two log files totaling 877GB. They're located in the following folder:

[INDENT]/home/USER/.local/Share/Trash/Files[/INDENT]

When I try deleting them from within Ubuntu (17.04), I get a small dialogue box saying they're deleted and offering an "Undelete" button. However, the files don't disappear and when I check disk use, I'm still down to 52 MB free on a 1 TB drive. I've tried using Nautilus as superuser to delete the files but get the same result.

I've tried changing permissions for the files and the folder and I've tried loading Knoppix via DVD to delete the files. When I boot Knoppix from DVD and delete the files, they disappear but when I get back into Ubuntu, they're still there taking up space.

Also, the Trash icon in my menu bar indicates there is nothing in it and when I right-click to get a "Delete" option, it's greyed out.

Does anyone have suggestions?

---

### Post by mastablasta on 2017-05-04
simplest solution save files you need to another disk, then "nuke" the drive and reinstall the OS.

---

### Post by steeldriver on 2017-05-04
Seems extreme - have you tried removing them from the command line? if there's nothing else you are likely to want to restore from the user's Trash folder, then you should be able to simply delete the whole thing:

```

rm -rf /home/USER/.local/share/Trash/

```

You will need sudo if you are attempting this as a user other than USER (or root)

---

### Post by Kerry Lange on 2017-05-04
Steeldriver, I will try via the terminal as you've suggested.

Mastablasta, since starting to use Ubuntu, I've lost count of all the times I've nuked the disk and re-installed. I'd thought of this myself for this instance but didn't want to give up that easily.

---

### Post by mastablasta on 2017-05-05
let us know how it went. file manager is just gui for terminal.

i think shift+del in file manager will remove the file without moving it to trash first.

seing that you can't delete the file with live OS i suspect something could be written in the disk table where file managers will not reach. which is why reformating might solve it. i could be wrong though. so do try other things first if you have the time.

---

### Post by dragonfly41 on 2017-05-05
Can you overwrite the log files with smaller files?

---

