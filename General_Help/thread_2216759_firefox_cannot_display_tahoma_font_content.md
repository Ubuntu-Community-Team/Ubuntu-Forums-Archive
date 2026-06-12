---
title: "firefox cannot display tahoma font content"
date: 2014-04-13
forum: General Help
---

### Post by shahab3 on 2014-04-13
Hi,

I'm using firefox 28 on Ubuntu 13.10
Recently I installed tahoma font, but firefox renders arabic/persian tahoma content as empty. (can not display content)

I think this is a font file permission issue, because when run firefox as root (sudo firefox) it works correctly.

Would you please help me how to remove the problem? (I really need to run firefox with normal user not as root)

My system conditions:
- I installed package:  msttcorefonts
- I copied fonts: "tahoma.ttf" and "tahomabd.ttf" from a Windows systems to "/usr/share/fonts/truetype/msttcorefonts" and ran "sudo fc-cache -f -v"
- run firefox: The arabic/persian content render empty as though there is no text there.
- run sudo firefox: All text dispalyed correctly
- chrome works correctly.
- I checked the permissions of font files and gave maximum access to them. 
- I have another font files at "home/.font" directory.

Thanks

---

### Post by dragonfly41 on 2014-04-13
The font is owned by root ... do this ..

```
sudo nautilus
```
navigate to File System > /usr/share/fonts/truetype/msttcorefonts

select tahoma.ttf and right click > properties > permissions

change owner and group from "root" to your "username"

---

### Post by buzzingrobot on 2014-04-13
All the fonts in /usr/share/fonts are owned by root:

```
lrwxrwxrwx 1 root root     16 Apr 10 10:14 verdanab.ttf -> Verdana_Bold.ttf
-rw-r--r-- 1 root root 154264 Nov 12  1998 Verdana_Italic.ttf
lrwxrwxrwx 1 root root     18 Apr 10 10:14 verdanai.ttf -> Verdana_Italic.ttf
lrwxrwxrwx 1 root root     11 Apr 10 10:14 verdana.ttf -> Verdana.ttf
-rw-r--r-- 1 root root 139640 Nov 12  1998 Verdana.ttf
```

Does English text render correctly in Tahoma?

---

### Post by shahab3 on 2014-04-13
> **buzzingrobot said:**
> All the fonts in /usr/share/fonts are owned by root:

```
lrwxrwxrwx 1 root root     16 Apr 10 10:14 verdanab.ttf -> Verdana_Bold.ttf
-rw-r--r-- 1 root root 154264 Nov 12  1998 Verdana_Italic.ttf
lrwxrwxrwx 1 root root     18 Apr 10 10:14 verdanai.ttf -> Verdana_Italic.ttf
lrwxrwxrwx 1 root root     11 Apr 10 10:14 verdana.ttf -> Verdana.ttf
-rw-r--r-- 1 root root 139640 Nov 12  1998 Verdana.ttf
```

Does English text render correctly in Tahoma?

Thanks for reply ...

No, English text with "tahoma" font renders empty too. (I tested it by posting a multilingual text both in English/Persian at Facebook. The post whole is displayed empty in firefox)

What's your idea?

---

### Post by buzzingrobot on 2014-04-13
> **shahab3 said:**
> 
What's your idea?

I wish I had one.

Working when FF is run as root certainly suggests a permissions problem.  But, the fact that it works in Chrome suggests it isn't.

"fc-match tahoma" will display what font fontconfig is actually using.  I don't have Tahoma installed here, and it tells me DejaVu Sans is used when Tahoma is specified.  I do have Verdana installed, and "fc-match verdana" produces "Verdana.ttf: "Verdana" "Normal".

---

### Post by shahab3 on 2014-04-14
*Running "fc-match tahoma" result:*
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 14: reading configurations from ~/.fonts.conf is deprecated.
tahoma.ttf: "Tahoma" "Normal"

*and running "fc-match verdana result:*
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 14: reading configurations from ~/.fonts.conf is deprecated.
Verdana.ttf: "Verdana" "Normal"


I guess to trace the problem in two ways, bus as I am not linux expert I don't know how:

1. As firefox doesn't load tahoma in normal mode and does it in root mode, I guess there is log error in normal about permission denied error. But I cannot find the error log of firefox. How can find it?

2. Uninstall tahoma font and install it again. I removed fonts from "/usr/share/fonts/truetype/msttcorefonts/" directory and ran fc-cache. Also tested it with font-manager there was no tahoma font shown there. But chrome shows text with tahoma font exactly! (it means there is font available.) How to uninstall tahoma (or a font in general) completely from system?!

I really need to fix this issue, I use firefox as my main browser.

Thanks in advance

---

### Post by dragonfly41 on 2014-04-14
Try running firefox in gksudo mode to test the font ...

gksudo firefox

re: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by buzzingrobot on 2014-04-14
It's possible Chrome isn't using Tahoma.  Highlight a word, right click on it, select Inspect, and see which font it is using.

---

### Post by shahab3 on 2014-04-14
> [COLOR=#000000]Try running firefox in gksudo mode to test the font ...[/COLOR]

[COLOR=#000000]gksudo firefox[/COLOR]

I ran, it works correctly like when when run by "sudo". (run by root configuration)

> [COLOR=#000000]It's possible Chrome isn't using Tahoma. Highlight a word, right click on it, select Inspect, and see which font it is using.

[/COLOR]

I tested it. Chrome shows actually using tahoma. like when I run firefox by sudo or gksudo!

---

### Post by dragonfly41 on 2014-04-14
A tutorial ...

[http://www.wikihow.com/Install-TrueType-Fonts-on-Ubuntu](http://www.wikihow.com/Install-TrueType-Fonts-on-Ubuntu)

---

### Post by shahab3 on 2014-04-14
> **dragonfly41 said:**
> A tutorial ...

[http://www.wikihow.com/Install-TrueType-Fonts-on-Ubuntu](http://www.wikihow.com/Install-TrueType-Fonts-on-Ubuntu)

Thanks dear "[COLOR=#000000]dragonfly41"  but I read plenty of tutorials about this.

The fonts themselves are owned by "root" and it's correct. I guess fc-cache utility reads and caches them in a cash or template place like as "/tmp" with wrong owner. Do you know where fonts are cached on ubuntu? 

In other words I want to know about work mechanism of "fc-cashe" utility and so on ...

Thanks for your replies.

[/COLOR]

---

### Post by dragonfly41 on 2014-04-14
O.K. no more tutorials .. but there is one link below you might follow ..

On ubuntu 12.04 I have Font Manager 0.5.7 for GNOME desktop in Applications > Graphics > Font Manager

available through Software Centre


Also look through home/user/.fonts 

If this hidden folder is not there create one.

Drag your user font tahoma.ttf into there as user font.

For Microsoft derived fonts

$ sudo apt-get install msttcorefonts 

Update cache with 

sudo fc-cache -f -v 

[COLOR=maroon][later edit] .. run "man fc-cache" for instructions for usage[/COLOR]


(info from old thread .. [http://ubuntuforums.org/showthread.php?t=275202&page=7](http://ubuntuforums.org/showthread.php?t=275202&page=7)

see post #72 )

---

### Post by bapoumba on 2014-04-14
Any error if you start up firefox from a terminal ?

---

### Post by shahab3 on 2014-04-15
**Solved !!!**

Thanks guys for your replies. As my first guess it was a access level issue. As it wasted my time I write here the way I removed the problem maybe useful for others!

I removed all tahoma fonts from my system and watched firefox rendered text empty yet!
The font-manager tools showed there was no tahoma font available but tool: gnome-font-viewer showed tahoma available when is ran by root privileges! (so I found the problem is here) I used the following command to run gnome-font-viewer as trace mode:

```
strace -f -e trace=open gnome-font-viewer 
```

And finally I found the owner of this directory and its files (that was contain of tahoma.ttf fonts!!) were root not my username 

```
~/.local/share/fonts
```

[SIZE=4]**Conclusion:**[/SIZE]

Never use "**gnome-font-viewer**" for installing a font. It doesn't treat fonts as is usual in installing tutorials!

Let's enjoy firefox!

---

