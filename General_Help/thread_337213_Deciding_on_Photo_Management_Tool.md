---
title: "Deciding on Photo Management Tool"
date: 2007-01-12
forum: General Help
---

### Post by firebadger on 2007-01-12
I am really struggling to decide on a photo management tool.  Before I make the enormous effort of organising and categorising my enormous photo collection I want to be sure that I make the right choice.  
I'm keen to insulate myself from the risk of having to do the organisational task again (it's several days work) so ideally I'd like standards such as IPTC tags used to store this info.

_Wishlist_

Essential:
[LIST]
[*]Standards based, not tied in to a tool specific data format.
[*]Flexible Tagging.  I don't need lots of predefined categories that may not be appropriate for me and I'd like to be able to add categories that do matter to me.  Additional keyword based tagging would also be useful.
[*]A good interface for tagging my images.  This is a big job, so I want it made as pleasant as possible.
[*]Fairly good searching capability.
[*]Virtual Collections based on the meta data.
[*]"Open With" capability to GIMP
[/LIST]

Preferred:
[LIST]
[*]Photos remain in situ
[*]Some sort of version control to link edits to the original file.  Or some sort of clever approach to this.
[/LIST]

Not Required:
[LIST]
[*]I couldn't care less about editing (rotation perhaps only exception), web publishing or any other tools not directly related to managing and viewing the collection in this piece of software.  I'd rather lose the clutter.
[/LIST]

_Current Eval: First Impressions_
[LIST]
[*]GThumb - Non-standard metadata storage.  
[*]F-Spot is too cluttered and gimicky and is too buggy.  Non-standard metadata storage.  
[*]Picasa cluttered, gimicky, proprietary and slow.
[*]Bluemarine - I like what it looks to offer, but I can't get it to run and the development seems to be happening at a snails pace.  Having said that, it has enormous potential.
[*]imgSeek - Doesn't write IPTC, seems a bit buggy and I had a lot of trouble trying to manage multiple files at once.
[*]KPhotoAlbum - Non-standard metadata storage.
[*]Mapivi - not tried yet, but looks a real candidate.
[/LIST]


Any thoughts anybody?

---

### Post by Oki on 2007-01-12
First off all; here is a very good thread about photo and graphic related programs: [http://ubuntuforums.org/showthread.php?t=293798](http://ubuntuforums.org/showthread.php?t=293798)

When it comes for tagging there are those stupid programs that makes a database, and the good ones that tags within the picture – where it belongs. Do never use the first ones!! 

Some programs that stores the tags in the metadata:

Latest version of digikam; [http://www.digikam.org/](http://www.digikam.org/) 
“Tags, Rating, Date and Time, Comments, Photographers ID, and Copyrights are stored in EXIF and/or IPTC metadata tags embedded in pictures.”
This applications also looks good to.

jBrout: [http://jbrout.python-hosting.com/](http://jbrout.python-hosting.com/)
Stores the data as IPTC keywords. Very good search functions (take a look at the demo). The interface is good, but it dosnt look so good.  [http://idea.zanestate.edu/archives/2005/11/photo-organizing-in-linux/](http://idea.zanestate.edu/archives/2005/11/photo-organizing-in-linux/)

ExifTagger:
[http://www.gnomefiles.org/app.php?soft_id=1859](http://www.gnomefiles.org/app.php?soft_id=1859)
[http://dague.org/ExifTagger](http://dague.org/ExifTagger)
Still young, but looks good. Think this one is less good for many photos. 

Mapivi: 
[http://mapivi.sourceforge.net/mapivi.shtml](http://mapivi.sourceforge.net/mapivi.shtml)

Picasa2
Dont like it myself!

---

### Post by firebadger on 2007-01-13
Thanks for your thoughts, I've looked at all 4 of those and I think I'm veering towards mapivi just now.
Which one did you go with and do you have any regrets?

---

### Post by Oki on 2007-01-14
As long as the program do save the info in the metadata, then you cant go wrong. Meaning; if you dont like the program any more then just change – the data will still be within the picture (and not in a stupid database) – thats the hole point. 

Perhaps you could tag some pictures with the ones you think looks good, open the picture and check that the data is (really) stored where you want it.

I like both Mapivi and jBrout, have not tried the others. 


“I couldn't care less about editing”: Can I ask why?

---

### Post by firebadger on 2007-01-14
I would prefer an application that concentrated on providing the collection managment features as well as possible.  The other bells and whistles such as red eye reduction can come later and actually, my preference would be to leave them out and keep the interface clean.  When I want to edit an image, I'll open it with the GIMP.

---

### Post by Oki on 2007-01-14
Ok, that sounds valid. But when a program can do as you want, then I dont mind using it even though it can do much more, like digikam. 

And my suggestion; dont use Gimp for your photos – take a look at the link I give you – there is a lot of other and much better programs for Linux when it comes to photo than Gimp. 

If you are going to make large prints, you want to edit them in 16 bit mode witch Gimp cant (yet).


Have fun:-D

---

### Post by Marsolin on 2007-01-15
My favorite photo manager is [digiKam]("http://linuxappfinder.com/package/digikam").  You need to make sure to have version 0.9 though, because its the first one that saves metadata to the individual images and not to its own database.

Since switching to it I tagged all of my photos and find that it is really easy to filter or search based on them.

digiKam supports all of the essential features you listed. The only one I'm not sure about that you listed as preferred is version control.

---

### Post by firebadger on 2007-01-15
Is there really a widely held belief that GIMP isn't appropriate for editing photos?  If so what alternative would you recommend?  Can you notice the difference between 8 bit and 16 bit images anyway?

I just had another look at digikam and it seems to have moved on a lot recently.  I think I will give it a trial.  I can come up with some sort of versioning process using tags I suppose.  I'll update this thread with my thoughts later.

---

### Post by dabl on 2007-01-15
I'm lurking and very interested to hear your results with Digikam, Firebadger.  I have a large photo organizing and management task ahead of me one of these days when retirement provides some time.  Thanks for sharing!  :)

---

### Post by firebadger on 2007-01-15
I installed the 0.9 version as recommended.  It's not available from the standard repositories, but you can get it by adding..
```
deb http://www.mpe.mpg.de/~ach/kubuntu/edgy ./
deb-src http://www.mpe.mpg.de/~ach/kubuntu/edgy ./
```
to your sources.list file.

I've been playing around with it for a couple of hours and I really like it.  It does everything I need although it does have a few little interface niggles, but they are only annoying to start with and after you get to know them they are easy to work around.  In fact, I've pretty much decided to commit to this tool already.

One thing I haven't figured out yet that you'd think would be trivial is how to zoom in to the image I'm viewing to examine portions of it at full resolution.  No doubt I'll figure it out soon and kick myself, but in the meantime any hints from anybody would be much appreciated.

---

### Post by Oki on 2007-01-15
In the link I gave you I wrote:
“GIMP is great software, but is often compared to PS – witch I think is a bit unfair. People often complain that Gimp can’t work in 16 bits, don’t have actions, don’t support colour management and  are not user friendly. I have red that this will be fixed in later updates ([http://en.wikipedia.org/wiki/GEGL)](http://en.wikipedia.org/wiki/GEGL)). “

Gimp can only work in 8bits, and yes, there is a different to 16 bits witch other Linux programs can. Perhaps not for smaler prints, or less editing, but when you are doing more then you can see it – or bigger prints.

To zoom press the icon with a magnifier. After that you can use the middle key on the mouse to move the picture, or the + - to zoom more in or out. 

Thanks for the links:-)

---

### Post by firebadger on 2007-01-15
Still can't get zooming to work.  When in view mode, clicking on the magnifying glass with the plus sign doesn't appear to do anything and the tool tip for the button reads "Increase Thumbnail Size".  When you then return to the Album mode, you notice the thumbnails have increased in size.  It seems that this must be a bug where these buttons aren't changing their behaviour to suit the View mode.

---

### Post by Marsolin on 2007-01-15
> **firebadger said:**
> Still can't get zooming to work.  When in view mode, clicking on the magnifying glass with the plus sign doesn't appear to do anything and the tool tip for the button reads "Increase Thumbnail Size".  When you then return to the Album mode, you notice the thumbnails have increased in size.  It seems that this must be a bug where these buttons aren't changing their behaviour to suit the View mode.

If you click on a thumbnail it should launch the Image Editor/Viewer.  By default it does a fit to screen and has the zoom in and out buttons grayed out.  If you click the Zoom AutoFit button to the right of them it will exit that mode and switch to displaying the image at its native resolution.  I hope that works for you.

---

### Post by firebadger on 2007-01-16
Thanks, that's a good workaround for now, but I'm sure that it should be possible in the view mode too.  I entered a bug [http://bugs.kde.org/show_bug.cgi?id=140131](http://bugs.kde.org/show_bug.cgi?id=140131)

---

### Post by jkroto on 2007-01-27
> **Marsolin said:**
> My favorite photo manager is [digiKam]("http://linuxappfinder.com/package/digikam").  You need to make sure to have version 0.9 though, because its the first one that saves metadata to the individual images and not to its own database.

Since switching to it I tagged all of my photos and find that it is really easy to filter or search based on them.

digiKam supports all of the essential features you listed. The only one I'm not sure about that you listed as preferred is version control.

I notice that digikam 0.9 still creates it's own digikam3.db file when I first use it.  Do you know what needs to be done to make sure the tags get written to the metadata and that a loss of the .db won't lose the data?

---

### Post by Marsolin on 2007-01-27
> **jkroto said:**
> I notice that digikam 0.9 still creates it's own digikam3.db file when I first use it.  Do you know what needs to be done to make sure the tags get written to the metadata and that a loss of the .db won't lose the data?

It creates the database still for speed, but the tags get written to the file as well. To confirm, check the pictures metadata using right siderbar.

---

### Post by jkroto on 2007-01-29
> **Marsolin said:**
> It creates the database still for speed, but the tags get written to the file as well. To confirm, check the pictures metadata using right siderbar.

Thanks for the info.  I have a fair number of pics that I have never organized and I would like to try to get it right on the first pass.

Also, do you have any tips or hints on what types of tags you use or how you use them.

---

### Post by mechanic on 2007-01-29
> **dabl said:**
>  I have a large photo organizing and management task ahead of me one of these days when retirement provides some time.  Thanks for sharing!  :)

Someone else with the mistaken belief that retirement brings leisure!

Regds, m.

---

### Post by Marsolin on 2007-01-29
> **jkroto said:**
> Thanks for the info.  I have a fair number of pics that I have never organized and I would like to try to get it right on the first pass.

Also, do you have any tips or hints on what types of tags you use or how you use them.

In order to keep the number of tags manageable and as useful as possible I limit them to people. I have all of my photos tagged with whomever appears in them so I can easily find pictures of my son, or him with his mom, etc.

If I want to add information about the location, what the photo is of, etc., I use the comments field. I find that this makes it easy to search and add new info.

---

### Post by jkroto on 2007-01-29
> **Marsolin said:**
> In order to keep the number of tags manageable and as useful as possible I limit them to people. I have all of my photos tagged with whomever appears in them so I can easily find pictures of my son, or him with his mom, etc.

If I want to add information about the location, what the photo is of, etc., I use the comments field. I find that this makes it easy to search and add new info.

Thanks again for the tips.
I was going along the same lines but with 5 brothers and sisters, me makes 6, plus the offspring of them total 13 at the moment, I'm trying to find a way to keep the tags to a minimum.

---

### Post by pjmckeown on 2007-04-04
Does Mapivi support Canon Camera Raw, and if not, are there other recommendations for RAW files, just organizing, I edit elsewhere.

Regards,

Patrick

---

### Post by Scunizi on 2007-04-09
It looks like digicam is KDE based.  Is that true?  If so how do I compile it for Gnome?  Also I've struggled trying to get mapivi working even after reading multiple threads.  Any suggestions?  Dapper user here.

---

### Post by Marsolin on 2007-04-09
> **Scunizi said:**
> It looks like digicam is KDE based.  Is that true?  If so how do I compile it for Gnome?  Also I've struggled trying to get mapivi working even after reading multiple threads.  Any suggestions?  Dapper user here.

You should be able to install it from the repositories. If the Dapper repositories don't have the version that you want there is a Digikam repo that you can add.

---

### Post by Martin-Herrmann on 2007-04-16
> **pjmckeown said:**
> Does Mapivi support Canon Camera Raw, and if not, are there other recommendations for RAW files, just organizing, I edit elsewhere.

Regards,

Patrick

No, Mapivi currently supports just one picture format: JPEG.

Regards
       Martin

---

### Post by Martin-Herrmann on 2007-04-16
> **Scunizi said:**
> Also I've struggled trying to get mapivi working even after reading multiple threads.  Any suggestions?  Dapper user here.

I need some more information for that:
Is Perl installed? Is Perl/Tk installed? Are the needed Perl modules installed (see [Requirements]("http://mapivi.sourceforge.net/mapivi.shtml#requirements"))?

Any error messages, when mapivi is started (in a shell)?

Regards
          Martin

---

### Post by adriantry on 2007-04-16
> **firebadger said:**
> Still can't get zooming to work.

I usually use ctrl + scroll wheel. This zooms in a lot of programs, including 
digiKam.

Adrian

---

