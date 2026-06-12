---
title: "[SOLVED] hd backup/reinstall dvd"
date: 2008-05-22
forum: General Help
---

### Post by grtgrampa on 2008-05-22
I need to make a backup/reinstall dvd for a hd partition. ==>> How?

I need Windows  :^(   for two reasons, my scanner isn't supported in Linux and neither is eBay Turbo Lister. Otherwise Windows would be outta' here!

I'm sure I'm not the only one suffering with this:
WinXP has done it to me again. Now I must reinstall it again from my WinXP recovery disk that was provided by HP, which begins by reformatting the hd into one big partition. Then I must spend time deleting the garbage that was bundled with it. Then I must reinstall the necessary software and hardware. Then cleanup and defragment. *** Then repartition. Then reinstall Ubuntu & Grub. Then "apt get" several times. Then I must reinstall my data.....OOPS.....I guess that shoulda' been the zeroth step !!! Back up data. Oh well.....

Wouldn't it be easier to burn a backup/reinstall dvd of a new, clean Windows partition that can be used to reinstall the partition at this point *** (see above) in the process when needed? There must be a way. I'm sure there's a way! I'm relatively new to Linux and Ubuntu, don't have the acronyms and buzzwords down yet, so need replies in regular English.
Someone Please Help.
.....John

---

### Post by mikewhatever on 2008-05-22
Take a look here [http://www.clonezilla.org/](http://www.clonezilla.org/). Looks promising, though I can't vouch for it yet.

---

### Post by grtgrampa on 2008-05-24
Dear Mikewhatever,  Thanks for the tip. I downloaded Clonezilla and burnt it to a bootable CD. Their instructions were complete and easy to follow. Using their directions on their internet page and on the screen I made an image of my WinXP partition and put it on my Linux partition after only the second try, it took about 2 hours. Then I rebooted and deleted all files from my Windows partition (yeah, I remembered to backup data first). I checked to make sure the partition was empty. Then I rebooted again into Clonezilla and restored the Windows partition from the image., it took about 15 minutes. When I rebooted again into Windows it was all there and working perfectly. 
.....John

PS The image was too big for dvd and my external HD was full of other stuff. Now I've got to figure out how to store the large images off the HD. Or maybe a new clean WinXP image with no data or other software will be small enough for dvd ..... or maybe I should buy an external HD dedicated to images ..... or ?

---

