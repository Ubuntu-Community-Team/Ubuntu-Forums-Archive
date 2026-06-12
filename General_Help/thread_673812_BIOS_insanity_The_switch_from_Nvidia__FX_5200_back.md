---
title: "BIOS insanity: The switch from Nvidia  FX 5200 back to Radeon"
date: 2008-01-21
forum: General Help
---

### Post by Semong on 2008-01-21
Ok I get home from work today to find a black screen on my monitor when I power up my computer. Upon further investigation I found out that apparently these W$ lusers I live with had bought an Nvidia GeForce FX 5200 for their computer and couldn't figure out how to make it work with windows XP. One of them got a thought into their head (yes a thought it's amazing) that the card was defective. In order to test this theory they took out my graphics card, put the NVIDIA card into my pci slot and started it up. Well ubuntu booted up just fine, read the card, prompted them to install the restriced driver and it worked like a charm. So they took the NVIDIA out and put my original card back in. Now for some odd reason Im getting nothing but a blank screen. I put the NVIDIA Card back in to my computer along with my old graphics card & went into my BIOS thinking that all I needed to do was set-up my video configuration but to my horror my BIOS doesn't have video config or any other option to select my card. Apparently it's supposed to auto-detect graphics cards (like it did with this f*cking NVIDIA card) and for some odd reason it isnt detecting my radeon. Hell, I even opened up the terminal and put in the command 'lspci -v' and it shows the NVIDIA but Ati Radeon RV100 QY is nowhere to be found. I thought, hey maybe they screwed up my graphics card so I put in my old dell card and got the exact same results. BIOS nor Ubuntu isn't detecting anything besides this damnable NVIDIA card. If there is anyone out there with any advice or suggestions at all I would be forever in your debt and greatly appreciate it.

---

### Post by Semong on 2008-01-21
bump

---

