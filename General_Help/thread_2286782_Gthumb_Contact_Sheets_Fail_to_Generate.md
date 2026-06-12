---
title: "Gthumb Contact Sheets Fail to Generate"
date: 2015-07-14
forum: General Help
---

### Post by Dennis N on 2015-07-14
I tried gthumb's contact sheet option for the first time. (Share > Contact Sheet > *options*). Of the two types of contact sheet, "Contact Sheet" (which should include captions) and "Image Wall" (images only) only the "Image Wall" is working for me. For the regular contact sheet with captions, the Save button does nothing. I wonder if I am doing something wrong here, or is it just broken? Does anyone know how to successfully generate the captioned "Contact Sheet" with gthumb? How do you get it to work?

Gthumb version is 3.2.7

---

### Post by QDR06VV9 on 2015-07-14
> **Dennis N said:**
> I tried gthumb's contact sheet option for the first time. (Share > Contact Sheet > *options*). Of the two types of contact sheet, "Contact Sheet" (which should include captions) and "Image Wall" (images only) only the "Image Wall" is working for me. For the regular contact sheet with captions, the Save button does nothing. I wonder if I am doing something wrong here, or is it just broken? Does anyone know how to successfully generate the captioned "Contact Sheet" with gthumb? How do you get it to work?

Gthumb version is 3.2.7
I have also tried with gthumb with no success and have kind of abandoned my efforts.
A few years back someone in the forum had a script, Oh Yes here it is [http://ubuntuforums.org/showthread.php?t=1720341](http://ubuntuforums.org/showthread.php?t=1720341)
And I remember Cheesemill liked Darktable but I have no first hand knowledge of either, so you might have to figure out if you can make one work
 to your liking.
Darktable how to [http://www.darktable.org/install/#ubuntu](http://www.darktable.org/install/#ubuntu)
Just trying to help out.
Rgards

---

### Post by Dennis N on 2015-07-14
Thanks for confirming my suspicion that the 'Contact Sheet' extension is broken. A flaw in an otherwise excellent program. Thanks for mentioning some other possible options too.

---

### Post by QDR06VV9 on 2015-07-15
Ok I got it to work 'Contact Sheet'..
I did not do anything fancy just real basic stuff for this.
What I did was point gthumb to a folder>My Pictures had a folder with a bunch of wallpapers in it.
Then I select all> control + a
Then I went to File(in gthumb top left) Down to Export To( options are some web based options Picasa flicker etc But there is Contact Sheet> & Contact Sheet & Image Wall
Then I chose Contact Sheet, an editor pops up went to the General tab, Then I Chose a theme for the contact sheet( Back to the General tab),  Toward the bottom where it Shows Theme> off to right of that is a  Plus button & a Pencil & a  X. Pick the Plus button  add the  theme, then save. After you save the theme you can now edit with the  pencil (or edit option). I also made the size in the layout tab to 256.
I Don't like the option to put all images on a single page(Yuck)
 Destination my home directory, file name 'contact sheet'


After you edit to your liking press save now, Wait for the magic and enjoy.(LOL)
Image Wall just worked.
Contact Sheet, add as many images you want on a page.(I think i went 9 images and 10 columns) 
I included Screenshots in the order of my instructions(If I dare to call it that):D
I will have to play around with it, but it looks like there is a lot of options there!(Meta, Naming, Size,yada yada)
Cheers

---

### Post by Dennis N on 2015-07-15
Great discovery! Thanks for investigating this further. I will try out your method later today and report back here. Stay tuned.

---

### Post by Dennis N on 2015-07-15
Hi runrickus,

Based on your information, I discovered that the "Share" Button on the toolbar also works. The key is defining and saving a theme, so that you have at least one in the theme box. That was the missing piece!  So when I then select the images from the gthumb window, the "Save" button is now active.

**Observations on Contact Sheets**:
Gthumb Version 3.2.8

Tests Done:
_Images from digital camera_, uniform 1600x1200, worked great on _all_ tests (including when a few are portrait): 
Tested up to 80 images in rows of 8 on single sheet and that works very well.
Multiple pages also work: e.g., 80 images, rows of 8, 56 per page.

_Other non-camera images of varying sizes_ can fail (but there is a workaround).
I tested with some computer wallpaper of mixed sizes and types.
_Single page_: works with limited number of images: 14 images worked, but 40 images failed.
_Multiple pages_: multiple page output with images of mixed dimensions and types often failed, e.g. 40 images, 20 per page, 5 cols: failed after first page. (2 images attached show this failure: pages 1 and 2 of output.)
_Workaround_: Failures can be fixed with the "squared" box checked in layout tab next to "size". Tested this "squared" size option workaround with multiple pages and up to 90 total images. It always worked and produced correct output.

_Summary_: All things considered, a valuable tool. Thanks again for your help.

Images: 1) first page of output is correct; 2) second page of output is bad. Fixed with workaround (not shown).

---

### Post by QDR06VV9 on 2015-07-16
> **Dennis N said:**
> Hi runrickus,

Based on your information, I discovered that the "Share" Button on the toolbar also works. The key is defining and saving a theme, so that you have at least one in the theme box. That was the missing piece!  So when I then select the images from the gthumb window, the "Save" button is now active.


_Summary_: All things considered, a valuable tool. Thanks again for your help.

Images: 1) first page of output is correct; 2) second page of output is bad. Fixed with workaround (not shown).
Nice! Glad you got the share option to work I always had failures when using that route even using the squared option?(I have a ppa for gthumb dev) 
Might have to remove the ppa and check again.
Your input of your experience with gthumb is as always informative.(worded well)
I also agree that gthumb is a valuable asset. And Love the Mustang picture still one of my Favs.
Kind Regards

---

