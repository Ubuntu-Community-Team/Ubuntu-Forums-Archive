---
title: "Avoid anti-aliasing for some font-sizes?"
date: 2004-11-05
forum: General Help
---

### Post by Julius on 2004-11-05
Is there anyway to disable anti-aliasing for a range of font sizes? I know KDE has got this option but in gnome it doesn't seem to exist. Some fonts and websites are actually readable with anti-aliasing disabled. With small font sizes, the text looks so blurry.

Thanks in advance.

---

### Post by diebels on 2004-11-05
You could do something to /etc/fonts/local.conf, see example around line 170 in /etc/fonts/fonts.conf.

But I think it's better to set a higher minimum font size in your web browser. Small fonts are for stupid designers.

Also if you have a high dpi monitor, go to fonts -> advanced in gnome-control-center and set dpi. Get your current dpi with "xdpyinfo | grep dots".

---

### Post by Julius on 2004-11-05
My /etc/fonts/local.conf it's just a small file. It only says something about subpixel rendering, and I'm not really sure what that is about, but I have seen similar options in advanced fonts configuration in gnome. 

"xdpyinfo | grep dots" says my current DPI is 101, but gnome fonts config says it's 96. I use 96 in windows anyway.

---

### Post by Julius on 2004-11-05
```

        <match target="pattern">
                <test qual="any" name="size" compare="less">
                        <double>10</double>
                </test>
                <edit name="antialias" mode="assign">
                        <bool>false</bool>
                </edit>
        </match>
        <match target="pattern">
                <test qual="any" name="pixelsize" compare="less">
                        <double>10</double>
                </test>
                <edit name="antialias" mode="assign">
                        <bool>false</bool>
                </edit>
        </match>

```

I have added that to my /etc/fonts/fonts.config file.
It does work OK, it will disable antialiasing for fonts that have less size than 8 or 9 actually. It works cool for every app except firefox: even though it works OK with webpages, the firefox GUI will still use antialiasing. This is something I can live with, I just wonder why it doesn't work on firefox. 

I'll post screenshots later.

---

