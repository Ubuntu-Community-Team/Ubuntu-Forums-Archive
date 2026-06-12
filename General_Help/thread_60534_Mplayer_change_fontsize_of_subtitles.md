---
title: "Mplayer change fontsize of subtitles"
date: 2005-08-28
forum: General Help
---

### Post by Nasso on 2005-08-28
I got an annoying problem with mplayer. I got working tvout and everything is just fine except for the subtitles, they are small!

I have tried to change the fontsize in /usr/local/share/mplayer/font/font.desc but that doesnt work! :(
have been googling like hell :/ can anyone help me?

---

### Post by ow50 on 2005-08-28
If you use gmplayer, you can do it the preferences dialog, if not you should edit ~/.mplayer/config.

The settings for the config file are: subfont-autoscale and subfont-text-scale. Check the [man pages](http://tivo-mplayer.sourceforge.net/docs/mplayer-man.html)  for the values they can take.

As an example here's the part about subtitles in my config file:
```
#==========
# Subtitles
#==========

# VobSubs
#========

# Align VobSubs (-1: as they want to align themselves)
spualign=-1

# Anti-alias VobSubs (4: best and slowest)
spuaa=4

# Default VobSub language to select
slang=fi,fin,en,eng


# Text-based subtitles
#=====================

# Find subtitle files (1: load all subs containing movie name)
sub-fuzziness=1

# Font
font=/home/osmo/.fonts/sapientsans/Sapi005.ttf

# Font encoding
subfont-encoding=unicode

# Subtitle file encoding
utf8=yes

# Resample the font alphamap (10: bold black outline)
ffactor=10

# Subtitle position (100: as low as possible)
subpos=100

# Subtitle alignment at its position (2: bottom)
subalign=2

# Font size (2: proportional to movie width)
subfont-autoscale=2

# Font blur radius (default: 2)
subfont-blur=1.0

# font outline thickness (default: 2)
subfont-outline=1.0

# Autoscale coefficient of the subtitle (default: 5)
subfont-text-scale=4.0

# OSD
#====

# Autoscale coefficient of the OSD elements (default: 6)
subfont-osd-scale=4.2
```

---

