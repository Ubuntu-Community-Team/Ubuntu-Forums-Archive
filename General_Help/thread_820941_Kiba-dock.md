---
title: "Kiba-dock"
date: 2008-06-06
forum: General Help
---

### Post by Kaneda187 on 2008-06-06
Hey guys thought Id share this with everyone,
I found this on the net I think its great fun and a great dock!

Dont forget to say thanks! Enjoy


sudo aptitude remove automake1.4

sudo aptitude install automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev checkinstall libglade2-dev

wget [http://usuarios.lycos.es/abrahamtamayo/kiba-dock-0.1.tar.bz2](http://usuarios.lycos.es/abrahamtamayo/kiba-dock-0.1.tar.bz2)

tar -xf kiba-dock-0.1.tar.bz2

cd kiba-dock

./autogen.sh

make

make install-schemas

sudo make install

---

### Post by Kaneda187 on 2008-06-07
Let me know how you get on if you install! ;)

---

### Post by HpZ on 2008-06-07
I'm already usng AWN. Is Kiba better than AWN?

By the way, nice little how to. Simple and easy to follow :)

---

### Post by knx2 on 2008-06-07
I have been waiting to get kiba-dock to work with the physics!!!! Thank you works perfect on hardy!

---

### Post by Kaneda187 on 2008-06-07
> **HpZ said:**
> I'm already usng AWN. Is Kiba better than AWN?

By the way, nice little how to. Simple and easy to follow :)
well I prefer it to awn, its more fun! the physics engine works really well! you should give it a try!;) search it on youtube and see what you think when you see it in action! 
enjoy and dont forget to say thanks

---

### Post by Kaneda187 on 2008-06-07
> **knx2 said:**
> I have been waiting to get kiba-dock to work with the physics!!!! Thank you works perfect on hardy!
yeah it works great!:) i spend way too much time just tweakin the physics and messin around with it!

enjoy!

---

### Post by knx2 on 2008-06-07
Well I rebooted and now kiba is broke.. 
All i get is (kiba-dock:6776): GLib-CRITICAL **: g_rand_int_range: assertion `end > begin' failed

Actually my fault... I changed the monitor number over 1 and that is why... just changed it back and now it works again! ;)

---

### Post by DXM31 on 2008-06-07
Whenever I try this I get a 404 on the wget:confused:

---

### Post by Blackrose75 on 2008-06-08
> **DXM31 said:**
> Whenever I try this I get a 404 on the wget:confused:

i have the same problem on this command line - wget [http://usuarios.lycos.es/abrahamtama...ck-0.1.tar.bz2](http://usuarios.lycos.es/abrahamtama...ck-0.1.tar.bz2) - 

it says . . .

HTTP request sent, awaiting response... 404 Not Found
03:03:29 ERROR 404: Not Found.

can someone care to help???

---

### Post by oon on 2008-06-08
> **DXM31 said:**
> Whenever I try this I get a 404 on the wget:confused:

right click and copy link location > [http://usuarios.lycos.es/abrahamtamayo/kiba-dock-0.1.tar.bz2](http://usuarios.lycos.es/abrahamtamayo/kiba-dock-0.1.tar.bz2)

and paste in you Terminal / console
> 
oonboy@MyUbuntu:~$ wget [http://usuarios.lycos.es/abrahamtamayo/kiba-dock-0.1.tar.bz2](http://usuarios.lycos.es/abrahamtamayo/kiba-dock-0.1.tar.bz2)
--14:35:17--  [http://usuarios.lycos.es/abrahamtamayo/kiba-dock-0.1.tar.bz2](http://usuarios.lycos.es/abrahamtamayo/kiba-dock-0.1.tar.bz2)
           => `kiba-dock-0.1.tar.bz2'
Resolving usuarios.lycos.es... 213.193.4.11
Connecting to usuarios.lycos.es|213.193.4.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 87,890 (86K) [application/x-tar]

100%[====================================>] 87,890        15.31K/s    ETA 00:00

14:35:24 (15.29 KB/s) - `kiba-dock-0.1.tar.bz2' saved [87890/87890]

Thanks :D

---

### Post by Kaneda187 on 2008-06-08
good job! thanks!

dont forget to say thanks if you like the dock!

---

### Post by Aa1usa on 2008-06-08
Hey I am having a problem. 

I'm in Ubuntu 8.4 and after the last step I type in "kiba-dock" and the a little blue circle with lines in it opens at the bottom of my screen. 

If I right click on it then I get options for things that I can edit the kiba dock but It always looks the same.

When I was making it I had some "nothings" also.


[QUOTE=]
aa1usa@aa1usa-desktop:~/kiba-dock$ make
make  all-recursive
make[1]: Entering directory `/home/aa1usa/kiba-dock'
Making all in akamaru
make[2]: Entering directory `/home/aa1usa/kiba-dock/akamaru'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/aa1usa/kiba-dock/akamaru'
Making all in dock
make[2]: Entering directory `/home/aa1usa/kiba-dock/dock'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/aa1usa/kiba-dock/dock'
Making all in gset-kiba
make[2]: Entering directory `/home/aa1usa/kiba-dock/gset-kiba'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/aa1usa/kiba-dock/gset-kiba'
Making all in icons
make[2]: Entering directory `/home/aa1usa/kiba-dock/icons'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/aa1usa/kiba-dock/icons'
Making all in utils
make[2]: Entering directory `/home/aa1usa/kiba-dock/utils'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/aa1usa/kiba-dock/utils'
Making all in files
make[2]: Entering directory `/home/aa1usa/kiba-dock/files'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/aa1usa/kiba-dock/files'
make[2]: Entering directory `/home/aa1usa/kiba-dock'
make[2]: Leaving directory `/home/aa1usa/kiba-dock'
make[1]: Leaving directory `/home/aa1usa/kiba-dock'

[/QUOTE]

---

### Post by Grishka on 2008-06-08
Kiba-Dock was very good. too bad the development has stopped. anyway, I'd like to see more docks with physics. I've tried pestering the AWN guys for that, but it seems they're busy with other things. :) at least for now. but if you let them know you want physics, maybe they'll implement it someday. anyway, here's an old kiba-dock package I got from the net years ago. I think this is the same version as this one (0.1). perhaps it will be useful for someone.

---

### Post by rated_emman on 2008-06-11
hey guys.. i have the latest kiba dock without the physics... do i have to uninstall that and then install this one? or do they just over write?

thanks in advance :D

---

### Post by Kaneda187 on 2008-06-15
> **rated_emman said:**
> hey guys.. i have the latest kiba dock without the physics... do i have to uninstall that and then install this one? or do they just over write?

thanks in advance :D
im not sure to be honest I would do a clean install, its always works better and its safer, good luck mate and post to let ppl know how it goes and dont forget to say thanks:)

---

### Post by Kaneda187 on 2008-07-05
Any problems with this recently? cuz i wanna install it again i just did a clean install of ubuntu hardy and im determined not to mess it up this time!:)

---

### Post by Grishka on 2008-07-05
> **Kaneda187 said:**
> Any problems with this recently? cuz i wanna install it again i just did a clean install of ubuntu hardy and im determined not to mess it up this time!:)

I've always used the .deb I posted a few posts up. always worked for me, and still does on Hardy, even on a 64-bit system.
oh, and there's a nice system tray packaged with it - kiba-systray.

---

### Post by enigno montoya on 2008-11-01
Howdy, I followed your directions and it works like a charm. Must one always launch Kiba Dock? It doesn't appear in my any menu. I just looked in the "read me" file and type in "kiba-dock" in terminal in order to have it on. Coming from OS X, I thought it would take over the GNOME Panel?

---

### Post by Shiv4m on 2008-11-02
It installed on my Ubuntu but when I try to install it, it doesn't work.

---

