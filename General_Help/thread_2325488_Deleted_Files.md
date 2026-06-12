---
title: "Deleted Files"
date: 2016-05-23
forum: General Help
---

### Post by Quarkrad on 2016-05-23
Running Mate 16.04.   Where do **Shift Del** files go?  I'm sure I've read that rather than send files to the Wastebasket you can permanently delete files by holding down the Shift key and then pressing Del.  I use this method to delete a file on my Desktop but it keeps reappearing the next day.  (This use to happen with the same file when I ran 14.04).  note.  It isn't in local/share/trash.

---

### Post by Impavidus on 2016-05-23
They are deleted. If you see the file reappearing the next day, some process must recreate the file every day.

---

### Post by vasa1 on 2016-05-23
> **Impavidus said:**
> They are deleted. If you see the file reappearing the next day, some process must recreate the file every day.
+1

And *ls -ali ~/Desktop* would help as well.

---

### Post by Quarkrad on 2016-05-29
It's back again - appeared today.  The  ls -ali ~/Desktop  command did not show the file when I deleted it - but does now it has come back.  Any ideas where to start looking?

---

### Post by Impavidus on 2016-05-29
Look at the name, type and contents of the file. That may give a clue about which application creates it. Is it the exact same file every time, or just a similar file? Look at the creation times. Any pattern in there?

---

### Post by Quarkrad on 2016-05-29
Originally this was a photo jpg file - it was deleted via Shift/Del.   When it come back it is always a plain text file, size 0 bytes.  This is not an 'issue' as such - I'm just fascinated how it comes back.  I do not have this with other files I delete - just this one!

---

### Post by Quarkrad on 2016-06-02
It's back again - how does this image/thing (it has 0 bytes) keep re appearing?

---

### Post by howefield on 2016-06-02
Which application(s) did you use to view, import or otherwise manage the image file ?

---

### Post by Quarkrad on 2016-06-02
Originally this was an email attachment (jpg) and from memory I just saved it on my Desktop and opened it with the default viewer.  It stayed on my Desktop for a few months and then I deleted it via Shift Del.   Obviously I cannot view it now as it is not a jpg file - it is just a text 0bytes file.  Like it is some sort of reference to something that was on my Desktop but isn't there any more.  I do not want the original - it has gone; I'm just interested in what is deciding to put this file repeatedly on the Desktop.

---

### Post by Quarkrad on 2016-06-08
6 days later it has come back - what is going on?

---

### Post by yetimon_64 on 2016-06-08
Do you run any backup software that may be trying to automatically maintain the desktop files ? Something like "backintime" or the like. 

This seems to be some process automatically trying to restore an old desktop file and I would suspect some sort of backup software. Does it appear on a regular time schedule like a scheduled backup/restore may be using (weekly etc)? 

Have you set any cron jobs for backup/restore etc ?

---

### Post by Quarkrad on 2016-06-09
I do not run any backup software.  I do have an gadmin/rsync profile but I run that manually.  Part of the rsync profile is /home so if this 'repeating event' were something to do with a backup process would not, logically, the whole of /home (hence all of my Desktop) be replace/repeated?  How could a process kick off a backup process but only choose one file?  Also, this is not a real file in that it is 0 bytes.  Although it was originally a jpg file and the icon on my Desktop looked like a picture it now appears looking like a text file although has the .jpg extension (I guess it would look like a text file as there is nothing there).

---

### Post by Quarkrad on 2016-06-13
Here he/she is again - is there another method I could use to delete this file?

---

### Post by Impavidus on 2016-06-13
Whether you use shift+del in the graphical file manager or use a terminal command, the file is deleted and gone (except that the contents, which don't exist in this case, remain on the hard drive until overwritten). It seems that some process tries to restore the file on the desktop every time it detects it's gone – but since the original in the email attachment is gone now, it only succeeds in creating a file, but not its contents.

I can't say which program tries to copy the file to the desktop. There may be a configuration file somewhere, presumably in your home directory or a subdirectory thereof, with an instruction to copy that file. You could try searching for files with the name of that empty jpeg in it. If you find such a file, it may give you a lead.

---

### Post by pfeiffep on 2016-06-13
"Originally this was an email attachment (jpg) and from memory I just  saved it on my Desktop and opened it with the default viewer.  It stayed  on my Desktop for a few months and then I deleted it via Shift Del.    Obviously I cannot view it now as it is not a jpg file - it is just a  text 0bytes file.  Like it is some sort of reference to something that  was on my Desktop but isn't there any more.  I do not want the original -  it has gone; I'm just interested in what is deciding to put this file  repeatedly on the Desktop."

I suggest carefully examining your email client.

---

### Post by Quarkrad on 2016-06-13
I use Thunderbird and the the original email has long been deleted.  It is neither in Thunderbird or on the mail server (viewed via browser).

---

### Post by pfeiffep on 2016-06-13
> **Quarkrad said:**
> I use Thunderbird and the the original email has long been deleted.  It is neither in Thunderbird or on the mail server (viewed via browser).
Empty trash on exit?
Compact folders?

---

### Post by Quarkrad on 2016-06-16
His back again - after doing all of the above.

---

### Post by Quarkrad on 2016-06-19
It's back again.

---

### Post by Quarkrad on 2016-06-23
Here we go again.

---

### Post by Quarkrad on 2016-06-25
Is there a way to delete this file?

---

### Post by Impavidus on 2016-06-25
There is no standard way to solve this problem (creating a new user should work, but that's too drastic). Some program must recreate this file when it sees it's gone missing, but the file system keeps no record of which program did it. We've given some leads, you'll have to play the detective. Have you searched for anything containing the file's name, as I suggested in post #14?

---

### Post by Quarkrad on 2016-06-28
I have done a search on the file name and it only appears twice, on my Desktop and on my backup Desktop.  I have never used the rm command because of the warnings this forum always alerts users to - it is often said that if used files are lost and the process is irreversible.  If I used the rm command on this file would it be lost forever (i.e. irreversible) - so even if a program were trying to put it back it couldn't because the file is completely destroyed?

---

### Post by sudodus on 2016-06-28
I often use ***rm*** with the option -i to remove files, and it works well for me. I have even made an alias for it, and stored in in ~/.bashrc near the other aliases.

```
$ [COLOR="#0000FF"]grep --color 'alias rm' ~/.bashrc[/COLOR]
[COLOR="#FF0000"]alias rm[/COLOR]='rm -i'
```

But I agree with *Impavidus*, I think that the cause of your problem is not how you remove it, but that it is re-created by some program.

---

### Post by Impavidus on 2016-06-28
I never really use the graphical file manager, always use rm to delete files. Old habit, coming from using Solaris (another member of the UNIX family, a relative of Linux) on low-resolution black-and-white monitors. Those monitors were already ancient by then.

But using rm and using shift-del in the graphical file manager do exactly the same thing behind the scenes: they call the unlink() system call. A simple del in the graphical file manager does something more complex. It moves the file to the trash directory and adds some information to a database to be able to restore it later to the original location.

Have you searched just for matching filenames or have you also searched in file contents, for any file that has the string "2014 HCC Vet of the Year - John Jones.JPG" mentioned somewhere in its contents? I was thinking, if a file with the same name is recreated every few days, its name must be stored in some file. If you can find the file in which its name is stored, you may know the progam responsible for recreating the file.

---

### Post by Quarkrad on 2016-06-28
I'm a bit of a newbie here - all I did was search on the matching file name.  I do not know how to search in file contents. Also - is there a terminal command I could use to find any file that has the string  "2014 HCC Vet of the Year - John Jones.JPG"?

---

### Post by steeldriver on 2016-06-28
> **Quarkrad said:**
> I have done a search on the file name and it only appears twice, on my Desktop [COLOR=#ff0000]**and on my backup Desktop**[/COLOR].

What is this "backup Desktop" exactly?

> **yetimon_64 said:**
> Do you run any backup software that may be  trying to automatically maintain the desktop files ? Something like  "backintime" or the like. 


> **Quarkrad said:**
> I do not run any backup software. 

---

### Post by Habitual on 2016-06-28
> **Quarkrad said:**
> I use Thunderbird and the the original email has long been deleted.  It is neither in Thunderbird or on the mail server (viewed via browser).

Excuse me if this has been suggested, but have you, can you tried|try a new Thunderbird profile?
Then see if this "artifact" comes back?

Also, I don't know about the "save session" feature(s) of Ubuntu, if any such exist...?

This "default viewer" originally opened it.
Some time later, you deleted the desktop article.
Some time later, this "default viewer" writes a 0 byte file there? # This is the stretch
I'd open this "default viewer" and see if the **M**ost **R**ecently **U**sed (something like that!) shows it, and optionally
can the MRU be cleaned out?

Just sayin'
Hope that helps?

Edit:
[COLOR=#ff0000]**"and on my backup Desktop**[/COLOR]"?
That changes things, sorry.

---

### Post by Quarkrad on 2016-06-28
I may have mislead re the backup - apologies if I have.  I have another HD that I use solely for backup and I used to have an auto script that backs-up up various partitions, including /home, to the backup HD when I shut down the pc.   Some time ago I stopped using the script so have no auto backup.  I still have my backup settings in gadmin rsync and run it manually when I want to do a backup.   Hence, me saying I do run any backup software.  I have not manually backed anything up since this thread was started.   This is why I saw the file in /media/backup/........./Desktop.   Following posts above I will a) first change thunderbird profile and see what happens  b) if file re appears delete file off /media/backup/......Desktop and see what happens  (although I'm not sure this is relevant).

---

### Post by Quarkrad on 2016-06-28
Hmm.... changing my thunderbird profile makes me lose everything (which I cannot afford to do).  For the purpose of this experiment would it be acceptable if I created a virtualbox 16.04 system and ran my email from there?   I could use virtualbox for my email comms and even not have an email client/thunderbird on my main machine.

---

### Post by Impavidus on 2016-06-28
I don't know about mate, but the default file search tool on my Xubuntu box (Catfish file search) can search for contents too. I may be able to come up with a nice bash loop that can to it from command line, but I'm not really a scripting master.

---

### Post by Quarkrad on 2016-07-16
It's back again today.  However - I took the suggestion in #15 and moved my email to a virtual guest and deleted TB from my OS - in including ~/.thunderbird.  Once in the VBox environment I have had no instances to the file on my Host Desktop or on the VBox guest Desktop - so I thought the problem had disappeared.  Yesterday I decided to put my email back onto my Host and get rid of the VBox Guest.  Today the file reappeared back on my Desktop.  This suggests it is something to do with BT but I'm not sure what to do from here.

---

