---
title: "Command line resolution"
date: 2013-01-29
forum: General Help
---

### Post by Gotti on 2013-01-29
So I almost have everything set up to my liking. Lightdm is disabled, startx starts fluxbox...everythings pretty much gravy.

The only complaint I have right now is the command like that I boot to (where I log in and start x from) has a very low resolution. The text is huge and looks awful. 

I have done a fair amount of googling on the issue, but every answer I can find deals with editing /etc/default/grub and uncommenting the following line:

GRUB_GFXMODE="1360x768x24"

I've done that...with no luck. Any other ideas out there? The point of me booting right to command line is to streamline the bootup process, so that I only have to load fluxbox if I need to. But I'm finding myself running startx right off the bat cause I can't stand to work with the huge font.

Thanks!

---

### Post by steeldriver on 2013-01-29
Did you check that 1360x768x24 is a supported mode (you need to drop to the grub prompt and run vbeinfo)?

Did you run sudo update-grub after editing /etc/default/grub?

You *may* also need to add

```
GRUB_GFXPAYLOAD=keep
```or
```
GRUB_GFXPAYLOAD=1360x768x24
```after the GRUB_GFXMODE line - I *think* otherwise the GRUB_GFXMODE value *may* only hold for the grub console itself - not for the post-boot VTs (but I'm confused about that, and I can't find clear documentation on the matter)

---

### Post by Gotti on 2013-01-30
Tried both of them...no luck. hmmmm...

---

### Post by SeanBlader on 2013-01-30
I will be interested to see if you get anymore pixels than 640x480 at 4 bit color out of your bios without loading a video driver that's run by X.

[http://en.wikipedia.org/wiki/Video_Graphics_Array](http://en.wikipedia.org/wiki/Video_Graphics_Array)

[QUOTE=Wikipedia]Video Graphics Array (VGA) refers specifically to the display hardware first introduced with the IBM PS/2 line of computers in 1987, but through its widespread adoption has also come to mean either an analog computer display standard, the 15-pin D-subminiature VGA connector or the 640×480 resolution itself.

...

VGA was the last graphical standard introduced by IBM that the majority of PC clone manufacturers conformed to, making it today (as of 2010) the lowest common denominator that almost all post-1990 PC graphics hardware can be expected to implement.[/QUOTE]

---

