---
title: "cli only only system and framebuffer"
date: 2008-01-29
forum: General Help
---

### Post by InDenial on 2008-01-29
hi all,

I have been trying out ubuntu with gnome a long time ago and I did not find it satisfying. I have a little ubuntu server only running though (headless with ssh access). I am running some console apps on it like irssi and hellanzb. I read a post though from someone about a cli only system with very interesting apps like finch(pidgin), fbi, etc.. all cli apps. 

My idea was to install that stuff on my little server (Pentium 200MMX..:D). Before I was going to try that on a running server I decided to install ubuntu 7.10 in vmware on my laptop. 

I have a MSI Megabook S270, AMD Turion 64, ATI Radeon X200M, resolution 1280*800

I tried changing /boot/grub/menu.lst by adding a vga statement and adding a video statement. any combination was a no go. 

I often got a message saying that I entered a wrong video code and after pressing enter I got a list to choose from. In this list were only 6 options and non of those gave the resolutions I wanted. (max 80*60).

Other things that happend were.. black screen, freezing at starting, just booting but without the right resolution. 

When I installed ubuntu I did get the nice Ubuntu logo so it should be working.

My questions are: 
1. Does anyone know how I can get this to work?
2. Is it the vmware that is the reason for this not working?
3. Is it the resolution that is not supported by vesafb?
4. What information do you need more to be able to help me?

Thanks in advance...

---

### Post by InDenial on 2008-02-11
Problem solved. Widescreen issue. Worked great on an old laptop with a normal screen.

---

