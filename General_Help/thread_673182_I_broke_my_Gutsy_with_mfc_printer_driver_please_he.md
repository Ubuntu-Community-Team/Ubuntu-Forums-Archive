---
title: "I broke my Gutsy with mfc printer driver please help"
date: 2008-01-20
forum: General Help
---

### Post by AgentZ86 on 2008-01-20
Well see this post to see what I did when trying to install printer drivers:

[http://ubuntuforums.org/showthread.php?t=123539](http://ubuntuforums.org/showthread.php?t=123539)

I also now attempted to do some other things because I could not understand my permission problem so someone suggested that I do this:

sudo -s

so I did and it asked for old password, then new password and I use the same pass I've always used.

I now ran the :
dpkg -i mfc240clpr-1.0.0-9.i386.deb
and
dpkg -i mfc240ccupswrapper-1.0.0-10.i386.deb
and
ln -s /etc/init.d/cupsys /etc/init.d/cups

and maybe a few other things suggested from the other thread.

But now I can't run synaptic or when I browse to my /tmp folder it's different then what use to be in there, I create some folders in the tmp folder and they are not there now ?

I don't know I'm considering re-intall, but that would be a real bummer since this things has been working so well since I've installed it, and I know it will again, but I just thought I might get this printer working properly.

Any ideas on how to fix this, see [http://ubuntuforums.org/showthread.php?t=123539](http://ubuntuforums.org/showthread.php?t=123539)
for details but please post how I can fix this problem back to where I was before I installed any of this stuff. I don't care about the printer at this point I just want to fix the problem then I'll try the printer stuff some other time unless someone can fix this along with the printer problem, then perhaps post in the other thread, 

Thanks
:popcorn:

---

