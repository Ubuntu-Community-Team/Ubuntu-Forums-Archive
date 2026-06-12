---
title: "Hardy won't boot at all"
date: 2008-05-28
forum: General Help
---

### Post by varaonaid on 2008-05-28
Hello!

I've search around the forums and can't find an answer to my issue.  I've just done a clean install of Ubuntu Hardy Heron (8.04) using the alternate install cd.  I completely wiped an existing windows drive and reformatted from scratch for Ubuntu.

When it starts to boot up it hangs at "running local boot scripts" and won't continue.  I finally managed to get it to a prompt using ctrl>alt>f1 and attempted the "startx" command and the response I got was basically that there is a problem with "X".  No valid modes are found, Screen(s) found but none have a usable configuration, fatal server error: no screens found.

So that's it.  I'm stuck and can't use my Ubuntu install at all.  Does anyone have any suggestions?  I'd *really* appreciate any help!

Thanks so much in advance.
Rae

---

### Post by werries on 2008-05-28
did you try booting a livecd first?
did you check the disk for defaults?

i say, check disk for defaults, if none, do a reinstall.
if there are, burn a new disk with a slower burn speed.

---

### Post by varaonaid on 2008-05-28
Yes, tried booting a live cd first, had the same problem and assumed it was having trouble because it wasn't "installed", which is why I went ahead and proceeded with the actual install.

I burned both the live cd and the alternate cd at 4x (the slowest my drive supports), I checked the MD5sums, and also ran the disk check utility when I started up each of the cd's.  So, I really don't think a new download and burn will solve this one, as much as I wish it would.  It's a problem with the screen and "x", I think.

Thanks for trying.  Any other thoughts, anyone?

---

### Post by werries on 2008-05-28
I have another thought, actually. What version of ubuntu?
because when I was installing ubuntu gutsy onto a friends computer, it had the same problem. X just wouldn't work at all.
When hardy came out though...it worked like a charm. no problems whatsoever.

---

### Post by varaonaid on 2008-05-28
> **varaonaid said:**
> Hello!

I've just done a clean install of Ubuntu Hardy Heron (8.04) using the alternate install cd.  I completely wiped an existing windows drive and reformatted from scratch for Ubuntu.


Yeah, as you can see from my original post, it's a fully clean install of Hardy with a clean partition set.  :(  Wish it was that simple...

---

### Post by inportb on 2008-05-28
Hm... sounds like a graphics issue. What video chipset do you have?

---

### Post by varaonaid on 2008-05-28
I'm embarrassed to say I'm not 100% sure (this isn't a primary use laptop, and it isn't mine) but I'm pretty confident after digging around a little online that it's a Via Unichrome chipset.  The model of laptop is Averatec 3225hs, if that helps any.  

But I agree, seems like it has to be the video issue.  Any assistance would be hugely appreciated!!

---

### Post by varaonaid on 2008-05-28
For what it's worth, I downloaded and burned a copy of Gutsy and it had problems booting into the live cd as well... bummer.  I guess it's a graphics issue.  I just really don't want to go an a new distro hunt, though.  So, if you think there are ways to fix it, that would be super.

---

### Post by werries on 2008-05-28
well since you can get into the terminal. try updating with
```
sudo apt-get update
```
and maybe with some googling, you can figure out what your driver is and download it.

---

### Post by varaonaid on 2008-06-02
Unfortunately, still haven't gotten it to work with no idea, other than problems with the video, what to do for it.  Strangely, this problem seems to be isolated to ubuntu because several other distros boot fine, so I don't believe that it's a hardware problem.  I wanted to stick with ubuntu since it's what I'm using on my other computer but it doesn't look like I'm going to be able to :(  If anyone has any other suggestions, please let me know.

Thanks again.

---

