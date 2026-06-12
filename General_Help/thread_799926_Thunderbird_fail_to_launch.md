---
title: "Thunderbird fail to launch"
date: 2008-05-19
forum: General Help
---

### Post by apogee on 2008-05-19
Hi there

I'm using Kubuntu 8.04

Everything was fine last week, this morning all hell has broken loose, and Googling all day has not yielded any solution yet.

Today, Thunderbird refuses to start. This is what I get in my terminal window:

```
ivan@apogee:~$ thunderbird

(thunderbird-bin:24005): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial Bold 12'

(thunderbird-bin:24005): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial Bold 27'

(thunderbird-bin:24005): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Trebuchet MS Bold 13.5'
*** Calendar schema version is: 7

(thunderbird-bin:24005): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial Bold 9'
Segmentation fault
ivan@apogee:~$

```

Some of the things I have already tried from Google searches include:
- Changed K > System Settings > Appearance > GTK ... > GTK Styles to use other. Ditto with KDE / GTK fonts
- Removed all recently installed apps that may have changed something somewhere.

If you need any other info, just tell me the command to type, or what buttons to click so I can reply with the correct info. (relative newbie here.) Thanks.

---

### Post by apogee on 2008-05-20
Now Firefox 3 Beta 5 (Build 2008041514) does not display fonts anymore ...

Please see attachment. Thanks.

---

### Post by apogee on 2008-05-21
Found my problem, and fixed it too (not bad for the new kid on the block, hehehehe :-)


a hidden folder : ~/home/.fonts
That folder all has symbolic links to the actual font files located in my fonts repository folder.

2 Problems:
1) Some of the actual font files had become corrupted. (Specifically tahoma.ttf and trebuchet.ttf)
Solution: restored good files from a Windows machine.

2) Some of the symbolic links to a few fonts no longer worked because the repository container folder had been renamed (none of these fonts were causing errors in the output window though, but probably would have at a later date.)
Solution: renamed the repository back to what it was so all the originals fonts can be properly located.

cheers.

---

