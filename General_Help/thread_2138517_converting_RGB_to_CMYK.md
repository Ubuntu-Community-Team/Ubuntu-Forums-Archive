---
title: "converting RGB to CMYK"
date: 2013-04-24
forum: General Help
---

### Post by Buntu Bunny on 2013-04-24
I need to convert some RGB jpegs to CMYK. Apparently Gimp can't do this. Any suggestions?

---

### Post by zero2xiii on 2013-04-24
Hay,

Not to be rude, but have you tried google? Where have you found that gimp can not do it? According to all the sources I found a gimp plug in can do this to numerous profiles.... So please be somewhat more specific.

I will not post the results here, since it seems you have done no research.

Cheers

---

### Post by Buntu Bunny on 2013-04-24
> **zero2xiii said:**
> Hay,

Not to be rude, but have you tried google? Where have you found that gimp can not do it? According to all the sources I found a gimp plug in can do this to numerous profiles.... So please be somewhat more specific.

I will not post the results here, since it seems you have done no research.


Excuse me? You can tell all that by what? The "I'm lazy" button on my forehead? As a matter of fact I have done quite a bit of research. Almost all the solutions are non-Linux, non-open source except Scribus, which keeps crashing on me. And how much more specific do you want me to get? I need to convert RGB jpeg photos to CMYK for printing. But, never mind, since it seems you have no answers.

---

### Post by Buntu Bunny on 2013-04-25
[http://www.rgb2cmyk.org/]("http://www.rgb2cmyk.org/")

---

### Post by zero2xiii on 2013-04-27
Ubuntu RGB to CMYKHay,

Just for the archive and to cool your fire:

google: "Ubuntu RGB to CMYK" gave:
[https://www.google.co.za/search?client=opera&q=Ubuntu+RGB+to+CMYK&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest](https://www.google.co.za/search?client=opera&q=Ubuntu+RGB+to+CMYK&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest)

Which leads to:
[http://ubuntuforums.org/showthread.php?t=1064787](http://ubuntuforums.org/showthread.php?t=1064787)
[http://askubuntu.com/questions/114858/how-to-convert-image-to-cmyk-in-gimp](http://askubuntu.com/questions/114858/how-to-convert-image-to-cmyk-in-gimp)
[http://blog.alastair.pro/2013/01/14/convert-rgb-to-cmyk-with-gimp-on-ubuntu-12-10/](http://blog.alastair.pro/2013/01/14/convert-rgb-to-cmyk-with-gimp-on-ubuntu-12-10/)

And I said I do not wish to be rude, but finding the above took my about 30 seconds? Which in my opinion is so fast, it does not require a forum post to find.

Again I do no WANT to offend you, I simply stated I do not wish to spoon feed anyone. And the above search is not even a very hardcore technical search.. As they say: K.I.S.S.... It does help to keep that in mind.

Cheers

---

### Post by Buntu Bunny on 2013-04-27
> **zero2xiii said:**
> Ubuntu RGB to CMYKHay,

Just for the archive and to cool your fire:

If you don't want to start a fire, don't light a match. :|

> Again I do no WANT to offend you, I simply stated I do not wish to spoon feed anyone. And the above search is not even a very hardcore technical search.. As they say: K.I.S.S.... It does help to keep that in mind.

The problem is that you made an *assumption*. You *assumed* I did zero research. You're still assuming it.  A minimalist question does not indicate no research. Sorry, I'm not going to bore folks with every detail of why I'm asking a question. I am not going to give a lengthy explanation of why I cannot get Gimp to do this for me. I was asking for alternatives, which, I think, is a legitimate question. 

Honestly? Because of your response I thought you were trolling, which is why I blew you off.  And that, was an assumption on my part.

---

### Post by zero2xiii on 2013-04-28
Hay,

Then I do apologize for the misunderstanding and "assumptions" on my behalf.

I did share some links in the above where imagemagik is used instead of the gimp, just for reference.

Good day.

---

### Post by Buntu Bunny on 2013-04-28
> **zero2xiii said:**
> I did share some links in the above where imagemagik is used instead of the gimp, just for reference.

Zero2xiii, it looks as though ImageMagick may be an option, thank you for that. It will be a learning curve for me because I do not do a lot in terminal, but if it does the job, it will definitely be worth it.

---

### Post by william_nbg on 2013-05-07
I just stuck the separate+ plun-in in the my plug-in directory and gimp convert my images to CMYK. It's working great for me.

a link:

[https://wiki.archlinux.org/index.php/CMYK_support_in_The_GIMP](https://wiki.archlinux.org/index.php/CMYK_support_in_The_GIMP)

---

### Post by Buntu Bunny on 2013-05-07
William_nbg, thanks! I've bookmarked the link. I'm glad it gives manual instructions. Looks like I've been needing to install ICC profiles.

---

### Post by william_nbg on 2013-05-07
Yeah, like I said, I didn't have to go through the whole install "make" stuff, just dropped the plug-in into the gimp plug-in folder in my home directory and it works great. I did have to copy the icc profiles into the icc directory. 

I have sent several things to the printer (who only accepts cmyk profiles) and had no problems.

---

### Post by Buntu Bunny on 2013-05-07
That sounds easy enough. Thanks so much for the info. Much appreciated.

---

### Post by Buntu Bunny on 2013-06-11
I've also found out that for my purposes (print publishing), Adobe Pro Distiller will also do this. Not a Linux solution, but it solves the problem within the overall context of my project.

---

