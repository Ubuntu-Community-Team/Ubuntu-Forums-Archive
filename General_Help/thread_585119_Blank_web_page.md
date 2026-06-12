---
title: "Blank web page"
date: 2007-10-21
forum: General Help
---

### Post by new2linux411 on 2007-10-21
Well let me start off by saying that Ubuntu isn't the only distro I've tried with the same problem. I'm using dapper on my laptop, and edgy on my desktop. Neither machine will properly display the web page [www.citicards.com](www.citicards.com) when I try to access it. The page starts to load, and just when you think it is going to work, the page just turns blank white. This is very frustrating because this is a page I need access to to view and pay my credit card account. It works just fine with XP, which I'm dual booting with edgy on my desktop. Any ideas if this is something that can be fixed? I have flash installed and some extra fonts, so I don't think that is the problem. I don't want to put windows on my laptop, but I do need access to that website, so that's the dilema. Any help resolving this would be greatly appreciated. Is this just something I need to change with my system, or is it just a Linux thing? Thanks in advance for any help and feedback. Hopefully this is the right area for this post..

---

### Post by spin2cool on 2007-10-21
The problem is some kind of flash ad that Citi is trying to pop up over the page.  Install the AdBlock Plus extension for firefox and use it to block the offending flash object.  I just started nuking stuff and got it to work by blocking these four items:

[https://www.citicards.com/cards/wv/swf/filter1.swf](https://www.citicards.com/cards/wv/swf/filter1.swf)
[https://www.citicards.com/cards/wv/swf/hpAdCont.swf](https://www.citicards.com/cards/wv/swf/hpAdCont.swf)
[https://www.citicards.com/cards/wv/swf/hpBannerCont.swf](https://www.citicards.com/cards/wv/swf/hpBannerCont.swf)
[https://www.citicards.com/cards/wv/swf/savecards.swf](https://www.citicards.com/cards/wv/swf/savecards.swf)

A little experimenting will tell you exactly which one it is, and you can unblock the others.

---

### Post by new2linux411 on 2007-10-21
Well, first off, thanks for your reply. I tried using that firefox extension you suggested. I was able to see most things on the page, but after trying to navigate through the site a little, I got an error message from the site. It said that either my browser or operating system  isn't fully supported by this site, I need to use a supported brower or OS to get the most out of this site(not exact words, but in a nutsheel). So I uninstalled the Adblock Plus extension and I'm back to square one. Just to make sure this wasn't an Ubuntu thing, I tried it with Freespire 2.0.6 with the same results. I know Freespire is now Ubuntu based, but I figured with the included out of the box plugins and codecs maybe it would be different. Well my quest isn't over yet. Thanks again for your feedback. If you or anyone else has any more ideas feel free to chip in.

---

