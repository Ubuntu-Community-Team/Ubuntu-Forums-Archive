---
title: "change default cpu scaling setting"
date: 2008-06-07
forum: General Help
---

### Post by Heggerud on 2008-06-07
#include <stdio.h>
int main()
{
    printf("Hello World/n");
    return (0);
} :lolflag:

anyway i have been an Xubuntu/Ubuntu user since 7.04 and off/on linux user since RedHat 8.0

well i built a microATX computer with an Athlon64 mobile 3400, i built it for playing Old Skool SNES/NES/GBx games on my s-video monitor and i keep my fans at a low rpm to keep it from sounding like an F-22, so i use the GNOME cpu scaling applet to keep it at 800Mhz & cool, but it defaults to back to "Ondemand" when i restart, which would be fine but it runs at 2.20Ghz when i use my emulators, so i set it to 800Mhz which works untill i restart my comp and it defaults to "Ondemand" so how do i set it to default to 800Mhz? :)

p.s. i'm running norm Ubuntu 8.04 32-bit

please be detailed, i'm no linux pro yet :mrgreen:

---

### Post by chavanak on 2008-06-07
Ondemand is the default setting. This is the ideal setting for scaling as the cpu power is used when it is necessary. There are threads related to this type "cpu scaling" in google mabe with ubuntu as suffix. But I recomend leaving this alone for majority of purposes (Even if the cpu sounds a bit). But then if you really want to do it, read the articles in this forum (search for it). Your question will be solved

---

### Post by Heggerud on 2008-06-07
yes "Ondemand" is fine for most things, but for my special application i need it to be 800Mhz for heat reasons, and i have not found anything on the forums yet, my post was the first thing to pop-up when i searched lol, but i will keep looking, if anyone could point me to a guide or something that would also help?

---

### Post by Heggerud on 2008-06-08
still need help

---

### Post by Heggerud on 2008-06-08
bump

---

### Post by unixg33k on 2008-06-08
I had the same problem - only way I found was to run the command line "cpufreq-selector" which ties into the applet.

I made a small script that ran "cpufreq-selector -g performance" and then put that script in the Session Startup Programs under System>Preferences>Sessions.  That made it go to performance.  If you do a "man cpufreq-selector", there's an argument "-f" that lets you manually enter a frequency in khz.  So, for 800mhz you'd do "cpufreq-selector -f 800000".


Hope that helps.

---

### Post by Heggerud on 2008-06-08
i fixed it [http://ubuntuforums.org/showthread.php?t=597998](http://ubuntuforums.org/showthread.php?t=597998) very easy!
Thanks for your help, this guide should work for you better also

---

