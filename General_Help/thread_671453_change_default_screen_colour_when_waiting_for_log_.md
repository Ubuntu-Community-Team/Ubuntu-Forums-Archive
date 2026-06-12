---
title: "change default screen colour when waiting for log in"
date: 2008-01-18
forum: General Help
---

### Post by jimbo54321 on 2008-01-18
hi all,

i have altered my login screen and back ground colour using the login window settings in administration.
i have also changed my splash screen in preferences.

my problem is when i have logged in and the splash screen appears the background is still the default colour from when ubuntu was installed.

can this be altered?

i know its not really a problem just being fussy but have been customizing a bit recently and this one colour why i wait for my desktop picture to load is the only thing left i want to change, then i will finally be 110% happy with ubuntu with no current reason ever to return to windows.

It has took 6 months of perseverence with ubuntu to get everything working but hey it uses 3 times less memory then when i boot to vista, and runs a million times faster

RESULT!!!!!!!!!!!!

Thanks for your time

---

### Post by shadyedsan on 2008-01-18
open up a terminal and type sudo gedit /etc/gdm/PreSession/Default to open it with text editor and where it says Background=dab013 or something like that change it to the number of the color you want

---

### Post by shadyedsan on 2008-01-18
> **shadyedsan said:**
> open up a terminal and type sudo gedit /etc/gdm/PreSession/Default to open it with text editor and where it says Background=dab013 or something like that change it to the number of the colour you want

i forgot to mention the colour should really be given in hex value

---

### Post by jimbo54321 on 2008-01-18
bugger just altered it tried black from gimp 000000 now cannot boot ubuntu. in windows getting your terminal command to try and set it back in recovery console. but never used it before

---

### Post by shadyedsan on 2008-01-18
the command should have opened up the default file in text editor and where it says near the bottom of the text

if [ "x$BACKCOLOR" = "x" ]; then
 		BACKCOLOR="#000000"
fi

it's the BACKCOLOR="#000000" you should change. recovery console wont help as that's microsoft windows not ubuntu linux

---

### Post by jimbo54321 on 2008-01-18
backcolor is what i altered, i did not mean recovery console i meant at grub boot menu select latest kernel with (recovery mode) wrote after it.

when i try and start ubuntu it just goes to a black screen with the cursor in top left instead of showing me the login screen. can i get into the file i altered and change it back inthe recovery console for my kernel

---

### Post by jimbo54321 on 2008-01-18
forget everything i fixed it cheers.

your command had worked.

for some reason my pc had gone on a go slow. went for a beer came back and login screen was their. when i logged on the background colour had changed.

thankyou jobs a good un

---

