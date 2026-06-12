---
title: "nautilus doesn't change icons entirely"
date: 2008-04-24
forum: General Help
---

### Post by newb1e on 2008-04-24
Just upgraded to Hardy RC:popcorn: and give nautilus another try (I was using PCManFM before)
I used [this instruction]("http://ubuntuforums.org/showpost.php?p=4441760&postcount=2") to use PCManFM and after the upgrade, I reversed the process to use nautilus.

But now nautilus now doesn't display the icons properly!
[IMG]http://img174.imageshack.us/img174/4043/screenshotwn5.png[/IMG]
As you can see, the home, trash and tar files are ok, but the folder, partition and image icons are not right (for the Leopard theme)
I have tried several things:
-remove PCManFM.
-reinstall nautilus
-delete and reinstall leopard theme.

-->no effect

If I change to "Human" theme, all icons are ok. But when I use "Leopard", the folders come back to "gnome" icon.:confused:

what should I do?:(

---

### Post by NoobixCube on 2008-04-24
I've been having the same problem too since I started using the Hardy beta.  I can tell you it has nothing to do with PCManFM (I'd never even heard of that before I saw your post).  All the icons that came with the install are fine, but none that I've added display the right folder icon.  It just displays the Gnome default, as in your screen shot.

EDIT:  I just read in another thread that Gnome 2.22 changed the way icons are named.  This isn't an Ubuntu problem, but a Gnome one.  It will be up to theme makers to fix their icon packs.  I haven't tried yet, but I think this could be fixed by making symlinks with the new name that point to the old icon.  Or, you could just rename the icons yourself *-)

---

### Post by stansford on 2008-04-24
Hi,
Totally agree with you guys - this is MOST annoying. I updated to Hardy and upon installing my favourite icon set, the folder icons in Nautilus stayed that poxy grey colour!

Even if it's a Gnome thing, you'd have thought they would have tested this prior to release wouldn't you?? I've noticed that some sets work OK, so it just seems bad luck that the sets I want to work with don't.

Can anyone provide instructions on how to fix this please?
I'd be very grateful!

thanks

---

### Post by ryanhaigh on 2008-04-24
Maybe the icon sets don't conform to the tango icon naming specification (pretty sure thats what it is) used by ubuntu/nautilus, there is a package called icon-naming-utils or something that MAY be able to help although I have never used it.

---

### Post by newb1e on 2008-04-24
> I've been having the same problem too since I started using the Hardy beta. I can tell you it has nothing to do with PCManFM (I'd never even heard of that before I saw your post).
Thanks, I was not sure if it's pcman or not, threw it in just in case.

The icons are now good:D I did it the quick and dirty way: Look in the gnome folder (/usr/share/icons) to find the icons' names and compare them to your icons. A little laborious though, if you have many icons wrong. 

For example, the Computer icon is computer.svg in gnome/scalable/devices, copy an icon with the same name into your_icons_folder/scalable/devices (png is ok)

---

### Post by chrisccoulson on 2008-04-24
The icon naming in GNOME has changed slightly in 2.22, breaking some existing themes. You either need to wait for theme developers to catch up, or perhaps modify the theme yourself if you are confident enough to do so.

---

### Post by brinux on 2008-04-24
I'm having this issue too - some of the coolest looking icon sets don't completely work.

I tried using the "icon-naming-utils" (mentioned in ryanhaigh's post above) to convert the icon sets, but it appears that program needs to have the "make" file used to create the icon set in the first place before it will work. :(

I think what I'll start playing with next in comparing the icon sets that DO work with the ones that don't and then figure out what links (shortcuts) need to be made to get the broken ones to work.  A lot of work, but if that does the trick, I'll post how I did it here.

---

### Post by stansford on 2008-04-25
> **newb1e said:**
> Thanks, I was not sure if it's pcman or not, threw it in just in case.

The icons are now good:D I did it the quick and dirty way: Look in the gnome folder (/usr/share/icons) to find the icons' names and compare them to your icons. A little laborious though, if you have many icons wrong. 

For example, the Computer icon is computer.svg in gnome/scalable/devices, copy an icon with the same name into your_icons_folder/scalable/devices (png is ok)


Hey Newb1e, could you possibly provide a little more info on how to do this please? 
I want to change the icon used for folders in Nautilus (currently grey) to something better. How do I find out what this icon's called? Many thanks

---

### Post by chrisccoulson on 2008-04-25
A good starting point it [**_here_**]("http://standards.freedesktop.org/icon-naming-spec/icon-naming-spec-latest.html"). I recommend sym-linking icons with the correct names to the old icons as opposed to copying them, as the icon sets can get quite large.

I have modified a couple myself (both nuoveXT themes), and I've asked the original developer for permission to distribute them. I haven't had a reply yet. There's still a few icons not working yet which I need to figure out though

---

### Post by stansford on 2008-04-25
> **chrisccoulson said:**
> A good starting point it [**_here_**]("http://standards.freedesktop.org/icon-naming-spec/icon-naming-spec-latest.html"). I recommend sym-linking icons with the correct names to the old icons as opposed to copying them, as the icon sets can get quite large.

I have modified a couple myself (both nuoveXT themes), and I've asked the original developer for permission to distribute them. I haven't had a reply yet. There's still a few icons not working yet which I need to figure out though

Chris - thanks. I'll post back when I've had a chance to read this.

---

### Post by []Milo on 2008-04-26
Noobix,Chris, thanks. I've been having the same this has been annoying me all day now until i found this thread.  At least i understand where the problem is now.

---

### Post by chrisccoulson on 2008-04-26
Out of interest, which icon sets are you having trouble with? I've already updated quite a few sets (Both NuoveXT themes, Gartoon and all the black-white-2 themes from gnome-look.org)

---

### Post by stansford on 2008-04-28
> **chrisccoulson said:**
> Out of interest, which icon sets are you having trouble with? I've already updated quite a few sets (Both NuoveXT themes, Gartoon and all the black-white-2 themes from gnome-look.org)

Hi Chris,
I've read the spec at the link but I've got to say I'm not much further on.
First off which sets need changing? I did a clean hardy install yesterday and when I installed my icons sets via the appearance menu they were installed in /home/angus/.icons/<set-name>. 

Now on a clean install this .icons dir is emtpty, so obviously the default icons aren't here to start with.

Next I found that a lot of sets go in /usr/share/icons. So I went there and can see the GNOME set that seems to be the default along with a load of others...but even then what do you change???
There are so many files. Which icon(s) are the ones displayed when you view folders in Nautilus tree view that I would need to change?
Also different sets seem to have different hierachies of sub dirs under them. Which are vital and which aren't?
Next I tried replacing a few icons with the ones I want, but mine were .png and the ones to replace were .svg. Can I just copy them over or do they have to be the same file type?

I thought I'd made a break through and that an icon in /scalable/places called "folder.svg" looked a good candidate. However when I replaced this and rebooted the same old grey folder icon was still there.

I realise that I just don't know enough about how these sets work. I'm just fiddling in the dark really. Have you come across a 101 on how icon sets work anywhere. I'm getting very frustrated that I can't get rid of these poxy grey icons! Yes there are some sets that work, but they usually have purple, light blue or bright orange icons - yuk! 
I just want some yellow ones that look nice, I will admit that I did like the colours Windows explorer used!

One set I'd really like to get to work is called "Dropline-Etiquette" it's over at art.gnome.org. Another I really like is called "CrystalforGnome-KidsIcons".

Sorry this is such a long post, but I suppose I've done a lot trying to resolve this. Can you give me any tips on how to effectively amend these sets. I mean what are the key things to do?

any help appreciated.

---

### Post by chrisccoulson on 2008-04-28
I'll have a look at those sets when I get home this evening and see how much work it would be for me to update them for you.

---

### Post by stansford on 2008-04-28
> **chrisccoulson said:**
> I'll have a look at those sets when I get home this evening and see how much work it would be for me to update them for you.

Thanks chris, much appreciated. 
You might struggle to get the kids icons, it's also nearly 6mb in size. So perhaps just looks at the dropline set.

---

### Post by stansford on 2008-04-28
> **chrisccoulson said:**
> I'll have a look at those sets when I get home this evening and see how much work it would be for me to update them for you.

Chris, I've managed to fix this...at least for me.

Here's what I did:

I've done a clean Hardy install and then installed my two fav icon sets "dropline-etiquette" and CrystalforGnome-Kids.
Neither of these display the full set of icons anymore (they did in Gutsy). Some show the default Gnome grey icon set which is very annoying and so naff.

The icons I really wanted to change were the folder icons shown in Nautilus under tree view, but I guess once you get the principle right, and find out what the icons are called it will probably work for whatever icons you want to change. OK here's what I did:

1. Compare the folder structure of standard icon sets that come with Hardy as installed in /usr/share/icons/ with your favourite sets installed probably in /home/.icons/<fav icons set name>. I looked at the default set called "Gnome" and another set called "Crux" both of which work but have different structures.

You need to do this to find out what the differences are between the folder structure in the sets that work and yours that don't work.

I discovered that in the "dropline-etiquette" (art.gnome.org) set, the difference was that the default Gnome set under the folder "scalable" there was a "places" folder. My set didn't have this places folder, instead it had a "filesystems" folder.

So the first thing I did was rename the folder called "filesystems" to "places" under /home/angus/.icons/dlg-etiquette/scalable.

2. The next thing to do is edit the "index.theme" file found in /home/angus/.icons/dlg-etiquette folder and using find and replace change all occurrences of "filesystems" to "places".

3. The last thing to do is to go back to the /home/angus/.icons/dlg-etiquette/scalable/places folder and make sure there is an icon called "folder.svg" or "folder.png" depending on which type of icons your icon set uses. 

For me this last point was key. Obviously if you can find the name of the icon you want to replace then you can make sure your set has one with the right name in the right place. For me I needed an icon called "folder.svg" in the places folder.

Then reload the icon set and bingo - the old grey default folder icons in Nautilus were gone.

Now there is one other scenario worth covering and that is what to do if there is no "scalable" folder in your icon set.

My "kids" icon set was like this and that is where the "Crux" defualt theme I mentioned earlier comes in. It too has no scalable folder so if your set is like that and just has a number of folders with the different sizes of icons on eg 16x16, 32x32 etc then below each of these folders you should still find your hierarchy of folders with names like "places", "apps" etc. Again all I had to do was follow the steps above and replace the folders called "filesystems" with ones called "places". 

Unfortunately, I didn't know which sized icons were being used, so I just changed them all. It seems sense to do this, but it's more work though!

Then reload the set again and you should see the icons you want.

So there you are! Hope this works for you like it worked for me.

---

### Post by chrisccoulson on 2008-04-28
Unfortunately, that only fixes the folder icon I think though. There are many other icons in that set which are broken as well, and I think it might be quite a bit of work to fix

---

### Post by stansford on 2008-04-28
> **chrisccoulson said:**
> Unfortunately, that only fixes the folder icon I think though. There are many other icons in that set which are broken as well, and I think it might be quite a bit of work to fix

Quite possibly, although I also fixed my home folder shortcut icon in this way too.

I'm willing to approach it on a "need to fix" basis, so it will do for me now.

I know you could ask the developer to fix the icon sets, but I'm not sure if these two I use still have active developers.

Anyway, I've picked up some useful info on how these sets works, so I'm happy enough.

---

### Post by Melcar on 2008-04-28
Yeah, it's annoying.  I remember the same thing happening in Gutsy, but it got fixed a few updates down the road.  I expect the same to happen in Hardy.

---

