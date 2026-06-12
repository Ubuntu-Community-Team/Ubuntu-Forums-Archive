---
title: "Cannot switch keyboard input language in 22.04.05 LTS with Wayland"
date: 2024-10-14
forum: General Help
---

### Post by hedden on 2024-10-14
I have two computers running Ubuntu 22.04.05 LTS (64 bit), one a desktop and one a laptop.
On my desktop computer, I have installed several foreign keyboard input languages so that I can type in foreign languages. I can switch the keyboard input language by clicking on the two-letter language abbreviation in the upper right corner and selecting the language I want. It is also possible to configure a keyboard shortcut to accomplish this. I have installed the keyboard input languages on my laptop, however I cannot switch the keyboard input language. I have tried restarting, I have tried removing the keyboard input languages and reinstalling them, but it makes not difference. The only major difference that I can find between the computers is that the windowing system on my desktop computer is Wayland and that on my laptop is X11.
I installed Ubuntu on my desktop (which uses the Wayland windowing system and works) a long time ago; I installed Ubuntu on my laptop (which uses the X11 windowing system and does NOT work) more recently. I do not recall being asked which windowing system to use when I installed Ubuntu.
First, is there any way to configure X11 so that I can switch the keyboard input language? If not, is there a good explanation about how to change the windowing system to Wayland?
Thank you,
Tom

---

### Post by hedden on 2024-10-14
I realized that it is possible to switch the windowing system by clicking on the gear icon on the login screen, so I tried that. I reinstalled all the foreign keyboard languages and now everything works as expected.

---

