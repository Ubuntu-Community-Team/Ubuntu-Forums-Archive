---
title: "Openoffice + Gutsy = ugly fonts"
date: 2008-02-06
forum: General Help
---

### Post by pestilence on 2008-02-06
Hello All,
I recently installed Ubuntu Gutsy, everything is great, except one small part...OpenOffice...I have horrible fonts...to be more presice here is a screenshot:
[[IMG]http://img03.picoodle.com/img/img03/4/2/6/t_openofficem_a484c3e.png[/IMG]](http://www.picoodle.com/view.php?img=/4/2/6/f_openofficem_a484c3e.png&srv=img03)

---

### Post by hyperair on 2008-02-06
This thing's been annoying me for a long time now, such that I totally gave up. OOo doesn't seem to like supporting Ubuntu's font rendering for some reason or other.

---

### Post by anaconda on 2008-02-06
what is wrong with that picture? doesn't look that bad.

You know that you can install fonts to OO.. eg. msfonts if that is what you want

---

### Post by danwood76 on 2008-02-06
That font looks nice :)

But as said the msfonts can be installed, the ubuntu-restricted-extras package has the MS fonts if you need them.

regards,
Danny

---

### Post by chewit on 2008-02-06
if you download wine & wine doors, you can install some Windows fonts onto open office

---

### Post by pestilence on 2008-02-06
msfonts are installed, but antialiasing looks horrible in Open Office, (it is enabled in Open Office, I also tryed disabling...but things became even uglier! )

---

### Post by hyperair on 2008-02-06
Agreed. The problem is with font hinting. Font hinting in OOo always uses grayscale hinting despite of what is set.

---

### Post by z0mbie on 2008-02-18
Anyway to fix the rendering?

Try this, it helps a bit by upgrading to the latest 2.3: [http://www.stchman.com/install_oo.html](http://www.stchman.com/install_oo.html)

---

### Post by cybergalvez on 2008-02-18
> **z0mbie said:**
> Anyway to fix the rendering?

Try this, it helps a bit by upgrading to the latest 2.3: [http://www.stchman.com/install_oo.html](http://www.stchman.com/install_oo.html)

Great website, I just followed it and switched out my ubuntu OOo for the official one, however, if your on a 64 bit build you will have to use force the install and install a 32 bit java, but other then that no real problems other then quickstarter - I just can't get that to work yet
Jose

---

### Post by melat0nin on 2008-04-18
Any ideas is OOo is going to catch up with the rest of Gnome?  The font rendering is pretty horrible.  I have my Gutsy machine looking silky smooth, on the desktop, but OOo really screws with that.  Since it's an app you by definition spend a lot of time looking at, it's important that it looks nice!

Why doesn't OOo obey the system-wide font rules/settings? :(

Here's an example of how bad it looks compared to my system-wide fonts:

[[IMG]http://img389.imageshack.us/img389/6338/ooofontszj4.th.png[/IMG]](http://img389.imageshack.us/my.php?image=ooofontszj4.png)

---

### Post by calc on 2008-04-18
The Ubuntu version in Hardy does font hinting properly after I added a patch to fix this issue. As far as I know the upstream version on Gutsy should look just as bad as the Ubuntu version in Gutsy so upgrading to it probably will not help any.

---

### Post by hyperair on 2008-04-18
I'm using OpenOffice.org in Ubuntu Hardy and honestly don't see any difference. The fonts all have grayscale (and lousy) hinting, while my settings are to have subpixel hinting.

---

### Post by melat0nin on 2008-04-18
> **calc said:**
> The Ubuntu version in Hardy does font hinting properly after I added a patch to fix this issue. As far as I know the upstream version on Gutsy should look just as bad as the Ubuntu version in Gutsy so upgrading to it probably will not help any.

I'm running 2.3, I noticed a howto somewhere on upgrading to 2.4 (evidently 2.4 isn't in the Gutsy repos because I haven't had an update for it).  Do you mean I shouldn't bother trying to upgrade to 2.4?  Should I just wait until Hardy?

---

### Post by calc on 2008-04-18
> **hyperair said:**
> I'm using OpenOffice.org in Ubuntu Hardy and honestly don't see any difference. The fonts all have grayscale (and lousy) hinting, while my settings are to have subpixel hinting.

I'm not sure what is different about your system but it definitely works properly here and for everyone I have asked after I added the patch. Here is a screenshot of what it looks like for me.

[[IMG]http://people.ubuntu.com/~ccheney/hardy-openoffice-font-hinting.png[/IMG]]("http://people.ubuntu.com/~ccheney/hardy-openoffice-font-hinting.png")

---

### Post by calc on 2008-04-18
> **melat0nin said:**
> I'm running 2.3, I noticed a howto somewhere on upgrading to 2.4 (evidently 2.4 isn't in the Gutsy repos because I haven't had an update for it).  Do you mean I shouldn't bother trying to upgrade to 2.4?  Should I just wait until Hardy?

Yes, upgrading to the upstream 2.4 will lose any and all Ubuntu specific patches including the fix for font hinting. So if you are interested in proper font hinting then upgrading to Hardy is the only way you will get that, unless the patch makes it into upstream's 3.0 release later this year.

---

### Post by Bachstudies on 2008-04-29
What is the patch that you installed? Care to share?

---

### Post by Bachstudies on 2008-04-29
> **calc said:**
> The Ubuntu version in Hardy does font hinting properly after I added a patch to fix this issue. 

Would you care to share this patch? My only other option appears to be installing the official OO 2.4 from the website. If the patch is already included in the Hardy version, some of my fonts still look terrible.

---

### Post by calc on 2008-04-29
> **Bachstudies said:**
> Would you care to share this patch? My only other option appears to be installing the official OO 2.4 from the website. If the patch is already included in the Hardy version, some of my fonts still look terrible.

Yes, the patch is already in Hardy, please attach a screenshot (png) showing the bad fonts. It could be the font you are trying to use wasn't created properly or there may be some sort of bug.

---

### Post by Bachstudies on 2008-04-29
> **calc said:**
> Yes, the patch is already in Hardy, please attach a screenshot (png) showing the bad fonts. It could be the font you are trying to use wasn't created properly or there may be some sort of bug.

Actually just been messing around with options in System - preferences - appearance - fonts. I turned sub-pixel smoothing on and under details I put hinting to none. For some reasons Openoffice looks perfect now. So thanks for your patch ;) Any explanations as to why doing this corrected the ugly rendering? I do have a laptop but I have not noticed this font problem in other apps.

As a side issue, when i just went into appearances - fonts again, all four radio buttons look active under smoothing! Weird...

---

### Post by calc on 2008-04-29
> **Bachstudies said:**
> Actually just been messing around with options in System - preferences - appearance - fonts. I turned sub-pixel smoothing on and under details I put hinting to none. For some reasons Openoffice looks perfect now. So thanks for your patch ;) Any explanations as to why doing this corrected the ugly rendering? I do have a laptop but I have not noticed this font problem in other apps.

As a side issue, when i just went into appearances - fonts again, all four radio buttons look active under smoothing! Weird...

OOo should work with any setting in Appearance -> Fonts, but you have to restart OOo before it takes effect. I think there is a patch to fix this for 3.0.

---

