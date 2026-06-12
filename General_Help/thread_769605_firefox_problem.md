---
title: "firefox problem"
date: 2008-04-26
forum: General Help
---

### Post by T2manner on 2008-04-26
i just intalled hardy heron and when i got on firefox and i had to install this thing for flash player. i installed the first option, it wasn't adobe..  but whenever theres an ad or something there's a big gray play symbol. and if i click it, i can see the ad. but it's not just for ads.
also the firefox is really slow.
is this just normal or what?

---

### Post by dontgetshocked on 2008-04-26
Been there done that.Switch back to Firefox 2 for now until they get the bugs out.I had the same problem.

---

### Post by darolu on 2008-04-26
I really don't know why they included a BETA version of Firefox in a 'final' release of Ubuntu, it was stupid in my opinion.
You can get the flash plug in working with ff3b5 installing ubuntu-restricted-extras
```
sudo apt-get install ubuntu-restricted-extras
```
I *Upgraded* to Firefox 2 also, but now I can't install Firebug which is the only reason I use Firefox over Opera...

---

### Post by dohko_xar on 2008-04-26
> **darolu said:**
> I really don't know why they included a BETA version of Firefox in a 'final' release of Ubuntu, it was stupid in my opinion.
You can get the flash plug in working with ff3b5 installing ubuntu-restricted-extras
```
sudo apt-get install ubuntu-restricted-extras
```
I *Upgraded* to Firefox 2 also, but now I can't install Firebug which is the only reason I use Firefox over Opera...

Firefox 3 was included in the release because Hardy Heron is a LTS, which means it will be supported for 3 years. I don't think Firefox 2 will be any good in 3 years. 2 months from now the final release of Firefox 3 will be here, so why don't you try and and help report the bugs?

---

### Post by jeyaganesh on 2008-04-26
If you like try Flock. It is an exactly firefox2 like browser with different pretty look. It supports lot of integrated community based sites like flickr,my space, facebook etc. with single click. Have a look at [www.flock.com](www.flock.com) and get it from [www.getdeb.net](www.getdeb.net) as a debian package. It will install itself easily wiht debian packager. Hope you may know this. Firefox 3 Beta5 is slower than its previous versions and also missing 'smart bookmark' button in ubuntu.

---

### Post by darolu on 2008-04-26
You can easily upgrade from Firefox 2 to 3 (when the final version comes out) so the LTS argument doesn't work here in my opinion.
And I have reported several bugs already, you can search my name in bugzilla =) 
Anyways T2manner let us know if that worked for you.

---

### Post by T2manner on 2008-04-28
i installed firefox 2 and still have the same problem with the flash

---

### Post by Bablefish on 2008-04-28
This worked for me Installing the latest Flash

copy and paste in terminal

 wget -c [http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.17ubuntu4_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.17ubuntu4_all.deb)
sudo dpkg -i gsfont*.deb
sudo dpkg -i flash*.deb

If you have the update manager on next time you boot you will get the very latest version of Flash installed

---

### Post by sschlangen on 2008-04-28
those sites dont work. we need to find out how to remove the flash player that is on the top of the list of flash plugins when you run firefox for the the first time. I am stuck just like you

---

### Post by T2manner on 2008-04-28
yeah. you're right sschlangen
help would be appreciated

---

### Post by sschlangen on 2008-04-28
> **T2manner said:**
> yeah. you're right sschlangen
help would be appreciated

Well hopefully this will work itself out and someone will come up with a solution. But in a way its our fault for just clicking through and not reading what we install.  I have tried everything from installing other flash plugins but it wont overide the flash plugin with the big play button

---

### Post by sschlangen on 2008-04-28
ok i got it t2
this is how i did step by step let me know if this works for you. 



Step 1.
---------------[COLOR="Red"]Open Terminal[/COLOR]
```

sudo apt-get purge flashplugin-nonfree gnash gnash-common swfdec-mozilla
```

Step 2.
```
sudo apt-get remove icedtea-gcjwebplugin openjdk-6-jre && sudo apt-get install alsa-oss compizconfig-settings-manager faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libflashsupport liblame0 sun-java6-fonts sun-java6-jre sun-java6-plugin unrar w32codecs
```

Step 3.
```
sudo apt-get purge flashplugin-nonfree gnash gnash-common swfdec-mozilla && sudo apt-get install flashplugin-nonfree libflashsupport
```


[COLOR="RoyalBlue"]I started on this thread[/COLOR]
[http://ubuntuforums.org/showthread.php?t=772665&highlight=firefox+flash](http://ubuntuforums.org/showthread.php?t=772665&highlight=firefox+flash)

[COLOR="RoyalBlue"]Then ended up here[/COLOR]
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

You shouldnt need to worry about installing any other free open source alternatives when it comes to media related sites. I hope this helps bud

---

