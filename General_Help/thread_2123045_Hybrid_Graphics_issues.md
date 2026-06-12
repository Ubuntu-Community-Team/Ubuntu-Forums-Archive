---
title: "Hybrid Graphics issues"
date: 2013-03-06
forum: General Help
---

### Post by Veuned on 2013-03-06
Hello all 

I have recently gone from windows 7 back to ubuntu on my HP Pavilion dm4-3011tx beats edition laptop with a Radeon HD 7470m and intell 3000 graphics.
In windows the catalyst controll centre controlled eveythign to do with the switching of my greaphics but in ubuntu i have downloaded and installed the linux verson and it says that it is unable to locate a installed device. i have tried a number of different things and have googles for hours on end tried vga switcheroo tried compiling drivers and the catalyst controll centere im just not having any luck with this at the moment. the main reason i want to work out the graphics is because of my battery life before i switched to ubuntu i could easily get 6 hours battery life but currently im only getting 1 hour if that and i play a lot of minecraft wich will work on linux but im currently only getting 20 ish fps aposed to the previous 160+ fps. another thing if i install any form of the amd driver manually compiled or whatever when i reboot and log in unity does not appear but my files and folders on my desktop do and i can access them also any application i have on my desktop will hapily open. any help with this issue would be apreciated and i dont want to be forced back to windows this quickly 

regards Veuned
[h=3][/h]

---

### Post by Mark Phelps on 2013-03-07
First of all, it's nearly impossible to read your post -- what with you mashing it all together like that!  Adding some blank lines would have helped.

Second, Hybrid Graphics is not supported well in Linux.  In Windows, the video drivers are provided by the folks that supply the laptops, in this case, HP.  But the same folks do NOT supply Linux drivers -- and the drivers available from AMD do not support Hybrid Graphics.

The few Linux solutions that work seem to involve turning off the more powerful of the graphics chipset -- which means disabling something you paid good money to get.

Sorry ... but until the laptop suppliers start supplying Linux Hybrid Graphics video drivers (which they're not likely to do) using Hybrid Graphics in Linux is always going to be a kludgy thing.

---

### Post by Veuned on 2013-03-09
my apologies at the time i was quite irritated and not thinking straight ill keep in mind that i should space out my wrighting a bit more so its easier to read.
i have made a bit of progress with this issue since then. 

from what i can tell vga switcheroo is able to enable the amd gpu in my laptop with the help of this script [http://asusm51ta-with-linux.blogspot.com.au/](http://asusm51ta-with-linux.blogspot.com.au/) and the ubuntu page on hybrid graphiccs here [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

the problem with it is that i get a notification saying atempting to switch to ati graphics in the top righ hand side of my screen but due to both the script and the page being out of date the gnome-sesson-save --logout part of this script isnt working because since then ubuntu switched to unity so the script cant stop and restart the xserver with that line.

so my next question is, is there a unity alternative to the gnome-sesson-save --logout feature if not im fine with just the xserver restarting alltogether im not going to be switching all the time so my sesson dosent have to be saved its not all that important.

regards veuned

---

