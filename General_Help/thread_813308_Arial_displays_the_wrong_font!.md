---
title: "Arial displays the wrong font!"
date: 2008-05-30
forum: General Help
---

### Post by Sonja on 2008-05-30
In OO.o and Firefox, when something calls for Arial, instead of displaying the mscorefonts Arial that I installed, it displays some other random font that looks like scarabs or insects with letters inside them.

It's probably a poor quality, free font I downloaded at some point in my life, but for some reason it thinks of itself as Arial and manages to override the proper Arial on my computer. How do I track down what file it is and delete it?

I tried "locate arial" and it didn't find it. It's probably a different file name.

---

### Post by BoojiBoy on 2008-06-23
I am having this exact issue with Kubuntu 8.04, here are some examples:

In OpenOffice 2.4.1;
[IMG]http://lh6.ggpht.com/dishpan.hands/SGBfk7HqrtI/AAAAAAAAAuU/qmWe1but8UA/snapshot3.png?imgmax=576[/IMG]

In the Font Installer (it's ok here)
[IMG]http://lh5.ggpht.com/dishpan.hands/SGBfk6XFlII/AAAAAAAAAuc/20EKekx6W-U/snapshot1.png?imgmax=576[/IMG]

In KPDF:
[IMG]http://lh3.ggpht.com/dishpan.hands/SGBfkxIPhyI/AAAAAAAAAuk/sbfngNyl2RA/s800/tick1.png[/IMG]

In KPDF Print Preview (it's ok here)
[IMG]http://lh3.ggpht.com/dishpan.hands/SGBflCUujCI/AAAAAAAAAus/sRkawMBK36k/s800/tick2.png[/IMG]

I have tried removing and installing the MS-core fonts to no avail.

Thanks,
BoojiBoy

---

### Post by molotov00 on 2008-06-24
To install Microsoft TrueType Fonts (including Arial)
```
sudo apt-get install msttfont
```

For other fonts:
```
aptitude search font
```

I'm honestly not sure if that will fix your issue. But it's what I would try.

---

### Post by iaculallad on 2008-06-24
> **Sonja said:**
> 
I tried "locate arial" and it didn't find it. It's probably a different file name.

A way of locating/knowing if arial is installed in your system is:

```
xlsfonts | grep -i arial 
```

Note: If nothing displays when you issue that terminal command, arial font does not exist in your sytem.

---

### Post by molotov00 on 2008-06-24
@iaculallad

sudo apt-get install msttfont does install arial for me. But for some reason the command (xls...) does not return an arial font. Why might this be? Does xlsfonts truly include a list of ALL fonts on a system?

---

### Post by iaculallad on 2008-06-24
> **molotov00 said:**
> @iaculallad

sudo apt-get install msttfont does install arial for me. But for some reason the command (xls...) does not return an arial font. Why might this be? Does xlsfonts truly include a list of ALL fonts on a system?

Why could that be? Try using the pattern-matching capability of xlsfonts, use wildcard to replace the part of arial (ar*.*).

---

### Post by Borlag on 2008-06-24
> **molotov00 said:**
> @iaculallad

sudo apt-get install msttfont does install arial for me. But for some reason the command (xls...) does not return an arial font. Why might this be? Does xlsfonts truly include a list of ALL fonts on a system?

My install said that msttfont cound't be found so I looked around a bit and found another package that has it. So... the correct install command should be:

sudo apt-get install msttcorefonts

This one did include Arial, but apparently it doesn't include every one of the most used fonts in Windows. For example Tahoma seems to be missing from this package.

---

### Post by fragos on 2008-06-25
The file name will be "Arial.ttf". Run "locate Arial.ttf" and you'll find all posible Arial fonts. Look for the file that is different from the others and it may be the problem. My systems font file is /usr/share/fonts/truetype/msttcorefonts/Arial.ttf. Two other locations had simlinks to my only Arial.ttf. I don't share your problem.

---

### Post by jrusso2 on 2008-06-25
> **Borlag said:**
> My install said that msttfont cound't be found so I looked around a bit and found another package that has it. So... the correct install command should be:

sudo apt-get install msttcorefonts

This one did include Arial, but apparently it doesn't include every one of the most used fonts in Windows. For example Tahoma seems to be missing from this package.

If you have a Windows install around I just copy the fonts folder off windows and keep a copy of that around and when I want some Windows fonts I just copy the ones I want out of that.

---

### Post by Sonja on 2008-06-25
/usr/share/fonts/truetype/msttcorefonts/Arial.ttf
/var/lib/defoma/gs.d/dirs/fonts/Arial.ttf
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf


Is it one of those?

---

### Post by Zorael on 2008-06-25
Make sure that your **~/.fonts.conf** file isn't the culprit. It can hijack and redivert fonts, potentially causing what you're describing. Just close down OO.o, rename the file to something else, and open up OO.o again to see if it worked. Do note that it's prepended with a dot, so if it doesn't show up in Nautilus/Dolphin/* you need to toggle Show Hidden Files.

```
$ mv ~/.fonts.conf ~/.fonts.conf.backup
```


If it didn't help, then well, at least you know the error is elsewhere.

---

### Post by fragos on 2008-06-25
> **Sonja said:**
> /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
/var/lib/defoma/gs.d/dirs/fonts/Arial.ttf
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf


Is it one of those?

/usr/share/fonts/truetype/msttcorefonts/Arial.ttf is the actual font. The other two are symlinks which should point to the actual font. "ls -l" will give you 1 line per file with owner, permissions and simlinks.

---

### Post by talgise on 2008-06-28
> **fragos said:**
> The file name will be "Arial.ttf". Run "locate Arial.ttf" and you'll find all posible Arial fonts. Look for the file that is different from the others and it may be the problem. My systems font file is /usr/share/fonts/truetype/msttcorefonts/Arial.ttf. Two other locations had simlinks to my only Arial.ttf. I don't share your problem.

you are the man... i have be stuck on this truetype problem for like 4 days.  thanks a bunch

---

