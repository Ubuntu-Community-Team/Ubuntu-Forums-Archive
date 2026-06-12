---
title: "I just want to burn an Audio CD, dangit"
date: 2005-06-10
forum: General Help
---

### Post by Nick Post on 2005-06-10
I can burn data CD, DVD, on both my sony and my NEC.  NEC goes to 32x and I have no problem, but only if burning data.

But Mp3->audio CD is causing buffer problems.  Why?  And worst of all, Gnomebaker takes 500 years to convert mp3 to audio before making a coaster for me, rather quickly though.  Graveman, same.  Don't know how to make Nautilus do audio cd.

I'm trading music with a guy at work, and he's more a CD in the car guy.  Doesn't even have a computer at home.  So, giving him a data cd with a couple of albums doesn't work.  At this point, I'm just mooching off him, which I don't like.

I'll log in at home and get all the specs, yadda yadda.  I'm new to linux, and when stuff like this comes up, it just makes me tempted back to the dark side.

NooooooOOOOOOOOooooo!

---

### Post by Alexander Kirillov on 2005-06-10
[QUOTE=Nick Post]I can burn data CD, DVD, on both my sony and my NEC.  NEC goes to 32x and I have no problem, but only if burning data.

But Mp3->audio CD is causing buffer problems.  Why?  And worst of all, Gnomebaker takes 500 years to convert mp3 to audio before making a coaster for me, rather quickly though.  Graveman, same.  Don't know how to make Nautilus do audio cd.

I'm trading music with a guy at work, and he's more a CD in the car guy.  Doesn't even have a computer at home.  So, giving him a data cd with a couple of albums doesn't work.  At this point, I'm just mooching off him, which I don't like.

I'll log in at home and get all the specs, yadda yadda.  I'm new to linux, and when stuff like this comes up, it just makes me tempted back to the dark side.

NooooooOOOOOOOOooooo![/QUOTE]
 Nautilus does not support making audio CDs - yet. 
I do not know why gnomebaker and graveman give you this much toruble, but as a workaround, try k3b. Yes, it is a KDE app - but it works in GNOME, too.

---

### Post by Burgundavia on 2005-06-10
For Breezy, we get to look forward to Serpentine

Corey

---

### Post by tread on 2005-06-10
>  Gnomebaker takes 500 years to convert mp3 to audio 

I had the same problem, I looked at top and mpg123 (which I think is the program gnomebaker uses to convert mp3 to wav) was taking just 2% .. even though the nice value was 0! Hmm .. maybe this is a bug to be filed though I wonder .. should it be an mpg123 bug or gnomebaker?

---

### Post by Joeb on 2005-06-10
Searching the forum, there seems to be a lot of people having problems with Gnomebaker, although, some have had luck with the older version 0.3 version.  It seems like the solution for most people has been to install graveman, k3b or xcdroast.

---

### Post by Nick Post on 2005-06-10
[QUOTE=Joeb]Searching the forum, there seems to be a lot of people having problems with Gnomebaker, although, some have had luck with the older version 0.3 version.  It seems like the solution for most people has been to install graveman, k3b or xcdroast.[/QUOTE]

Thanks everyone.  I think I'll start with K3b.  You never know, I might collect all six.

If this keeps up, I'll need to buy more CDs sooner rather than later.

---

### Post by brickbat on 2005-06-10
I had the same problem...installed K3b....Rockin.

I think its more mature.  KDE apps are really good.  If only they could tone down the eye candy and work more on the bugs and they would have a really killer environment.

ciao
bb

---

### Post by Joeb on 2005-06-10
[QUOTE=Nick Post]Thanks everyone.  I think I'll start with K3b.  You never know, I might collect all six.

If this keeps up, I'll need to buy more CDs sooner rather than later.[/QUOTE]


While you are trying to resolve this burning problem, you might also want to tell whatever package you are using not to delete the iso image it creates.  That way, if it does bomb out, you only need to burn the image to disk and not wait while it creates the image each time.

---

### Post by Nick Post on 2005-06-10
Dang, Joeb, you're my hero.  I need to check to see where it's putting the ISOs.

---

### Post by Nick Post on 2005-06-11
K3b worked great.  A 45 min audio cd in 6 min (looks like my processor is holding my 32x NEC back to around 10x).

Now, that said, is there any reason with K3b working so well for me to keep Gnomebaker or Graveman?  I'm probably going to just remove them.

---

### Post by Joeb on 2005-06-11
[QUOTE=Nick Post]K3b worked great.  A 45 min audio cd in 6 min (looks like my processor is holding my 32x NEC back to around 10x).

Now, that said, is there any reason with K3b working so well for me to keep Gnomebaker or Graveman?  I'm probably going to just remove them.[/QUOTE]


You could safely remove Gnomebaker and Graveman.  If in doing so, it might say something about ubuntu-desktop is dependent on it and will be removed, too.  That's fine if it is.  Ubuntu-desktop is a meta-package of all of the packages that are installed with the base install (allows for easy update of the packages by the developers), but it isn't required for a user system.

As for your burn speed being 10x, that could be your cpu, it could also be the media and possibly whether dma transfers aren't enabled for the drive (although they probably are if you're getting 10x).

---

