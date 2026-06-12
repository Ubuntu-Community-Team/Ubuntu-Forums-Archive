---
title: "Firefox 3 Horrible Font Rendering"
date: 2008-01-12
forum: General Help
---

### Post by SpookyET on 2008-01-12
I know that Firefox 3 uses Gecko 1.9 which uses Cairo for rendering.

I do not know if there is something disabled in these Firefox 3 builds, but the font rendering compared to Firefox 2 is horrible. Nor, can I test Firefox 3 on other platforms since I have fully switched to Ubuntu.

The anti-aliasing is bad. Truthfully, it looks like sIFR (for the web designers who know what sIFR is) replaced headings using Flash v6, which leads me to believe that Cairo is the problem since it uses vectors.

Needless to say, the screenshots have a high resolution. Make sure that the zoom level is at 100% before you compare.

For those that have kin eyes and notice the name of the browser in the titlebar, [Swiftfox]("http://getswiftfox.com/") is an optimised Firefox build available for many CPUs. It is not different than the official Firefox build in terms of features. Firefox 3 Beta 2 has the exact same font rendering.

Swiftfox provide deb files. Meaning, you can have Firefox 2, and Firefox 3 Pre-Beta 3 working side by side. But, you cannot run them at the same time with the same profile.

To run Firefox 2 and Swiftfox at the same time, do, "firefox -no-remote -P 'someotherprofilethandefault'" in a terminal window. Or, do "firefox -profilemanger" first if you do not have a profile. Make sure no other instances are opened.

[Firefox 2 100%]("http://bayimg.com/MAieLaAbo")
[Firefox 3 100%]("http://bayimg.com/maieMaabo")

[Firefox 2 110%]("http://bayimg.com/mAiePaaBo")
[Firefox 3 110%]("http://bayimg.com/NAIEaaABO")

[Firefox 2 120%]("http://bayimg.com/NaIEdAABO")
[Firefox 3 120%]("http://bayimg.com/nAieEAABO")

[Firefox 2 Ubuntu Forums 100%]("http://bayimg.com/nAIeFAabo")
[Firefox 3 Ubuntu Forums 100%]("http://bayimg.com/NAIEGaabO")

[Firefox 2 Ubuntu Forums Thread 100%]("http://bayimg.com/naIeHaabo")
[Firefox 3 Ubuntu Forums Thread 100%]("http://bayimg.com/naieIAAbo")

EDIT: The site converted my PNGs to JPEGs creating artificats. I have uploaded the original files into a zip for those who want to diff them in Photoshop.
[ORIGINAL FILES]("http://www.2shared.com/file/2710300/9e54895f/Firefox_2_vs_Firefox_3_Font_Rendering.html")

PS: The first generation page zooming of Firefox 3 is pretty crappy. There are many artifacts created, and I'm not talking about image pixelation. If you zoom [Digg]("http://digg.com"), you'll start seeing black borders around image elements.

---

### Post by sicofante on 2008-02-16
I agree. I just tried the latest FF 3 beta 2 and I have the same issues with fonts.

May I ask what makes Firefox and OpenOffice override system font rendering and doing things their own (worse) way? Isn't it weird that the two most popular open source apps behave so badly under Linux?

---

### Post by PmDematagoda on 2008-02-16
> **sicofante said:**
> I agree. I just tried the latest FF 3 beta 2 and I have the same issues with fonts.

May I ask what makes Firefox and OpenOffice override system font rendering and doing things their own (worse) way? Isn't it weird that the two most popular open source apps behave so badly under Linux?

Why are you using Firefox Beta 2 when Beta 3 has been released? That pretty much explains your problem.

Also, I do not see any problem with OpenOffice concerning font rendering, could you please post a screenshot.

---

### Post by SpookyET on 2008-02-16
> **sicofante said:**
> I agree. I just tried the latest FF 3 beta 2 and I have the same issues with fonts.

May I ask what makes Firefox and OpenOffice override system font rendering and doing things their own (worse) way? Isn't it weird that the two most popular open source apps behave so badly under Linux?

OpenOffice is just stupid. Firefox was compiled wrong. Take a look at my last post [http://forums.mozillazine.org/viewtopic.php?t=619955](http://forums.mozillazine.org/viewtopic.php?t=619955)

The LCD patches might have patent problems. So mozilla compiles firefox against stock cairo. Ubuntu must make sure that they enable system cairo when they compile firefox.

I'm running FF3 Beta 3 compiled by me. It looks awesome.

---

### Post by Arathon on 2008-02-18
How can I get a version of cairo >= 1.5.2 so that I can build Firefox myself?  Ubuntu's repos only have 1.4.x....  =(

---

### Post by Skrible on 2008-05-08
"The reason you have no subpixel hinting is that Fx3 uses the in-tree cairo library, which has no LCD-filtering patches applied. You, or your distro's package maintainer, will have to compile it with following option in .mozconfig: -enable-system-cairo. You'll also need to use this command: export LDFLAGS='-lX11 -lXrender' "

[http://forums.mozillazine.org/viewtopic.php?t=602280&postdays=0&postorder=asc&postsperpage=15&start=15](http://forums.mozillazine.org/viewtopic.php?t=602280&postdays=0&postorder=asc&postsperpage=15&start=15)

---

