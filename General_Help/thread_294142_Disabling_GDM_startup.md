---
title: "Disabling GDM startup"
date: 2006-11-06
forum: General Help
---

### Post by razor7 on 2006-11-06
Hello, I´m tryning to disable graphical start up on boot on Edgy 6.10.

I have erased the GDM link in /etc/rc2.d, but when I try to boot, the Usplash screen stops loading at the end and never shows me the prompt to login in text mode, like 6.06 does.

Also, If i restore the link to GDM, the things work ok again...

Any idea?


Thanks a lot.

---

### Post by tronica on 2006-11-06
press alt+F2, type 

> services-admin

then go down to graphical login manager, and uncheck it.

---

### Post by razor7 on 2006-11-06
Thanks tronica, I did all that and i get this screen...jeje...

Any Idea?

---

### Post by tronica on 2006-11-06
i thought you didn't want the login screen? I just thought you wanted to be dumped at a prompt each boot.

---

### Post by razor7 on 2006-11-06
Yep...I want to boot and after a good boot, be dumped at text login...

---

### Post by tronica on 2006-11-06
so are you stuck at that the loading screen? you will always see that screen, unless you do some hacking

---

### Post by razor7 on 2006-11-06
OK...ready to receive hack info dude...

Thanks...

---

### Post by tronica on 2006-11-06
not much of a hack i guess, but try this

> 
sudo apt-get remove usplash

then reboot and see if that does it.

---

### Post by razor7 on 2006-11-06
Yes pal, it has done the job...now booting flawless in test mode.

Thanks a lot...!!!

---

### Post by lonce on 2006-11-06
If you remove usplash, what do you see when booting?  Text scrolling by?

---

### Post by peibol on 2007-03-25
I will try it right now, but I suppose it will be like any other regual linux bootup in text mode: it is text scrolling by.

---

