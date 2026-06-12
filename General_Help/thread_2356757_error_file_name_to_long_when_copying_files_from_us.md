---
title: "error file name to long when copying files from usb to home directory"
date: 2017-03-26
forum: General Help
---

### Post by bradw2600 on 2017-03-26
greetings all, 

I am getting a error that says my file names are to long when copying to home directory from usb drive. File and folder names are less than 100 characters. using ubuntu server 16.04.2. Searched the forum for an answer but came up empty. My search terms were "long file names" and "copying long file names" Is there a work around. I am dealing with video files with both mp4 and flv format. There are hundreds of study files  and 50 or so directories so renaming is out of the question.

thanks all

---

### Post by TheFu on 2017-03-27
The system limitation as far as Linux is concerned is stored in the limits.h file.
/usr/include/linux/limits.h is the file - 
```
#define PATH_MAX        4096    /* # chars in a path name including nul */

``` so any full path less than 4K long should be fine, as far as Linux is concerned. Windows used to have a lower limit - like 256 characters - actually, Unix had a lower limit in the old days - I've had to rebuild all the software on a system, including the kernel at a client site over the limitation.

So we need to look for other limiting factors.  
The file systems used/involved have limits on total path length. Which file system is used on the USB drive?  There is a wikipedia article about file systems which compares some keep values/limits.  [https://en.wikipedia.org/wiki/Comparison_of_file_systems](https://en.wikipedia.org/wiki/Comparison_of_file_systems)
255 characters appears to be common limit for most currently used filenames - directories are different.  If any part of a total path is over 255 characters, that could be the issue.

Exactly how are you trying to copy the files?

If you use **rsync** or **cp** at a shell prompt, it should work fine.  There are other options too.

Plus, if you want to rename the files in bulk, that is possible using a regex pattern matching-renaming tool called '**rename**' There are other tools that can to smart bulk renaming too.  I only use rename and one built into an image viewing program myself, so cannot really help with other GUI tool suggestions. Sorry.

---

### Post by bradw2600 on 2017-03-27
Thank you for your reply. I think you gave me enough info to try and figure it out. I tried```
 /media/bw/Seagate Backup Plus Drive$ cp -r /media/bw/ \Seagate  \ Backup\ Plus \Drive \linux ~
``` and it is still running. I expect it to run for awhile as the linux directory is 33gig. So far no error messages. I would assume it would list a linux directory and some sub directories with files but in nothing showing in the gui files yet and it has been running fifteen minutes or so now. On another note, how in heck to I rename \Seagate \ Backup\ Plus \Drive to something else? When I am at /media/bw and I try to cd to it tells me it is not a directory or file so what is it? I may respond later tonight after cp command is finished or tomorrow as I have many more directories to copy over from usb to ~. Thank you very much for replying

---

### Post by bradw2600 on 2017-03-27
the code in earlier post was copying the whole usb drive, however I figured out how to copy just the two directories I needed to copy. I was able to copy about 2/3 of one and 1/2 the other but still receiving file name to long errors and it skips those files. These are videos for studying for lpi exams and redhat exams so renaming is not something I can do and still know what each video is. There are hundreds of them so writing them all down and then renaming and then renaming again when copied over is not the way I want to go.

Any suggestions and oh yes the usb is formatted ntfs file system and I cannot format it or I will lose the files.

---

### Post by TheFu on 2017-03-27
a) really should have used rsync.  If there is a failure, restarting will be 100000x faster.  rsync is a tool every computer user should become familiar with, IMHO. It is an amazing tool for copying data around, securely.

b) You cannot rename a directory that is a mount point when it is mounted or "in-use"  Just name it whatever you like in the /etc/fstab entry. An empty directory should be created too, with the ownership and permissions you want.  This assumes it is a Unix file system, not FAT-whatever or NTFS.  If you didn't use the fstab to control the mount, you probably are using gvfs.  I hate gvfs for a number of reasons, mainly because it doesn't use real mounts and because it is slower than a real mount- perhaps 30% slower. Try changing the label on the disk when it isn't mounted and I think gvfs will pick that up.  I don't mount non-temporary storage under /media/. Prefer to control where storage gets mounted and don't want some automatic file manager mount tool screwing up my storage.  

c) be extremely careful with seagate equipment. Please. I've been burned a number of times by their consumer level stuff. They used to make great HDDs - still have some of those spinning now - almost 13 yrs old.  Then something changed inside Seagate and their disks have never been the same quality since.

d) I never allow spaces or special characters in file or directory names. It can break all sorts of poorly written scripts, like my scripts.  It is easier just never to allow spaces, at least for me.  Do whatever you like, but you'll have to always wonder if that program/script you want to run handles odd filenames correctly.

---

### Post by TheFu on 2017-03-27
NTFS and most Linux file systems have different limitations about file and directory names.  You'll need to clean up all the incompatible names on NTFS so they are compatible with whatever file system you are copying onto. I don't recall the main issues now - haven't used NTFS in a very long time.  Google found this: [https://www.mtu.edu/umc/services/digital/writing/characters-avoid/](https://www.mtu.edu/umc/services/digital/writing/characters-avoid/)

---

### Post by Impavidus on 2017-03-28
> **bradw2600 said:**
> Thank you for your reply. I think you gave me enough info to try and figure it out. I tried```
 /media/bw/Seagate Backup Plus Drive$ cp -r /media/bw/ \Seagate  \ Backup\ Plus \Drive \linux ~
``` and it is still running. I expect it to run for awhile as the linux directory is 33gig. So far no error messages. I would assume it would list a linux directory and some sub directories with files but in nothing showing in the gui files yet and it has been running fifteen minutes or so now. On another note, how in heck to I rename \Seagate \ Backup\ Plus \Drive to something else? When I am at /media/bw and I try to cd to it tells me it is not a directory or file so what is it? I may respond later tonight after cp command is finished or tomorrow as I have many more directories to copy over from usb to ~. Thank you very much for replying

That command has an awful lot of spaces and backslashes in it, and I don't think it does what you intend. That's why it's recommended not to use too many spaces in file/directory names. Your cp command actually tells to copy 5 directories recursively into your home directory. Those five directories are
"/media/bw"
"Seagate"
" Backup Plus" (mind the leading space)
"Drive"
"linux"
Given the directory where you issued the command, the first will work and copy everything in /media/bw (including "Seagate Backup Plus Drive"), the last one may work too (copying one directory from that drive), the middle three will probably fail.

---

### Post by bradw2600 on 2017-03-28
Finally found the files that needed renamed, renamed them and good to go as everything copied over fine. Those directing names are a mess or perhaps that seagate blah blah blah is a screwed up name but this is how ubuntu 16.04.2 reports it. I will try to rename when it is unmounted but I have got a lot to learn. Thank you both for the replies. Time to start learning this stuff but sure glad winblows if off my machines.

---

### Post by HermanAB on 2017-05-18
The easiest way to rename bad names is with a GUI file manager.  Just run Nautilus, right click on it and select rename.

---

