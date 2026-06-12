---
title: "Hard Drive Problem? Can't install to hard drive from USB or VirtualBox"
date: 2014-05-05
forum: General Help
---

### Post by John_Ryan on 2014-05-05
I have an older PC; Dell Emachines el1200-07w; it originally ran Windows XP, ran fine for a while, it stopped connecting to the internet one day, i couldn't figure out why.  Years go by, I try to start it, learn that i can install missing drivers and it works again.  I decide to upgrade to Ubuntu 13.?? (saucy salamander) via USB boot.  It's cool, I play around with the theming, then realize mom and pop would actually use this computer if it had a Mac theme.  Couldn't get the dock to work, googling around, i figure i'll downgrade to an older distro, 12.something, i believe., where docky would work. Booting the older distro from USB, something didn't work and it asks "do you want to do something to your pendrive and maybe it will work?" (during this installation, too, it asks do you want to make this OS your permanent OS or something??) I say sure (to both of those things).  Still doesn't work, then when i try to boot from USB, my boot menu now recognizes my USBpendrive as a harddrive instead of a USB drive, i try to boot from it anyway, no luck.  Then I couldn't boot the previously working saucy salamander (via the original USB, and then a new USB), then I try to boot Mint Petra via USB(old and new) , doesn't work.  I burn Linux Mint petra to a DVD, it boots and installs fine. 

The part where the problem probably lies.... 

I checked the MD5sums, ran memtest and no problems, reformatted the harddrive when Linux mint was working from the USBs (Mint only ran when the USB was in, when i tried to install from there, i'd get errno5, saying the disc was scratched or the computer was too cool/hot)

Now that Mint is running fine after the DVD install, I installed virtual box, and am running backtrack 5, but I can't install from there.  This time at 40% i get "Errno 30 - Read-only File System, this is often due to a faulty cd/dvd..." same thing i got when i was trying to install saucy, mint from USB.  It's a Hitachi Hard drive.

---

