---
title: "Symbolic links or similar - merging directories"
date: 2007-09-23
forum: General Help
---

### Post by Zorael on 2007-09-23
I've two harddrives over which my multimedia content is split. In other words, I have two directories - */media/main/video* and */media/misc/video* - which both contain video files. However, due to space limitations I can't keep them on the same drive, so when I'm looking for something in particular I first have to hunt it down.

In Windows, I wrote a batch file that made .lnk links to each subdirectory in each video directory, and placed them in a folder on my desktop. Think of them like shortcuts; clicking on A.lnk took me to C:\video\A, clicking on B.lnk took me to D:\video\B, etc.

In this wonderful world of ext3, with mount --bind and symbolic links, is there some way to make a directory and mount or link the contents of several directories into it? In other words, merge them into a meta-reference directory, so that it would "contain" - or rather, link towards - both A and B at the same time? I imagine the reference directory would have to be read-only.

Does such a solution exist?

---

### Post by prince_niceguy on 2007-09-23
there are two ways which I know of.

1. create link.  Just sudo nautilus and then navigate to these two folders and right click make link. copy these two links to your home directory/vidoes let say. so both the directory would be available by just clicking in your videos folder.

2. mount both the drives in your home/videos/A and home/videos/B directory.

---

### Post by Zorael on 2007-09-23
Yes, but that would be on a per subdirectory basis. What I'm looking for (if it exists), is some way to merge the actual video directories, creating the illusion that A and B are in the same - joint - video directory.

> 2. mount both the drives in your home/videos/A and home/videos/B directory.
A and B are not **drives** as such - think of them as Anime and Bollywood; both subclasses of video. In other words, what I want to do is mount both /media/main/video and /media/misc/video into /home/zorael/video, in which both A and B would be referenced towards.

I get the feeling the only solution would be to make symbolic links towards each subdirectory and place them in /home/zorael/video - though arduous, the result would be the same; only it wouldn't update automatically. :)

---

### Post by odiseo77 on 2007-09-23
Just tried making a hard link between two directories but it returned an 'Operation not allowed' error. So a quick search on google.com/linux returned [kdiff3]("http://kdiff3.sourceforge.net/doc/dothemerge.html"), which is on feisty's repositories (haven't used it, so I can't help you beyond this suggestion... only, make sure to back up all your data before you proceed!).

Regards.

---

### Post by cwaldbieser on 2007-09-24
You can create a folder with symbolic links to all of your video files, but you would need to add a new link every time you added a file to one of the real directories.
Edit: Oops, I should have read more carefully.  You did just say that.

---

### Post by pbhj on 2008-05-12
unionfs?

---

### Post by Zorael on 2008-05-27
UnionFS actually looks like just the thing. Is there a guide someplace as to how to set it up in a non live CD environment?

My googling skills fail me.

---

