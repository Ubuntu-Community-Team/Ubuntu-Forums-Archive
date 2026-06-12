---
title: "clear xprofile"
date: 2017-05-10
forum: General Help
---

### Post by Alduins_Khajiit on 2017-05-10
I had edited my xprofile because I had a dell 1600x900 monitor and I needed that resolution but now I got a new monitor that is 1920x1080 and I am trying to follow the same steps to add 1920x1080_75 to the xprofile. I did the same nano xprofile in the terminal, I can add the new resolution but I do not need the old 1600x900 entries. It will not let me overwrite those old entries and I can only add stuff after the old entries.

The old entries have

```
xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
xrandr --addmode VGA1 1600x900_60.00
xrandr --output VGA1 --mode 1600x900_60.00
```

Which I want to remove.

So I can add

```
xrandr --newmode "1920x1080_75.00"  220.75  1920 2064 2264 2608  1080 1083 1088 1130 -hsync +vsync
xrandr --addmode VGA1 1920x1080_75.00
xrandr --output VGA1 --mode 1920x1080_75.00
```

I tried the 'replace text; keyboard shortcuts but no matter where I type and no matter how much I highlight, the old entries seem to be completely unaffected. Like if they are permanently in there and I cannot erase the text whatsoever.

I Googled 'Ubuntu clear xprofile" but didn't get any relevant results so I threw quotes around 'Ubuntu "Clear xprofile"' and then it said "No results for. searching without quotes." And the same junk results.

I find it hard to believe that nobody has ever asked this nor is there any kind of information on how to remove the old entries.

---

