---
title: "cannot get the bbc streams to work"
date: 2008-01-07
forum: General Help
---

### Post by revelationman on 2008-01-07
I have tried everything under the sun ,  MPlayer is garbage  just audio  codecs have  been installed ,  

I have checked all the   help posts 

This is driving me crazy  I am lost for words  

So does anyone have an answer for this 

This is a terrible browser people should not have these issue's  

Sorry  folks just frustrated being at this  thing all morning

---

### Post by shifty2 on 2008-01-07
Have you tried install ubuntu-restricted-extras (search for that term in synaptic)? I needed the windows media codecs to be able to play the videos from the website.

---

### Post by philinux on 2008-01-07
Down load realplayer from here.

[http://ubuntu.org.ua/commercial/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb](http://ubuntu.org.ua/commercial/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb)

you need the feisty version cos the gutsy version fails to set up the helix dna plugin for the streaming audio.

It's a bug which hopefully will get fixed soon. see launchpad for details.

---

### Post by narf y akim on 2008-01-28
Hello revelationman,
I have the same problem with bbc web. Tell us  if you solved the problem. I have Gutsy in my laptop and I don't want to do a downgrade to Feisty ... for the moment.

---

### Post by narf y akim on 2008-02-01
Hello,
I'm just posting to say I’ve solve the problem with Real Player and BBC and  NHK webs. The solution is in the community contributed documentation webpage:

[https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods)

After install it I followed the instructions under the title: RealPlayer freezes or playback is jerky.
It works great to hear audio files, and also it works well with video files under low resolution.
Hope this help somebody!

---

### Post by AndyCooll on 2008-02-01
Hmmm ...I'm quite surprised you needed to go to those lengths to get streaming of BBC websites working for you. They work fine for me and I simply use the default totem-mozilla plugin for Firefox. 

From a vanilla installation I simply install the usual extra gstreamer codecs required for Totem to play music files (mp3, wma etc). And on the website itself I default to the "Windows Media" option. That's it.

:cool:

---

### Post by narf y akim on 2008-02-01
OK, I'm quite new in Linux-Ubuntu. What is "a vanilla instalation"? And what's the name of the usual extra gstreamer codecs in the synaptic repos? Really I'd prefer to use totem but I didn't know it was possible with ram files. Do I have to install the totem plugin also?

---

### Post by AndyCooll on 2008-02-01
By "vanilla" I simply mean a clean Ubuntu install with the default settings (i.e. an out-of-the-box install).

I don't install them via Synaptic, I usually simply open up Totem and play a few files (e.g. mp3, video etc) and Ubuntu prompts to install the codecs. However, it seems to install the gstreamer good, bad and ugly packages and ffmpeg. The totem-gstreamer and totem-mozilla packages are usually already installed.

When in Synaptic make sure you have all the the "downloadable from the Internet" repositories are ticked (Settings > Repositories).

:cool:

---

### Post by kelvin spratt on 2008-02-01
Mplayer is what I always use never had a problem all you do is make sure video is set to min x11, gl, or gl2, which ever you are using in preferences,  and the Mozilla plug-in is enabled.

---

### Post by ubuntu-freak on 2008-02-02
If you're missing anything else, check out my complete [how-to](http://ubuntuforums.org/showthread.php?t=661833).
 
Nathan

---

### Post by narf y akim on 2008-02-03
> **reassuringlyoffensive said:**
> If you're missing anything else, check out my complete [how-to](http://ubuntuforums.org/showthread.php?t=661833).
 
Nathan

Thank you very much! I have followed your how to, it wasn't easy for me, I didn't download all the packages, but finally I have the bbc videos working at high quality. Thanks, again.:popcorn:

---

### Post by ubuntu-freak on 2008-02-03
> **narf y akim said:**
> Thank you very much! I have followed your how to, it wasn't easy for me, I didn't download all the packages, but finally I have the bbc videos working at high quality. Thanks, again.:popcorn:

 
I'm glad it helped.
 
Why didn't you download all the packages? Did you enable the medibuntu repo as explained in part 1?
 
Don't give up. :-)
 
Nathan

---

### Post by narf y akim on 2008-02-04
Because I&#8217;m afraid of overwriting something that&#8217;s already working ok. I don&#8217;t know what happens when you download and install a package that you already have like Media Player and Real Player.

---

### Post by ubuntu-freak on 2008-02-04
> **narf y akim said:**
> Because I&#8217;m afraid of overwriting something that&#8217;s already working ok. I don&#8217;t know what happens when you download and install a package that you already have like Media Player and Real Player.

Nah don't worry about that. It skips whatever you already have. Trust me. Just ignore the RealPlayer deb, and if you have java5 uninstall it, everything else is okay. At least you will know you have everything.
 
Nathan

---

### Post by narf y akim on 2008-02-06
Well finally I have followed your advice and everything works fine, thanks, great job. Now I have a new application: Sun Java 6. And I have a question about it. Is there any serious application for Java but games? I used to play a lot 2 or 3 years ago but no more:(

---

### Post by ubuntu-freak on 2008-02-06
> **narf y akim said:**
> Well finally I have followed your advice and everything works fine, thanks, great job. Now I have a new application: Sun Java 6. And I have a question about it. Is there any serious application for Java but games? I used to play a lot 2 or 3 years ago but no more:(

 
I'm glad my how-to helped. 
 
It's good to have java. Some desktop apps use it too, like frostwire. I always hide the menu entries in "Internet" and "Preferences" though. Never needed them.
 
Nathan

---

