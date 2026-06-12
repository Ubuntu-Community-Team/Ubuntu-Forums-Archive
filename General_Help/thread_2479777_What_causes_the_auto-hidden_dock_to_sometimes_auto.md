---
title: "What causes the auto-hidden dock to sometimes auto-reveal?"
date: 2022-10-06
forum: General Help
---

### Post by Mountaingod on 2022-10-06
I want to find out what triggers the Dock to reveal when auto-hidden.

Some examples (the Dock is always set to auto-hide and starts out hidden):

1. I have my browser open, and messaging software open in front of that.
I click a URL in the messaging software for opening in my browser.
A new tab opens in my browser, focus shifts from messaging software to browser such that the latter is foregrounded,
**and the Dock reveals on the left of my screen for a second, before hiding again**.

Note that the Dock does not reveal in this way when alt-tabbing between windows.

2. I have Virtualbox running a VM in full-screen. Assorted application windows behind that.
**The dock will randomly reveal on the left of my screen for a second, before hiding again**.
Often I believe this could be triggered by notifications in Ubuntu, or maybe is part of wider Virtualbox jankiness wrt keeping/losing focus:

[https://askubuntu.com/questions/1196175/mouse-suddenly-stops-working-in-ubuntu-running-as-guest-in-virtualbox]("https://askubuntu.com/questions/1196175/mouse-suddenly-stops-working-in-ubuntu-running-as-guest-in-virtualbox")
[https://superuser.com/questions/1718057/mouse-not-working-on-virtualbox-6-1-34]("https://superuser.com/questions/1718057/mouse-not-working-on-virtualbox-6-1-34")
[https://www.quora.com/Why-can-I-move-my-mouse-but-cannot-click-in-a-VirtualBox-with-Ubuntu]("https://www.quora.com/Why-can-I-move-my-mouse-but-cannot-click-in-a-VirtualBox-with-Ubuntu")

I could probably remember more examples with time; basically this Dock behaviour seems quite janky / random and I want to understand what causes it.
[B]Desired behaviour would be, auto-hidden Dock only reveals when the mouse cursor touches the left edge of the screen, or there are no application windows open so the desktop is visible.
[/B]

I am prepared to do some picking apart of the Dock software to investigate this, but would be new to doing it.

---

