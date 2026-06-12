---
title: "Minimal bash like line editing is supported grub error"
date: 2018-07-10
forum: General Help
---

### Post by camcia on 2018-07-10
Hey, so this is my problem, I have a dual boot with Windows 10 and Kubuntu 18.04 installed. 

Today I was copying some fonts to my /usr/share/fonts, so I executed the console in the fonts folder I was going to move but by mistake I did /* instead of just * it was something like 

"sudo mv /mnt/Files/Fonts/Sansation//* /usr/share/fonts/truetype/" 

and it threw some errors and Firefox froze, so I opened the /usr/share/fonts folder and there was a boot folder plus some other files that souldn't be there, then everything was freezing and I tried to reboot or log out but it wouldn't do anything so I had to force shut down my laptop. When I turned it on again, it showed something like this in grub "minimal bash like line editing is supported grub", I can exit and boot into windows, so I did a clean Kubuntu installation but it's still showing that message in grub. 

I also tried this [https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/](https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/) but it won't work either. 

I ran the boot info script [https://paste2.org/42BvajJC](https://paste2.org/42BvajJC)

---

