---
title: "Putting songs on Sansa C250"
date: 2008-04-08
forum: General Help
---

### Post by kyletreubig on 2008-04-08
Hi,

I've recently started using Ubuntu and got a Sansa C250 (2GB) mp3 player just yesterday.  When I connect the player to my computer, it shows up as a mounted device and I can view the folders.

When a copy and paste mp3 files (either individually or a folder at a time), upon unmounting and disconnecting the player, I am unable to successfully turn it on.  It freezes on the "SanDisk" startup screen.  If I delete the files I just put on, the player starts up fine.

I believe I am connecting in MSC mode (setting the Hold switch and holding down the rewind button--I forget where I read that), and the automatic connection seems to be MSC as well.  I do not see any option under settings to set the USB connection mode.

Once, I got the player to start up correctly after I had written some files (to the MUSIC folder).  The songs did not show up at all, yet the amount of free space the player reported back reflected the amount of space taken up by the files I was able to copy to the player.

Dragging and dropping the files (as opposed to right clicking, copying, and pasting) appears to make no difference.

I've even typed "sync" in a terminal before unmounting the player (to flush out any pending write actions).

I can sync songs to the player in Windows Media Player when I run Windows XP, but I've just discovered Ubuntu and loving it--so I'd really like to be able to put songs on the player in Ubuntu rather than having to start up Windows.

Any suggestions would be much appreciated!

thanks,

Kyle

---

### Post by kyletreubig on 2008-04-09
Update:

I updated the firmware to that of a different region and I got the USB setting option in the settings menu.  The player is definitely in the MSC configuration.

I've again tried to copy files over to the player, and place them in the MUSIC folder--yet they do not show up on the player.

---

### Post by kyletreubig on 2008-04-09
Just in case this helps: I'm running Ubuntu 7.10 (same results for Windows XP though), the firmware version on the mp3 player is v03.02.05P (asian/pacific rim).

And my current is issue is that the player doesn't detect songs that have been transfered to the player in MSC mode (even though it detects the presence of these files via memory usage).

Is it possibly an issue with the mp3 ID tags?

thanks in advance,

Kyle

---

### Post by kyletreubig on 2008-04-10
I have solved the issue.

Turns out that a song (or folder) with whitespace in it (instead of an underscore) will cause the player to freeze.  So I removed the whitespaces from the files/folders that I wanted on the player.  Wouldn't you know it--they showed up on the player.  However, they were all listed under Unknown Artist and Unknown Album and referenced by the file name, rather than the track title.  Thus it was apparent that there was an issue with the ID3 tags.

I did a little bit of research and it seems that the Sansa player is picky about what ID3 tags it will read.  So I removed all tags from the files, and re-did the ID3v2.4 tags (I don't know if the player can't use ID3v1 tags or if the presence of both causes it to crash).

Now the songs were under their respective artists, folders, and had the correct track name.  However, certain albums, when I put them on the player, caused the player to freeze during the Refresh Database stage.  After thinking about it for a while, I realized that all albums/artists that caused this freeze had a genre with a space (like Hard Rock).  So I re-tagged those songs to have a single-word genre, and now everything is working beautifully.

So the moral of the story:
Don't drag and drop folders or files with whitespace--use underscores.
Use ID3v2 tags.
Don't use whitespace in the genre tag.

---

### Post by kelsey.chris on 2008-04-20
Thanks for sharing - I was just beginning to struggle with the same issue.

---

