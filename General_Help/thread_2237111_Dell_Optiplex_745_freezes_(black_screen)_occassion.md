---
title: "Dell Optiplex 745 freezes (black screen) occassionally [14.04]"
date: 2014-07-30
forum: General Help
---

### Post by Raymond_van_Hout on 2014-07-30
Hi there, 

Pretty new in this Ubuntu environment, so I hope you guys could help me.

Since a couple of days i'm running on 14.04 (64bit) and I like what i've seen so far. However, sometimes the PC 'freezes', or 'crashes' if you will. This happens, for example, when I try to open a webapp (eg Amazon, Youtube, etc.). This also happens when I try to use to standard videoplayer (VLC works great though!). When I open such an app or try to play a video, I will get a black screen. The same happens by the way when I open 'system settings'. However, with opening 'system settings' the screen will be 'blacked out' by no longer than a second or so and works fine besides this. With the opening of webapps or videoplayer the screen stays black, sound keeps working however (when a Youtube video (via Firefox, not the webapp obviously) is playing for example).  Sometimes I can recover by pressing some key combinations (I believe crtl + alt + del works). In that case the desktop reopens with all the apps closed that I was using. 

Any ideas what might be the problem? Since i'm very new with this please give detailed instructions on how to operate the terminal, or something like that, i've any of you would like to have a crash report, etc. 

Your help is very much appreciated! 

Kind regards,


Ray 

P.s. if I have used any bad English, i'm not a native speaker ;)

---

### Post by ibjsb4 on 2014-07-31
Please post your computer specs (cpu, ram, video card).

---

### Post by Raymond_van_Hout on 2014-07-31
CPU: Intel Core 2 CPU 6300 @ 1.86 GHz x 2
RAM: 3 GB
Video card: Intel 965Q (which is, i'm pretty sure, onboard).

What also might be relevant is that I have two harddrives (real ones, not just partitions), both SATA 7200 disks, not SSD. The Windows Vista partition is on the C drive, Ubuntu on the D drive.

---

### Post by ibjsb4 on 2014-08-02
This could be a driver issue.

[https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=20046&lang=eng&ProdId=2800](https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=20046&lang=eng&ProdId=2800)

[https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=13815&lang=eng&ProdId=2800](https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=13815&lang=eng&ProdId=2800)

Last two post.
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/984452](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/984452)

A general search.
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Intel+965Q+drivers&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Intel+965Q+drivers&as_qdr=all&sa=Google+Search&lang=en)

Hope that helps, good luck.

---

### Post by Raymond_van_Hout on 2014-08-03
Thanks a lot for your help so far! 

On the basis of your reply, i've downloaded, installed and ran the Intel Graphics Installer for Ubuntu 14.04 64bit. After reboot, the problem isn't solved. 

Also, on this page: [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads) you can download 2014Q2 Intel Graphics Stack Release. I didn't, because it seems to have a more develloping purpose. Is this right? Or can we solve the problem here? 

Or any other thoughts on what might be the problem.

Once again, your help is very much appreciated!

Kind regards, 

Ray

---

### Post by Raymond_van_Hout on 2014-08-06
Anyone?

---

### Post by ibjsb4 on 2014-08-06
I do not run Ubuntu/Unity, but I would think it should run fine on that computer.  I had hope someone with Unity experience would come along.

You could try adding a different desktop environment to you current install and see if it makes any difference.
```
sudo apt-get install gnome-panel
```
This will give you what is called the 'Flashback' desktop.
Log out and when you log back in, click on the icon at the login screen and then choose Flashback (metacity).

Someone in the mean time will hopefully come along and help you with the Unity desktop.

---

### Post by Raymond_van_Hout on 2014-08-07
No luck either :(.

And by doing as you told - but this is of course because of the Gnome-panel - the interface looks completely different.

---

### Post by ibjsb4 on 2014-08-07
Yes, the look is completely different.  The object was to get you off the compiz window manager to see if that was the problem, but no joy :(

I am out of ideas at the moment, if I think of anything else today, I will post back.

---

### Post by Raymond_van_Hout on 2014-08-07
Yes, it's hard to locate the problem. Thanks for all your tips though! 

Any other thought are welcome!

---

### Post by Martin_Gunther on 2014-11-26
Can't help, but another one having the same issues, and I found another thread as below:

[http://askubuntu.com/questions/553353/youtube-freeze-chromium-38-0-2125-111-ubuntu-14-04-1?newreg=2cf5c67dac514b3b912ad93bd2790d91](http://askubuntu.com/questions/553353/youtube-freeze-chromium-38-0-2125-111-ubuntu-14-04-1?newreg=2cf5c67dac514b3b912ad93bd2790d91)

I'm sorry but I can't help, but have the same issues, and also have an older Intel Core2Duo laptop with Intel 965 GFX. Identical, where by screen goes blank, but all lights and sound, etc continues, and can't ALT-CTL-F1, etc...

Specs: Intel Core2Duo T7300 @ 2.00Ghz x 2, 4GB RAM, Intel 965GM, 64-bit


It has happenned once in a while (was actually when I visited the apple website when they launched the new iphones, twice, and now twice this evening). It does happen mainly when browsing something (youtube, and apple website confirmed). I saw your points about:


GLib-Critical, and low and behold, I have these:


Nov 26 20:58:40 gunja-laptop gnome-session[2164]: GLib-CRITICAL: g_environ_setenv: assertion 'value != NULL' failed


Nov 26 21:04:01 gunja-laptop gnome-session[2280]: GLib-CRITICAL: g_environ_setenv: assertion 'value != NULL' failed


So intel graphics, and similar items in the syslog...


A few other people with same issue I've found:


[http://askubuntu.com/questions/534883/laptop-screen-goes-black-but-laptop-still-running](http://askubuntu.com/questions/534883/laptop-screen-goes-black-but-laptop-still-running)
[http://askubuntu.com/questions/543790/youtube-causes-black-screen](http://askubuntu.com/questions/543790/youtube-causes-black-screen)




Didn't have these issues with same hardware on 12.04.

Did you ever get a resolution to it?

---

