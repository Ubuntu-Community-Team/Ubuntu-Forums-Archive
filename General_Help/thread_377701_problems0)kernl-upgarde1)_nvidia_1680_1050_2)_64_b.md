---
title: "problems:0)kernl-upgarde1) nvidia 1680 1050 2) 64 bit 3) ctrl alt f1 screen bad 4)cdx"
date: 2007-03-06
forum: General Help
---

### Post by avishalom on 2007-03-06
my first instinct was to go to the "beginner's forum" and write a message titled HELP ! ! ! ! ! 1 !! !
but after reading the general guidelines i figured i had enough computer experience not  to post there. 
i'm posting to general, because maybe these problems are related, and together they don't belong on any other forum.

i am running an athlon x2 64 bit amd with m2npv , onboard video , and edimax 7128 wireless card.

i am generally new to ubuntu, i have used used linux before , and command line too , but somebody else was admining 



so here are the problems i've encountered.
1) the wireless was not exactly out of the box and not exactly 
[http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)
or
 [http://ubuntuforums.org/showthread.php?t=156075](http://ubuntuforums.org/showthread.php?t=156075)
either, but after i finally got it to work. i clicked the "updates " icon on the menu bar, and the kernel upgraded from 2.6.17-10-generic to 2.6.17-11-generic (maybe it wasn't that button but one of the apt-get updates i don't know)

anyway, i had to recopy the files to the new kernel.

is there a way around that , or are kernel updates rare enough not to worry about this.

2) next, i got Hebrew to work, this was easy enough, but anyway i did it twice, I'm not sure if because i played around with the xorg.conf or the kernel thing.

3) next, i tried to set my screen resolution straight , 1680x1050 (22"wide) i couldn't get 
dpkg-reconfigure xserver-xorg to work no matter what i tried (nv,vesa,16bit)
(ctrl-alt-f1 , gdm stop, then dpkg...)
then i installed the nvidia drivers
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
and it sort of worked 
that is i got the 1680x1050 resolution when in x and also the scrolling was smooth, 
however , the fonts were'nt sharp enough , i got sharper fonts hooking up my laptop via the d-sub input to the screen, and i know DVI shouldn't be worse than that, 
i tried to ctrl-alt-f1, to have another go a the dpkg-reconfigure, 
**but now the text mode was really bad, the fonts werelooked interlaced, and i could not see the bottom line of the console (where i write.) it only shows up after "enter" and i'm not that good a typist**

so i tried the envy script, [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html), and it crashed my X totally, so i reverted to an earlier version of xorg.conf, and i'm back to 1024x768 for now.

4) i am having trouble downloading w32codecs to see a dvd, i'm online and everything, but the freecontrib repositories don't seem to work. 
i didn't spend much time on that. 
neither on getting flash to work, 
i saw the page on installing 32 bit ff for amd64 , but didn't do it yet. 

on the whole i've spent about 3 evenings with this, and the end is not in sight , 
does anyone have a better experience with ubuntu for 32bits? or with 6.06 for that matter?

---

