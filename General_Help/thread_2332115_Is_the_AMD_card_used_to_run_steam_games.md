---
title: "Is the AMD card used to run steam games ?"
date: 2016-07-28
forum: General Help
---

### Post by stefanoskikristijan on 2016-07-28
Hey guys installed successfuly ubuntu 16.04 and downloaded steam to play dota2. I can successfuly awake the ```
AMD GPU with DRI_PRIME=1 glxgears
``` . But how can i tell that i run Dota 2 using it or what do i need to do to run the game using it ? Btw my card is Raden HD8500M which is supported.
Thanks.

---

### Post by kyrithis on 2016-07-29
The Radeon HD8500M is an integrated GPU for a laptop, so I'm able to guess that (unless you've installed a new graphics card), your laptop is most definitely using it. There are no other options for your computer (or any of your games) to use. This means that once you boot up a game, said game will automatically use that GPU.

---

### Post by stefanoskikristijan on 2016-07-29
> **kyrithis said:**
> The Radeon HD8500M is an integrated GPU for a laptop, so I'm able to guess that (unless you've installed a new graphics card), your laptop is most definitely using it. There are no other options for your computer (or any of your games) to use. This means that once you boot up a game, said game will automatically use that GPU.

No actually its hybrid graphics laptop, intel HD4000 + AMD HD 8500M and the amd card isnt used by default i think :/

---

### Post by &amp;KyT$0P# on 2016-07-29
Step 1 would be to run [FONT=Courier New]glxinfo[/FONT] in that specific way (instead of glxgears), and check if the information it outputs is consistent with what you expect.  Once you have that working how you like, then try with the game.  At that point I'd think any further required tweaking would likely be specific to the game itself.

---

