---
title: "mplayer/xine Aspect Ratio problems"
date: 2005-08-29
forum: General Help
---

### Post by c-m on 2005-08-29
In windows i used to use MediaPlayerClassic (and no thats not the old microsoft thing) which is an excellent player. With MPC i when outputting to my widescreen tv i was able to select 16:9 aspect ratio and the video would then be presented in widescreen format. By this i mean on the TV everything would appear correct aspect ratio, while on the monitor with this setting the video would appear streched vertically, since the monitor is not 16:9.

This was perfect for video playback on the TV. Now that i'm using ubuntu however this does not seem to work. If i select dvb or anamorphic in xine, the video ouput is not streched to fit a 16:9 TV but is further squashed making it appear distorted on the TV.

The same goes for mplayer, which is actually worse since it restarts itself everytime the aspect ratio is changed.

does anyone know a fix for this at all?

---

### Post by arnieboy on 2005-08-29
[QUOTE=c-m]In windows i used to use MediaPlayerClassic (and no thats not the old microsoft thing) which is an excellent player. With MPC i when outputting to my widescreen tv i was able to select 16:9 aspect ratio and the video would then be presented in widescreen format. By this i mean on the TV everything would appear correct aspect ratio, while on the monitor with this setting the video would appear streched vertically, since the monitor is not 16:9.

This was perfect for video playback on the TV. Now that i'm using ubuntu however this does not seem to work. If i select dvb or anamorphic in xine, the video ouput is not streched to fit a 16:9 TV but is further squashed making it appear distorted on the TV.

The same goes for mplayer, which is actually worse since it restarts itself everytime the aspect ratio is changed.

does anyone know a fix for this at all?[/QUOTE]
Try vlc. it should not give u problems
```
sudo apt-get install vlc
```

---

### Post by c-m on 2005-08-30
thanks for the effort but i'm affriad you misunderstand. Say i play a DVD which has a native aspect ratio (AR) of 16L9 on my monitor in xine. The AR wil be correct since there will be black bars to the top and bottom of the picture, which is to be expected since my monitor is not 16:9. Now say i also plug in my TV which is 16:9 format. Playing the same dvd with will result in their being black bars to the top and to the bottom of the pitcure on the TV, which their should now be. 

Its is as if the x server assumes the TV is the same resolution as the monitor, which it is not.

But the main problem i am getting at is that regardless of what resolution the screen is, when set to 16;9 media player classic would fill correctly a 16:9 screen. My question is are their any linux players that can do this?

---

### Post by arnieboy on 2005-08-31
[QUOTE=c-m]thanks for the effort but i'm affriad you misunderstand. Say i play a DVD which has a native aspect ratio (AR) of 16L9 on my monitor in xine. The AR wil be correct since there will be black bars to the top and bottom of the picture, which is to be expected since my monitor is not 16:9. Now say i also plug in my TV which is 16:9 format. Playing the same dvd with will result in their being black bars to the top and to the bottom of the pitcure on the TV, which their should now be. 

Its is as if the x server assumes the TV is the same resolution as the monitor, which it is not.

But the main problem i am getting at is that regardless of what resolution the screen is, when set to 16;9 media player classic would fill correctly a 16:9 screen. My question is are their any linux players that can do this?[/QUOTE]
the reason why I asked u to install vlc is because it deals with aspect ratios perfectly. good luck!

---

### Post by c-m on 2005-08-31
you'll have to excuse the typos and gramatical errors in my last post, i was a little under the influence. But i did try VLC and could not for the life of me find any setting to change the AR. All of the players play the video back in its original AR but thats not the problem. The issue is that a 16:9 movie does not fill the screen when outputed to the TV. Media player classic and zoomplayer in windows would do the same, but the difference is when i selected 16:9 mode on those they did fill the TV screen.

I think i may have to manually setup my TV a another screen in the X server and correctly set its resolution, but i don't know if the linux nvidia drivers support this here is my current xorg.conf concerning Tv-out.

> 
Section "Device"
	Identifier	"NVIDIA Corporation NV31 [GeForce FX 5600]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option "TwinView" "true"
	Option "TwinViewOrientation" "Clone"
	Option "TVOutFormat" "S-VIDEO"
	Option "TVStandard" "PAL-I"
	Option "SecondMonitorHorizSync" "30-50"
	Option "SecondMonitorVertRefresh" "60"
	Option "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480;512x384,512x384"
	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true" 





---

### Post by arnieboy on 2005-08-31
[QUOTE=c-m]you'll have to excuse the typos and gramatical errors in my last post, i was a little under the influence. But i did try VLC and could not for the life of me find any setting to change the AR. All of the players play the video back in its original AR but thats not the problem. The issue is that a 16:9 movie does not fill the screen when outputed to the TV. Media player classic and zoomplayer in windows would do the same, but the difference is when i selected 16:9 mode on those they did fill the TV screen.

I think i may have to manually setup my TV a another screen in the X server and correctly set its resolution, but i don't know if the linux nvidia drivers support this here is my current xorg.conf concerning Tv-out.[/QUOTE]
I am positive that u can change the aspect ratio with mplayer. when u right click on the main movie window while playing a dvd, one of the options lets u change the aspect ratio (1:1, 4:3, 16:9 etc). make sure u use gmplayer (not the terminal based mplayer). with vlc, there should also be an option. well am at work right now. when I get back home to my ubuntu box, i will do all the checking and let u know exactly how to change the aspect ratios on different media players in linux. one should fit the bill for u and fill ur tv screen. if its an issue with TV out, u will have to serach on these forums or or google as such to see if there is any fix. but I myself have changed the aspect ratios of movies in mplayer and totem-xine while playing dvd's on my comp. My tv isnt connected to my comp, so i cant recreate and troubleshoot the exact situation that u are facing.

---

### Post by c-m on 2005-08-31
[QUOTE=arnieboy]I am positive that u can change the aspect ratio with mplayer. when u right click on the main movie window while playing a dvd, one of the options lets u change the aspect ratio (1:1, 4:3, 16:9 etc). make sure u use gmplayer (not the terminal based mplayer). with vlc, there should also be an option. well am at work right now. when I get back home to my ubuntu box, i will do all the checking and let u know exactly how to change the aspect ratios on different media players in linux. one should fit the bill for u and fill ur tv screen. if its an issue with TV out, u will have to serach on these forums or or google as such to see if there is any fix. but I myself have changed the aspect ratios of movies in mplayer and totem-xine while playing dvd's on my comp. My tv isnt connected to my comp, so i cant recreate and troubleshoot the exact situation that u are facing.[/QUOTE]
 yeah both xine and mplayer let you change the AR. but what i'm talking about is imgaine i am watching recorded HDTV content and its playing both on my monitor and my Tv (through tv out) at the same time. Now i select 16:9 AR in mplayer. now on the monitor which is square or 4:3 the picture should look stretched vertically, the people will look long and thin so that when its shown on the wider screen of the TV they look normal again. 

The whole thing is very hard to describe especially if you don't use tv-out yourself. Its not a major problem, just something i thought i'd try and fix so i can tick it off my list.

I appreciate the help.

---

