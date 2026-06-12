---
title: "Want to try Beryl without messing up your install?"
date: 2006-11-15
forum: General Help
---

### Post by kvonb on 2006-11-15
Want to know what all this talk about Beryl, GLX, AIGLX, wobbly windows stuff is?

Try this:

Get yourself a copy of the standard Edgy CD, boot from it, then follow this howto I made:

[http://wamrfixit.homeip.net:8000/modifications/beryl-on-edgy-livecd/modification-beryl-on-edgy](http://wamrfixit.homeip.net:8000/modifications/beryl-on-edgy-livecd/modification-beryl-on-edgy)

Keep in mind that I did this with an ATI 9200se (cheap unbranded) and have a decent Internet connection.  I think the downloads are about 11megs from memory, but you don't have to waste them when you are finished!

Cool extra stuff:

I worked this out yesterday: copy the .deb files that you downloaded while installing Beryl above (you will need a place to copy them to, ie a mounted partition or network share).  Then when you have installed Edgy, just copy those .debs into /var/cache/apt/archives/partial on your fresh install and do the howto again.  It picked them up for me, saving bandwidth/waiting :).

Another cool thing I discovered is that if you setup your xorg.conf how you want it before installing, Edgy copies the working/modified xorg.conf to your fresh install, so that when you first boot Edgy, your graphics are working straight away!  Cool stuff.

Let me know how you went.

Regards,  Kev :)

---

