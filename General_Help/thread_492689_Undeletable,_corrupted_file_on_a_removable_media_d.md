---
title: "Undeletable, corrupted file on a removable media device"
date: 2007-07-05
forum: General Help
---

### Post by Seantiago on 2007-07-05
So I have this little weiner mp3 player that I was really looking forward to using:

[http://www.cowonamerica.com/products/iaudio/f2/](http://www.cowonamerica.com/products/iaudio/f2/)

But now I have this issue. It won't let me copy any files to it. I believe I've traced the problem down to this one silly little corrupted directory that is just screwing everything up. I would remove it, but it keeps telling me that I don't have permission to get rid of it, that this is a read-only file system, etc, even when I use sudo to try to delete or move it. Some fool on another forum who had a similar issue said he was going to have to reformat it. (I would ask him for specifics, but I'm having trouble tracking him down) Reformatting seems pretty extreme, and I'm not even really sure how to do that in the first place. 

Also, I've tried deleting it on different computers (including windows machines), but nothin' doin'. And it doesn't show up in the mp3 player's menu (i.e. tracklistings and such).

Any ideas?

Oh, and this is the output of ls -l /the/path/the/themp3players/shittyassfile:

```
total 0
?--------- ? ? ? ?                ? Joanna Newsom - The Milk-Eyed Mender

```

Thank you.

---

### Post by PaulFr on 2007-07-05
Did you try **dosfsck** ? If you want to delete the file, see the **-d** option in the man page.

---

### Post by Seantiago on 2007-07-05
Here's the output of dosfsck:

```

sasquatch@sasquatch-laptop:/media/IAUDIO/MUSIC/Muzak$ dosfsck -d /media/IAUDIO/MUSIC/Muzak/Joanna\ Newsom\ -\ The\ Milk-Eyed\ Mender
usage: dosfsck [-aAflrtvVwy] [-d path -d ...] [-u path -u ...]
               device
  -a       automatically repair the file system
  -A       toggle Atari file system format
  -d path  drop that file
  -f       salvage unused chains to files
  -l       list path names
  -n       no-op, check non-interactively without changing
  -r       interactively repair the file system
  -t       test for bad clusters
  -u path  try to undelete that (non-directory) file
  -v       verbose mode
  -V       perform a verification pass
  -w       write changes to disk immediately
  -y       same as -a, for compat with other *fsck
sasquatch@sasquatch-laptop:/media/IAUDIO/MUSIC/Muzak$

```

So it seems like that didn't work. Could it have anything to do with the fact that the bad file is a directory, not  a normal file?

---

### Post by PaulFr on 2007-07-05
My instructions were not clear, my mistake. We will have to find out which device to use:

1. One way is to remove your player properly (using unmount/eject) and physically remove the device.
2. Then open a terminal, and run ```
mount
``` in that terminal.
3. Now insert your player, and again run ```
mount
``` in the terminal and see the difference. There should be only one new line, and the first column of that line will be of the form /dev/xxx (this is the device to use for dosfsck).

So now run ```
dosfsck /dev/xxx
``` where you replace /dev/xxx with the device you found in step 3 above.

---

### Post by Seantiago on 2007-07-05
/dev/sda appears to be the name of the device.

dosfsck /dev/sda produces a list of what appears to maybe be addresses, followed by 

```
1) Copy original to backup
2) Copy backup to original
3) No action
?

```

Choosing 3 gives me this:

```
/.Trash-sasquatch/Muzak/Incredibad
  Contains a free cluster (49073). Assuming EOF.
/MUSIC/Muzak/Joanna Newsom - The Milk-Eyed Mender
  Contains a free cluster (57766). Assuming EOF.
Reclaimed 31799 unused clusters (520994816 bytes).
Free cluster summary wrong (128662 vs. really 183160)
1) Correct
2) Don't correct

```

And after choosing "Correct" I get this:

```
Leaving file system unchanged.
/dev/sda: 159 files, 64264/247424 clusters

```

So it would seem nothing's changed. And the corrupted file is still there. :(

Note: I get the same results if I choose "Copy original to backup."

---

### Post by PaulFr on 2007-07-05
I was checking if dosfsck was working. Now run ```
dosfsck -r /dev/sda
``` This will actually change the filesystem.

There seems to be a difference between your current boot block and the backup boot block, that is why dosfsck is asking you (Copy Original to Backup, Copy Backup to Original, No Action). Since you are more interested in your file right now, I would suggest No Action as your response. Otherwise, once your player is working properly, and you have verified it, you can run dosfsck again, and choose Copy Original To Backup to make the backup copy of your boot sector identical to your original.

---

### Post by Seantiago on 2007-07-06
That got rid of it! Thank you so much!

---

