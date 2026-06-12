---
title: "Firefox in Edgy Flash Adverts appear on top"
date: 2006-11-12
forum: General Help
---

### Post by tedrogers on 2006-11-12
Hi,

I don't know if anyone else has this problem, but you know some websites have pop-up info in a box (on the same screen) when you scan you mouse over an icon or something...for example...on TV guides like [www.radiotimes.com](www.radiotimes.com)...well I have this issue where flash adverts appear on top of everything....so the pop-up box appears underneath the advert. This is most annoying.

Anyone else have this issue and know of a potential fix?

I know that I had to do some ammendments to the install of flash, found on this forum in the WIKI, because firefox crashed as soon as I installed flash....show here

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

The ultimate solution to this turned out to be much more simple....all I needed to do was set a default depth of 24 bits for my graphics. So I have pretty much ignored the above link in the WIKI now, undone any changes I made using it, and just set a default depth of 24 bits in my /etc/X11/xorg.conf

I have tested it since and it is definitely not an issue with 16 or 24 bits on the gfx, so now I'm stumped.

It also happens with Epiphany browser as well as Firefox, so maybe it's a plain old Flash thing.

Any advice appreciated.

---

