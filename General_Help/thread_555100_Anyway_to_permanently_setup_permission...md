---
title: "Anyway to permanently setup permission..?"
date: 2007-09-19
forum: General Help
---

### Post by Phelan on 2007-09-19
I'd like the power of sudo nautilus without having to type it in the terminal...I've seen it said that you can read/write to the home folder default, but ubuntu wouldn't let me.  I want to use NTFS-3g ( a seperate subject) but I'd like to be able to read/write anywhere on my linux partition (I realize this is risky). 

:confused:

---

### Post by prince_niceguy on 2007-09-19
add yourself to root group...

---

### Post by Phelan on 2007-09-19
Sorry, I have seen about this but don't know how..? Thanks :)

---

### Post by jviscosi on 2007-09-19
> **Phelan said:**
> I'd like the power of sudo nautilus without having to type it in the terminal...I've seen it said that you can read/write to the home folder default, but ubuntu wouldn't let me. I want to use NTFS-3g ( a seperate subject) but I'd like to be able to read/write anywhere on my linux partition

I've done this in the past to other programs, but couldn't remember how. Google suggests the answer is to set permissions to 4711 on the executable, e.g., **[FONT=Verdana,Arial,Helvetica][SIZE=2]sudo chmod u+s /usr/bin/nautilus[/SIZE][/FONT]**[FONT=Verdana,Arial,Helvetica][SIZE=2] from a terminal, setting the SUID bit so that it runs with root permissions.  I'd maybe first try it on a copy of nautilus and make sure it does what you want.

[/SIZE][/FONT]> **Phelan said:**
> (I realize this is risky).

Yup! I am no expert in this area, but I think Nautilus isn't going to be expecting to always run with these permissions so it might behave in an unsafe manner, completely aside from the fact that you could nuke your whole filesystem by doing this. Is there some way to accomplish your purpose without always running Nautilus with root permissions? (I'm assuming your desire to write anywhere in the file system via Nautilus is a means to an end and not the end itself.)

---

### Post by Phelan on 2007-09-20
I dont get it though.  Linux is so powerful and diverse, yet it wont even give you enough power to mess itself up, what's up with that?  I got my NTFS-3g working, but now I have to figure out how to get XMMS to play my mp3's that are on my windows partition, is this possible?

How should I have my home folder setup?  A downloads folder and a few others.  It's just hard to fathom not needing to access a program files menu and EVERYTHING of my personal files having to go into "home".  I guess I should be treating "home" the same as "c:"...and just make folders in there.

Does anyone have any information (besides ubuntu FAQ and documentation) on transferring mp3's from windows to linux partitions?

:popcorn:

---

### Post by mojoman on 2007-09-20
> Linux is so powerful and diverse, yet it wont even give you enough power to mess itself up, what's up with that? 

Sure it does. Just get into the habit of always using the root account. I wouldn't do it myself, but hey, I just don't want to mess up my system...

> now I have to figure out how to get XMMS to play my mp3's that are on my windows partition, is this possible?

[URL="https://help.ubuntu.com/community/RestrictedFormats/MP3?highlight=%28mp3%29"]
https://help.ubuntu.com/community/RestrictedFormats/MP3?highlight=%28mp3%2[/URL]9

> How should I have my home folder setup?  A downloads folder and a few others.  It's just hard to fathom not needing to access a program files menu and EVERYTHING of my personal files having to go into "home".  I guess I should be treating "home" the same as "c:"...and just make folders in there.

I myself have the following setup. The computer have two users, each have a folder of their own according to their username which is located in in the home folder. Also, in the home folder I have a number of shared folder. These are for example download, movies, music, etc. Both users can read, write and execute freely in these common folders but not in the other users home folder. This is possible as both users belong to a group which owns the shared folders. My advice would be to read up on the manual for the bash command chmod. It takes a while to get  the hang of it but it's worth the effort, especially since permissions is a fundamental aspect of Linux.

> Does anyone have any information (besides ubuntu FAQ and documentation) on transferring mp3's from windows to linux partitions?

But you can read your windows partition, can't you? Why not simply copy it? Or, if you prefer, install software that allows you to write ext3 from windows and copy from windows to linux. Or am I missing something here?

Hope this helps.
/mojoman

---

### Post by Phelan on 2007-09-20
> 
But you can read your windows partition, can't you? Why not simply copy it? Or, if you prefer, install software that allows you to write ext3 from windows and copy from windows to linux. Or am I missing something here?
 
Yes, actually I can.  I was trying to avoid moving them to the linux partition, but if I can simply read them from the ntfs partition, I guess it doesn't matter.  

I appreciate all the help, you guys and this forum is a great place, couldn't have done 99% of the stuff I've gotten done with ubuntu without this place.

---

### Post by jviscosi on 2007-09-20
> **Phelan said:**
> Yes, actually I can.  I was trying to avoid moving them to the linux partition, but if I can simply read them from the ntfs partition, I guess it doesn't matter. 

You might want to consider putting a symbolic link in your home directory that points to the directory on the Windows drive that you want to access.  Then it'll look and act just as if that directory lives in /home.

I have the same sort of setup as mojoman, with two user directories in /home and then a /home/share where the MP3s, pictures, videos, etc., live.  Symbolic links in the user home directories point at /home/share making it extremely convenient to access the shared files.  Of course, my wife hardly touches the Linux box since she got an iBook years ago, but having the /home/share also makes it easy to share files with the Mac via Samba.

---

