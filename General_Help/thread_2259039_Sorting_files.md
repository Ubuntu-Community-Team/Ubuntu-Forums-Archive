---
title: "Sorting files"
date: 2015-01-01
forum: General Help
---

### Post by mac-2check on 2015-01-01
Hello,

I've got a little problem with my music files, when I copy an album to a mp3 player it goes from the last track to the first and then the player plays the album backwards (track 10, 9, 8 etc). I found out its because the music files had been unpacked and copied this way - Unrar does not unpack files in accordance to their numbering.

 I'm looking for a way to re-sort my music files according to their numbers, so each every abum will be rewritten.

It's a but tricky to explain for me, but I hope you got it. If not, I'll be glad to explain it in a different way.

Thanks for replies,

Martin

---

### Post by schragge on 2015-01-01
I don't quite get it, but it looks like the last file copied gets played first. How do you copy files? In file manager? Which one -- nautilus, dolphin, thunar? How do you select files to be copied? What mp3 player is it?

---

### Post by ajgreeny on 2015-01-01
Are you suggesting they are played according to their timestamp sequence?

If so you could always change the timestamps using **touch -d "time" /path/to/file** to reorder them.

It may, however, be more likely that the ID3 tags, rather than file-names, are setting the order the files play in your player.
If your player accepts and acts on playlists that may be an even better way to proceed.

---

### Post by mac-2check on 2015-01-01
its an old mp3player, it does not take in concern names of files, but only the order in which the files are copied on it. Look at the attachment - the album i sorted by modification date and the thing I need is a command or a program which can rewrite the files and the order will be the way it should - 1,2,3 and so on. 

I always copy whole folders.

I hope now it makes a bit more sense, it would be hard to explain even in my native language ;)

---

### Post by schragge on 2015-01-01
Well then the touch hack suggested by **ajgreeny** should work. I'm even not sure -d switch is needed. Something like
```
touch -c {10..01}-*.mp3
``` may be enough.

---

### Post by papibe on 2015-01-01
Hi mac-2check.

Most mp3 players that I know of, order files using the files' ID3 tags. I would make sure that the tags are not the problem before doing anything.

If you confirm that is just the modification time what is being used to sort the files, the 'touch' approach mentioned by ajgreeny and schragge should work.

I would just add that in case the player's file system is not 'Linuxy' you may need to do something like:
```
for i in {10..01}; do sleep 1; touch "$i"*.mp3; done
```
(or sleep 2, or 3),

Let us know how it goes.
Regards.

---

### Post by Dennis N on 2015-01-01
Any reason you are sticking with that player? Audacious for example, will list a set of files selected as a group in alphabetical order of the filenames. So if they all have track numbers, selecting all as a group would end up listing them in track order.

---

### Post by ajgreeny on 2015-01-03
I think the OP is talking about hardware; a mobile mp3 player, not software on his computer!

PS: I really like audacious as well. It's fast, simple, and does exactly what it says on the tin.  Most music player GUIs are overkill in my opinion.

---

### Post by Dennis N on 2015-01-03
> **ajgreeny said:**
> I think the OP is talking about hardware; a mobile mp3 player, not software on his computer!

PS: I really like audacious as well. It's fast, simple, and does exactly what it says on the tin.  Most music player GUIs are overkill in my opinion.

You could be right. Didn't occur to me. Wonder if it was solved. As for Audacious, I don't like players that keep their own music libraries/databases. I like to do it my way.

---

### Post by mac-2check on 2015-01-03
thanks for responses, yes it is a hardware.

the command touch seems alright, however, I tried the line you wrote here and it didn't change anything.

I'll try to explain it once more. The external player does not care about tags, the only thing that matters is in what order the files were copied to the external player. The problem begins with unpacking a downloaded album. unrar does not unpack it piece by piece but rather randomly(often begins with the last track), and then when I copy it to my music folder which is on another harddrive, thunar copies it the way it was unpacked. The way I solve this is manually - I drag the files piece by piece from one folder to another.

If I want to rectify an album which is in a bad order I need to copy it away from my music folder, remove the one in the music folder and copy it back one by one.

I hope it makes sense now. It is not that vital to solve it, its more like an inconvenience. I have had the player since xmas 2005 - longer than I would ever expect, but its still working good....

---

### Post by Holger_Gehrke on 2015-01-03
You might want to try copying from the command line. When you do a 'cp * /media/<Name of your player's directory>' the bash expands the '*'-wild card in sorted order.

---

### Post by schragge on 2015-01-03
Well, thunar-archive-plugin by default uses *file-roller* to extract files from archives. You can install xarchiver, add it to *Open with...* menu (see [post=13197802]this post[/post]), or even make it default application to open archives. Xarchiver has an option *Sort archive by filename* (menu **Action > Preferences** or just press **Ctrl+F**). Try if it solves your issue with rar. You also can sort files in Thunar after extracting them from archive (menu **View > Arrange Items**). Plus, Thunar Bulk Renamer is quite a powerful feature. Besides, there are such tools as [fatsort]("http://manpages.ubuntu.com/manpages/trusty/en/man1/fatsort.1.html") and [mussort]("http://manpages.ubuntu.com/manpages/trusty/en/man1/mussort.1.html"). Never used them, but from description they look promising.

---

### Post by lisati on 2015-01-03
I agree that having tracks play in the "wrong" order can be annoying, particularly if you're used to an album playing in a particular order or if you're listening to an audio book and want to listen to chapters in sequence.

I've used fatsort on my MP3 player, with some success. It has been a while, so I can't remember the exact command.... :(

---

### Post by mac-2check on 2015-01-03
well, I tried xarchive and it unpacks archives alright, so I think my problem is solved as I put on my mp3 player mostly new albums.

thanks for help guys ;)

---

