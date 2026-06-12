---
title: "Japanese font changed on uprade to 13.04"
date: 2013-04-30
forum: General Help
---

### Post by Stonecold1995 on 2013-04-30
Apparently, on upgrade from 12.10 to 13.04, the default Japanese font has changed.  While it looks *much* better when it's large, when it's at the default size for the web browser, terminal, applications, etc it looks TERRIBLE.

New font (larger):

[IMG]http://i44.tinypic.com/2lvmi6x.jpg[/IMG]

New font (size 9):

[IMG]http://i41.tinypic.com/orhunr.jpg[/IMG]

Old font (larger):

[IMG]http://i42.tinypic.com/200xrfs.jpg[/IMG]

Old font (size 9):

[IMG]http://i42.tinypic.com/2cpzw2g.jpg[/IMG]

Is there a way I can make the new font look smoother when it's smaller (anti-aliasing or something)?

---

### Post by jarekm9 on 2013-05-02
I agree as well, Japanese is unusuable. Clearly whoever chose it doesn't read or write Japanese. Even simple Kanji like &#27671;&#12434;&#20184;&#12369;&#12390;&#12288;is impossible to read unless I hit CTR-+ many times over. I want the previous font. Go to a website like msn.co.jp and try figuring out that mess... It's like having to read everything in comic sans font. Comic sans font isn't the default in English speaking countries, so why is that Japanese font the default?

---

### Post by Stonecold1995 on 2013-05-02
Some online forms use a different font...  Is there a way to download this font and set it as the default?

[IMG]http://oi44.tinypic.com/14jc7c3.jpg[/IMG]

[IMG]http://oi41.tinypic.com/160cyl0.jpg[/IMG]

---

### Post by Urzumph on 2013-05-18
After a bit of messing around I've managed to change the default fonts.

You need to create a directory /home/<yourusername>/.config/fontconfig and in it put a file called fonts.conf with the following text:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<!-- $XDG_CONFIG_HOME/fontconfig/fonts.conf for per-user font configuration -->
<fontconfig>

<!--
        use VL Gothic font when sans-serif is requested for Japanese
-->
<match>
        <test name="family">
                <string>sans-serif</string>
        </test>
        <edit name="family" mode="prepend">
                <string>VL Gothic</string>
        </edit>
</match>
<match>
        <test name="family">
                <string>serif</string>
        </test>
        <edit name="family" mode="prepend">
                <string>MS Mincho</string>
        </edit>
</match>

</fontconfig>
```

(You might want to change the font names to suit your tastes).

Next, you need to rebuild the font cache:
```
sudo dpkg-reconfigure fontconfig
```

And now you should have nicer looking fonts :)

(Note that this is a per-user change. If you have other users you'll either have to figure out how to change the system settings or do this change for every user)

---

