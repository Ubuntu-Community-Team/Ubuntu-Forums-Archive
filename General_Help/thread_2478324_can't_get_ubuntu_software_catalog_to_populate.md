---
title: "can't get ubuntu software catalog to populate"
date: 2022-08-23
forum: General Help
---

### Post by cryofreeze666 on 2022-08-23
i've built a new computer and installed ubuntu.  i did this because windows 7 was to much of a pain to install in this new hardware.  for some reason every time i turn on this computer it doesn't connect to the internet, and i have to turn the network connection off and back on again.  even after i do that the software catalog will not populate.  trying to find programs like MangoHUD, every time i manually type in mango's title it only brings up Goverlay.

my motherboard is a meg x570 unify (ms-7c35) with an amd ryzen 9 5900x 12 core cpu.  i installed the 22.04.01 version of ubuntu, and this is the first time i have come across this problem.  my other computers are running older versions of ubuntu and populate the catalog imediately. is there something i'm missing in the settings?  i've got everything set to automatic so i could get the other software and updates i need but it won't populate.  do i need to go back to an earlier version, is there a bug i haven't found mention of yet, or is there something in my bios messing with ubuntu?  i would truly appreciate the help, since i would like to turn this system into a miner.  thank you

---

### Post by cryofreeze666 on 2022-11-03
well, it doesn't seem to be working in 20.04 either.  for some reason i still have to turn my wired network off then back on whenever i want to use something as mundane as the internet.  have a feeling that this may be a password issue to my router.  learning the same way i did on windows breaking the **** out of it, and then fixing it on my own digging around in the program.  who said linux wasn't the same as windows  roflmao.

---

### Post by Holger_Gehrke on 2022-11-03
Do you mean you're stuck on a window with a stylized shopping back, a progress bar that doesn't move, and the text "Software catalogue is being loaded" ? Ubuntu Software / Snap Store / gnome-software / Software Center (same thing, all of them; just different names and a bit of cosmetics) seems to be prone to cache corruption. Try erasing the cache, it should be in a subdirectory of '~/.cache/' ('~/.cache/gnome-software' for gnome-software on XUbuntu 22.04, might be different for other flavours / variants of the app).

Holger

---

### Post by cryofreeze666 on 2022-11-15
> **Holger_Gehrke said:**
> Do you mean you're stuck on a window with a stylized shopping back, a progress bar that doesn't move, and the text "Software catalogue is being loaded" ? Ubuntu Software / Snap Store / gnome-software / Software Center (same thing, all of them; just different names and a bit of cosmetics) seems to be prone to cache corruption. Try erasing the cache, it should be in a subdirectory of '~/.cache/' ('~/.cache/gnome-software' for gnome-software on XUbuntu 22.04, might be different for other flavours / variants of the app).

Holger

well thank you for the response, all it took was for me to kill the shopping ap and i was able to populate the ubuntu software ap.  now i have to write a new thread looking for the open source drivers for my wired lan, still having to turn the network off then back on to use the internet.

---

### Post by cryofreeze666 on 2022-12-03
oh by the way none of that ever occurred, but now to the new wierd.  i just went to download a new cryptomining overclocking program since i purchased a radeon 6800 to work with my nvidia 3060ti.  GreenWithEnvy doesn't seem to work with radeon.  my problem is back, i open ubuntu software with the explore tab open, open the search bar, type in program names, and get no results found for everything.  even tryed searching for sudoku, got a list including the one i've installed.  why cant i find the alternative programs for green with envy? i'd like to overeclock my radeon properly.  

has nvidia turned into windows "the only game in town"?  the hardware companies say they support nothing but windows.  it looks like the guy who maintains green with envy is switching to radeon and is looking for someone to take his place maintaining the program.  kinda wishing i was more software savy, i'd build one for both since i use both.

---

