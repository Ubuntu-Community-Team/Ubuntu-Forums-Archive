---
title: "[NOT SOLVED, GAVE UP] How to open HUGE JPEG?"
date: 2013-04-17
forum: General Help
---

### Post by alphaamanitin on 2013-04-17
Hello Fellow Forum Goers:

Any ideas on how to open HUGE, and I mean FREAKING HUGE (>200 MB) jpg images?  Sometimes gthumb will partially open it, but it will freeze so the image is there, but I cannot sort through images or do anything to the image; additionally, if I want to quit gthumb I actually have to kill it via terminal, not the GUI X button at top right.  

I have three photos like this.  They were produced on a scanner at insane resolution settings and I cannot access the original images to create smaller (both in resolution and MBs) images.  I need ot get them to a point were I can work with them.  GIMP will not even open them.  It gets to what looks ~99 % loaded and then freezes.  

Thanks,

AlphaA

---

### Post by ibjsb4 on 2013-04-17
Doesn't seem that big to me, nomatter, try ..

[ATTACH=CONFIG]241476[/ATTACH]

I should add that you will not have to open the pic, just right click on it and resize.

---

### Post by alphaamanitin on 2013-04-17
Thanks I'll give it a shot.  Just out of curiosity, what is the largest jpg you have seen?

AlphaA

---

### Post by ibjsb4 on 2013-04-17
> **alphaamanitin said:**
> Thanks I'll give it a shot.  Just out of curiosity, what is the largest jpg you have seen?

AlphaA

Now that you ask and I take a look around, I haven't :D

Must of been thinking of something else.

---

### Post by tgalati4 on 2013-04-17
*Hugin* is a photo stitcher.  It can handle large files.

```
sudo apt-get install hugin
```

It has a learning curve, but it is quite powerful.

*Posterazor* also handles large images for printing across several sheets of paper.  It might have some tools for shrinking the image.

---

### Post by alphaamanitin on 2013-04-22
Hugin will open it, but I am on the left side of the bell curve.  I still cannot figure out how to open or resize it (right clicking does not bring up any resizing options).

AlphaA

---

### Post by VanillaMozilla on 2013-04-23
Use ImageJ, from the National Institutes for Health.  Professional software for research, open source, commonly used for handling huge images of all kinds.  And you can resize with a couple of clicks.  Also easy to use, with not too steep a learning curve.  You need File > Open, Image > Adjust > Size, and File > Save As....  You can get it from the repository.

---

### Post by coldraven on 2013-04-23
I created a 400MB tiff file in Gimp without any trouble. Give it a try.

---

### Post by Zill on 2013-04-23
alphaamanitin:  You could resize the images with the [ImageMagick Mogrify Command-line Tool]("http://www.imagemagick.org/www/mogrify.html")
```
sudo apt-get install imagemagick
```

---

### Post by s.fox on 2013-04-23
What are your system specifications?

---

### Post by alphaamanitin on 2013-04-23
So, imagemagick froze the computer trying to resize the image.  I should have mentioned this earlier but here is what I have tried: ImageJ, GIMP, gthumb, Digikam, firefox, chromium, Photoshop, and even Windows Photo Viewer.  Everything but Windows Photo Viewer failed to open the file, the programs just hang in "loading image" for 30 or 40 min.  Windows Photo Viewer will open it and promply freeze rendering opening the image pointless.  Not that it was helpful anyway as I need to edit the photo.

I have a System76 Ppan9:
Intel(R) Core(TM) i7-3630QM CPU @ 2.40GHz
15946 MiB RAM
Running Xubuntu 12.04 LTS

AlphaA

---

### Post by Zill on 2013-04-23
> **alphaamanitin said:**
> So, imagemagick froze the computer trying to resize the image...
Sounds like the image could be corrupted. :-(

Do you get any error message when using the mogrify resize command via the terminal?

---

### Post by alphaamanitin on 2013-04-23
Nope.  When I say freeze, I really mean freeze.  Nothing worked, not even the mouse or keyboard shortcuts.  I waited 20 minutes and then held down the power button.  I finally got Ristretto to open it, but like Windows Picture Viewer (or Photo Viewer cannot remember the name) it opened, gave no error, and froze to where nothing could be done.  I had to kill the program via kill command.

AlphaA

---

### Post by Buntu Bunny on 2013-04-23
Do you really need it all that badly?

---

### Post by alphaamanitin on 2013-04-23
Well, I could redo it, but it will be a huge pain in the butt.  Right now it is more the principle of the things and figuring it out than anything else.

AlphaA

---

### Post by cocoakekeyu on 2013-04-23
the #9 say is right

---

### Post by alphaamanitin on 2013-04-24
> **cocoakekeyu said:**
> the #9 say is right

As I have already stated, attempting to resize using that program just made the entire computer freeze, resulting in the necessity of holding down the power button to force the computer to shut down.  I tried to resize at 25, 50, and 75 % of original and each time the computer froze; so no, reply #9 is not "right" in this instance.

I wish there was a button to mark a thread abandoned with no answer, as this isn't solved but I am through with it.

AlphaA

---

### Post by BuntuSeriously on 2013-04-24
Probably too late for my 2 cents' but I thought I might post on this anyway ;)

I've seen this type of behavior before.  Anecdotally, it seems to all come back to swapfile corruption.  When possible, I now do my installs without a swap partition; and haven't looked back.

If you've got the RAM, this is truly the way to go.

Hope you can get things sorted out here; as I understand what a bugger it can be --

---

### Post by VanillaMozilla on 2013-04-26
Something doesn't make sense here.  200 MB is not that large an image.  Using ImageJ I have worked with volumes (i.e., 3-dimensional images) that were over 5 GB (you do have to set the maximum amount of memory that you will allow it, however--in other words, read the directions).  I don't think software is the problem.  You say you have 16 GB of memory on your computer and you are using a 64-bit system?  You should have plenty.

And freezing your computer?  Doesn't make sense.  I suppose you could be really, really out of memory, but if so, the image is not the problem.  To check that, just type
free
in a terminal and post the result.  The relevant number is the second number on the "-/+ buffers/cache:" line.

I think it's more likely that there's something else wrong, like something in your system setup, or a hardware problem or something.  Maybe you need to check your memory the next time you start the computer.  A bad memory chip could do this.

---

### Post by VanillaMozilla on 2013-04-26
> **BuntuSeriously said:**
> I've seen this type of behavior before.  Anecdotally, it seems to all come back to swapfile corruption.
No, the OP says he has 16 GB of RAM.  He shouldn't be using the swap file for a paltry 200 MB image.

---

### Post by alphaamanitin on 2013-04-26
I don't think it is the system or the RAM.  I would guess that the most likely cause is some sort of error in the jpeg itself.  I am 99.999% sure it isn't the RAM as I have completely used up my RAM during analysis of large datasets of DNA sequences.  I don't know what the error is, but there must be an error in the jpeg.  When I tried to resize with imagemagick it froze instantly, so I think there is some sort of error stopping things from dealing with it correctly.  So far only Windows Picture Viewer and Ristretto have even managed to open them, and they will only let me quit the program and nothing else.

AlphaA

---

### Post by VanillaMozilla on 2013-04-26
A program should never fail just because you feed it erroneous data.  The fact that all programs fail with it suggests to me that it's not software, since so many diverse programs with different code bases are failing with it.  I would still run a memory test.  It takes only a little while.  And have you tried on a different computer?

---

### Post by alphaamanitin on 2013-04-27
> **VanillaMozilla said:**
> A program should never fail just because you feed it erroneous data.  The fact that all programs fail with it suggests to me that it's not software, since so many diverse programs with different code bases are failing with it.  I would still run a memory test.  It takes only a little while.  And have you tried on a different computer?

I'm sorry but it is simply not true that "a program should..."  Plenty of programs fail, crash, freeze, etc due to errors in files or inproper coding to deal with issues in files.  In fact, many pen testers love finding these bugs in programs because sometimes this can be used to break into a system.  For god's sake there is a whole hacking technique center around this type of thing: Fuzzing.  

I also do not agree with your logic that the wide variety of programs failing to open it indicates hardware.  I see no reason to believe that is any more likely than the jpeg image is not correctly formatted.  Since jpeg is a standard format the programs expect any jpeg to conform to that standard, if during the scan of the image and the transfers the file became partially corrupted that could also be the reason most programs are not dealing with the image.

For example, I have, back when I had good ol' 56k dial-up, downloaded jpegs from the internet that were only partial images.  What I mean is that sometimes an image would only have ~50% of the image and the rest would be black.  Well, in that case I have had some programs that would open the image and display the half that was downloaded and the half that was black while others would not open it at all.  Instead it would give an error saying that the image was damaged an could not be opened.

Yes, I have also tried to open it on two different computers: an Acer AspireOne and a custom made desktop, both running windows 7.  Both of these computers would, as I described before, Windows Photo Viewer would open the image but freeze.  I couldn't zoom in or zoom out or flip through the other images in the folder as typical.  Additionally, the desktop with a 16 gb RAM, AMD Phenom II x6 1100T cpu, ATI Radeon HD 6850 gpu running windows 7 x64 ultimate addition would not open the image in Paint.Net or Adobe PhotoShop CS5.  Both the programs just stalled out at about 90% loading.  I also just tried it at work today on a mac running 10.5.8 OSX. It stated there was an error in the image file.  

Nevertheless, I agree that it is worth checking to makre sure that my mem is fine.  Still though, I have tried to open the file on my linux OS of my laptop while my virtual machine, which I gave by default half the total RAM, was running Windows 7 x64 Ultimate.

AlphaA

---

### Post by sudodus on 2013-04-27
1. Can you upload the huge jpeg file somewhere, so that we, who have some many good tips, can try ourselves? It is enough if *one* of us succeeds and shares the result.

2. Maybe the image dimensions, width x height, are too big for the internal representation, that some internal variable will overflow? In this case, image editing programs might differ.

---

### Post by Thee on 2013-04-27
Yeah upload the image so we can try, if you feel comfortable doing that, of course.

---

### Post by dino99 on 2013-04-27
A few steps to follow:

- check the system first: no video driver issue, no xsession-errors errors, no dmesg errors
- if you know which program have built these "jpeg" images, check they are really "jpeg" (not an extension change/rename, not a closed image format with drm ...)
- is renaming that "jpeg" make the load easier ?

---

### Post by VanillaMozilla on 2013-04-27
If there's something wrong with the image file, I would expect an error message.  That fact that not one viewer gave an error message suggests that there is some other problem.  If you want to upload the image somewhere, I can take a look at it.  It's up to you.

---

