---
title: "Media Lag"
date: 2014-12-19
forum: General Help
---

### Post by combat-bamse on 2014-12-19
Hello!

I'm new to Linux and Ubuntu so please have some patience and understanding ;)

For the last few months, various types of media, music, movies, streaming etc, begun to lagging or hack. Doesn't matter if it's local files on computer or streamed via YouTube, Spotify or various on line services. You can watch a movie or listen to music anywhere from a few seconds to a few minutes and it starts to lagging/freeze up, sometimes only for a few seconds, sometimes up to 5 sec. Then it continuous for a couple of minutes and the problem comes back.
OS itself works flawlessly as far as I can see.


Various forums I have read and when tried to google for the problem, saying it may be the display/graphic drivers. I did change the proprietary drivers to Nvidia, can't say 100% if it was after this that it started, but I do not exclude it. Have tried to return to previous drivers, however, cannot find them, and all other options are Nvidia's own.


Can this really be the cause of ALL the problem, even music that is not graphic depending?? If so what can I do or what driver should I use to solve the problem??
[COLOR=#000000][FONT=Verdana]

[FONT=arial]AMD Phenom II X86, GeForce GTX 460 (see picture), Ubuntu 14.04
[/FONT]
[/FONT][/COLOR][ATTACH=CONFIG]258685[/ATTACH]

---

### Post by sudodus on 2014-12-19
Welcome to the Ubuntu Forums :-)

It is easy to uninstall the proprietary nvidia driver. You need not install another driver, the built-in nouveau driver should be used automatically, and you can re-install the proprietary driver if that was not causing the problem.

You can also check if the performance of local HD video clips is good. It local video is also lagging, you might select a lighter desktop environment, for example

- LXLE - ultra light - comes with the Ubuntu flavour Lubuntu
- XFCE - medium light - comes with the Ubuntu flavour Xubuntu

Both are much lighter than standard Ubuntu in old and middle-aged computers. [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

-o-

There might be problems with your internet connection (that is lags), or problems due to a bad flashplayer. Adobe does not provide the best support for linux. You might be able to use html5 for YouTube, which might work better. Browse the internet for tips and tutorials, for example

[http://www.htmlgoodies.com/html5/tutorials/how-to-view-html5-videos-on-youtube.html](http://www.htmlgoodies.com/html5/tutorials/how-to-view-html5-videos-on-youtube.html)

---

### Post by combat-bamse on 2014-12-19
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

It is easy to uninstall the proprietary nvidia driver. You need not install another driver, the built-in nouveau driver should be used automatically, and you can re-install the proprietary driver if that was not causing the problem.

You can also check if the performance of local HD video clips is good. It local video is also lagging, you might select a lighter desktop environment, for example

- LXLE - ultra light - comes with the Ubuntu flavour Lubuntu
- XFCE - medium light - comes with the Ubuntu flavour Xubuntu

Both are much lighter than standard Ubuntu in old and middle-aged computers. [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

-o-

There might be problems with your internet connection (that is lags), or problems due to a bad flashplayer. Adobe does not provide the best support for linux. You might be able to use html5 for YouTube, which might work better. Browse the internet for tips and tutorials, for example

[http://www.htmlgoodies.com/html5/tutorials/how-to-view-html5-videos-on-youtube.html](http://www.htmlgoodies.com/html5/tutorials/how-to-view-html5-videos-on-youtube.html)

Thank's for replying! :)

I doubt it is the computer, its not that old........okey she may be 5 years old my litle tin-can but she's still strong! 
How do I unistall the current proprietary drivers? I cant use/select revert button.
The first month or so everything worked flawlessly, local files on HDD over 8GB 1080p movies went perfectly on VLC. Even online streaming with 720p files went flawlessly and listening music on Spotify went without a glitch. I have a 30/30Mbit fiber internet connection, so it's not to slow connection either.
And then, for some reason, if it was new software updates or changing proprietary drivers it started laging.

---

### Post by sudodus on 2014-12-20
When you have found a proprietary driver, that works well, you should not replace it with another one.

But now you need to try various alternatives. Please note that you are running ***331.38 from nvidia-331-updates*** now (if it would turn out to be the best one after all).

How to install and remove depends on the version of Ubuntu that you are running. So please confirm that you are running Ubuntu 14.04 LTS and is it updated to 14.04.1 LTS? Check with

```
lsb_release -a
```

In that case it should work to start a text screen with

***ctrl + alt + F1***

stop the graphical desktop environment with

```
sudo service lightdm stop
```

remove the driver with

```
sudo apt-get remove nvidia-331-updates
```

I think you need to reboot the computer to make the change complete.

[COLOR=#696969]Otherwise you can try to restart the graphical desktop environment with

```
sudo service lightdm start
```

The graphical desktop environment is on 'screen 7' at

***ctrl + alt + F7***[/COLOR]

---

### Post by mc4man on 2014-12-20
You could check in nvidia-settings to see if there is a Powermizer option. If so try setting it to Performance rather than the default of Adaptive
This is just a per session change so don't reboot till you've checked out.
One big difference between the nvidia & nouveau drivers is nouveau always runs chip at full clock speeds

---

### Post by combat-bamse on 2014-12-26
> **sudodus said:**
> When you have found a proprietary driver, that works well, you should not replace it with another one.

But now you need to try various alternatives. Please note that you are running ***331.38 from nvidia-331-updates*** now (if it would turn out to be the best one after all).

How to install and remove depends on the version of Ubuntu that you are running. So please confirm that you are running Ubuntu 14.04 LTS and is it updated to 14.04.1 LTS? Check with

```
lsb_release -a
```

In that case it should work to start a text screen with

***ctrl + alt + F1***

stop the graphical desktop environment with

```
sudo service lightdm stop
```

remove the driver with

```
sudo apt-get remove nvidia-331-updates
```

I think you need to reboot the computer to make the change complete.

[COLOR=#696969]Otherwise you can try to restart the graphical desktop environment with

```
sudo service lightdm start
```

The graphical desktop environment is on 'screen 7' at

***ctrl + alt + F7***[/COLOR]

Thank you VERY MUCH! It worked!
I'v tried now for a couple of days streaming and listening music, and it works perfectly now! No glitches or freezing of frames!

> **mc4man said:**
> You could check in nvidia-settings to see if there is a Powermizer option. If so try setting it to Performance rather than the default of Adaptive
This is just a per session change so don't reboot till you've checked out.
One big difference between the nvidia & nouveau drivers is nouveau always runs chip at full clock speeds

When I have more time I'll probably also try to see if  this also may work for future reference!



For Ubuntu and graphic performance, does it mater witch graphic drivers I'll use for Ubuntu? So far I cant't tell/see any difference in graphics. But if I would play some games or work with Hi-res picture/movie editing, would I loose performance or something by using nouveau compared to nvidia?

---

### Post by sudodus on 2014-12-26
The general reply is: Yes it matters which graphic drivers you use for Ubuntu. Particularly for some chips/cards some drivers work well, some work but are slightly buggy, some do not work at all. You must test what works for you. If you are lucky many of the available drivers work.

Particularly for demanding tasks like playing HD video or running 3D graphics, proprietary drivers can be much better, for example you can use 3D acceleration and you can use the GPU for tasks like VDPAU to reduce the work load for the CPUs.

---

