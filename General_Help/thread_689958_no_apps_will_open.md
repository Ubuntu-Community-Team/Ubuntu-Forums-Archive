---
title: "no apps will open"
date: 2008-02-06
forum: General Help
---

### Post by bikr on 2008-02-06
I am a newbie to linux. I have had ubuntu 7.10 installed for a week and was loving it. I am using a dell inspiron 1100 laptop. I appolligize ahead of time for my horrible spelling and grammer. I am going to try to describe the series of events that happend leading up to the apps not opening.

Yesterday I was setting the WEP code for wireless (had been running it without any encryption) and it froze. The caps lock and scroll lock lights were blinking. When I attempted to reboot it would freeze on the splash so I booted it without the splash and found it was stoping at  

```
Starting common unix printing system: cupsd
```

I took the wireless card out and it booted up. This was odd because I had never had to do this before. The desktop takes 2-3 times longer to load then normal. Once the desktop loads no applications will run. When I click on an app the bar on the bottom says "starting (insert app name here)" then after a few seconds dissapears. I read in another post that it could be a ram issue but everything was working flawlessly (and much faster than xp) before. let me know what other info you need or what you want me to post.

thanks

---

### Post by jrd on 2008-02-06
Log in and press ctrl alt f2 (this will give you a non gui session) then log in and  type "groups"

then press ctrl alt f7 to go back to the gui and tell us what the output was.

If you can get a terminal in the gui then you can just use that instead of going to the non gui session.

---

### Post by bikr on 2008-02-08
jrd, 
   This is the output.
```
matt adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev
```

when I turned the computer on today I was able to open firefox once and then from that point on nothing would open.

---

### Post by bikr on 2008-02-08
alright it seemed to fix itself? I think it was the wireless card. first the apps would open if I clicked on them then put the wireless card in then pulled it out right away, and then it would only work doing the opposite. Now it works fine with it kept in and i was even able to set the WEP up. hopefully it stays this way, may have to never turn it off again to be sure :)

---

