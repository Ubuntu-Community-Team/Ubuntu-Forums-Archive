---
title: "OpenOffice fonts suddenly a LOT better.  What happened?"
date: 2006-12-15
forum: General Help
---

### Post by jrjazzman on 2006-12-15
Just launched the OO.o spreadsheet app and instantly realized that something was different.  I could actually read the text without squinting.  The fonts are suddenly much better.  Does anyone know what caused this?  I don't remember seeing an update.

---

### Post by Suzan on 2006-12-15
Wow! Yes, indeed! The fonts are suddenly much better!!!!!!!!!!!!!!!!!!!!!!!!

Yipiiiieh!

I don't know, which update caused this. It wasn't an OpenOffice update I think. Fontconfig maybe... ??

---

### Post by l.tambiah on 2006-12-17
Wish I could say the same :-(...

---

### Post by Suzan on 2006-12-17
This is, how my OpenOffice looks like:

[[IMG]http://img510.imageshack.us/img510/1796/openofficean7.th.png[/IMG]](http://img510.imageshack.us/my.php?image=openofficean7.png)

It's very good!

---

### Post by l.tambiah on 2006-12-17
See Attachment for mine:-

---

### Post by Suzan on 2006-12-17
Have you tried it with font-aliasing in OpenOffice?

---

### Post by kolinab on 2006-12-17
Um, pretty sure I read somewhere this week that a new version of OpenOffice was released, and even that it improved fonts. When you download automatic updates in Ubuntu does it update all your applications too?

---

### Post by Littleweseth on 2006-12-17
Hear this ma' brothers - you have been shown *the glory* of apt-get update; apt-get upgrade. Hallelujah! :p

(Yes, when ubuntu auto-updates it updates every package on your system by default.)

---

### Post by jrjazzman on 2006-12-17
> **kolinab said:**
> Um, pretty sure I read somewhere this week that a new version of OpenOffice was released, and even that it improved fonts. When you download automatic updates in Ubuntu does it update all your applications too?

It should, unless you've disabled the main repositories.  

Note: the current OO.o fonts are not great, probably not even good.  They're just not as atrocious as they were.

---

### Post by Suzan on 2006-12-18
Ubuntu will only update to the new OO-version if it's

- a security update
- if the packages are backported


And the fonts of MY OpenOffice are great now. See my screenshot above. And I have still the Edgy OpenOffice 2.0.4! I have NOT updated to the new version.

---

### Post by steve.horsley on 2006-12-18
l.tambiah : I think you need to install the package msttcorefonts, which is in the repositories. This is a set of Microsift fonts, including Times New Roman. Alternatively, stick with fonts that you have actually got installed on your machine. Personally, I think Times New Roman looks cramped, and I prefer Bitstream Charter.

---

### Post by noynac on 2006-12-18
> **kolinab said:**
> Um, pretty sure I read somewhere this week that a new version of OpenOffice was released, and even that it improved fonts. When you download automatic updates in Ubuntu does it update all your applications too?

OpenOffice 2.1 was released on 12/12/06. The release notes are at:

[http://development.openoffice.org/releases/2.1.0.html](http://development.openoffice.org/releases/2.1.0.html)

There is no reference in the release notes to fonts, but there are many unspecified bug fixes, and I hope they take care of the font problem.

---

### Post by jrjazzman on 2006-12-18
Coming from the Windows world, I don't think I've ever used a program that didn't use the system's font rendering facilities.  I would be interested to know why OO.o doesn't follow the same pattern.  This is another area that contributes to the problem of linux apps and desktops looking disparate and uncoordinated.

---

### Post by xopher on 2006-12-18
> **l.tambiah said:**
> See Attachment for mine:-

Man that's really awful :/

---

### Post by FluffyElmo on 2006-12-18
I think if you enable all the repositories it will update all your packages but out of the box it's just security fixes. I saw an OO update a few days ago so that may have been what improved the fonts, though as an Abiword aficionado I never noticed... ;)

---

### Post by noynac on 2006-12-18
I just enabled the "proposed updates" repository, and then checked for updates. It does show a whole bunch of updates to OpenOffice. 

Do most people install proposed updates? Overall, my install is working well, and I don't want to mess with things.

---

### Post by jrjazzman on 2006-12-18
> **noynac said:**
> I just enabled the "proposed updates" repository, and then checked for updates. It does show a whole bunch of updates to OpenOffice. 

Do most people install proposed updates? Overall, my install is working well, and I don't want to mess with things.

I do not use the proposed updates repository.

---

### Post by l.tambiah on 2006-12-18
> **Suzan said:**
> Have you tried it with font-aliasing in OpenOffice?

Yes this is what makes it look like yours ;-). However I use to use the microsoft truetype fonts like verdana in the gnome font settings and set it to monochrome which gives a truetype font experience. In openoffice you would turn font-aliasing off and it would appear with the same true type fonts as the GNOME desktop. 

I think as well people have different preferences too, it seems most like font-aliasing text whilst I didn't. I have my gnome settings now on lcd and have enabled the font-aliasing in open office, but I'm gradually begin to like font-aliasing, over my truetype fonts I use to use with monochrome rendering.


Attachemtn shows rendering with lcd and medium hinting with font-aliasing on in open office.

---

### Post by FluffyElmo on 2006-12-18
I don't use the proposed repository, but I do have backports and a couple of other repositories enabled. I suspect this is where my OO updates came from. My sources.list is based on the ubuntu-guide which you may want to try first, I'd say it's been pretty well tested by now.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

The proposed repository, from what I understand is something of a beta test area. If I wanted a more recent version of a package I'd grab it from there before going elsewhere. I'd say if you use it the overall risk to your system is pretty small. A couple of thoughts on using cutting edge repositories though...

1. You can enable the repository, install *selected* updates (like OpenOffice), then disable the repository and refresh. This will let you have the most current versions of certain packages while minimizing the risk to your overall install.

2. If any new packages causes problems, you can revert to the previous version. In Synaptic you can select the package and on the menu go to *Package->Force Version* to select any of the previous versions.

Hope some of this rambling helps, Good Luck!

---

### Post by FluffyElmo on 2006-12-18
l.tambiah, if you use an LCD you may want to look around for some of the posts on matching your dpi settings more closely with the dpi of your LCD display. Most people do it for prettier anti-aliased fonts, and every how-to has a slightly different set of settings depending on their preferences. I think matching the dpi might show more of an improvement with non-aliased fonts?

I did this with Dapper when I moved from a CRT to a LCD and it helped a lot. Edgy looked decent out of the box so I didn't bother and have no idea what instructions I used. Maybe it's not even necessary anymore but if you're tweaking font settings that's where I'd start...

---

### Post by noynac on 2006-12-18
Thanks FluffyElmo for the response. I know little about the repositories and how they work. The information you provided is helpful.

---

### Post by FluffyElmo on 2006-12-19
No problem, glad it was useful. I spent some time with pre-release builds a while back and learned a lot of stuff the hard way:)

---

### Post by rev_b on 2006-12-19
OpenOffice 2.1 fixed the ugly font problem. Now I can use fonts without antialiasing and they are rendered properly. Thank you OOo developers!

[[IMG]http://img72.imageshack.us/img72/6253/ffnz3.th.png[/IMG]](http://img72.imageshack.us/my.php?image=ffnz3.png)

---

### Post by jrjazzman on 2006-12-19
> **rev_b said:**
> OpenOffice 2.1 fixed the ugly font problem. Now I can use fonts without antialiasing and they are rendered properly. Thank you OOo developers!

[[IMG]http://img72.imageshack.us/img72/6253/ffnz3.th.png[/IMG]](http://img72.imageshack.us/my.php?image=ffnz3.png)

Is it just my browser, or are these screenshots REALLY small?

---

### Post by kolinab on 2006-12-19
Yup, they're small. Just 493 X 349. But big enough that I got the idea!

---

### Post by jrjazzman on 2006-12-19
> **kolinab said:**
> Yup, they're small. Just 493 X 349. But big enough that I got the idea!

Something weird is going on..the bottom of the image says 493x349, but the png is actually 150x121, and that is how FF is rendering it on my machine.

---

### Post by rev_b on 2006-12-19
> **jrjazzman said:**
> Is it just my browser, or are these screenshots REALLY small?

err... actually the image is a link for a full size picture in imageshack, just to save bandwidth. Isn't it clickable in your browser?

[IMG]http://img72.imageshack.us/img72/6253/ffnz3.png[/IMG]

Here is the full image, anyway.

---

### Post by jrjazzman on 2006-12-19
> **rev_b said:**
> err... actually the image is a link for a full size picture in imageshack, just to save bandwidth. Isn't it clickable in your browser?

[IMG]http://img72.imageshack.us/img72/6253/ffnz3.png[/IMG]

Here is the full image, anyway.

that's better.. the original image is not clickable for me.  The link is directly to the small png, no HTML or anything that would provide a link.

---

### Post by rev_b on 2006-12-19
Strange. Works fine in FF 2.0.

---

### Post by jrjazzman on 2006-12-19
> **rev_b said:**
> Strange. Works fine in FF 2.0.

That is bizarre.  

I've done a little bit of HTML in my days.  How could a URL to a PNG image contain a link?

---

### Post by rev_b on 2006-12-19
> **jrjazzman said:**
> That is bizarre.  

I've done a little bit of HTML in my days.  How could a URL to a PNG image contain a link?

This is the code 

[PHP][[IMG]http://img72.imageshack.us/img72/6253/ffnz3.th.png[/IMG]](http://img72.imageshack.us/my.php?image=ffnz3.png)[/PHP]

I don't know, but it displays fine here as a clickable link in both firefox and opera 9...

---

### Post by jrjazzman on 2006-12-19
Fixed it.. I went to QuickLinks > Edit Options and enabled the "Show images" option.  Prior to this, I only saw a URL, which linked to the small image.  I wonder how many people who don't  have this option turned on are wondering why these images are small.

---

### Post by opioid on 2006-12-28
What a coinkydink--I came here to research my f'ed up beyond compare OO fonts, and lo, and behold; they are fixed! I have such good timing :)

---

### Post by Treviño on 2006-12-29
Check this for OpenOffice 2.1 patched for better font support: [http://ubuntuforums.org/showthread.php?p=1945924](http://ubuntuforums.org/showthread.php?p=1945924)

Please, let me know what you think about it...

BYE! ;)

---

### Post by fragos on 2006-12-30
Check out System-> Preferences-> Font.  The selected font renedering has a big impact on appearance.  Pick the one that looks best to you.  The font you're actually using impacts rendering as well.  I've grown fond of DejaVu Sans Condensed for my default font.

---

