---
title: "Avidemux"
date: 2007-01-27
forum: General Help
---

### Post by Lowfront on 2007-01-27
Now for school I need to edit a couple things.  All I want to do is be able to cut sense out of a file I downloaded.

I have avidmux up and running but can't figuer out how to cut a scene out.
Also is there a better program for a simple cut of video?

thanks
Dave

---

### Post by dexter on 2007-01-27
To delete a piece of video:
- go to the starting point of the piece you want to delete
- press the button with the A on it (selection:: start)
- go to the end of the piece you want to delete
- press the button with the B on it selection:: end)
- press delete

tada :)

---

### Post by Lowfront on 2007-01-27
Doesn't seem to be working.....should it change the file instantly so say I cut the beginning out the beginning should be gone instantly right?

not working

---

### Post by Lowfront on 2007-01-28
?

---

### Post by iamhugeinjapan on 2007-01-28
Usually with editing programs you mark the bits you want to keep or remove and then you tell it to save/reencode etc.  It's not instant.

---

### Post by Lowfront on 2007-01-29
what other program should I try it for just basic cutting?  I can't figuer this one out

---

### Post by Lowfront on 2007-01-30
?

---

### Post by akudewan on 2007-01-30
Hi there!

Cutting scenes is quite easy with avidemux. There is also another video editing tool called Lives. Check it out: [http://lives.sourceforge.net/](http://lives.sourceforge.net/)

But I find Lives more confusing compared to avidemux.

Let me walk you through the avidemux steps:

1) Open the video

2) Now, go to the start of the scene you want to cut out. You see a "marker A" at the toolbar at the bottom. Click it. (Or you can use Edit>Set Marker A)
[[IMG]http://i6.photobucket.com/albums/y229/akudewan/screenshots/th_A.png[/IMG]](http://i6.photobucket.com/albums/y229/akudewan/screenshots/A.png)


3) Next, go to the end of the scene you want to cut out, and click on "marker B."
[[IMG]http://i6.photobucket.com/albums/y229/akudewan/screenshots/th_B.png[/IMG]](http://i6.photobucket.com/albums/y229/akudewan/screenshots/B.png)


4) Now, the part of the video that you want to delete has been selected. Go to Edit > Delete, and this section will be deleted.
[[IMG]http://i6.photobucket.com/albums/y229/akudewan/screenshots/th_del.png[/IMG]](http://i6.photobucket.com/albums/y229/akudewan/screenshots/del.png)

5) Play the video, and make sure its the way you want.



6) All thats left is saving the video. Select the Video and Audio codecs from the left hand side toolbar. (Use Copy to copy the codecs of the original video). Select the output format, and click Save. Don't overwrite the original file.
[[IMG]http://i6.photobucket.com/albums/y229/akudewan/screenshots/th_codec.png[/IMG]](http://i6.photobucket.com/albums/y229/akudewan/screenshots/codec.png)


7) Thats about it! Test the saved file in your favourite media player.

Let me know if it worked.

:)

---

### Post by Lowfront on 2007-01-30
ok i figuerd it out


thanks for much but my problem was that I wasn't stopping the video where I wanted stop and end.

Now what would  be the easiest way to get the files to a dvd.  Should I convert them with this program or is there a good dvd burning program for ubuntu thats easy and will take care of most file type?

---

### Post by akudewan on 2007-01-31
Yes, Avidemux can convert to dvd for you. It creates an Mpeg file, and then you can convert it into an image using mkisofs, and burn it.
Use Auto > DVD, and then save the file

There's also one called DeVeDe. Its very nice, and faster than avidemux. [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

---

