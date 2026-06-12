---
title: "Lubuntu main screen change from second screen?"
date: 2017-08-20
forum: General Help
---

### Post by dfuu on 2017-08-20
Hi!
I am trying to install Lubuntu on my old laptop (acer aspire 7745g but it shouldn't matter for this issue). The problem this laptop has is very simple: the screen display doesn't work anymore, other than that everything works perfectly. That's fine, i'm just plugging a monitor in my VGA out and things are okay.

So, i'm booting from a bootable usb containing Lubuntu 16.04.3 and go directly in the live session (I can't install directly from the installer because the install gets stuck on the "preparing ti install lubuntu" screen, likely because of corrupt files so I want to sort the problem from the live-session first).

My problem is my external monitor is considered "screen 2" of an extended display by default, meaning I don't have access to the menu, i can't launch a terminal...etc... All I can do is clicking on "install lubuntu" (but I have some gparting to do beforehand otherwise it fails) and the trash bin.
I won't question why the extended display is default on a live-session because it simply makes no sense: What do I do?

This is the first time I'm using ubuntu (I'm on debian on my other computers, I want this one under ubuntu to be able to play some games without having to dual-boot a windows session), I don't know where things are, the keybinds..etc... even tough after checking I found that there is none by default to bring a terminal out.

So, is there something simple I can do or do I go back to another distribution right away?

Thanks in advance,
dfuu

---

### Post by dfuu on 2017-08-20
=> Right click in the desktop, desktop preferences => desktop icons => display "my documents"
=> open my documents, tools => open current folder in terminal
And now you have a terminal so you can start to do things.

In the terminal
x@x: xrandr --query
get the name and resolutions of the screens. you want to exchange the positions on the primary and secondary since the leftmost screen is automatically considered primary
Remember to check the resolution of the monitor you want to use as primary as (n x m) because you want to place the new secondary screen just after the first once.

x@x: xrandr --output "screen1" --pos nx0 --output "screen2" --pos 0x0 for me it was (so that you have a model)

x@x: xrandr --output LVDS --pos 1600x0 --output VGA-0 --pos 0x0

I have no idea how I change the title of the thread as "solved".

---

