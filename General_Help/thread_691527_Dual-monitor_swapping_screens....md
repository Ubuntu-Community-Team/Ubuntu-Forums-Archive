---
title: "Dual-monitor swapping screens..."
date: 2008-02-08
forum: General Help
---

### Post by Xiol on 2008-02-08
Hey folks, got a weird problem here.

I've got two monitors, both 19", one widescreen (1440x900 - via DVI) the other 'normal' (1280x1024 - via VGA). 

I've managed to get the monitors setup and working fine dual screen, passing windows around, etc, with a bit of fiddling and hand-configuring the config file. Then I discovered nvidia-settings, but that is besides the point.

My widescreen monitor is on the left, the normal one on the right. I want my widescreen to be my primary monitor and the other the secondary one, but I can't figure out how to swap the screens around so it shows up that way in nvidia-settings. I can't swap the leads around (which would be the simple option) as only the widescreen supports DVI and due to my setup here I can't plug it in via VGA. It seems that whatever is connected via DVI becomes the secondary monitor, with VGA taking preference.

I'm dual booting, and in Windows it's just a case of ticking a box and dragging the screens around, but this doesn't seem to be working under Ubuntu.

Long story short - My xbox and my PC are connected through the widescreen monitor, PC on DVI, XBox on VGA, so I can't swap them. Also due to physical positioning I can't have the normal monitor as my primary.

Ideas?

---

### Post by Zachre on 2008-02-08
Yes, I seem to be having the same problem my one monitor that is plugged in through a DVI adaptor is always the primary which is above and to the left and annoying to be the primary screen.

I have seemed to be able to mess around with xorg.conf enough that I got it to the point where they both become the primary yet are different desk spaces, hard to explain more along the lines that they both have the menu at the top but only one has the icons of my external HD and my downloads etc and they stay seperate, however i find it kind of annoying to have the menu on the one screen when i wouldn't be using it for that, any help would be greatly appreciated.

Thanks in advance Zach

---

### Post by Zachre on 2008-02-09
Update

Well it seems the only way I could figure out how to get my monitor as primary was to hook it up through VGA and add my secondary monitor as my DVI however,

My dual monitor setup is not side by side, but a little ajar'd, and when I use twin view my (as windows would say) start menu defaults to the secondary monitor again which is on the left, I am not sure why it likes the left monitor (which is up and ajar'd so much) and also when I position my monitors correctly the "dead space" zone is actually dead space where my mouse can still go and move about, which is strange as of using Separate X mode I essentially cannot move for ex: my firefox window to and from the monitors they are essentially separate.

Very strange, I am sure I will figure something out soon thou, my second time going through this I figured out there was no use in editing my xorg.conf but rather just use the nvidia-settings command.

---

### Post by Xiol on 2008-02-09
I've had a look at my xorg.config file (I come from a Gentoo background, so hand-editing configuration files is second nature) but I can't seem to see how to swap which one is primary and which one is secondary around. I was thinking you could just swap the screen definitions around, but I can only find one screen definition... Will have to take another look but I'm on Windows at the minute.

---

### Post by zoro on 2008-02-19
Let us know if you sort it out - I'm having the exact same problem.

Both monitors are working, my desktop icons appear on the left monitor (DVI) and the menus and new windows appear on the right one (VGA). I want the right one to be secondary, but it appears as though its primary no matter what.

Thanks,
Daniel

---

