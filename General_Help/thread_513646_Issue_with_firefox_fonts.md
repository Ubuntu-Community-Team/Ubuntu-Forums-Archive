---
title: "Issue with firefox fonts"
date: 2007-07-30
forum: General Help
---

### Post by mikecool36 on 2007-07-30
Hi guys this is my first post on here so if you can be forgiving about if I have placed this in the wrong post.   I have recently switched from windows xp being my main operating system to ubuntu and have been using the system constantly for the last 2 months.  Overall I am very impressed with the quality and stability of many of the applications.

The only slight problem im having is with the fonts on firefox.  When browsing webpages fonts look a little strange to what im used to in i.e. It seams that on my system web fonts come out thicker, possibly a bit more blurry then what they do in windows.

To make things a little more clearer I have included a screen shot of what i get in linux and windows xp.  Searching the forms I learnt that you had to install the msttfonts package as the fonts there are not open source and so cant be distributed with ubuntu.  This made things a little better but its still not what im after.

As I say this is only a minor little thing and i can still browse around the web but after hearing some good feedback about these forms I thought I would give it a try and see if anyone can help rather then me suffering quietly lol.

Mikecool
(Learning slowly but surely:))

---

### Post by kens8 on 2007-07-30
Check out [this post]("http://ubuntuforums.org/showthread.php?t=343670").  It helps a lot.

---

### Post by mikecool36 on 2007-07-31
Unfortuntley that did not really help me.  The page still looks like the same in firefox.  Although the rest of the font rendering is fine.

I have installed galleon and tested out the page in there and it looks fine.  So it seams that firefox is not picking up the new font settings.  So maybe there is a setting in firefox that i need to change.

---

### Post by mikecool36 on 2007-07-31
I think i have managed to get my fonts looking the way i want them now.  But i thought I would but down what i have done just in case it helps anybody else.

I downloaded msttcorefonts but this does not include tahaoma which is what the ubuntu site uses on its front page.  So i got a copy of tahomah and placed it in /usr/share/fonts/truetype/custom

And applied the file contained in this post [http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)

I also followed the guide above about patching the freetype

Hope this helps

---

