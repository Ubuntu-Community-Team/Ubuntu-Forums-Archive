---
title: "Is this a sign my hard disk drive is about to go out?"
date: 2024-03-11
forum: General Help
---

### Post by SpaceManJack on 2024-03-11
[h=1]So  I just sent a few vids to the trash and I went and tried to recover  them and it won't let me it's saying "could not determine original  location of" "the item cannot be restored from trash" is this a bug? Or  is this a sign my hard drive is about to give out?[/h]
Is  this a bug? Or do you think it's a sign my hard drive is about to crash  on me? I'm using a hard disk drive from 2015 though I've only really  started putting heavy use into it in just the past few years, I didn't  really use this computer from 2015 to 2020 cause I was mainly using my  laptop instead.


There's a folder  in the trash with pics in it and it won't let me restore the pics  either. I can view the pics but I can't move them out of trash or  restore them.


Everything else appears to be working just fine. It just won't let me restore items from trash is all.

I also tried using the command line. I tried the commands 

 cp -r ~/.local/share/Trash/videos ~/Downloads

and 


cp ~/.local/share/Trash/videos/my_vid.mp4 ~/Downloads

and it tells me


cp: cannot stat No such file or directory

Also I can successfully "cd" into trash and even list all the file names in trash by doing "ls", or at least I think it's the "ls" command, I did this a few weeks ago so I'd have to refresh my memory but I know by using command line I can navigate into the trash folder and list all the file names but it will not let me move anything out of trash.

Is this a bug with the software or is my hard drive about to give out on me? If you think my hard drive is fine then tell me?

---

### Post by yancek on 2024-03-12
I've never seen the error messages you are reporting and rarely use Trash.  The first cp command you posted would not be expected to do anything.  The second cp command should if you are logged in as the correct user and are in that user /home/ directory.  Commands are case sensitive so is the directory 'videos' or 'Videos'?

With regard to the original errors you reported, did you delete them from the user /home directory as that user?  Did you delete them as another user (root with sudo)?  From an external drive?

---

### Post by SpaceManJack on 2024-03-20
> **yancek said:**
> I've never seen the error messages you are reporting and rarely use Trash.  The first cp command you posted would not be expected to do anything.  The second cp command should if you are logged in as the correct user and are in that user /home/ directory.  Commands are case sensitive so is the directory 'videos' or 'Videos'?

With regard to the original errors you reported, did you delete them from the user /home directory as that user?  Did you delete them as another user (root with sudo)?  From an external drive?

"did you delete them from the user /home directory as that user?  Did you  delete them as another user (root with sudo)?  From an external drive?" 

I am using a PC and I AM NOT using an external drive. I am using my own home PC so I'm using my own account. 

Can you just confirm with me, are you able to send a video to trash and successfully recover said video from trash? Cause once I've sent a vid or a picture to trash it will not let me recover it. It's funny though if I accidentally send something to the trash it will let me "undo" it but once something has officially been sent to trash I can't recover it.

And yes I'm aware it's case sensitive.

Everything else seems to be functioning just fine though. Do you think my hard drive is about to go out on me? Or is this just a weird Linux bug?

---

### Post by SpaceManJack on 2024-03-20
> **yancek said:**
>   The first cp command you posted would not be expected to do anything. 

I have a folder in trash named "videos", are you saying the first command doesn't move an entire folder?

---

### Post by TheFu on 2024-03-20
The drive might be really full and there might not be room in the Trash to hold it. That's just a guess.

Linux is always a multi-user system, even if only 1 human is logging in. there are 10s of userids on your system (any Linux system will have lots of users), so we cannot assuming anything.  My personal desktop has 62 users, for example.  Usually, they ignore everything in my HOME, but sometimes I might use sudo to explicitly delete something and that wouldn't be using my normal userid.  Hence, the reasons why those questions were asked.

Nobody can predict when a HDD will fail.  The best tools we have only give a hint that is 78% accurate, assuming we are paying attention to the hints.  22% of the time, they fail without any hints, so having good backups is mandatory for anything storage on any storage medium - disk, ssd, flash drive.  The command is **smartctl**.  There are lots of how-to guides for using it on the internet and a few threads in these forums with explicit examples.

Also, trash can be handled differently based on the DE you have installed.  LXQt and Gnome and Mate and Cinnamon and KDE and XFCE are all different DEs. Don't expect them to work the same. They may, but they might not.

I think there are other options than just the 2 you've proposed. ;)  I always assume I'm doing something wrong first, before anything else. When ever things don't work as I might expect, it is usually due to some factor I didn't consider that forced the result I was seeing.

---

### Post by The Cog on 2024-03-20
You say that "cp ~/.local/share/Trash/videos/my_vid.mp4 ~/Downloads" gets the response "cp: cannot stat No such file or directory".

```
ls -l ~/.local/share/Trash/videos/my_vid.mp4        # I expect this says No such file
cd ~/.local/share/Trash/videos/
ls -l
```
and look for odd characters or spaces in the filenames. the "ls -l" will show you how to escape odd characters.

And it occurs to me that another possibility is the the "videos" are broken symlinks - links to real files that no longer exist. Again"ls -l" will show you if that's the case.
And to answer your original question: No I don't think it's a sign of a failing hard disk or even a corrupt disk. I think it's probably something simple like wrong filename (case, odd characters) or maybe broken links.

EDIT:
**tea for one** points out what the problem almost certainly is (in the next post). I deserve a slap for not noticing. Doh!

---

### Post by tea for one on 2024-03-20
For Ubuntu, Trash contains 3 folders - expunged, files and info
Deleted files and folders are under files
Can you open a terminal and enter:-
```
cd ~/.local/share/Trash/files
```
```
ls
```
Anything there?

---

### Post by SpaceManJack on 2024-03-28
> **tea for one said:**
> For Ubuntu, Trash contains 3 folders - expunged, files and info
Deleted files and folders are under files
Can you open a terminal and enter:-
```
cd ~/.local/share/Trash/files
```
```
ls
```
Anything there?

"Anything there?" Yes all the names of the files are showing up.

But here's the thing, so using the GUI, not the command line, so using the GUI, I go into files and go into trash and there's a button called "Restore" but I can't restore anything at all. Now I'm assuming I should be able to restore stuff from the trash using the GUI, but I can't. So either this is a weird bug or what... I don't know. 

Can you confirm that I should indeed be able to restore stuff from trash using the GUI? 

And here's the thing I can't restore stuff using the GUI or the command line so again, is this some weird bug?

But anyhow please answer this question, can you confirm with me that I should indeed be able to restore stuff from trash using the GUI?

---

### Post by tea for one on 2024-03-28
> **SpaceManJack said:**
> Can you confirm that I should indeed be able to restore stuff from trash using the GUI? 
Using Ubuntu 22.04 and Files 42.6, you definitely should be able to restore both files and folders from trash using GUI.

If you send a folder containing files to Trash, you cannot open the folder within Trash and restore a file contained therein.
You will see a message "Could not determine original location of "file"
You certainly should be able to restore the complete folder.

---

### Post by yancek on 2024-03-28
The system should be able to restore, copy, move and all the other options you see when using a GUI so it is not the system, it is some other problem.  I just tested these options and they all succeeded.  You were asked to post the output of some ls commands run against your Trash directory but only said the files were there and did not show the output of the command: the owner:group or permissions, spaces or unusual characters in the file names so members are left to guess.

I also tested by creating a directory with files in it in my /home/user directory and was able to copy them to the Trash directory and from the Trash directory successfully.  Post the output of the ls commands suggested and run df -h to see the size and amount used on your mounted partitions.  After that you may need to run some software to check on your hardware and possible failings.

---

### Post by TheFu on 2024-03-28
The disk could be full too.
A **df -Th -x squashfs -x tmpfs -x devtmpfs** and **df -i** would be useful to see storage full issues.  Check the simple things first.

---

### Post by The Cog on 2024-03-28
"Could not determine original location of "file" could be because the original location is not present in ~/.local/share/Trash/info. 
If that's the case, one possible cause could be the disk being full so that although the file can be moved to trash, it can't create the info file saying where it was moved from.

---

