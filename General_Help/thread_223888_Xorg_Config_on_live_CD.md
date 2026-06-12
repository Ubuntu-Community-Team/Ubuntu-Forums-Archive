---
title: "Xorg Config on live CD"
date: 2006-07-27
forum: General Help
---

### Post by sjw on 2006-07-27
Hi Ubuntu's

I'm building a Badger-based LiveCD for some training, and I've got one fairly major problem bugging me.

We've preseeded most of the information that you would normally get prompted for(location, language, etc), but we still get prompted to set the screen resolution during boot.

Is the Preseed directory the right place for this information, or is it somewhere else?

thanks

---

### Post by bazzer on 2007-08-01
if most of your other preseed info works it's in the right location. I've just solved a small issue with a preseed file with this little snippet:

```
xserver-xorg xserver-xorg/autodetect_monitor boolean true 
xserver-xorg xserver-xorg/config/display/modes multiselect 1280x1024, 1024x768, 800x600 
xserver-xorg xserver-xorg/config/monitor/lcd boolean true 
xserver-xorg xserver-xorg/config/monitor/selection-method select Medium 
xserver-xorg xserver-xorg/config/monitor/mode-list select 1280x1024 @ 60 Hz
```

The main problem I was encountering was that the modes weren't being picked up by the system, due to me cutting and pasting from various websites. Turned out the 'x' in between the horizontal and vertical dimensions weren't 'x's after all, they were superscript 'multiplied by' characters...  D'oh! 

The above code works with Feisty, for Dapper you may have to replace xserver-xorg with xserver-xfree86 but ymmv

---

