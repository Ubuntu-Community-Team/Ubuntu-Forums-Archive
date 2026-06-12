---
title: "HOWTO: Use autohinter for some fonts, native for others"
date: 2008-04-22
forum: General Help
---

### Post by croddy on 2008-04-22
I've been troubled for some time by fontconfig-config's insistence that I select either the autohinter or native hinting for all font families on my system. For some, like the Bistream Vera/DejaVu fonts, the native hints look much better, particularly for bold text. But for other fonts on my system, the autohinter produces much more legible text.

Fortunately, it is possible to use the autohinter by default, and then override that configuration, using native hinting for an explicit list of fonts. I had some trouble finding an answer to this on the web so once I'd figured it out I thought it might be helpful to post here for others that shared the same frustration.

First, use debconf to set fontconfig to use the autohinter by default:
```
$ sudo dpkg-reconfigure --force -plow fontconfig-config
```
You'll be asked whether you want to use the Autohinter, Native, or None. Select **Autohinter**. (You'll also be asked what subpixel rendering mode you prefer and whether to enable bitmapped fonts. This is a matter of personal preference, but I recommend "Automatic" and "No".)

Second, write a local configuration that will override the autohinter for specific font families. Do this by editing /etc/fonts/conf.avail/51-local.conf, adding the section shown in bold:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
        <!-- Load local system customization file -->
        <include ignore_missing="yes">local.conf</include>

        <!-- Override autohinter for the fonts below-->
[B]        <match target="font">
                <test qual="any" name="family">
                        <string>Bitstream Vera Sans</string>
                        <string>Bitstream Vera Serif</string>
                        <string>Bitstream Vera Sans Mono</string>
                        <string>DejaVu Sans</string>
                        <string>DejaVu Serif</string>
                        <string>DejaVu Sans Mono</string>
                        <string>Verdana</string>
                </test>
                <edit name ="autohint" mode="assign"><bool>false</bool></edit>
        </match>[/B]
        
</fontconfig>

```

The font families shown here are simply an example. You can easily add a new "<string>Font Name Here</string>" line for any font for which you prefer native hinting.

Keep in mind that after saving the new configuration, you must restart any applications you want to follow it.

I have only tested this on 8.04 RC, but it should apply to 7.10 as well, since the fontconfig configuration layout is substantially identical.

---

