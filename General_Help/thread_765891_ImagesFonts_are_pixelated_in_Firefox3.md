---
title: "Images/Fonts are pixelated in Firefox3"
date: 2008-04-24
forum: General Help
---

### Post by nikaine on 2008-04-24
Hi, I hope this problem haven't been solved already since I did a search on this forum and firefox's forum, but couldn't find a solution.

I am having problems reading the fonts on the forums that I visit daily and the images that are posted on the forum are very pixelated. All the fonts are somehow in courier new.

I did installed my video card driver and the visual effects are working just fine on Ubuntu 8.04. 

And earlier, I was trying to go on citi.com to pay my bills, the site would load, but after a second it would just go blank. I get a glimpse of the site's layout, but it would flash into a blank white screen.

Please help!


[[IMG]http://img162.imageshack.us/img162/7007/picoy0.jpg[/IMG]](http://imageshack.us)
[[IMG]http://img222.imageshack.us/img222/2001/fontfd5.jpg[/IMG]](http://imageshack.us)

---

### Post by bluemax on 2008-05-24
I'm having this problem also in FIrefox 3 beta 5. Fonts look fine for me though, but images are all pixelated. It's as if every image was half-resolution and Firefox stretched each one. Doesn't happen in any other program.

---

### Post by ghindo on 2008-05-25
I'm using Firefox 3 Beta 5 on Ubuntu 8.04 and I'm getting a similar problem to the second poster's.  Fonts are fine, but images are pixelated as all hell.  I was having this problem on Windows, as well.  

Is this a widespread problem?  Can we report this as a bug?

**Edit:** Pressing Ctrl+- solves this issue, at least temporarily.  But why is it doing it in the first place?

---

### Post by thedaylights on 2008-06-15
Ditto here. Running Firefox 3 (beta 5?) and Ubuntu 8.04 I get pixelated images. But otherwise wooohooo I love both the new firefox and Hardy Heron!! :)

---

### Post by ucf on 2008-06-15
View > Zoom > Zoom text only

[(source and more info)]("http://support.mozilla.com/tiki-view_forum_thread.php?locale=en-US&forumId=1&comments_parentId=29934")

I have the [no squint]("https://addons.mozilla.org/en-US/firefox/addon/2592") addon installed, so I changed it like this:
View > Zoom > Zoom Settings (No Squint) > Primary Zoom Method > Text Zoom (text only)

---

### Post by PCZahra on 2008-07-01
I have the same problem, but mostly just with PNG images. I first noticed it with XKCD.com, and thought nothing of it until I saw it from another computer. Any font other than system defaults are also displayed pixelated. Looks as though it tried to smooth them but then squashed them down to half size and stretched them out again. Sometimes that makes diagonals look almost invisible.

---

### Post by PCZahra on 2008-07-20
Firefox is out of beta and this issue is still not resolved. I don't use zoom, and it doesn't seem related.

---

### Post by monikgtr on 2008-08-01
+1 with this issue :/ 

My fonts are fine now, I changed the default font to FreeSans, and I must say it's the best one I've used so far... but the images do look horrible :/

still no solution? :(


**Edit:**
I found in this thread [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/191791](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/191791) a solution, which is to change the layout.css.dpi settings to 96. It didn't work for me, but it did for some others so, if you wanna give it a go.. go ahead :P

---

