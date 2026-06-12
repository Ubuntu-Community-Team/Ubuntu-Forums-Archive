---
title: "Compose Keys for keyboard layouts other than English"
date: 2020-11-18
forum: General Help
---

### Post by jchwenger on 2020-11-18
Hi,

I'm using Ubuntu 18.04 and am very happy, and come here with a small question on [compose keys]("https://help.ubuntu.com/community/GtkComposeTable")[:]("https://help.ubuntu.com/community/GtkComposeTable):") I know how to use them (and do so a lot!) in English, but often find myself in the odd position of having to switch to the English keyboard from a French one in order to input a special character. I could not find any indication as to whether compose keys are also available in other keyboard configurations, and if they differ depending on that, where is the list of CK for each language, etc. An interesting use case is the capital "c cédille", that I can type easily in English, like so: Ç, but not when my French keyboard is activated!

Any hint would be appreciated!
Best, and thanks in advance,
Jeremie

---

### Post by Impavidus on 2020-11-18
I've no difficulty typing Ç using the AFNOR-standardised AZERTY French keyboard layout on Xubuntu 20.04. Assuming your compose key is still a compose key (I use the key with the logo of that other operating system), the same character combinations should work. The key combinations may change – I have to type compose - q instead of compose ' a on my US keyboard when I use French layout to type á – but c and , are on the same keys in US and French (and UK) layout, so no change for Ç.

Different layouts don't only relabel the keys. In some cases certain positions on the keyboard may not have a separate key (for example, the key with the \ on my US keyboard, between the enter and backspace keys, doesn't exist on a French keyboard). If your compose key is one of those, it may not work properly.

---

### Post by Raffles727 on 2020-11-20
I also use use the "switch keyboard" technique for writing in French, à, ç, é, and è are easy enough but still haven't figured out how to do their capital forms with the keyboard, I use the character map.

---

### Post by jchwenger on 2020-11-30
Hi,

Thanks for your replies, and sorry for the delay! My keyboard is actually the UK one, and I'm then switching to QUERTZ (Swiss French). It must have something to do with the compose key, I wonder. Everything works fine with the UK layout, using Shift+AltGr, but none of the combinations (nor input in Unicode), seem to be activated on the other keyboard. I wonder if there is an option somewhere to know what the compose key is for each layout, whether there is one assigned, and how to do so. 

I found a hack with Tweaks: if I assign the compose key to, say, scroll lock, it works (strangely again, not if I assign it to AltGr, which works fine as the 3rd level selector in QUERTZ), but the default behaviour, Shift+AltGr, doesn't, which is a bit disappointing.

Maybe a fix has been introduced in Ubuntu 20, I've been meaning to upgrade for a while, that might just do it.

---

### Post by Impavidus on 2020-11-30
I've never tried with compose set to shift+AltGr. In fact, that option isn't even offered on Xubuntu 20.04.

---

### Post by Paddy Landau on 2020-11-30
> **Impavidus said:**
> I've never tried with compose set to shift+AltGr. In fact, that option isn't even offered on Xubuntu 20.04.
It's default on Ubuntu and Lubuntu. It's important to note that AltGr+Shift is different from Shift+AltGr, and that they are also activated differently.

So:

[LIST]
[*]**AltGr+Shift**: Press AltGr, and while holding it down, press Shift. *Don't let go* when pressing the next button(s). In the examples below, I indicate this with a plus-sign ([COLOR=#ff0000]+[/COLOR])
[*]**Shift+AltGr**: Press Shift, and while holding it down, press AltGr. *Let go* before pressing the next button(s). In the examples below, I indicate this with a comma ([COLOR=#ff0000],[/COLOR])
[/LIST]
Examples (on my keyboard; your keyboard might differ):

[LIST]
[*]AltGr+Shift [COLOR=#ff0000]+[/COLOR] 1 — results in the upside-down exclamation mark "¡"
[*]Shift+AltGr[COLOR=#FF0000],[/COLOR] 1[COLOR=#FF0000],[/COLOR] 1 — also results in the upside-down exclamation mark "¡"
[*]AltGr+Shift [COLOR=#ff0000]+[/COLOR] 4 — results in a quarter "¼"
[*]Shift+AltGr[COLOR=#ff0000],[/COLOR] .[COLOR=#FF0000],[/COLOR] = — results in a bullet "•"
[/LIST]
There are four "orders" (levels) to a keypress. Using the number 1, which when shifted (on my keyboard) shows an exclamation mark, here are the four orders:

[LIST=1]
[*]1 (i.e. unshifted) — results in 1
[*]Shift+1 — results in !
[*]AltGr+1 — results in ¹
[*]AltGr+Shift+1 — results in ¡
[/LIST]
Repeated with 4 (on my keyboard):

[LIST=1]
[*]4 — results in 4
[*]Shift+4 — results in $
[*]AltGr+4 — results in €
[*]AltGr+Shift+4 — results in ¼
[/LIST]
The four orders don't include the compose key Shift+AltGr.

Fun stuff! Try doing that in Windows :p
> **Impavidus said:**
> I use the key with the logo of that other operating system
Place of interest:

The "Windows key", on Linux, is known as the "Super key". On a Mac keyboard, it's the "place of interest" (&#8984;) symbol. Some non-Windows and non-Mac keyboards use a diamond (&#9671;) for the Super key.

You can reassign the Super key, but I'd leave it as is.

---

### Post by jchwenger on 2020-11-30
All this is super awesome!! I've been using it all for a while, so nice, although I'm far from really mastering it all. The very weird thing is that everything works when I'm using the UK variant, but only the actual compose key behaviour vanishes when switching to QUERTZ (French/Switzerland)(other alt, altgre, shift+altgre + key things work fine)....

---

