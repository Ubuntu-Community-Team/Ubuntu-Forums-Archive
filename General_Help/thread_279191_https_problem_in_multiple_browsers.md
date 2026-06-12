---
title: "https problem in multiple browsers"
date: 2006-10-17
forum: General Help
---

### Post by tanc on 2006-10-17
I'm having a nightmare of a problem. Short of reinstalling the OS (I don't want to do this!) I've tried everything I can think of.

Certain https sites are completely inaccessible to me, when I try and access them, I get a time out (eventually)

for instance: [https://www.bb.rdg.ac.uk](https://www.bb.rdg.ac.uk) (my university's VLE - important for me to access!

mail.google.com redirects me to the https:// sign-in page, same problem, same with yahoo's signin page, same with my university webmail [http://www.mail.rdg.ac.uk](http://www.mail.rdg.ac.uk) (i assume that redirects me to an https as well)

Very occasionally it works, but only for one refresh, if i try and follow a link it fails.

But not for every https page...i can access the webproxy at [https://www.proxyweb.net](https://www.proxyweb.net) fine, along with various other https pages...

The same happens in lynx, firefox and opera.

Konqueror works fine, but won't display the pages I'm trying to view properly so that's not much use... (gmail in konqueror is a nightmare!)

I've gone down the profile route, i've completely removed every trace of firefox and reinstalled from apt from scratch...and now I'm really scratching my head! It's really starting to annoy me, and I can't get any work done, because everything I need to access for university is hindered by the problem!

I've installed ethereal and tried doing a packet sniff on konqueror and firefox, but don't really know enough about what I'm looking at to determine if anything significant is happening. I'm running 6.10 (Gnome) I think (upgraded from 6.06) and it's not showing any updates that need installing. 

Please help!

Thanks

---

### Post by marianom on 2006-10-17
SSL might be disable from your browsers.
Check this article for example as a solution for firefox:
[http://kb.mozillazine.org/SSL_is_disabled](http://kb.mozillazine.org/SSL_is_disabled)

---

### Post by tanc on 2006-10-17
As I mentioned, it does the same in Opera (but not Konqueror) but not on every https site...but I checked anyway, and all the settings were as per that article says they should be...

---

### Post by dcstar on 2006-10-18
> **tanc said:**
> I'm having a nightmare of a problem. Short of reinstalling the OS (I don't want to do this!) I've tried everything I can think of.

Certain https sites are completely inaccessible to me, when I try and access them, I get a time out (eventually)
.......

Possibly your machine only has 56 bit encryption running instead of 128 bit.

---

### Post by tanc on 2006-10-18
> **dcstar said:**
> Possibly your machine only has 56 bit encryption running instead of 128 bit.

If that's the case, how do I resolve that, and why would it work in Konqueror and not the others?

Also I used to be able to login to gmail for instance, would an update have removed 128bit support?

Thanks

---

### Post by tanc on 2006-10-19
So err...how do I do that?

---

### Post by metalheart on 2006-10-19
Have you tried the SSL test from above mentioned mozillazine.org page?

[http://weblogin.bu.edu/troubleshooting?cmd=ssl](http://weblogin.bu.edu/troubleshooting?cmd=ssl)

---

### Post by tanc on 2006-10-19
I have indeed, they all passed. 

Not all https sites are a problem. 

I've tried other browsers: opera doesn't work, konqueror does.

---

### Post by metalheart on 2006-10-19
Have you presented with a certificate dialog, when you visit [https://www.bb.rdg.ac.uk?](https://www.bb.rdg.ac.uk?)

---

### Post by tanc on 2006-10-19
no...nothing until it times out...

---

### Post by metalheart on 2006-10-19
Go to Edit -> Preferences -> Connection Settings and select Auto-detect proxy... Then restart Firefox.

---

### Post by tanc on 2006-10-19
after a long pause detecting settings, it acted in exactly the same way as previously...frustrating huh?

I'm fairly certain it's not a browser issue...i only installed opera to test this issue, and it's doing exactly the same thing, what I don't get is why konqueror works. A shared library somewhere which K doesn't use? I've got no idea!

Thanks!

---

### Post by tanc on 2006-10-20
Any further ideas before I download a new ubuntu image?

---

### Post by metalheart on 2006-10-20
Try booting off from Ubuntu Live CD and browsing the Web. I'm not convinced this is Ubuntu problem because as you sed it sometimes works and sometimes not.

---

### Post by tanc on 2006-10-20
I'll try...it only works very very occasionaly...once in the last two weeks of trying to fix it...see if i can find the live cd...

---

### Post by tanc on 2006-10-20
As you suggested, firefox on the livecd doesn't work (it doesn't have konqueror)

i've investigated the router and can't find anything settings or otherwise that would be causing this, rebooted, powered off the router etc.

What I don't understand is why konqueror always works. Does anyone know what it does differently that enables it to bypass whatever problem all the other browsers are having?

It would appear that ftp and gaim are also not working...

This is incredibly frustrating!!

---

### Post by metalheart on 2006-10-20
Can you connect to the internet without router?

---

### Post by dcstar on 2006-10-20
> **tanc said:**
> As you suggested, firefox on the livecd doesn't work (it doesn't have konqueror)

i've investigated the router and can't find anything settings or otherwise that would be causing this, rebooted, powered off the router etc.

What I don't understand is why konqueror always works. Does anyone know what it does differently that enables it to bypass whatever problem all the other browsers are having?

It would appear that ftp and gaim are also not working...

This is incredibly frustrating!!

Do a forum search for "disable ipv6" and try some of those solutions, I don't know if it will be any use but it is worth a try.

---

### Post by tanc on 2006-10-21
> **dcstar said:**
> Do a forum search for "disable ipv6" and try some of those solutions, I don't know if it will be any use but it is worth a try.

I love you!!!!

It worked, disabling ipv6 and it works like a dream

evolution and gaim still aren't working, but web browsing does.

Thanks!!!

---

