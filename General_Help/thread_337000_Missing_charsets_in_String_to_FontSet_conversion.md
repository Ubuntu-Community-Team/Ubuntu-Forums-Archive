---
title: "Missing charsets in String to FontSet conversion"
date: 2007-01-12
forum: General Help
---

### Post by os.getlogin on 2007-01-12
I did a new install of Edgy, but I'm having font problems.  When I start Matlab or xfontsel or any number of applications, I get:

```

% xfontsel                             
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset

```

I've tried to adjust my xorg.conf as indicated here: [http://www.ubuntuforums.org/showthread.php?t=268024&highlight=Missing+charsets+in+String+to+FontSet+conversion](http://www.ubuntuforums.org/showthread.php?t=268024&highlight=Missing+charsets+in+String+to+FontSet+conversion)

My new xorg.conf has a font path of:
```

Section "Files"
        # path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

```

After restarting X (ctrl-alt-backspace) it doesn't work.  Any ideas?

It's odd that all of the fonts are in /usr/share/fonts/X11 and not in /usr/share/X11

---

### Post by os.getlogin on 2007-01-12
It doesn't seem to matter.  If I do
```

LC_ALL=C xfontsel

```
then there are no warnings.  Nevertheless, either way does not impact the fonts as far as I can tell.  It's odd that the directories are incorrect though.

---

### Post by LeighLogan on 2007-01-17
I'm using Edgy as well and had noticed lots of errors about fonts. It didn't bother me until recently when I was trying to run a 3rd party package (Mathematica) and it would crash. It also gave font errors when I ran it. I decided to try to change my xorg.conf as per the link you mentioned above. 

I found that my font paths were set to "/usr/share/X11/fonts/..." rather than the "/usr/share/fonts/X11/..." location. 

I Commented the /X11/fonts lines and replaced them with /fonts/X11 lines. I rebooted and this worked for me. More of my font errors have stopped and, most importantly for me, Mathematica is running without crashing now!

I wonder if having both sets of FontPaths is causing some conflict for you. Have you tried commenting out the "old" font lines and just leaving the new ones?

--Leigh

---

### Post by os.getlogin on 2007-01-21
Yeah, I tried commenting them out.  I think it's just a path anyway, so it doesn't matter if there's anything there or not.  I'm about to install Mathematica myself, so this is good to know.

It seems there should be a bug report submitted.  Not sure how to do this though.  The font path is clearly wrong.

Later,
nate

---

### Post by longbow on 2007-05-01
I've encountered the same problem with matlab, still get no clue.

I've commented out the all the fontpath lines in xorg.conf. However, via "xset q", the correct fontpath is still listed.

So I guess there are other problems with edgy.

---

