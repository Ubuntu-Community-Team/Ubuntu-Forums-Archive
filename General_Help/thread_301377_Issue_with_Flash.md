---
title: "Issue with Flash"
date: 2006-11-17
forum: General Help
---

### Post by Brandnew70x7 on 2006-11-17
Hey guys. I got Ubuntu sort of out of neccessity becuase I lost my XP Pro CD and also becuase I really wanted to try out Amarok (Which I love) but I really like it a lot now and will probably be sticking with it in some form.

Firstly, i'm using Dapper.

As far as my flash question goes, I have been trying to access Adult Swim fix today with no results. I followed the flash installation instructions to the T but when I go back to the site after I log out and back in it still says I need Flash! Anyone have this problem and know of some help?

---

### Post by aidanr on 2006-11-17
if you just went to the adobe site to download the flash player, it's still on flash 7, you want the flash 9 beta which you can get [here]("http://labs.adobe.com/downloads/flashplayer9.html")

---

### Post by Brandnew70x7 on 2006-11-17
Yeah I thought that might be it but i'm now using

    File name: libflashplayer.so
    Shockwave Flash 9.0 d55

to no avail :(

Anyone gotten this site to work?

---

### Post by aidanr on 2006-11-17
yeah its working for me, i copied libflashplayer.so to /usr/lib/mozilla/plugins ,if you had flash 7 installed, make  sure there are no other files in that directory relating to flash and also you may want to try deleting ~/.mozilla/pluginreg.dat and ~/.mozilla/firefox/pluginreg.dat (they'll be recreated when you restart firefox)

---

### Post by Brandnew70x7 on 2006-11-17
I neglected to mention i am using Firefox 2.0. Will this have any bearing on it? If so how would I revert back?

---

### Post by aidanr on 2006-11-17
im also using ff2:-k

---

### Post by Brandnew70x7 on 2006-11-17
I'm definitely on Version 9, I did as you wrote and still nothing :( What is going on with this?

---

### Post by aidanr on 2006-11-17
is it just this site thats not working? does [this]("http://labs.digg.com/swarm/") site work?

---

### Post by Brandnew70x7 on 2006-11-17
Yeah that site works fine!

---

### Post by aidanr on 2006-11-17
try clearing your cookies perhaps?
heres another [site]("http://labs.adobe.com/wiki/index.php/Flash_Player:9:Update:Full-Screen_Mode:Demos") thats probably better for testing your flash 9 installation

---

### Post by Zyphrexi on 2006-12-02
hey, you guys with the flash 9 installed. Does the adult swim fix work for you? I think it needs the activex control installed too. Yeah I know.

---

