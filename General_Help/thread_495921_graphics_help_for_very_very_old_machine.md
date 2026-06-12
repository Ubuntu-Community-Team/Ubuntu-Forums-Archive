---
title: "graphics help for very very old machine"
date: 2007-07-08
forum: General Help
---

### Post by marshall.robert on 2007-07-08
Hi, im putting some life back into an old pc (a whopping 233mhz overclocked to an almighty 266mhz and 160mb ram, 2mb ati rage pro graphics!)for my dad with xubuntu and i cant seem to get the resolution higher than 800 * 600, and i know that it has gone up to 1024*768 before, but that was under windows me. i have tried dpkg-reconfigure xserver-xorg and that didnt take it any higher... i also plugged in a pci graphics card but upon boot up it went all funky and colourful with lots of symbols...

so if anyone has any possible solutions to this problem they will be greatly appreciated

-rob

---

### Post by AlexThomson_NZ on 2007-07-08
2mb gfx isn't much- are you sure you are not trying to get 1024x768 24bpp or something?

---

### Post by marshall.robert on 2007-07-10
depending on what bpp is, then probably. is 24 too much?

---

### Post by AlexThomson_NZ on 2007-07-10
bpp = bits per pixel (ie. how many colors are supported)

To render 1024x768 = 786,432 pixels

Each pixel is 24 bits, so that's 18,874,368 bits on a screen

That's 2,359,296 bytes = 2.25Mb, so that's why I think you are failing.

You might have to drop down to 16-bit mode, or even 8-bit.

---

### Post by marshall.robert on 2007-07-10
oh right, i get it now. ill probably try tomorrow as its a bit late now and i shall be turning in soon. if i drop down to 16 bit then it should be about 1.5mb so hopefully that will work

cheers :)

-rob

---

### Post by AlexThomson_NZ on 2007-07-10
No prob- good luck!

---

### Post by marshall.robert on 2007-07-11
it worked, thanks for your help :)

-rob

---

