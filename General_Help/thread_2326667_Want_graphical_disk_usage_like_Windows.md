---
title: "Want graphical disk usage like Windows"
date: 2016-06-03
forum: General Help
---

### Post by Acharn on 2016-06-03
This is pretty trivial. I'm using Ubuntu 14.04 with the Unity desktop at the moment. I'd like a really simple graphic display of how much of the disk has been used. In Windows the Properties tab on a drive brings up a pie chart the the space used in one color and the free space in another color. There's more information presented as text, but that's irrelevant to my need. I can't find a similar utility in Ubuntu, probably because I don't know how to form a search key for what I want. There's a utility called Disk Usage Analyzer that does a reasonably good job of showing what's using up your disk space, and at the top level it shows as a bar the amount of space free and the space used. It takes quite a long time to load, because it analyzes the space used pretty thoroughly. Of course there's the command line 'du', but it's not very pretty.

---

### Post by HermanAB on 2016-06-03
Hmm, well, next time try Kubuntu.  Unity is just a slightly less cripple version of Gnome, so you should not expect too much of it.

---

### Post by leunam12 on 2016-06-03
It's the same in Ubuntu. Open Nautilus and right-click on the drive that you want to check (on the left pane) and select 'Properties'.

I hope that is what you are looking for.

---

### Post by vasa1 on 2016-06-03
Will *ncdu* fit?```
sudo apt-get install ncdu
``` if you want to retain the .deb in */var/cache/apt/archives* or ```
sudo apt install ncdu
``` if you don't need to retain the .deb.

---

### Post by mcduck on 2016-06-03
Just open System Monitor, it shows you the disk usage...

---

### Post by oldos2er on 2016-06-03
Maybe the program *filelight* will show what you're looking for. It's in the repositories.

---

### Post by ventrical on 2016-06-03
> **Acharn said:**
> This is pretty trivial. I'm using Ubuntu 14.04 with the Unity desktop at the moment. I'd like a really simple graphic display of how much of the disk has been used. In Windows the Properties tab on a drive brings up a pie chart the the space used in one color and the free space in another color. There's more information presented as text, but that's irrelevant to my need. I can't find a similar utility in Ubuntu, probably because I don't know how to form a search key for what I want. There's a utility called Disk Usage Analyzer that does a reasonably good job of showing what's using up your disk space, and at the top level it shows as a bar the amount of space free and the space used. It takes quite a long time to load, because it analyzes the space used pretty thoroughly. Of course there's the command line 'du', but it's not very pretty.

Disk Usage Analyzer should be working lickety split! :) What type of system/hdd are you using?

Regards..

---

### Post by Acharn on 2016-06-04
Ah! Exactly what I wanted. Not as colorful as the red and blue of Windows, but just what I was looking for. Thanks.

---

### Post by Cavsfan on 2016-06-04
Or you could go with a conky. It can show you much data about your system: temps, fan speeds, disk usage, kernel name, video driver, etc. etc. etc. 
But, be forewarned it is addictive. :p

This is my Arch Linux system:

[[IMG]http://en.zimagez.com/miniature/screenshot2016-06-0415-27-41.png[/IMG]]("http://en.zimagez.com/zimage/screenshot2016-06-0415-27-41.php")

I'm not really supposed to be posting this as it's the next generation of conkywx which is to be released soon.
I'll boot into my Xubuntu 16.04 system and show you my version of VinDSL's conky.

---

### Post by Cavsfan on 2016-06-04
This is a nice conky on Xubuntu 16.04 that doesn't take up a lot of room and is set so you can be surfing and still see the system information from VinDSL's conky.

[[IMG]http://en.zimagez.com/miniature/screenshot2016-06-0415-49-23.png[/IMG]]("http://en.zimagez.com/zimage/screenshot2016-06-0415-49-23.php")

[[IMG]http://en.zimagez.com/miniature/screenshot2016-06-0415-50-20.png[/IMG]]("http://en.zimagez.com/zimage/screenshot2016-06-0415-50-20.php")

Granted I have a 28" monitor but it is highly adjustable for even a laptop screen.

If you are interested just post some questions in this thread and someone will point you to the good stuff: [HOWTO: VinDSL Conky Script]("http://ubuntuforums.org/showthread.php?t=1771033")

I wouldn't start reading from page 1 though because a lot has changed. I would just post a question on the last page if you are interested.

---

### Post by izznogooood on 2016-06-04
> **HermanAB said:**
> Hmm, well, next time try Kubuntu.  Unity is just a slightly less cripple version of Gnome, so you should not expect too much of it.

Thank you for this extremely helpful comment.

---

