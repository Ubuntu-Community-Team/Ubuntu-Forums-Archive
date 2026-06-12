---
title: "Slow Xorg load at boot up, ATI card, Gutsy to Hardy upgrade"
date: 2008-06-19
forum: General Help
---

### Post by hoatu on 2008-06-19
I recently upgraded from Gutsy to Hardy, and since then it takes me about 5 minutes to boot up to the desktop. 

Using bootchart I've worked out that my boot takes just under a minute, and then xorg starts to boot (the loading circle icon with the human background, prior to a login screen). Getting this far including the boot takes around 4 minutes.

Once I get to the desktop and log-in everything graphically runs as fast as you'd expect. It's just the login!

Now:

- I've been dicking around in xorg.conf to investigate the effect of the graphics driver in use on the total boot time. I've tried using the frglx driver, the open source ati driver and plain old vesa. With frglx, the boot time took over 4 minutes. This improved by a few minutes with the open source ati driver, but I don't want to use this because scrolling windows and videos embedded in webpages are juddery with it. Vesa lost me my 3d acceleration as expected, and I want to keep compiz so I don't want to use that either. 

- Some posts on forums suggest that xgl is out of date with Hardy, and AIGLX is the way to go. I uninstalled xgl and now I've lost 3d acceleration with compiz. Is AIGLX what I want? Is xgl actually a pre-req to use AIGLX? Can Compiz be configured to look for AIGLX and not xgl? NB. 

I'd like to use the close-source ATI driver - it runs perfect when I actually am logged in; I want to keep compiz going and get logged in from a cold boot within the minute or so that you'd reasonably expect. Gutsy was a lot faster but I don't know whos door to lay the blame at: Ubuntu, AMD or XOrg? 


Any advice or comments of your own battles with ATI cards would be useful.

hoatu.

---

### Post by Rocket2DMn on 2008-06-20
What video card are you using?
```
lspci | grep VGA
```
And yes, we don't use xserver-xgl anymore if your card supports 3d on its own, so that should be removed.
If your card is older than a Radeon 9500, you will have to use open source drivers, see this thread - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)
Hardy uses a new version of X which relies more on autodetection, so you can reconfigure to a generic type xorg.conf with
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Then restart X with CTRL+ALT+BACKSPACE

---

### Post by mtbsoft on 2008-06-23
I had various issues, including getting compiz to work, when I upgraded Gutsy to Hardy (Inspiron 9400 with X1400).  Did a clean, fresh install instead and ALL graphics problems went away - installed, selected restricted drivers, restarted, done!  If you can do a clean install I would recommend it.

---

