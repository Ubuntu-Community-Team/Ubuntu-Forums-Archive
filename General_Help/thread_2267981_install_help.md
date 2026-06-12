---
title: "install help"
date: 2015-03-05
forum: General Help
---

### Post by longshanks62 on 2015-03-05
hi.
I am new to linux although I have tinkered with it on and off, I use a windows7 set up on my desktop with two spare drives. What I want to do is install Ubuntu 14.04 LTS on one of these drives and create a dual boot system. what I need is a blow by blow how to install for idiots. many thanks
Brian

---

### Post by sudodus on 2015-03-05
Please describe your computer and its system! Otherwise we can only guess.

- Are you running in UEFI mode or BIOS/CSM mode?

Please specify
- Brand name and model of the computer
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

---

### Post by longshanks62 on 2015-03-05
Hi
PC is  home built around an ASUS M/B, AMD Phenom II x4 955 cpu 3.2 Ghz
Bios mode
4Gb Ram
ATI Radeon HD 5400 series graphics card
network adapter realtek PCIe GBE family controller

---

### Post by nerdtron on 2015-03-05
If you have two drives:

1. Connect one drive and install windows 7.
2. Disconnect first drive and connect second drive.
3. Install Ubuntu on the second drive (just use the auto install).
4. Reboot Ubuntu, just to confirm it's working.
5. Connect the windows Drive but be sure that the BIOS will boot first the Second (ubuntu) drive.
6. Now boot the computer and you should only boot into Ubuntu desktop.
7. Open terminal in Ubuntu and run "sudo update-grub"
8. After that reboot the computer and you should see that you are now able to choose which OS you want during bootup.

---

