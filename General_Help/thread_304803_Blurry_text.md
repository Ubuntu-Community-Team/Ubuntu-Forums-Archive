---
title: "Blurry text"
date: 2006-11-22
forum: General Help
---

### Post by jinxen on 2006-11-22
Hi! I recently installed ubuntu 6.10 again. And the text in applications, internet everywhere is kinda of blurry and does not look good. I will post 2 secreens for you to look at, every answer will help!

Regards, Tommy

---

### Post by PrinceArithon on 2006-11-22
Looks good to me, maybe it's one of your settings??  Try a higher resolution maybe??

---

### Post by jinxen on 2006-11-22
hmms, it surly doesn't to me :P hehe, i have the highest res 1280 x 1024. But i can only set the refresh rate to 56 for some reason. In windows for and mac os x and can set it to 75. Isn't that kinda weird?

---

### Post by renzokuken on 2006-11-22
yeah i used to get that but it disappeared eventually, i think it went when i installed the nVidia driver

sorry cant be more help, i didn't intentionally try and sort it out but it did it when i did something else.

---

### Post by jinxen on 2006-11-22
ok, thats not good then :P I to have the nvidia driver installed, but i dont remember it to be good before i installed the nvidia driver?

---

### Post by renzokuken on 2006-11-22
actually, i think it may have sorted out when i installed the msfonts package, cant remember if its in synaptic or not though

---

### Post by jinxen on 2006-11-22
hmms, that kinda rings a bell.. Maybe i have installed them before... I will try that. thx

---

### Post by jinxen on 2006-11-22
Someone knows where/how to install msfonts btw? :P


sry, found how to do it. Must remember google is your best friend :P

---

### Post by renzokuken on 2006-11-22
[http://www.ubuntuforums.org/showthread.php?t=288566&highlight=font+blurred](http://www.ubuntuforums.org/showthread.php?t=288566&highlight=font+blurred)

[http://www.ubuntuforums.org/showthread.php?t=278001&highlight=font+blurred](http://www.ubuntuforums.org/showthread.php?t=278001&highlight=font+blurred)

[https://launchpad.net/distros/ubuntu/+source/fontconfig/+bug/63403](https://launchpad.net/distros/ubuntu/+source/fontconfig/+bug/63403)

check these out, may be a solution in there,

---

### Post by jinxen on 2006-11-22
ok, thanks alot. I checked out the threads you posted. And i finally gotit to work. Others seemed to have a problem with a~/.font.conf file, but i didnt even have that file so i created one that contained this. And after that, it worked! Thanks! :)

Tommy

> 
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>


---

### Post by renzokuken on 2006-11-22
no trubs.....glad it worked 

happy ubunting

---

### Post by stormyuk on 2007-01-14
> **jinxen said:**
> Hi! I recently installed ubuntu 6.10 again. And the text in applications, internet everywhere is kinda of blurry and does not look good. I will post 2 secreens for you to look at, every answer will help!

Regards, Tommy

Hiya, I have just had to come back in Windows because I am getting the exact same random blurred text exactly like your screenshots.

Its giving me a headache, so back in XP (with no anti-aliasing, cleartype or anything) and its all sharp again if a little rough compared to ubuntu.

I have tried enabling and disabling anti-aliasing and hinting but nothing helps.

Can you give a n00b an easy guide to follow how to fix it, if you did?

(where is ~/font.conf in the file structure or where should I put it?)

Thanks,

Mike

---

