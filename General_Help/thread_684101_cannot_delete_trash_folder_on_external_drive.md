---
title: "cannot delete trash folder on external drive"
date: 2008-01-31
forum: General Help
---

### Post by spacedoggy on 2008-01-31
ok, my first post to ubuntu forums so go easy on me lads. my external drive has a trash folder containing 4 files in a subdirectory that I can't delete because they contain special characters in the filenames. when ever i click on them in Nautilus, they dissappear before I can see their properties which is freaking me out... here's my term so far...


spacedog@spacedog-laptop:/media/My Book/.Trash-spacedog/111/ADS$ ls -la
total 96
drwx------ 2 spacedog root 65536 2005-03-19 12:20 .
drwx------ 3 spacedog root 32768 2007-08-23 22:56 ..
?--------- ? ?        ?        ?                ? $!.
?--------- ? ?        ?        ?                ? &#2037;$$.
?--------- ? ?        ?        ?                ? jetswhq.
?--------- ? ?        ?        ?                ? pwaehq.
spacedog@spacedog-laptop:/media/My Book/.Trash-spacedog/111/ADS$ rm pwaehq. 
rm: cannot remove `pwaehq.': No such file or directory
spacedog@spacedog-laptop:/media/My Book/.Trash-spacedog/111/ADS$ rm pw*
rm: cannot remove `pwaehq.': No such file or directory

spacedog@spacedog-laptop:/media/My Book/.Trash-spacedog/111/ADS$ fdisk -l

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x309b45f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60800   488375968+   c  W95 FAT32 (LBA)


spacedog@spacedog-laptop:~$ sudo fsck /dev/sdb1
fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  67:33/1d, 68:eb/3d, 69:1b/ef, 70:33/14
1) Copy original to backup
2) Copy backup to original
3) No action


I didn't know what to select from this so I ctrl C'd out any thoughts on how to get rid of the little blighters? Thanks gang.

S-Dawg! :guitar:

---

### Post by imtheguru on 2008-01-31
% cd /path/to/subdirectory/on/external/drive
% sudo rm * -rf

Cheers.

---

### Post by spacedoggy on 2008-02-01
thanks for your help imtheguru but no joy yet...

spacedog@spacedog-laptop:/media/My Book/.Trash-spacedog/111/ADS$ sudo rm * -rf
[sudo] password for spacedog:
spacedog@spacedog-laptop:/media/My Book/.Trash-spacedog/111/ADS$ ls
$!.  &#2037;$$.  jetswhq.  pwaehq.
spacedog@spacedog-laptop:/media/My Book/.Trash-spacedog/111/ADS$ sudo rm * -r
rm: cannot remove `$!.': No such file or directory
rm: cannot remove `&#2037;$$.': No such file or directory
rm: cannot remove `jetswhq.': No such file or directory
rm: cannot remove `pwaehq.': No such file or directory

...kicker eh? :confused:

---

### Post by aeiah on 2008-02-01
could you just reformat the drive with gparted? after backing up the useful bits of course. or will this keep happening and thus be a pain in the *** to keep doing?

---

### Post by mc4man on 2008-02-01
have you tried highlighting the .trash folder itself and then going shift/delete on keyboard

edit; in the future using shift/delete will delete files/folders outright - bypassing the .trash

---

### Post by spacedoggy on 2008-02-01
> **mc4man said:**
> have you tried highlighting the .trash folder itself and then going shift/delete on keyboard

edit; in the future using shift/delete will delete files/folders outright - bypassing the .trash

yes tried that, I get the same messages as in te terminal, saying that the 4 files don't exist and asking me to skip them


> **aeiah said:**
> could you just reformat the drive with gparted? after backing up the useful bits of course. or will this keep happening and thus be a pain in the *** to keep doing?

I would, but there's 500GB to back up and I havn't got the space :(

---

### Post by spacedoggy on 2008-02-02
any other thoughts on this problem guys? got my back up against the wall on this one? am i even asking in the right place? any help appreciated. 

free popcorn to whoever helps me!!! :popcorn:

---

### Post by SpiderGorilla on 2008-02-02
Okay, this is going to sound extremely dumb, but try this, eh?

rm "pwaehq."

Try it with the quotes, man. See if that works. If it DOESN'T, try this:

mv "pwaehq." "/home/usernameforyourmainsystem/FileNameThatCantPossiblyBeHiddenByTheSystem" (no spaces in that, of course, unless you want them)

sudo chmod 0777 "FileNameThatCantPossiblyBeHiddenByTheSystem"

rm "FileNameThatCantPossiblyBeHiddenByTheSystem"

---

### Post by spacedoggy on 2008-02-02
> **SpiderGorilla said:**
> Okay, this is going to sound extremely dumb, but try this, eh?

rm "pwaehq."

Try it with the quotes, man. See if that works. If it DOESN'T, try this:

mv "pwaehq." "/home/usernameforyourmainsystem/FileNameThatCantPossiblyBeHiddenByTheSystem" (no spaces in that, of course, unless you want them)

sudo chmod 0777 "FileNameThatCantPossiblyBeHiddenByTheSystem"

rm "FileNameThatCantPossiblyBeHiddenByTheSystem"

nice idea spidy, no joy for the spacedog though, same deal, says there's no file to rm, mv or chmod
this startin to piss me off :( I guess I could try install windows but I'd feel all dirty, yuck :P

---

### Post by SpiderGorilla on 2008-02-02
Wow, man. I just have no idea then, command-line wise. Is this disc one that you wish to keep in tact or can it be formatted and all data deleted?

---

### Post by mc4man on 2008-02-02
Maybe stupid question - can you post the exact name of file including special characters ?
Do you know anyone with a windows box you could try removing files with?

---

### Post by spacedoggy on 2008-02-02
not really an option to move the files and format, she's a usb2 disk with 400GB on her. that take most of a day and I'd have to borrow another disk. I'm worried about where these files came from as they look like well hidden code, adware/malware, I'd be worried about opening the folder on a windows box

---

### Post by spacedoggy on 2008-02-02
spacedog@spacedog-laptop:/media/My Book/.Trash-spacedog/111/ADS$ ls
$!. &#2037;$$. jetswhq. pwaehq.

these are the filenames, but in terminal view they are coloured red with a grey background, nor sure is that, ls -color function or something to do with the file itself

thanks guys for your thoughts and ideas so far :KS

---

### Post by mc4man on 2008-02-02
i don't think I'd worry to much about them, they're similar to .nfo files, in other words even though they're not seen as such they're just text files

---

### Post by spacedoggy on 2008-02-04
I guess... *sigh* :(

---

### Post by mc4man on 2008-02-04
It certainly would be safe to delete in windows (if possible)
From left field - have you tried renaming them?

---

### Post by spacedoggy on 2008-02-05
yeah, linux simply refuses to see them :(, guess I'll dig out my bart PE disk

---

### Post by geirha on 2008-02-05
After the filesystem has been fixed, those files should be possible to delete. Windows partitions is best left for windows to check and fix, so connect it to a windows box and run scandisk on it.

---

### Post by spacedoggy on 2008-02-05
thanks everyone, I booted a BART PE disk and I still got the 'file doesn't exist' error 

cmd fixed it
del *.* in old fashioned dos prompt did it

I don't think the partition was ever corrupted, but that the files were placed there and named using directory control characters by malware or something. it sucks that i needed windows to fix it, but I guess it is indeed a windows file system, thanks for your input guys!

---

