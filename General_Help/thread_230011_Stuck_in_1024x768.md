---
title: "Stuck in 1024x768"
date: 2006-08-05
forum: General Help
---

### Post by bb2120 on 2006-08-05
I've just installed Dapper and can't change the screen resolution to 1280x1024 - the option doesn't exist in screen resolution preferences. I never had this problem running Breezy. I've got a ATI Radeon 9200 card. 

Any ideas on how to pump up the resolution? Everything's a bit pixelated at the moment...

---

### Post by taurus on 2006-08-05
Did you install a driver for your ATI graphic card!  Then, you can either edit your /etc/X11/xorg.conf by hand or reconfigure your X again with...

Edit by hand:
```

sudo gedit /etc/X11/xorg.conf

```
Reconfigure X:
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by bb2120 on 2006-08-05
Sorry, I'm pretty new to linux - I should have said :)

Okay, I edited the /etc/X11/xorg.conf and saved it. Then I did the 
```
sudo dpkg-reconfigure xserver-xorg
```

Then I restarted. Nothing's changed. 

Can someone please put this more clearly?

---

### Post by Jagot on 2006-08-05
You may want to try installing the drivers for your graphics card:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

