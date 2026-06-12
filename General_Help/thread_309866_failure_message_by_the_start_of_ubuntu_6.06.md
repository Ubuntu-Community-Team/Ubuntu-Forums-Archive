---
title: "failure message by the start of ubuntu 6.06"
date: 2006-11-30
forum: General Help
---

### Post by framfield on 2006-11-30
I got error message always when I start my system and also when I am going to keyboard configuration. The whole message you can see at: [http://fabik.co.uk/error.png](http://fabik.co.uk/error.png)

According that message I should include some information out of terminal. Here they are:

xprop -root | grep XKB:
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "gb", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "gb", "", ""

gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd:
layouts = [uk,sk]
model =
options = [grp grp:alt_shift_toggle]
overrideSettings = true

I've got this problem since I installed slovak language package ( i don't use it, always use english, but I need slovak keyboard sometimes) and after that I visited keyboard configuration and added slovak language. I got that message straight there after I added keyboard language. since that time I get this message always when I start my ubuntu 6.06. I can click on the message and it disapears, but slovak keyboard language doesn't work and I still can't change keyboard and have only GBr.
I am not a linux expert, so an easy explanation would be great if there is any or just a solution what to do to get both keyboards language working and stop appearing that failure message.
My laptop configuration is: Dell Inspiron 640m, centrino core 2 duo 2 ghz, 4 mb l2, 1 gb ram. intel 850 chipset.

---

