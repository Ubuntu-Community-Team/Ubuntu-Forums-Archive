---
title: "Colors in ncurses-based apps (think MC) are wrong in terminal"
date: 2022-02-06
forum: General Help
---

### Post by Freek07 on 2022-02-06
On one of my machines, the colors in terminal are wrong. 
Instead of dark-blue , midnight commander is cyan. Frame buffer is enabled, but tput --colors reports only 8 colors.

Via X terminals, colors are fine - so it must be a shell (and not ncurses) thing.
To give you an idea, I have the thing on the right side; it should be the theme on left side (image borrowed from web): 
[IMG]https://user-images.githubusercontent.com/685879/55087737-dcc3e980-50aa-11e9-91f8-f24a7e35cdba.png[/IMG]

I have installed ncurses-term, but it's the same...

---

### Post by schragge on 2022-02-06
> **Freek07 said:**
> but tput colors reports only 8 colors.
I guess that's the reason. See [256 colors in console (tty)](https://unix.stackexchange.com/questions/254234) @U&L SE.

I'd just select another skin from **/usr/share/mc/skins/**. E.g., try
```
MC_SKIN=dark mc
```

---

### Post by The Cog on 2022-02-06
What kind of terminal does your commadn prompt think you have?
My local terminal says this:
```
~$ echo $TERM
xterm-256color

```

---

### Post by schragge on 2022-02-06
@**The Cog**. As I understand the question, the OP asks about Linux console. So their TERM must be **linux**.

---

### Post by Freek07 on 2022-02-08
Thank you. 
First, I'm talking about console (non-GUI). 

My term is linux (I tried changing it to other values but it didn't fix my problem).

I tested this on more machines (1x ubuntu, 1x KDE Neon, 2x debian, 1x raspbian). All Debian & clones :)

All have the same TERM value ('linux'), tput colors returns 8 colors for all of them.
However, when I run colortest-8, I get different shades of same colors.
I can't screenshot the console, but the difference for blue is as on the screenshot above.

Curiously, both original Debian machines display colors """correctly""", but ubuntu, neon and raspbian don't (they display those light shades instead of dark ones).

When I run fbterm, colors in all machines with "wrong" colors get "fixed". But I'd like to use basic terminal.

So I'm not really sure what to try now - it looks like the color support is OK, but the palettes are off.
Can that be changed somewhere?

---

### Post by schragge on 2022-02-08
On my Ubuntu 20.04 LTS install there are two palettes: **/etc/console-setup/vtrgb** and  **/etc/console-setup/vtrgb.vga**. Choose the one you like more:
```
sudo update-alternatives --config vtrgb
sudo systemctl restart setvtrgb
```
Or edit/create your own, then
```
sudo update-alternatives --install /etc/vtrgb vtrgb /etc/console-setup/vtrgb.custom 99
```

[Coping With Color on the Linux Console (and XTerm and friends)]("https://www.n0nb.us/blog/2020/02/coping-with-color-on-the-linux-console-and-xterm-and-friends")
[Configure VGA colors linux (ubuntu)]("https://superuser.com/questions/1185824")

---

### Post by norobro on 2022-02-08
> **Freek07 said:**
> Can that be changed somewhere?Have you tried changing the gnome-terminal Palette? 

hamburger -> Preferences -> "select profile" -> Colors

---

### Post by Freek07 on 2022-02-08
Yes, changing to non-default second palette (vtrgb) fixed the colors.
I can finally see my files in mc :)

Thank you :)

---

### Post by norobro on 2022-02-08
You're welcome! I went a couple of rounds with that once upon a time. 

I set the gnome-terminal palette to "Linux terminal" and use the mc46 skin which gives me bright white text on a dark blue background. My daughter calls it 70's style.

---

