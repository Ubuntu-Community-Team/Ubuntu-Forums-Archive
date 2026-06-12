---
title: "Edgy upgrade screwed up my top panel"
date: 2006-10-27
forum: General Help
---

### Post by urIkon on 2006-10-27
After the upgrade of Edgy from Dapper, I started getting a few weird problems.  During the upgrade, icons kept switching themselves out to other ones, and error messages kept popping up saying Ubuntu couldn't find the icons or something akin to that.  Now, my top panel is all screwed up. The Applications, Places, and System area of the panel is completely blacked out unless I click on said area, and everything on the clock side of the panel is...garbled... would be the only way to describe it.  Also the boot splash doesn't load, I just get the white text detailing what is happening until the login screen appears. Aside from being annoying, I'm not sure if there are other, more serious problems associated with this?

Edit: As I use the machine more, more graphic problems become apparent, i.e. progress bars in azureus not displaying, etc.
I have no spiffy graphics card, and didn't have to install any extra drivers with dapper.

Edit 2: OR how would I just reinstall edgy... don't wish to wipe my partitions or anything, but just let this bad boy try again?

---

### Post by urIkon on 2006-10-27
After some toying I've discovered it has something to do with transparency...any ideas? Status bars on azureus are still all screwed up though so I don't know.

---

### Post by NoWhereMan on 2006-10-27
maybe try reinstalling ubuntu-desktop
sudo apt-get install ubuntu-desktop
it should download missing packages if any

bye

---

### Post by rudiz on 2006-10-27
sudo apt-get install --reinstall ubuntu-desktop

---

### Post by seamus7 on 2006-10-28
I have had a few applets on my desktop panel act funny when I try to make my panel transparent. If I use a solid color, they're all there and display fine. This is the only problem I've noticed since upgrading to Edgy. (fingers crossed)

---

### Post by Unconscious on 2006-10-30
Apparently it has something to do with transparency. As soon as I made it a solid color, the crap dissappeared. Is this a known bug? Has it been reported?

---

### Post by taiye on 2006-10-30
I found changing the driver in the xorg.conf file from "vesa" to "fglrx" got rid of the problem.

---

### Post by Unconscious on 2006-10-31
That won't work for me. My driver is "i810". Anybody have a solution for me?

---

### Post by seamus7 on 2006-11-13
Still can't find a fix for my transparency problems after I upgraded to Edgy... Some of the panel applets display multi-colored noise in the background instead of transparency when I set the panel background to any degree of transparency. (yes I know it's not true transparency that is being displayed)

---

