---
title: "[SOLVED] Viewing my desktop on my TV using s-video"
date: 2007-11-11
forum: General Help
---

### Post by valleyman7 on 2007-11-11
I have my Dell 9300 set up so I can see my desktop on my TV using S-Video. I have a Nvidia Ge Force GO 6800 card and I haven't been able to figure out how to do this with Ubuntu. I have the latest version 7.10 installed. Any help would be greatly appreciated. The reason I want to be able to set this up is I watch movies on my TV and this is one of the items I would like to be able to do before I go to Ubuntu as my main operating system. Thanks for any help.:confused: 

"Experience is a wonderful thing, it enables you to recognize a mistake when you make it again."

Lyle Hensley
Enjoying Every Breath
Retired  US Army
1957 – 1978
My Blog

---

### Post by overdrank on 2007-11-11
> **valleyman7 said:**
> I have my Dell 9300 set up so I can see my desktop on my TV using S-Video. I have a Nvidia Ge Force GO 6800 card and I haven't been able to figure out how to do this with Ubuntu. I have the latest version 7.10 installed. Any help would be greatly appreciated. The reason I want to be able to set this up is I watch movies on my TV and this is one of the items I would like to be able to do before I go to Ubuntu as my main operating system. Thanks for any help.:confused: 

"Experience is a wonderful thing, it enables you to recognize a mistake when you make it again."

Lyle Hensley
Enjoying Every Breath
Retired  US Army
1957 – 1978
My Blog

HI and you should be able to setup in the nvidia settings using this command, ```
gksudo nvidia-settings
``` Good luck! :)

---

### Post by valleyman7 on 2007-11-12
Thanks for the information I will give it a try.

---

### Post by NT4usB on 2007-11-12
Hopefully it's that easy!
I did it on Dapper by modifying the xorg.conf so I know how to do it from the inside. If you don't succeed, there's always the old fashioned way...

btw, thanks for your service!

---

### Post by valleyman7 on 2007-11-14
Well that was pretty easy. Now I just need to get it fine tuned with the correct resolution. I want to thanks both of you for your post. and thanks for acknowledging my Military service. I pray daily for all my brothers and sisters who are now fighting for my freedom. Stay safe and thanks again. I am sure I will be back looking for more answers. PS I am really enjoying Ubuntu.:)

---

### Post by valleyman7 on 2007-11-22
I was able to configure the TV for use, the only problem that I am having is I saved the setup or at least thought I did, but when I start Ubuntu I see a Nvidia Logo before I login, but I don't see my desktop, so I am not doing something right. When I set the options I saved the settings to the xconfig file I beleive.
 Any suggestions would be appreciated. I want to thank you for the help.

---

### Post by valleyman7 on 2007-11-22
Correction I save the settings to the xorg.conf. :confused:

---

### Post by valleyman7 on 2007-11-24
I managed to really screw my screen resolution up. Now I have a 600 and 800 option only. I wounder does Ubuntu have a restore option? I couldn't be that lucky. Back to the drawing board and I thought I was doing so well. :(

---

### Post by NT4usB on 2007-11-24
Are you confident directly editing xorg.conf?

you can run ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` to make x reconfigure the video. Restart x to see the change.
It will undo many of the changes you've made to xorg. It does make a backup of your running xorg so you can go back to it.
You can combine the good stuff from the reconfigured xorg with your old xorg and (hopefully) get it working.

---

