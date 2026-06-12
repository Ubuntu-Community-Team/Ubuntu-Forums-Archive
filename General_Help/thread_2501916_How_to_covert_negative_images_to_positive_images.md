---
title: "How to covert negative images to positive images"
date: 2024-10-26
forum: General Help
---

### Post by satimis on 2024-10-26
Hi all,

How to covert negative images to positive images

I have posted this question before but I couldn't find a reliable solution.

Running on Terminal ```

$ convert -negate source.png target.png

```

But the quality of the positive images converted are poor.

**[COLOR="#FF0000"]Steps performed by me creating the negative images on films[/COLOR]**
1.  Use a 12" tablet as light box
2.  Mount the film on film holder
3.  Place the film holder on top of the tablet
4.  Take photos with a mobile phone camera mounted on a tripod

I have no problem taking negative images from films but I couldn't find a solution converting the negative images to quality positive images.

Please help or advising me where I should post my problem for a solution?

Thanks in advance

Regards

---

### Post by ajgreeny on 2024-10-26
Are you trying to do this with command line or using a GUI application?  I am certain imagemagick can do it but can't give you the command now as I'm on an Android tablet.

Don't forget many if not all GUI  image editors, eg gimp, can do the job easily though I can't comment on the quality of the output image.

---

### Post by satimis on 2024-10-26
> **ajgreeny said:**
> Are you trying to do this with command line or using a GUI application?  I am certain imagemagick can do it but can't give you the command now as I'm on an Android tablet.

Don't forget many if not all GUI  image editors, eg gimp, can do the job easily though I can't comment on the quality of the output image.
Hi ajgreeny,

Thanks for your advice.  I have tried command line before but the quality of the positive image was not good.  I think that this is not the road for me to follow.

Regards

---

### Post by dragonfly41 on 2024-10-26
Recently I suggested in another post leveraging Wolfram language.

Same applies to this requirement.

But admittedly Wolfram features can be rather overwhelming. 

[https://reference.wolfram.com/language/ref/ColorNegate.html](https://reference.wolfram.com/language/ref/ColorNegate.html)

---

### Post by ajgreeny on 2024-10-26
I have just used imagemagick to convert a positive photograph to negative then used nomacs to invert that image back to positive.
All went very well with no real difference between the original and the double converted.

Just to be sure I also did this in both directions, positive to negative then negative to positive 3 times each using the most recently converted image so I ended with 4 versions of each image, positive and negative.
I could detect no difference between the 8 total of images and all exif data was retained etc etc. and the images all appeared visually identical

The command used was very simple ```
convert positive.jpg -negate negative.jpg
```
Why not give it a try?

---

### Post by satimis on 2024-10-26
> **dragonfly41 said:**
> Recently I suggested in another post leveraging Wolfram language.

Same applies to this requirement.

But admittedly Wolfram features can be rather overwhelming. 

[https://reference.wolfram.com/language/ref/ColorNegate.html](https://reference.wolfram.com/language/ref/ColorNegate.html)
Hi dragonfly41,

Thanks for your advice.

I'm searching for a simple and straightforward solution, if possible.  I have hundreds of negatives to develop.  I can further treat the developed positives on GIMP or Darktable.

Regards

---

### Post by dragonfly41 on 2024-10-26
Intuitively I would use a tool such as Albert, write a Python extension to automate the process. You can then write your own commands in the popup query field. Try the standard plugins.

P.S. Example of custom Albert / Python script here:

[https://github.com/albert-ying/ImageTools](https://github.com/albert-ying/ImageTools)

*Actually the above post is not related to Albert launcher. The developer is named Albert.*

Here is another attempt to show examples of plugins. But write your own..

[https://github.com/bergercookie/awesome-albert-plugins](https://github.com/bergercookie/awesome-albert-plugins)

---

### Post by satimis on 2024-10-26
> **ajgreeny said:**
> I have just used imagemagick to convert a positive photograph to negative then used nomacs to invert that image back to positive.
All went very well with no real difference between the original and the double converted.

Just to be sure I also did this in both directions, positive to negative then negative to positive 3 times each using the most recently converted image so I ended with 4 versions of each image, positive and negative.
I could detect no difference between the 8 total of images and all exif data was retained etc etc. and the images all appeared visually identical

The command used was very simple ```
convert positive.jpg -negate negative.jpg
```
Why not give it a try?
Hi ajgreeny,

Thanks for your advice.

I have tried long time ago on Terminal running```

$ convert negative.jpg -negate positive.jpg

```
The quality of the postive.jpg was poor.

I just tried it again, with the same poor positive image resulted.  No improvement

Regards

---

### Post by satimis on 2024-10-26
> **dragonfly41 said:**
> Intuitively I would use a tool such as Albert, write a Python extension to automate the process. You can then write your own commands in the popup query field. Try the standard plugins.

P.S. Example of custom Albert / Python script here:

[https://github.com/albert-ying/ImageTools](https://github.com/albert-ying/ImageTools)

*Actually the above post is not related to Albert launcher. The developer is named Albert.*

Here is another attempt to show examples of plugins. But write your own..

[https://github.com/bergercookie/awesome-albert-plugins](https://github.com/bergercookie/awesome-albert-plugins)
Hi dragonfly41,

Is it the plugin for GIMP?  I haven't added it

Regards

---

### Post by Dennis N on 2024-10-26
In GIMP, it's in the Colors menu.
Open the image file, then
Colors > Invert

---

### Post by ajgreeny on 2024-10-26
Are these negative images actual photographic negatives that you've scanned and want to invert to positives for printing or just to archive the pictures?

I have tried many times to do that with some old B/W negatives and some 35mm slides but never managed to get anything to work well enough so I suspect it may need a dedicated negative scanner.
Alternatively, though I've not tried this myself, try scanning using a backlit screen placed over the negative to ensure enough white light is passing through the negative as it sits on the scanner.
Perhaps that is what you did already when you said " Use a 12" tablet as light box"?

---

### Post by dragonfly41 on 2024-10-26
I have this very old, ancient, scanner which I have never applied to my  old 35mm film and slides which go back to last century. I might reawaken interest. However it requires my dual boot Windows to run the scanner.

[https://support.usa.canon.com/kb/s/article/ART126898#:~:text=Once%20the%20preparations%20for%20film,the%20calibration%20slot%20is%20obstructed](https://support.usa.canon.com/kb/s/article/ART126898#:~:text=Once%20the%20preparations%20for%20film,the%20calibration%20slot%20is%20obstructed).

---

### Post by qyot27 on 2024-10-26
In AviSynth:
```
ImageSource("%03d.png", start=1) # image sequence 001.png, 002.png, 003.png ...
Invert()
```

---

### Post by HermanAB on 2024-10-27
The problem is that a scanned negative film is not a simple mathematical inverse of a positive photo, and no matter how much you play with Hue and Tint, you won’t get it right. I have only ever managed to convert film to B&W and Sepia tones  with acceptable quality.

I think you will need something very smart to do the conversion.  The Wolfram suggestion is probably the way to go.

---

### Post by satimis on 2024-10-27
> **Dennis N said:**
> In GIMP, it's in the Colors menu.
Open the image file, then
Colors > Invert
Hi Dennis,

Thanks for your advice.

That was what I did in the past.  The quality of the postive image is still poor, similar to running 'convert" command on Terminal; ```

$ convert negative.jpg -negate positive.jpg

```
Further adjusting is needed.  I used Color -> Curve

But I have hundreds of negatives.  I'm trying finding an easier solution.  I don't mind converting them one-by-one.

Regards

---

### Post by dragonfly41 on 2024-10-27
> 
[COLOR=#000000]But I have hundreds of negatives. I'm trying finding an easier solution. I don't mind converting them one-by-one.[/COLOR][COLOR=#000000]
Here is another automation plan.
(1) Install Recoll
(2) Let Recoll index your entire desktop and devices (go away and leave it running for a long time on first usage)
(3) Return after indexing completed and open the Recoll GUI
(4) In query field type [ext:jpg] - meaning show all  files with extension .jpg
(5) Sort the files as you wish to plod through them
(6) If your cursor hovers over query field you will see a popup giving examples of complex queries
(7) Select the *.jpg you wish to process.
(8) Right click and you see multiple options

Now it becomes interesting.

You might wish to apply a custom script to different file types.

For this automation customisation go to [Preferences] in Recoll topbar.

[GUI configuration].

[User Interface tab] > [Choose Editor Applications] > [Native Viewers].


In long list look for Mime Type   [image/jpeg]

 Untick: [Use Desktop preferences by Default] 

e.g. image/jeg has command [ristretto %f] associated.

This gives you an opportunity to substitute default command with your own custom script (ending in %f which means use the selected file from Recoll index).

Now all options are open and I will not go so far as exploring how to apply say a custom Python script to selected MIME type.

For example I map:

**MIME Type**           **Command**
application/pdf       masterpdfeditor %f

So "pair" MIME type with an application such as Gimp, ImageMagick, Wolfram and apply to the image you select in Recoll GUI.

Recoll is an ingenious tool.


I use it to index and open CherryTree notes such as:

application/xml     cherrytree %f


Having written above I see that MIME type *.jpg does not open in Recoll (only jpeg is listed) so you will need to add a new value image/jpg with associated viewer/script.


[FOOT NOTE]

As an additional refinement you can use Recoll to display all of your hundreds of images in a search profile. Test the process first. Then the rabbit out of a hat trick is to move to another smart tool Actiona to progress automatically through every image one by one by emulating the keyboard and mouse actions. Sit back and watch it running through your images like a movie by controlling Recoll as a target window in Actiona. This "image factory" workflow might also use Albert as previously discussed, where Albert drives Actiona whch in a chain drives Recoll ...   ... and Wolfram if you take that step.[/COLOR]

---

### Post by satimis on 2024-10-27
> **dragonfly41 said:**
> [COLOR=#000000]
Here is another automation plan.
(1) Install Recoll
(2) Let Recoll index your entire desktop and devices (go away and leave it running for a long time on first usage)
(3) Return after indexing completed and open the Recoll GUI
(4) In query field type [ext:jpg] - meaning show all  files with extension .jpg
(5) Sort the files as you wish to plod through them
(6) If your cursor hovers over query field you will see a popup giving examples of complex queries
(7) Select the *.jpg you wish to process.
(8) Right click and you see multiple options

Now it becomes interesting.

You might wish to apply a custom script to different file types.

For this automation customisation go to [Preferences] in Recoll topbar.

[GUI configuration].

[User Interface tab] > [Choose Editor Applications] > [Native Viewers].


In long list look for Mime Type   [image/jpeg]

 Untick: [Use Desktop preferences by Default] 

e.g. image/jeg has command [ristretto %f] associated.

This gives you an opportunity to substitute default command with your own custom script (ending in %f which means use the selected file from Recoll index).

Now all options are open and I will not go so far as exploring how to apply say a custom Python script to selected MIME type.

For example I map:

**MIME Type**           **Command**
application/pdf       masterpdfeditor %f

So "pair" MIME type with an application such as Gimp, ImageMagick, Wolfram and apply to the image you select in Recoll GUI.

Recoll is an ingenious tool.


I use it to index and open CherryTree notes such as:

application/xml     cherrytree %f


Having written above I see that MIME type *.jpg does not open in Recoll (only jpeg is listed) so you will need to add a new value image/jpg with associated viewer/script.


[FOOT NOTE]

As an additional refinement you can use Recoll to display all of your hundreds of images in a search profile. Test the process first. Then the rabbit out of a hat trick is to move to another smart tool Actiona to progress automatically through every image one by one by emulating the keyboard and mouse actions. Sit back and watch it running through your images like a movie by controlling Recoll as a target window in Actiona. This "image factory" workflow might also use Albert as previously discussed, where Albert drives Actiona whch in a chain drives Recoll ...   ... and Wolfram if you take that step.[/COLOR]
Hi dragonfly41,

Lot of thanks for your detail advice and time spent to help me.

I'll test Recoll on a VM of VirtualBox, because this is my daily work PC.


[B][COLOR="#FF0000"]EDit
===[/COLOR][/B]
I found an old 128GB SSD.  Can I use it for this test ?


Regards

---

### Post by dragonfly41 on 2024-10-27
I have just come back to this thread. Regarding spending time on this don't worry since it has brought this up the stack of things I must do. I plan to use Recoll to index multiple MIME types to "get order out of chaos" in my desktop.  to migrate multiple, multiple files into an Obsidian data vault. A constellation.

Now it is quite a good idea to place your archives into a 128GB SSD. You can then point Recoll to only that SSD and make it do its magic. In Recoll you can choose a specific location of the files to be indexed rather than the entire desktop (although if you do index the entire desktop you will find images buried away as say thunderbird email attachments and other hidden places). So desktop is wide scan, specific SSD is narrow scan. But remember that there must be headroom for Recoll to place its index which is large.  Suggest that you read the Recoll forum since Python can be used as Recoll driver. This fits well with use of Albert python extensions. But this might be too much of a step for you.

One thread in forum: [https://www.freelists.org/post/recoll-user/Augment-recoll-db-with-metadata-from-external-db,1#google_vignette](https://www.freelists.org/post/recoll-user/Augment-recoll-db-with-metadata-from-external-db,1#google_vignette)

RSS feed can also be installed in LifeRea.

Just to confuse further a few days ago I stumbled onto Adobe upload facility where you can upload and convert images into SVG.  Free.  Then the SVG code can be viewed in Inkscape and the colours in different fills (XML code) can simply be changed. I plan to experiment later with this idea .. much later.   [https://www.adobe.com/express/](https://www.adobe.com/express/)

---

