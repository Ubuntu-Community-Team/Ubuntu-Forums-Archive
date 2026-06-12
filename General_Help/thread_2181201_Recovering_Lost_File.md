---
title: "Recovering Lost File"
date: 2013-10-16
forum: General Help
---

### Post by sukhgill112 on 2013-10-16
I have been working on some research for 2 weeks and lost the file today.  I was working on it in my Ubuntu partition (docx file) and moved it over to windows partition so I could do some editing with office.  I know I probably don't have this set up properly as I am new to Ubuntu.  However upon booting up windows the file was nowhere to be seen.  I went back to Ubuntu and the file was also missing in the windows folder I had moved it to.  I went to libre and tried accessing recent documents and it says the file doesn't exist.  It wasn't in my trash and I tried to see if it was accidently changed to a hidden document, no dice.  Please help.  I would appreciate any help.  I am running Ubuntu 13.04.

Thanks

---

### Post by leclerc65 on 2013-10-16
Try the Find cmd

$ find [path...] -iname '*string*'

where 'string' = partial name of the file

---

### Post by sukhgill112 on 2013-10-16
> **leclerc65 said:**
> Try the Find cmd

$ find [path...] -iname '*string*'

where 'string' = partial name of the file

It was not able to locate the file.  Does that mean it has been deleted?

---

### Post by Colin_Deisenroth on 2013-10-16
if you can't find it in either directory, it seems like it got deleted, but maybe you can provide some background on how your system is setup.

- What is the path to where you had the file originally
- What is the path to where you moved the file to
- What tool/method did you use to move the file (command line? gui?)
- Were any messages or errors shown after moving the file? Did you see the file appear in the other directory?

You can use the find command from a lower directory using sudo, so it would be sudo find / -iname '*string*'
Maybe you moved it to a directory, then something mounted on top of that directory so the file is no longer visible, but if you unmount the file would be visible again.

-Colin

---

### Post by sukhgill112 on 2013-10-16
> **Colin_Deisenroth said:**
> if you can't find it in either directory, it seems like it got deleted, but maybe you can provide some background on how your system is setup.

- What is the path to where you had the file originally
- What is the path to where you moved the file to
- What tool/method did you use to move the file (command line? gui?)
- Were any messages or errors shown after moving the file? Did you see the file appear in the other directory?

You can use the find command from a lower directory using sudo, so it would be sudo find / -iname '*string*'
Maybe you moved it to a directory, then something mounted on top of that directory so the file is no longer visible, but if you unmount the file would be visible again.

-Colin

I had it on my ubuntu desktop (/home/sukh/desktop).  I had my windows 8 (/home/sukh/Windows 8/Users) directory mounted and I dragged it into the windows 8 directory from the ubuntu desktop.  It showed the file was there and there were no errors.  Then I logged off ubuntu and went into windows 8.  Initially when I opened the folder in windows 8 it showed a bunch of old files in the directory that were there and then immediately deleted  them leaving nothing in the folder.  I tried the sudo find and unmounting the directory, no luck.

---

### Post by leclerc65 on 2013-10-16
Scan the whole partition if you have to. It doesn't take long.

---

### Post by Colin_Deisenroth on 2013-10-16
This wouldn't change things for this file, but you may consider using Dropbox in the future. It integrates perfectly with both linux and windows desktops, and you wouldn't have to "move" or risk deleting anything. I believe you get about 2gb free.

For the current file...

1) Can you mount the root of the windows partition and scan it with find?
sudo mkdir /tmp/windowsdir
sudo mount /dev/sdb1 /tmp/windowsdir (whatever your windows partition is)
sudo find /tmp/windowsdir -iname '*string*'
(test out the find command with a file you know exists to see if it's actually working as you think to find files)
there's also a modification to find to find files created within the last 1 day
sudo find /home/ -mtime -1

2) You should try some tests with other files to repeat what you did before. See if you do the exact same thing with another file if it appears in windows or if it also disappears. Check if the expected behavior is actually what is happening. This may give you some insight into what went wrong.

---

### Post by sukhgill112 on 2013-10-16
> **leclerc65 said:**
> Scan the whole partition if you have to. It doesn't take long.

Nothing comes up.  I am running foremost?  Just read about it on some forums.  Do you think this will be able to help me?

---

### Post by sukhgill112 on 2013-10-16
> **Colin_Deisenroth said:**
> This wouldn't change things for this file, but you may consider using Dropbox in the future. It integrates perfectly with both linux and windows desktops, and you wouldn't have to "move" or risk deleting anything. I believe you get about 2gb free.

For the current file...

1) Can you mount the root of the windows partition and scan it with find?
sudo mkdir /tmp/windowsdir
sudo mount /dev/sdb1 /tmp/windowsdir (whatever your windows partition is)
sudo find /tmp/windowsdir -iname '*string*'
(test out the find command with a file you know exists to see if it's actually working as you think to find files)
there's also a modification to find to find files created within the last 1 day
sudo find /home/ -mtime -1

2) You should try some tests with other files to repeat what you did before. See if you do the exact same thing with another file if it appears in windows or if it also disappears. Check if the expected behavior is actually what is happening. This may give you some insight into what went wrong.

Alright I tried those suggestions:

1)  I mounted the windows directory to a tmp folder and searched it.  Again no luck.
2) I tried doing the same thing again.  This time the whole folder didn't show up in Winows 8.  When I went back to access the folder in Ubuntu i got the following error:
"[B]This location could not be displayed.
[/B]Sorry, could not display all the contents of “PQI”: Error when getting information for file '/home/sukh/Windows 8/Users/Sukh/PQI/test.docx': Input/output error"

I am not sure why but it won't access that folder anymore and I can't see it at all in windows 8.  

I will definitely be using some sort of back up

---

### Post by Hypnoz on 2013-10-17
Here is a tutorial page that shows how to mount a windows partition on ubuntu/linux

[http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/](http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/)

I believe you also need to install the ntfs-3g package.

I guess ideally you'd keep tweaking your settings until you can read/write files from both filesystems on the other. If you don't have that kind of patience then something like dropbox would be the other option.

---

