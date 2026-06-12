---
title: "Program for ripping data cd's?"
date: 2007-02-21
forum: General Help
---

### Post by miceagol on 2007-02-21
I'm trying to find a program that can rip data CD's. The CD I'm trying to rip to an image is a combined audio and data CD. k3b thinks it's an audio CD I'm trying to rip, and gives me audio CD ripping options, thus I can't use it. I've also tried dd and cdrecord, but both of them don't support DVD-ROM's. Any programs out there that can do this task for me?

---

### Post by angryfirelord on 2007-02-21
sudo apt-get install lame ripperx. RipperX is a little weird to use, expecially since it doesn't use gtk or qt (basic gui), but that's what I use.

---

### Post by miceagol on 2007-02-21
> **angryfirelord said:**
> sudo apt-get install lame ripperx. RipperX is a little weird to use, expecially since it doesn't use gtk or qt (basic gui), but that's what I use.

Like k3b it only recognizes the audio track on the CD. How do I make it rip the data track?

---

### Post by angryfirelord on 2007-02-21
What type of "data" do you have? I'm a little confused.

---

### Post by punx45 on 2007-02-21
are you trying to rip it? (extract data to readable formats (mp3,avi, etc) or make an image of it?(make an exact copy)

i dont have k3b handy in front of me at the moment, but there should be a 'copy disc' or similar option that will create an image (.iso) of the CD regardless of content.

===

is this an 'enhanced' retail music CD?

if that is the case, the music you can rip as MP3/Ogg whatever you like, and then the video files are probably in a directory on the disc somewhere as mpeg or avi etc.   that was the case the last time i looekd at an enhanced CD.

---

### Post by miceagol on 2007-02-22
> **angryfirelord said:**
> What type of "data" do you have? I'm a little confused.

This is a CD with one audio track and one data track, and I want the data track. The data track is a mix of everything. The type of files is really irrelevant in this case.

---

### Post by miceagol on 2007-02-22
> **punx45 said:**
> are you trying to rip it? (extract data to readable formats (mp3,avi, etc) or make an image of it?(make an exact copy)


In my first post I said clearly I wanted an image of it.

> **punx45 said:**
> 
i dont have k3b handy in front of me at the moment, but there should be a 'copy disc' or similar option that will create an image (.iso) of the CD regardless of content.


I tried it, but k3b only "sees" the audio track, so I get no option to rip it as an image.

> **punx45 said:**
> 
is this an 'enhanced' retail music CD?


That is correct. 

> **punx45 said:**
> 
if that is the case, the music you can rip as MP3/Ogg whatever you like, and then the video files are probably in a directory on the disc somewhere as mpeg or avi etc.   that was the case the last time i looekd at an enhanced CD.


I'm not interested in the audio track, just the data track, and I'd like to have the complete track, not just the videos.

Anyway, thanks for your help. If anyone could try to rip a data track of a mixed audio/data CD, I would appreciate a dummies guide if you manage it. :)

---

### Post by reclusivemonkey on 2007-02-22
mkisofs should do the trick. However, you will need to read the "man" for instructions.

---

### Post by miceagol on 2007-02-22
> **reclusivemonkey said:**
> mkisofs should do the trick. However, you will need to read the "man" for instructions.

Thanks. The man page was so long I'll have to wait to test it. ;)

---

### Post by punx45 on 2007-02-22
my bad.. missed select key words :-k 

mkisofs would be your best bet for creating an image since k3b appears to be uncooperative.  the problem is, im not sure if you will be able to isolate a certain portion of the disc.

are you unable to access the data portion of the disc all together?   i suppose it wouldn't be outside the realm of possibility that the producers of this album, in their infinite wisdom, somehow hid the data part, and made it only readable from a windows pc with some sort of autorun function, or proprietary software :(

---

### Post by miceagol on 2007-02-23
> **punx45 said:**
> my bad.. missed select key words :-k 
are you unable to access the data portion of the disc all together?   i suppose it wouldn't be outside the realm of possibility that the producers of this album, in their infinite wisdom, somehow hid the data part, and made it only readable from a windows pc with some sort of autorun function, or proprietary software :(

The data track is readable... ;)

---

