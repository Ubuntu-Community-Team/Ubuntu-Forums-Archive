---
title: "Start Up Manager...Is there one?"
date: 2008-05-26
forum: General Help
---

### Post by davidkyn on 2008-05-26
Hi,
Having problems with things like Awn Manager not starting up on start up as it should, and I would also like to get others to go on startup like Cario Clock ect....

I was hoping I could gain controll back of Awn Manager to get it going like it should and just play with other programs by using such a Program Like:
Start up Manager......Is there such a thing in Ubuntu?????

---

### Post by VMC on 2008-05-26
> **davidkyn said:**
> Hi,
Having problems with things like Awn Manager not starting up on start up as it should, and I would also like to get others to go on startup like Cario Clock ect....

I was hoping I could gain controll back of Awn Manager to get it going like it should and just play with other programs by using such a Program Like:
Start up Manager......Is there such a thing in Ubuntu?????

I think your talking about SUM. Here's alink that helps explain it:
[http://ubuntusoftware.info/sum.html](http://ubuntusoftware.info/sum.html)

---

### Post by davidkyn on 2008-05-27
AWESOME!!!!!!!
Someone else was able to help me out in the multimedia sections explaining how to use the system/preferences/sessions app & it did the trick for me.

But WOW...I just skimmed that link and hading straight back there...I though only windows could do that.

Later man...I'm going to be working on that for the rest of the day:

lol Cheers..........Hey man...Actually do you know where I can find an install guide...Im not that smart with Ubuntu yet?
I just did a quick search and ca'nt find much in here on it...which I find hard to beleive...i will search again.  I'd love to change my log in screen and all that.  Need a guide to install though...I'm not up with all the terminology just yet, but getting there.....thanks again

---

### Post by sweeneytodd on 2008-05-27
replying to wrong thread

---

### Post by madelaki on 2008-05-27
The startup screen is called GDM. You can download GDMs from [http://www.gnome-look.org](http://www.gnome-look.org), and install them from System > Preferences > Welcome (or Login, can't remember) Screen. About installing, I strongly suggest you download .debs for now, they are like Windows's .exes. You can find most of them at [http://www.getdeb.net](http://www.getdeb.net)

---

### Post by jocko on 2008-05-27
> **madelaki said:**
> The startup screen is called GDM. You can download GDMs from [http://www.gnome-look.org](http://www.gnome-look.org), and install them from System > Preferences > Welcome (or Login, can't remember) Screen. About installing, I strongly suggest you download .debs for now, they are like Windows's .exes. You can find most of them at [http://www.getdeb.net](http://www.getdeb.net)
This has nothing to do with the question that was asked in this thread.

---

### Post by madelaki on 2008-05-27
> This has nothing to do with the question that was asked in this thread.

> lol Cheers..........Hey man...Actually do you know where I can find an install guide...Im not that smart with Ubuntu yet?
I just did a quick search and ca'nt find much in here on it...which I find hard to beleive...i will search again. I'd love to change my log in screen and all that. Need a guide to install though...I'm not up with all the terminology just yet, but getting there.....thanks again
Last edited by davidkyn; 22 Minutes Ago at 01:53 AM. 

Read the whole thread.

---

### Post by jocko on 2008-05-27
> **madelaki said:**
> Read the whole thread.

Sorry. I missed that post. I just thought you assumed that startup manager = login manager, but I assumed wrong.

---

### Post by davidkyn on 2008-05-27
Hey guys,
No Dramas...Peace.....I installed start up manager through add/remove.  I am finding it very dificult to open the correct file types though.  somthing like a .os or somthing like that?

I am using Login Window for the login screens, but can't get SUM (start up manager to work with the very few files I can find.

I know I should read more carefully and I try my best...sometime I just have trouble processing what I am reading is all, which is my problem, no one else....It's kewl...sorry if I miss read anyone here.

Thanks guys...I got login screens going well and the backgrond color now too (Thanks)...I guess I will eventually work out the splash screens too...might have to do it manually...although I am having trouble with gimp actually saving the file as .xpm.gz...It's a shame the .os files are hard to find and open in SUM.

I better shut now...I really do complicate things:)
Thanks to all for replying!
PSSS........do you have to drag and drop files like in loging window app (took me ages to work that one out!)

---

### Post by angry_johnnie on 2008-05-28
To change the login window:

Download the theme you want to use, ([www.gnome-look.org](www.gnome-look.org) has tons of them). It will be a compressed file (either .tar.gz or .tar.bz2).

Don't extract it, just put it in some folder.

Then, go to:

**System > Administration > Login Window > Local**

click on the **add** button.

Navigate to the directory where you saved the compressed file.

Select it, and click on the **install** button.

You'll then be able to use it.

You could also do this in a terminal:

```
sudo apt-get install gdm-themes
```

It will install a few extra themes you'll be able to use.




Startupmanager handles GRUB and USplash.

GRUB splashimages are kept in /boot/grub/splashimages.
If you haven't installed any images, and are just seeing the usual, white-on-black, GRUB menu, then that directory doesn't even exist yet. :-)

Some images are available in the repositories, too.

Do this in a terminal.

```
sudo apt-get install grub-splashimages
```

Then you can open startupmanager and choose one of them.
GRUB background images are compressed files, too.  You could also get a few more of them from gnome-look.  The format would be image.xpm.gz.  You can install them with startupmanager.  You could create them, but Hardy (8.04) doesn't quite like imagemagick (at least, in my computer), and grub splash images have to be converted to 14 colors and a resolution of 640x480.


USplash is the image and progress bar you see while the computer is booting.  The format would be something.so.  There's some available at gnome-look, and they can also be installed with startupmanager.



As for the autostarted programs, go to

**System > Preferences > Sessions**


The first tab is called **Startup Programs**

Click on **New**

For awn, the entry would look like this:

[B]Name:  AWN (or whatever you want)

Command:  avant-window-navigator.[/B]

It's the same for anything else you want to have automatically started.

---

### Post by davidkyn on 2008-05-28
Thanks angry-johny,
I just cut and paste all that in my special docs on setting up and will let you know how I go...big night after setting up a ubuntu files server..yawns...zzzzzzzzzzzz

I appreciate your well written reply and have updated as you recommended.  catch ya tomorrow dude :)

---

