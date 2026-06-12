---
title: "Ubuntu Tweak not remembering user folder locations if changed"
date: 2014-05-17
forum: General Help
---

### Post by John_Curry on 2014-05-17
Hi all, Ubuntu tweak is not remembering when I change the "User Folder" locations. As in example I have changed the Public Folder to the shared Data drive but when I log back in, it is reset to the default location (/home/john/Public)

The shared Data is a separate hard disk, formatted to NTFS but is mounted on startup

Any ideas?

---

### Post by John_Curry on 2014-05-18
any of you knowledgeable chaps any suggestions?  :D

---

### Post by coldcritter64 on 2014-05-18
NTFS does not support Linux filesystem permissions. The "Public" folder is a system generated folder.

The fact NTFS doesn't support linux permissions may possibly be the reason for the constant resetting of the folder when changed in Ubuntu tweak. "Tweak" may be letting you do an alteration the system then sees as a problem on a restart. 

Have you tried to change the folder setting to a Linux filesystem location and does it hold there after a reboot ? From my experience, I'd expect that location to be reset being on an NTFS partition (Windows filesystem) with the Public folder location being set by the Linux OS.

---

### Post by John_Curry on 2014-05-18
hi cold critter

yes your correct. Selecting a Linux Filesystem folder is remembered by Tweak (after a reboot) but not if its an NTFS folder. Is there anyway around this restriction? I have a dual boot system with Windows 8.1 so could really do with 'shared folder' location for both OS's

Many thanks

---

### Post by coldcritter64 on 2014-05-19
> Is there anyway around this restriction?I really don't think so, being a file system from another OS that doesn't support Linux permissions, I could stand to be corrected if someone says it is possible via some hack I don't currently know of etc., but I really doubt that will be the case. 

Why not just share an NTFS folder for the 2 systems to use in common without using the "Public" folder. 

Maybe change the capital P and call it "public" ... would be enough to differentiate your folder from the system supplied "Public" folder, after all _*Linux is case sensitive in naming*_. 

"Public" and "public", although the same name to you, are 2 very separate folders to the OS. You then wouldn't need to use "tweak" to move the system folder (a possible "workaround" for you to consider, if you want to use the name "public" for your shared folders).

Using a common NTFS data partition between Windows and Linux is common practice, only the name you chose for your storage clashed with a system supplied folder, that's the only problem you seem to have struck here.

---

### Post by John_Curry on 2014-05-19
Well I tried directing the 'music' folder on Linux to '/shared Data/Test' on NTFS but still no luck. Hence it leads me to believe its not simply a naming issues. I guess I am not understanding the problem here as Ubuntu remembers and reconises the NTFS file system during run time. Its only on a reboot, does it lose the link. So why not have these Default Folders (Music, Movies, Public etc) simply as links to whatever folder I choose on NTFS, and reference them at initialization of the OS.  For example: I can just make a shortcut on the Linux desktop to an NTFS folder and that will be remembered and I can change my choice in Applications to remember specific folders on a NTFS file system (like Transmission etc). 

Seems like from what you are saying, its more complicated than that.

However, I did notice that my the default music player (sorry can't remember the name) also looses the location of my Music library on NTFS.

hmm, back to the drawing board ...

---

### Post by coldcritter64 on 2014-05-19
> formatted to NTFS but is **mounted on startup** How are you doing that ? With an /etc/fstab entry or by some other means ?

Assuming the mounting is going correctly, you have NO need to shift the folders with "tweak" at all. 

Create another folder, store your files in there and you will have access to them from both systems. Make links to them as usual on the desktop etc as you mention, and there should be no problem. 

IF you start trying to shift the folder with tweak, you run into the original problem. I really don't understand why you are trying to move those system provided folders anyhow, just create another folder and link to it as you noted.

I know Windows does allow shifting of the system folders; carrying this example to Windows, try to locate a Windows music folder on a Linux partition, put simply it won't work, not compatible filesystems and Windows doesn't even recognize a Linux partition in the first place (look at one in the Windows disk management tool). 

At least Linux allows you to read and write to MS, the other way round doesn't happen at all. That is why I originally expected the idea of yours to work on a Linux filesystem folder and also expected it to fail on NTFS, very different filesystems in function/design. So yes, I suppose you are right, I'd guess it to be more an incompatible filesystem for Linux to operate on, hence the automatic resetting. Trying the different name was a bit of a long shot really (quote from my last post : a possible "workaround" : :)). Cheers.

---

### Post by John_Curry on 2014-05-19
ok I think I am fine now. My process was this (using my MUSIC folder as an example): I wished to share this with Windows 8.1 as when I am logged on there I want access to it (so I can listen to music while I'd doing Windows stuff. Hence my personal Music Directory is on my NTFS hard disk labelled 'SharedData/Music'. So what I did was ...

~$ sudo mkdir /mnt/SharedData
~$ sudo chown john /mnt/Movies
~$ sudo gedit /etc/fstab
and add in the line ...
UUID=46A2DD69A2DD5E4D /mnt/SharedData     ntfs             users,defaults 0 0 

and in Ubuntu Tweak, changed the default to /mnt/SharedData/Music

SAVE --> REBOOT and volia!

I added all the files to RhythemBox, restarted to see if all their and yes they have been renamed. I have repeated the same process for the default Folder locations (namely Downloads/Videos/Documents etc) in Tweak and it seems fine now. 

Many thanks for your tips, got me on the right direction. \\:D/

---

### Post by coldcritter64 on 2014-05-22
Good to see this working, that is very well done. 

One last tip, rather than using sudo with graphical applications it is always best to use gksudo or gksu (sudo is used for command line/terminal), the Graphical Sudo section in the Rootsudo Documentation link in my sig explains why. If this is working ok now, could you please mark as solved as well, the last link in my sig is a guide for how to do so, if needed. Cheers, coldcritter64

---

### Post by John_Curry on 2014-05-23
ok thats useful. I didn't know about gksudo. Will read up about it

---

