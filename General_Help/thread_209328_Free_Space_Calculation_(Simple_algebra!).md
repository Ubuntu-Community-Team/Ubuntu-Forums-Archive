---
title: "Free Space Calculation (Simple algebra!)"
date: 2006-07-05
forum: General Help
---

### Post by Mr. Picklesworth on 2006-07-05
I have a 512 MB Compact Flash card, which previously contained a number of videos and small SCUMM games.

I can estimate that the space consumption here was around 300 MB (can't be sure, as I never checked), with 30 MB being taken up by the SCUMM games.
This leaves about 200 MB free.

Today, I deleted those videos (deleted the folder they were in, anyway) and proceeded to add the new ones to find to my horror that Ubuntu was claiming that the card still only has 200 MB of free space, and wouldn't let me write the new files!

Unmounting it and mounting again made no difference, and going to Properties for the card tells me:
Contents: 98 items, totalling 36.0 MB
Free space: 209.9 MB

This is a previously tried and tested good quality CF card, known to carry up to 482 MB of data. (The small MBs whose existence is taken advantage of to trick people).

So, it appears that Ubuntu forgot to delete my files, or it forgot how to do basic algrebra when I deleted the videos.
Defragmenting seems like a bit too much work for a long term solution since, for all I know, this happens with hard drives too, which would be a pain... and I don't want to go around defragmenting my CF card whenever I delete a file when even cheezy little file managers on my DS can do it successfully; it just wouldn't be right :P

Any ideas what I can do to fix this from ever happening again, or will I just have to wait/submit a bug report?
Thanks in advance!


Edit:
Windows says 400 MB free.
Weird...

---

### Post by atoponce on 2006-07-05
[quote=Mr. Picklesworth]I have a 512 MB Compact Flash card, which previously contained a number of videos and small SCUMM games.

I can estimate that the space consumption here was around 300 MB (can't be sure, as I never checked), with 30 MB being taken up by the SCUMM games.
This leaves about 200 MB free.

Today, I deleted those videos (deleted the folder they were in, anyway) and proceeded to add the new ones to find to my horror that Ubuntu was claiming that the card still only has 200 MB of free space, and wouldn't let me write the new files!

Unmounting it and mounting again made no difference, and going to Properties for the card tells me:
Contents: 98 items, totalling 36.0 MB
Free space: 209.9 MB

This is a previously tried and tested good quality CF card, known to carry up to 482 MB of data. (The small MBs whose existence is taken advantage of to trick people).

So, it appears that Ubuntu forgot to delete my files, or it forgot how to do basic algrebra when I deleted the videos.
Defragmenting seems like a bit too much work for a long term solution since, for all I know, this happens with hard drives too, which would be a pain... and I don't want to go around defragmenting my CF card whenever I delete a file when even cheezy little file managers on my DS can do it successfully; it just wouldn't be right :P

Any ideas what I can do to fix this from ever happening again, or will I just have to wait/submit a bug report?
Thanks in advance!


Edit:
Windows says 400 MB free.
Weird...[/quote] Look for any dot files or directories lying around.  I bet that when you deleted all your files, it created a .trash and put everything in there.  Seems odd that Windows is saying that your drive is empty, though.

---

### Post by David Corrales on 2006-07-05
Yep, I've had the same problem with the .Trash directory and flash cards. That shouldn't happen though... it's confusing.

---

### Post by Mr. Picklesworth on 2006-07-05
OK, thanks!


I guess writing that stuff onto there via Windows instead was a bit risky, but it doesn't seem to have harmed anything.

---

### Post by mkljun on 2006-07-14
Hi there!

I also found it strange today when my wife claimed that she deleted all photos from a CompactFlash. But when put back into camera, camera claimed that it only had space for one photo. 

So I put it back to a card reader, opened a console and was suprised that:
# cd /media/OES-DIGITAL
# ls -la
DCIM .Trash

So what the hell is that .Trash dir doing there :). It's probably pecaution for those that often delete files that they need. But I just "converted" my wife from XP to Ubuntu and these kind of things .... she might eventulay get used to. But I know she will never use a rm command :). Is there a workaround?

# rm -R .Trash

---

### Post by equal on 2006-07-14
Yeah it's an odd thing, but Ubuntu will create a .Trash folder in any external drive when you delete files. Eliminating it is easy enough. Before disconnecting the unit, just empty your Trash. It'll clear that folder too.

---

### Post by Lord Illidan on 2006-07-14
Is there any way to prevent these portable drives and stuff using .trash directories?

---

### Post by TrinitronX on 2006-07-14
I think a good solution in the future would be to send deleted files from portable drives to the main .Trash in your homedir, instead of creating a new one on the drive.

---

### Post by zitch on 2006-07-14
Another good idea would be to empty the trash bin when unmounting and when writing new files onto the media that would have not have enough room otherwise.  It would be best if this and all of the other types of functionality could be configured by the user...

---

### Post by mkljun on 2006-07-14
Found a simple solution:

Select photos on a CompacfFlash
Edit->Cut

Go to local Dir
Edit->Paste

;)

---

### Post by skale on 2006-07-14
maybe you could create a .Trash file which really is a symbolic link to the working directoriy's .Trash. Worth a shot.
**sudo rm /media/floppy0/.Trash***
**ln -s /home/yourname/.Trash /media/floppy0/.Trash***
The * is just there because I can't remember if on the drive it says .Trash or .Trash-yourname. I wouldn't actually write it like that.

---

