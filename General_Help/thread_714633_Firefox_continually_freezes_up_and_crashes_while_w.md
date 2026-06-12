---
title: "Firefox continually freezes up and crashes while watching flash videos"
date: 2008-03-04
forum: General Help
---

### Post by charlescarroll1 on 2008-03-04
My Firefox crashes 2 out of about 5 or 6 times I load a web page with a flash video.  I have searched through threads with similar issues, but it seems none have been resolved.

I'll be on Youtube watching videos, and it'll freeze up and I'll have to force quit Firefox.  Like I said, this will happen 2 out of about 5 times I load a different page.

I have the newest version of Adobe Flash Player plugin installed (flashplugin-nonfree).
I have also tried different web browsers like opera, epiphany, galeon, and a couple others, and I have the same issues with flash videos, so I assume that it might have something to do with the plugin (I'm not sure if this plugin is used for all these browsers though).

Any help or suggestions would be greatly appreciated.

---

### Post by Bubba64 on 2008-03-04
I am not sure what is causing your problem but here is a link to other plugins and codec info which may help your overall performance some of them are in synaptic and some are in add remove but if your comfortable with the terminal you can use the suggested download method.
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
I just noticed we live in the same town you must familiar with Free Geek they have classes there for more education in Linux.

---

### Post by tors on 2008-03-04
A workaround that works for me is to open the flash-movies in new tabs all the time.

---

### Post by zxscooby on 2008-03-04
i found that using an older version of flash player 9.xxx fixes the problem 
[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=1)

---

### Post by charlescarroll1 on 2008-03-04
> **Bubba64 said:**
> I am not sure what is causing your problem but here is a link to other plugins and codec info which may help your overall performance some of them are in synaptic and some are in add remove but if your comfortable with the terminal you can use the suggested download method.
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

Are these the codecs I am to install?
sudo apt-get install alsa-oss compizconfig-settings-manager faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 msttcorefonts sun-java6-fonts sun-java6-jre sun-java6-plugin unrar w32codecs

I installed them, so far so good.

> **Bubba64 said:**
> 
I just noticed we live in the same town you must familiar with Free Geek they have classes there for more education in Linux.
Yeah I am actually.  I went there as a "temporary intern" by a non-profit organization known as SE Works.  I wasn't recognized as an intern though, but a volunteer.  I worked/volunteered there for about 4 months or so.  I took a couple basic Linux command line courses there, FUN STUFF.  Do you volunteer there?

---

### Post by Bubba64 on 2008-03-05
> **charlescarroll1 said:**
> Are these the codecs I am to install?
sudo apt-get install alsa-oss compizconfig-settings-manager faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 msttcorefonts sun-java6-fonts sun-java6-jre sun-java6-plugin unrar w32codecs

I installed them, so far so good.


Yeah I am actually.  I went there as a "temporary intern" by a non-profit organization known as SE Works.  I wasn't recognized as an intern though, but a volunteer.  I worked/volunteered there for about 4 months or so.  I took a couple basic Linux command line courses there, FUN STUFF.  Do you volunteer there?

I also have every plugin from the Mozilla add on page installed,  here is the link I have them all installed. I also have VLC installed and all the gstreamer stuff in add remove which may have down loaded some of the suggestions of the first link I sent you. I am not an expert on Linux, but I have learned how to find what I have done, and what not to do generally.
[https://addons.mozilla.org/en-US/firefox/browse/type:7](https://addons.mozilla.org/en-US/firefox/browse/type:7)
I have never volunteered at Free Geek I started out buying a box with Dapper installed for 30 bucks then I bought an old IBM thinkpad and abused their tech service so much that I do some probono work for them now to pay them back all their help and because they do a great service for the community. The last computer I got they gave me for helping them out for free 1.8 gig that you would adopt as a volunteer. So downloading the list above fixed your flash situation?

---

