---
title: "Time between consecutive key strikes"
date: 2015-05-31
forum: General Help
---

### Post by happyytilton on 2015-05-31
I have a multi-boot laptop (Dell E1705) with Win XP, Mint 17.1, and Ubuntu 14.04 LTS.
I'm having trouble typing from the keyboard and that is, the delay time between consecutive key strikes is way too long. I have to be deliberately slow when typing, for if I'm too quick the 2nd key-strike is not accepted (appears to be ~3/4sec between presses), and I'm a slow typer.

For example....
typing the word "too", usually yields "to",
using the backspace key has to be done slowly, unless key is held down.

This does not happen in Mint 17.1 or Win XP, so I know it is not the computer nor the keyboard. It has to be a keyboard setting in Ubuntu, itself.
I've been to, All Settings -> Keyboard, and the only options there are for, "Key presses repeat when key is held down", but nothing for repetitive key-strikes.

I hope I've explained this well enough.

---

### Post by v3.xx on 2015-05-31
Ubuntu (Unity) is resource demanding.  Is your laptop up to it?

Could also be a matter of settings and/or drivers.

What are your laptop specs?

---

### Post by happyytilton on 2015-05-31
Would not think the laptop is the problem.
1.83GHz dual core 32bit
2Gb Ram
7200rpm 160Gb HDD

Didn't do this before, just started noticing this about 10 days ago. I'd say a setting, somewhere got changed.
As I said, it does not happen in Mint 17.1 or XPPro.

---

### Post by v3.xx on 2015-05-31
Sign into your guest account, see if its the same.

---

### Post by HermanAB on 2015-05-31
Here is something:
[https://askubuntu.com/questions/140255/how-to-override-the-new-limited-keyboard-repeat-rate-limit](https://askubuntu.com/questions/140255/how-to-override-the-new-limited-keyboard-repeat-rate-limit)

And this:
System Settings > Universal Access > Typing > Bounce Keys

Set the toggle for Bounce Keys to on and adjust the delay to as short as is necessary to remove the bouncing issue, but not so short that you end up typing "adres" instead of "address".

---

### Post by happyytilton on 2015-05-31
> **HermanAB said:**
> 
And this:
System Settings > Universal Access > Typing > Bounce Keys

Set the toggle for Bounce Keys to on and adjust the delay to as short as is necessary to remove the bouncing issue, but not so short that you end up typing "adres" instead of "address".

That was exactly what it was doing and is the answer to my problem.

---

