---
title: "AWN not working in hardy."
date: 2008-04-24
forum: General Help
---

### Post by lszanto on 2008-04-24
Since Gutsy I have been using AWN(avant window navigator) which is a dock like app, I have been using it instead of a bottom panel and works very nicely for me. When I went to install it in Hardy I followed this guide: 
[http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml) which didn't work so I looked round the ubuntu forums and found this: [http://ubuntuforums.org/showthread.php?t=733129](http://ubuntuforums.org/showthread.php?t=733129) which didn't work either. The problem ISN'T installing it installs the app fine and I can find it in the Applications > Accessories and System > Prefrences but for some reason it just will not start, I have reinstalled and restarted but nothing works.

thanks in advance, Luke

---

### Post by natrixgli on 2008-04-24
please open a terminal and run it from there, and post the output. To run awn from the terminal: 

1) Applications > Accessories > Terminal
2) type 'avant-window-navigator' and press enter

Also you need compiz running for awn to work, so you might have a look in System > Preferences > Appearances and make sure you have desktop effects on.

I am using Hardy with awn, it works swell. (a fair bit sexier than the panel, too.) I do feel a bit like a wannabe Mac user though.. ;)

-n8

---

### Post by isaacj87 on 2008-04-24
> **lszanto said:**
> Since Gutsy I have been using AWN(avant window navigator) which is a dock like app, I have been using it instead of a bottom panel and works very nicely for me. When I went to install it in Hardy I followed this guide: 
[http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml) which didn't work so I looked round the ubuntu forums and found this: [http://ubuntuforums.org/showthread.php?t=733129](http://ubuntuforums.org/showthread.php?t=733129) which didn't work either. The problem ISN'T installing it installs the app fine and I can find it in the Applications > Accessories and System > Prefrences but for some reason it just will not start, I have reinstalled and restarted but nothing works.

thanks in advance, Luke

Hey, try running this command in Terminal for me real quick.

```
sudo ldconfig
```

Oh and like the user said above me...check and make sure you have Compiz Fusion running.

---

### Post by lszanto on 2008-04-24
Oh wow I'm so dumb, I forgot I didn't have compiz fusion working, its all up now, thanks guys!

---

### Post by natrixgli on 2008-04-24
> **lszanto said:**
> Oh wow I'm so dumb, I forgot I didn't have compiz fusion working, its all up now, thanks guys!


*"Smooth move, exlax!"*  :lolflag:


Glad to hear you got it sorted! Oh, and did I just quote the movie "The Explorers"? Dear lord...

-n8

---

### Post by angry_johnnie on 2008-04-25
And now, with Hardy, Metacity can be used as a compositing manager.  So, if you enable that function, you don't even have to turn on compiz in order to use AWN.  Neat, huh?

---

