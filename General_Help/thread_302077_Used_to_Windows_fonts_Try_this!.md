---
title: "Used to Windows fonts? Try this!"
date: 2006-11-18
forum: General Help
---

### Post by skwillz on 2006-11-18
Alright I hope I'm not rehashing common knowledge here, but since I had to figure this out on my own-- even after reading many threads here, I think it's worth telling.

I'm used to the crisp look of fonts in Windows. I love Linux but it always bugged me that the fonts looked so funky (I'm a big visual/GUI type person). The trick is pretty simple.

-Install the msttcorefonts package.
-Go to System -> Preferences -> Fonts
-Select Monochrome for font rendering.

You'll probably need to adjust all your system fonts to be something from the msttcorefonts library.

Restart may be necessary if you want to apply the changes to Firefox, OpenOffice, etc..

Looks great, huh? Well, at least it looks nice if you're used to the fonts in Windows. :KS

---

### Post by skwillz on 2006-11-18
BTW, here is a screenshot in case you are curious to see how it looks before changing anything.

[IMG]http://img179.imageshack.us/img179/8672/smoothfontslq3.jpg[/IMG]

The only thing I am noticing is that bold text is not properly smoothed out, but I'll work around it.

---

### Post by Dale61 on 2006-11-18
To each their own, I suppose, but why use the monochrome setting?  I use the best shapes setting for a far more cleaner, crisper look, and it makes it easier to read.

---

### Post by skwillz on 2006-11-18
The monochrome setting is the only one that will allow the microsoft truetype  fonts to look 'correct'. 

I think the other 3 settings (best shapes, subpixel, etc) are designed to work in tandem with the default fonts that come with Ubuntu.

I actually find this way to be much easier to read since I used Windows for such a long time (and still do).

---

### Post by philippe_carlo on 2006-11-18
Ever seen Mac fonts? Now. that's something I would sign up for!

---

### Post by skwillz on 2006-11-18
Funny, I always get the feeling that the look of Mac fonts is similar to the look of fonts on Linux, only they like to make everything BOLDER.

But how was this relevant to the thread?

---

### Post by yopnono on 2006-11-18
or you can use this guide

[http://ubuntuforums.org/showthread.php?t=208396&highlight=ms+font](http://ubuntuforums.org/showthread.php?t=208396&highlight=ms+font)

---

### Post by ferd on 2006-11-18
Yes, I installed the fonts. While I was experimenting with the look of the new fonts, swiftfox crashed. I can no longer start swiftfox or firefox although I have uninstalled and reinstalled both through synaptic. Reinstallation of Ubuntu-Kubuntu is not an option.](*,)

---

### Post by yopnono on 2006-11-18
Open the fx swiftfox through the terminal

---

### Post by IYY on 2006-11-18
> **yopnono said:**
> or you can use this guide

[http://ubuntuforums.org/showthread.php?t=208396&highlight=ms+font](http://ubuntuforums.org/showthread.php?t=208396&highlight=ms+font)

I like this guide best. Still, it's difficult to say which fonts look better, the Windows (sharp) or Ubuntu (blurry) ones. I guess it also depends on monitor size/resolution.

---

### Post by Grog140 on 2006-11-18
What are the names of the fonts?

---

### Post by strabes on 2006-11-18
I use the mac fonts. They look better than window$'s or ubuntu's default fonts imho.  [http://www.supriyadisw.net/2006/04/mac-font-on-dapper-drake](http://www.supriyadisw.net/2006/04/mac-font-on-dapper-drake)

---

### Post by ferd on 2006-11-18
> **yopnono said:**
> Open the fx swiftfox through the terminal

/usr/lib/swiftfox/run-mozilla.sh: line 131:  5315 Floating point exception"$prog" ${1+"$@"}
/opt/firefox/run-mozilla.sh: line 131:  5343 Floating point exception"$prog" ${1+"$@"}
This is what I get when I try to run swiftfox and firefox through the terminal.

---

### Post by yopnono on 2006-11-18
No you should not run the run-mozilla file. Use the firefox file.

 /opt/firefox/./firefox
same with swiftfox

---

### Post by ferd on 2006-11-18
> **yopnono said:**
> No you should not run the run-mozilla file. Use the firefox file.

 /opt/firefox/./firefox
same with swiftfox

/opt/firefox/./run-mozilla.sh: line 131:  6286 Floating point exception"$prog" ${1+"$@"}

Seems to be much the same. Thanks for trying. Opera is OK.

---

### Post by ferd on 2006-11-19
> **ferd said:**
> /opt/firefox/./run-mozilla.sh: line 131:  6286 Floating point exception"$prog" ${1+"$@"}

Seems to be much the same. Thanks for trying. Opera is OK.

The next day. I removed all residual package parts of swiftfox and then reinstalled swiftfox using synaptic and FEBE to solve my problem.:)

---

### Post by bailout on 2006-11-19
skwills, I was going to offer to marry you when I read your post but I can't find the 'monochrome' setting in kubuntu :( I have always disliked font rendering in Linux and would love to get mine as clear as windows.

In KDE font control there is only 'use anti-aliasing for fonts' checkbox. This has a configure button which allows the anti-aliasing settings:

'Exclude range'
'use subpixel rendering' - RGB/BGR/verticalRGB/vertical BGR
'hinting style' - none/slight/medium/full

There is also a force dpi setting.

But no monochrome setting that I can see. If anyone knows how to set this in kde I would love to know.

---

### Post by skwillz on 2006-11-20
bailout--

I think you can disable anti aliasing to get the same effect.

---

