---
title: "Ubuntu Won't Run After Login"
date: 2006-12-18
forum: General Help
---

### Post by superchief on 2006-12-18
I have created and setup a full ubuntu edgy machine. It all works fine until i reboot it. Once rebooted it experiences the following problem.

On first login, the screen res is set to 1024 x 768 and will not go any higher, i restart the interface (not sure the exact terminoligy so i will say ctrl + alt backspace) and the screen res goes back to 1280 x 1024. After i login in, the interface just sits there and never goes to the desktop.

Weird?

If anyone can point me in the right direction it would be great.

---

### Post by aliyanage on 2006-12-18
Hi there,

what happens when you shutdown and just normally boot the computer? do have the same issue?

regards
aliyanage

---

### Post by superchief on 2006-12-18
yep, shutdown completely to the point of switching plugs off, lol and then back on again.

Screen res problem, restart interace and then .... nothing. I have managed to get in once and i got an error with nautelus (i think thats how u spell it). But since then, no

---

### Post by aliyanage on 2006-12-18
I can't garantie for anything but go to command prompt and then try this:

```
apt-get install ubuntu-desktop
```

ps. after booting up just hit ctrl+alt+F2 to get to the command prompt
let me know how it worked :-)

---

### Post by Skat on 2006-12-18
Something similar happens to me.  After the last kernel update (2.6.17-10-generic) i am not able of getting to my desktop.  I do log in ing GUI mode, but it stays with the background of the login screen.

I tried to install kubuntu-desktop but it does the same thing... any ideas?

I`m usin 6.10

---

### Post by superchief on 2006-12-21
I tried that but alas it did not work, i have uninstalled my nvidia drivers because i thought that might be causing the problem and now i am unable to re-install them. Not only that, the problem is still there :(. And now my entire install is corrupt for some reason :(, i am not having much luck. Might it be worth going back one version of ubuntu, this seems a bit unstable

---

