---
title: "Firefox blurry fonts"
date: 2007-03-02
forum: General Help
---

### Post by frychiko on 2007-03-02
Feisty is bloody awesome and there's only one thing stopping me making a full switch to Linux and the problem is below. 

Does anyone know how to, or at least point me in the right direction on how to remove aliasing on Japanese fonts in Firefox? They are very blurry unlike in Windows XP.
There is no anti-aliasing on Japanese fonts elsewhere in the system. (apart from OpenOffice, but I will look into that later.)

You can see here in the below examples:

**System (desktop, notepad etc) VS. Firefox**
[IMG]http://pigster.net/other/system-vs-browser.png[/IMG]

**Browsers: Linux Ubuntu VS Windows XP**
[IMG]http://pigster.net/other/browser-linux-vs-xp.png[/IMG]

cheers!

---

### Post by frychiko on 2007-03-02
Okay, found a solution.

You need to copy windows japanese fonts over to linux. You can find how to do this below:
**[http://po-ru.com/articles/os-x-quality-font-rendering-in-ubuntu/](http://po-ru.com/articles/os-x-quality-font-rendering-in-ubuntu/)**

After this, I found some information regarding removing ant-aliasing on chinese characters:[B]
[http://wiki.debian.org.hk/w/Make_Debian_support_Chinese_(eng)#Installing_FireFly_Bitmap_Fonts_.28Recommended.29](http://wiki.debian.org.hk/w/Make_Debian_support_Chinese_(eng)#Installing_FireFly_Bitmap_Fonts_.28Recommended.29)[/B]

So basically, merge the below with the fonts.conf file from the first website. Instructions on where to put the file can be found on the first website.

```

<match target="font">
  <test name="pixelsize" compare="less_eq">
    <double>16</double>
  </test>
  <test name="family" compare="eq">
      <string>MS Gothic</string>
      <string>MS Mincho</string>
      <string>MS PGothic</string>
      <string>MS PMincho</string>
      <string>Kochi Mincho</string>
      <string>Kochi Gothic</string>
  </test>
  <edit name="embeddedbitmap" mode="assign">
    <bool>true</bool>
  </edit>
  <edit name="antialias" mode="assign">
    <bool>false</bool>
  </edit>
</match>

```

See the screenshot below to see what the outcome looks like:
[IMG]http://pigster.net/other/ubuntu-fonts.png[/IMG]
Just like windows XP, great!

---

### Post by frychiko on 2007-03-02
Only problem left is that fonts are mono-spaced, working on a solution...

---

