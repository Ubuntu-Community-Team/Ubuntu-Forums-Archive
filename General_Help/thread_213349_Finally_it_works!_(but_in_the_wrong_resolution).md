---
title: "Finally it works! (but in the wrong resolution)"
date: 2006-07-11
forum: General Help
---

### Post by Over Haze on 2006-07-11
First the good news. Dapper Drake arrived this morning and is the only Linux Live CD to EVER work in my PC! Finally I have known the joy of turning on my PC and not seeing the windows logo! Everything seemed to work fine except for one thing, it set itself to the wrong screen resolution and would no let me change it. My screens default resolution is 1280 by 1024 but ubuntu set to 6xx by 4xx this is lower than my screen should technically be outputting at, at all. 

I attempted to change the resolution but the drop down box refused to drop down. I was using the 64 bit version. Anyone have any advice?

---

### Post by caserio on 2006-07-11
Hi,

Post your /etc/X11/xorg.vonf

---

### Post by Over Haze on 2006-07-11
Sorry should have said, I'm completely new to Linux so please assume I know nothing!

---

### Post by nik on 2006-07-11
Applications - Accessories - Terminal

Enter "gedit /etc/X11/xorg.conf" without the quotes, copy and paste the content here.

---

### Post by mlind on 2006-07-11
What you need to do here is the usual drill, backup your /etc/X11/xorg.conf
and then open up a terminal from Applications > Accessories > Terminal and type
```

sudo dpkg-reconfigure xserver-xorg

```

You can find plenty of threads dealing with the same issue using the forums search.

---

### Post by Over Haze on 2006-07-11
Seems fairly academic now as it also wont detect my USB wireless cards. As that is my only way of connecting to my network and thus the Internet that would be the big problem right now.

---

### Post by mlind on 2006-07-11
> **Over Haze said:**
> Seems fairly academic now as it also wont detect my USB wireless cards. As that is my only way of connecting to my network and thus the Internet that would be the big problem right now.

What's the brand/model of your wireless cards?

---

### Post by Over Haze on 2006-07-11
Its a netopia 3d reach USB wireless adapter.

Here is the exact model

[http://www.netopia.com/equipment/pdf/3D_R_Wireless_Adapt_DS.pdf](http://www.netopia.com/equipment/pdf/3D_R_Wireless_Adapt_DS.pdf)

---

### Post by mlind on 2006-07-11
> **Over Haze said:**
> Its a netopia 3d reach USB wireless adapter.

Here is the exact model

[http://www.netopia.com/equipment/pdf/3D_R_Wireless_Adapt_DS.pdf](http://www.netopia.com/equipment/pdf/3D_R_Wireless_Adapt_DS.pdf)

I don't own a wireless, so I'm not the right person to help you on this. I know from other forum posts that some people have had hard time to get their wireless devices working.

This wiki page should help you, it contains good general setup & configuring info
[http://doc.gwos.org/index.php/Networkwifi](http://doc.gwos.org/index.php/Networkwifi)

You should also search using netopia as keyword, preferably from HOWTO section.

---

