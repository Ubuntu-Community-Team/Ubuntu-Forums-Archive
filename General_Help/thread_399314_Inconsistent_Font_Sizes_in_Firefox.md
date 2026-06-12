---
title: "Inconsistent Font Sizes in Firefox?"
date: 2007-04-02
forum: General Help
---

### Post by UnrealMiniMe on 2007-04-02
Hiya,
I'm sorry to make my first post here a request for help, but I'm a total Linux noob :o)
I've been running the AMD64 version of Edgy for a few days and I've gotten just about everything up and running (bmc43xx support, nVidia drivers, multimedia codecs, 32-bit Firefox with Flash, Java, etc.) except for one thing:

*Reasonable-sized fonts.*

You see, from the moment I installed Ubuntu, the 64-bit version of Firefox had a problem where some fonts were normal-sized (with respect to how pages looked in Firefox under Windows XP), some were super-giganto-sized, and some were even a bit smaller than normal.  Since some pages have huge fonts and some have small fonts, I can't just reduce or increase font size across the board.  Outside of Firefox, my fonts look fine to me (though I'm not a font expert or anything).
I was hoping the problem might be specific to my version of Firefox, but I was proven wrong when I installed the 32-bit version for AMD64:  It has the same issue.

I've installed msttcorefonts and gsfonts-x11, though they (at least the msttcorefonts) originally did not seem to be showing up in my list of fonts.  After reinstalling them a couple of times, they're now showing up, but I still have the font size issues.

I've attached a pair of screenshots to illustrate my problem.  In one shot, I've shown the page I created this post on.  As you can see, the fonts are generally normal-sized, if a bit small.  In the next shot, I've shown the results of Google search.  The fonts here are of simply gargantuan proportions.  The fonts are this large on a good deal of sites, and even worse, there are some sites that have a mixture of very large and very small font sizes (in the Google shot, note that my search query and the Search button have much smaller fonts than the rest of the page).
Note:  Sorry the images are scaled down...they were originally 1280x1024, but apparently Photobucket won't host images larger than 1024x768 for free.  Hopefully what I've shown is enough to give the general idea, though.

This is a real pain, so hopefully someone can help me out!  I've tried searching these forums, but I have not yet found the solution to my problem.  Since I had this problem right out of the box, I'm hoping that it's a common problem that I just overlooked the solution to.  If anyone can help me out, I'd greatly appreciate it!

[IMG]http://img.photobucket.com/albums/v258/Mini-Me/NormalFonts.png[/IMG]
[IMG]http://img.photobucket.com/albums/v258/Mini-Me/HugeFonts.png[/IMG]

---

### Post by chewearn on 2007-04-02
Not sure if you have tried the Firefox fonts settings.  It is located in
Menu > Edit > Preferences > Content

You can set the default font and size; or click the "Advanced..." button.  In my case,  most websites' font are too small, so I forced it to a larger font size, by setting the "minimum font size".  The default "monospace" font is also quite ugly, so I changed that to New Courier.  In the worst case, you can uncheck "Allow pages to choosing their own fonts".

---

### Post by UnrealMiniMe on 2007-04-02
Wow, this is going to sound really stupid, but it did work to some degree...I had tried it before, but it wasn't changing anything whatsoever (however, that was *before* msttcorefonts were showing up - I should have known to try it from preferences again after the Microsoft fonts began showing up).

If I change the font size with Ctrl-Mouse wheel, everything on the page changes, but if I change it in Preferences, I can now make the large fonts smaller while keeping the normal-sized fonts the same.  That's really...odd.  I guess it only "applies" to some fonts, perhaps.

Something's still wrong, though - changing the size of the font now works, but changing the actual name of the font still doesn't affect anything (I can even change to Webdings without any visible difference).  Also, I can't seem to find the "right" font size.  In OpenOffice.org Writer, changing the fonts works perfectly, and 12-point fonts look correct (or at the very least, I don't remember them being differently sized in Windows).  In Firefox, despite the font size slider now working, 12-point is quite small (the closest I can get to "normal" looking is 16-point, but it still doesn't look right).  Any other suggestions?

Thanks

---

### Post by chewearn on 2007-04-02
It depends on how the web page is coded.

Another thing to try is changing the Gnome fonts preference in Top Panel Menu > System > Preferences > Font (if you are running Ubuntu instead of Kubuntu or Xubuntu).

Here you can set fonts across most applications, but you have to restart Firefox to see the effect in your webpages.

If you click on the "Details..." button, the DPI / resolution setting will allow you to tweak the font size with respect to your screen size/resolution ratio.

---

### Post by UnrealMiniMe on 2007-04-02
Thanks, but I've played around with that, too...unfortunately, it increases/decreases the DPI universally, which is not what I want:  Fonts are "normal" everywhere outside of Firefox.  They're perfect in OO.org, Thunderbird, GNOME panels, etc.  It's only Firefox where the sizes are "off" (I am, however, able to change font names if I don't let sites pick their own, so that part of the problem is resolved).  It's certainly much better now that I can change the size (no more gargantuan fonts), but it'd be nice to get things "standardized."

---

### Post by kerry_s on 2007-04-02
Your not understanding, you need to make the "size" the same as the "minimum size" and uncheck "allow pages to choose..." That way it will only use 1 size font for all web pages. I also recommend you have a text zoom extension( [https://addons.mozilla.org/en-US/firefox/search?q=zoom&status=4](https://addons.mozilla.org/en-US/firefox/search?q=zoom&status=4) ).

---

### Post by UnrealMiniMe on 2007-04-02
I just did as you suggested:  I unchecked the box about allowing pages to choose their own fonts and I set both the size and minimum size to 12 (then I tried a few other sizes).

Unfortunately, the fonts are still a different size than in OpenOffice.org...to test, I copied some text from Firefox to OpenOffice.org Writer and compared how big each program says the font is, and they report different sizes (though OO.org actually does resize the font when it's pasted...sometimes).  For instance, OO.org reports that Firefox 12-pt is 10-pt (hard for me to tell if any actual resizing is going on, but they're looking pretty similar).  Firefox 15-pt and 16-pt both come out as 12-pt in OO.org (I'm pretty sure that OO.org slightly resizes the Firefox 16-pt font to make it OO.org 12-pt, and that Firefox 15-pt font = OO.org 12-pt).  However, you have indeed fixed my major problem, though:  By setting the font size and minimum font size to be 15, pages look as they should!  Thanks :)

I'm still confused why Firefox seems to use a different font size scale than OO.org, though...is it supposed to?  I was under the impression that across all GNOME applications, fonts that are 10-pt, 12-pt, 16-pt, etc. would be of the same size (since there's a single DPI setting for all of GNOME).  Are the different applications somehow using different DPI settings?
I suppose I'm kind of just nitpicking at this point:  Pages now look as they should (well, after rechecking the box about letting pages pick their own fonts)...I'm now just confused why Firefox uses a different font point-size scale than OO.org, I guess.

Thanks again :)

P.S.  What exactly does the text zoom extension do?  There aren't any reviews of it or anything, so I'm not sure how it differs from typical Firefox text zooming (ctrl-mousewheel)

---

### Post by chewearn on 2007-04-02
Actually, I don't have this problem of inconsistent font size between Firefox and OpenOffice.  Only problem I have was fonts were generally too small.

---

### Post by UnrealMiniMe on 2007-04-02
Yeah, I didn't really expect that it was normal...I wonder what the problem is?

---

### Post by Eduardo Serra on 2007-04-03
I have the same problem with some pages, try gamespot and tell me if letters are bigger for you to

---

### Post by kerry_s on 2007-04-03
> P.S. What exactly does the text zoom extension do? There aren't any reviews of it or anything, so I'm not sure how it differs from typical Firefox text zooming

It does the samething, you just get the convince of icons. :)

What if firefox is the right size and open office is the wrong size? :)

---

### Post by UnrealMiniMe on 2007-04-03
> **Eduardo Serra said:**
> I have the same problem with some pages, try gamespot and tell me if letters are bigger for you to

Well, after setting all font sizes to be the same (regular and minimum sizes), Gamespot looks about right to me - there's probably something subtly wrong (since I'm still fiddling with settings and trying to figure out "exact" fonts), but there's nothing glaring at the moment like mile-high fonts or anything.  My biggest problem, the huge fonts on some pages, was fixed by setting the font size and minimum font size in Firefox to a lower number (the font size defaulted to something like 22 or 26, and there was no minimum font size).  I'm still having a hard time finding the "right" font size, though...it's hard to pinpoint the right settings for font, minimum font, zoom, etc.

As for whether OO.org's or Firefox's fonts are correct, kerry_s:  Good question! ;)  Nevertheless, OO.org's idea of 12-pt seems much more in line with what I was used to in Windows, so I'm assuming it's using a more "standard" scale than [my possibly slightly broken version of] Firefox is.  When I say "standard" scale, I should add that I'm aware that Microsoft's idea of DPI is not exactly "correct" (since, for example, they keep 12-pt fonts the same size *in pixels* across all displays, rather than the same size in inches).  However, my main concern at this point is being able to view webpages as their designers intended - since most people use Windows, it's usually safe to assume that's the standard font setup that web designers have in mind.

Thanks again :)

P.S. (Again)  I tried installing the Text Zoom extension, but it's only for a very old version of Firefox...therefore, I can never really be sure what level of zoom I'm at. :/

---

### Post by kerry_s on 2007-04-03
I'm using this 1 for zoom and address bar clear button> [https://addons.mozilla.org/en-US/firefox/addon/2671](https://addons.mozilla.org/en-US/firefox/addon/2671)
I use this one because it has 2 things i use, so i don't need 2 extensions.

I also use this 1 on another machine> [https://addons.mozilla.org/en-US/firefox/addon/2540](https://addons.mozilla.org/en-US/firefox/addon/2540)
I use this 1 because another extension already provides a clear button so all i needed was the zoom. I like how you can just right click any button to reset the zoom.

---

### Post by UnrealMiniMe on 2007-04-05
I ended up using the more basic one, and it's working great :-)  Thanks!

---

### Post by tommie74 on 2007-05-05
I found this somewhere in this forum:

The problem is with Firefox, not the system. Here is the easiest fix:

type about:config in the address bar [enter]
find layout.css.dpi (type dpi in the filter)
change the value to '0' -- this forces firefox to use system font settings
restart firefox

No need to mess with other configuration files.
That was for Firefox 2.0 and up.

For Firefox 1.5, just go to Preferences > Content > Fonts & Colors
Go to the advanced dialog box, and tell it to use system font settings.

---

### Post by tommie74 on 2007-05-05
Found this somewhere in this forum:

The problem is with Firefox, not the system. Here is the easiest fix:

type about:config in the address bar [enter]
find layout.css.dpi (type dpi in the filter)
change the value to '0' -- this forces firefox to use system font settings
restart firefox

No need to mess with other configuration files.
That was for Firefox 2.0 and up.

For Firefox 1.5, just go to Preferences > Content > Fonts & Colors
Go to the advanced dialog box, and tell it to use system font settings.

---

### Post by barcode on 2008-04-27
I have this problem too since installing Hardy Heron. Never had it with previous release and it only happens when I used the nvidia drivers. Really, really annoying. Tried all the solutions here but non work.

---

### Post by andylawrence on 2008-04-28
I have the same issue and it seems to be related to widescreen resolutions (mine is 1680x1050).  I fixed the font issues in Firefox by opening about:config and changing layout.css.dpi to 96.  I imagine if you change this value to whatever your system wide default is set to in System->Preferences->Appearance->Fonts->Details it will make your fonts look right in Firefox.

---

### Post by chewearn on 2008-04-28
For system wide dpi setting, which affects font size, I have since learnt of this method:

1. Measure your display horizontal and vertical dimensions in millimeter.

2. Add the following in xorg.conf "Monitor" section:

 	```

 	DisplaySize <horz> <vert>
``` 
where <horz> and <vert> are the dimensions measure in 1.

Note: I haven't tried this in hardy, hope it works.

---

