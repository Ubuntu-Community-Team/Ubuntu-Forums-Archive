---
title: "Problem running a program, someone help please?"
date: 2006-07-22
forum: General Help
---

### Post by vyndalas on 2006-07-22
I have tried several attempts to install Daimonin, a low graphic mmo to see what its about. I had to configure it from source, which I might add I am quite proud to be able to do all on my own now. But that aside, when I try to run the client, this happens, could someone please give me some pointers on what my problem may be?

root@ubuntu:/home/beanz/Downloads/daimonin/client/src# ./daimonin
List Video Modes
All resolutions available.
VideoInfo: hardware surfaces? no
VideoInfo: windows manager? yes
VideoInfo: hw to hw blit? no
VideoInfo: hw to hw ckey blit? no
VideoInfo: hw to hw alpha blit? no
VideoInfo: sw to hw blit? no
VideoInfo: sw to hw ckey blit? no
VideoInfo: sw to hw alpha blit? no
VideoInfo: color fill? no
VideoInfo: video memory: 0KB
**** NOTE ****
With sound enabled SDL will throw a parachute
when the soundcard is disabled or not installed.
Try then to start the client with 'SDL_AUDIODRIVER=null ./daimonin'
Read the README_LINUX.txt file for more information.
ERROR sprite.c: Can't load sprite ./bitmaps/palette.png
load_bitmap(): Can't load bitmap ./bitmaps/palette.png
ERROR sprite.c: Can't load sprite ./bitmaps/font7x4.png
load_bitmap(): Can't load bitmap ./bitmaps/font7x4.png
ERROR sprite.c: Can't load sprite ./bitmaps/font6x3out.png
load_bitmap(): Can't load bitmap ./bitmaps/font6x3out.png
ERROR sprite.c: Can't load sprite ./bitmaps/font_big.png
load_bitmap(): Can't load bitmap ./bitmaps/font_big.png
ERROR sprite.c: Can't load sprite ./bitmaps/font7x4out.png
load_bitmap(): Can't load bitmap ./bitmaps/font7x4out.png
ERROR sprite.c: Can't load sprite ./bitmaps/font11x15.png
load_bitmap(): Can't load bitmap ./bitmaps/font11x15.png
ERROR sprite.c: Can't load sprite ./bitmaps/intro.png
load_bitmap(): Can't load bitmap ./bitmaps/intro.png
Segmentation fault
root@ubuntu:/home/beanz/Downloads/daimonin/client/src# ./daimonin
List Video Modes
All resolutions available.
VideoInfo: hardware surfaces? no
VideoInfo: windows manager? yes
VideoInfo: hw to hw blit? no
VideoInfo: hw to hw ckey blit? no
VideoInfo: hw to hw alpha blit? no
VideoInfo: sw to hw blit? no
VideoInfo: sw to hw ckey blit? no
VideoInfo: sw to hw alpha blit? no
VideoInfo: color fill? no
VideoInfo: video memory: 0KB
**** NOTE ****
With sound enabled SDL will throw a parachute
when the soundcard is disabled or not installed.
Try then to start the client with 'SDL_AUDIODRIVER=null ./daimonin'
Read the README_LINUX.txt file for more information.
ERROR sprite.c: Can't load sprite ./bitmaps/palette.png
load_bitmap(): Can't load bitmap ./bitmaps/palette.png
ERROR sprite.c: Can't load sprite ./bitmaps/font7x4.png
load_bitmap(): Can't load bitmap ./bitmaps/font7x4.png
ERROR sprite.c: Can't load sprite ./bitmaps/font6x3out.png
load_bitmap(): Can't load bitmap ./bitmaps/font6x3out.png
ERROR sprite.c: Can't load sprite ./bitmaps/font_big.png
load_bitmap(): Can't load bitmap ./bitmaps/font_big.png
ERROR sprite.c: Can't load sprite ./bitmaps/font7x4out.png
load_bitmap(): Can't load bitmap ./bitmaps/font7x4out.png
ERROR sprite.c: Can't load sprite ./bitmaps/font11x15.png
load_bitmap(): Can't load bitmap ./bitmaps/font11x15.png
ERROR sprite.c: Can't load sprite ./bitmaps/intro.png
load_bitmap(): Can't load bitmap ./bitmaps/intro.png
Segmentation fault

I checked file permissions on the bitmaps, all good there. I'm confused myself. Any suggestions appreciated. Thanks again in advance.

---

### Post by tseliot on 2006-07-22
Moved to a more appropriate section

---

