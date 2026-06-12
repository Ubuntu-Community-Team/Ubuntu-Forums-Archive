---
title: "Wubi Error 01!!!"
date: 2008-07-10
forum: General Help
---

### Post by mowogo1820 on 2008-07-10
Hi,
     I'm new to the whole Ubuntu world.  A friend told me to try out Wubi to install Ubuntu on my Laptop that currently has Windows Vista Home Premium on it (I hate vista).  For the record, my antivirus is aVast Antivirus Home Edition (Its free).  I downloaded the newest version of Wubi and tried to install it on my laptop and aVast antivirus picked up a virus within the begining of the Ubuntu installation.  I tried to ignore the virus and continue the installation of Ubuntu with Wubi and Wubi generated an error and closed down.  What steps can I follow in order to install Ubuntu on my system/Laptop.  I want to install it as a duel install.  Who out there can help me with this problem I'm experiencing?

Thank You For You Time!

---

### Post by welshmike on 2008-07-10
I had what may be the same problem.
[http://picasaweb.google.com/mikecymro/WubiGone/photo#5221365343026743794](http://picasaweb.google.com/mikecymro/WubiGone/photo#5221365343026743794)
So is there really a Trojan horse virus associated with Wubi or what is the situation please?

After getting p*ss*d off today with MicroSoft XP Automatic Updates stopping access to the web with KB951748 I'm disappointed that Wubi Ubuntu fouls up with my Avast antivirus.

---

### Post by welshmike on 2008-07-10
To get around what may be a false positive trojan detection by Avast stopping Wubi install I uninstalled Avast and installed Free Grisoft AVG. Wubi install has now completed. I've reported the false positive to Avast.

---

### Post by mowogo1820 on 2008-07-10
Don't get me wrong, I love my Avast Antivirus.  Maybe I'll uninstall Avast, install wubi and then install Avast again.  Thanks for the help!

Does this mean Avast is incompatible with Ubuntu?  Also, will Ubuntu Duel Boot along side Vista without any errors?  Unfortunately, Vista is my only choice for my main operation system right now for my Laptop.  It's a Toshiba Satellite A215-S5837 with a BIOS that happens to be designed for Vista.  I enjoy using Windows XP.  I ran it on this laptop for about three months and had several Issues.  None of my function keys worked, my battery life lasted for 50 minutes and I had several system beeps coming from the laptop everyday.  Toshiba Support told me that they didn't know what was wrong with it.  I finally reverted back to Vista and that solved most of the errors.  However, I'm unable to use several programs because of compatibility issues (that really sucks).  With the exception of the size of my 160 GB HDD, I really like the laptop and don't have the money to go blow on another laptop.  I was told that Ubuntu has drivers for most of the laptops out there on the markets (I don't know if thats true or not).

Along with the major issues I'm having trying to get and use Ubuntu, as a final thought, will Ubuntu run Windows based software?

---

### Post by minhmeoke on 2008-07-10
This is a known issue, Avast raises a false positive during Wubi installation, you may need to temporarily disable it. Once you install Ubuntu, it should be fine. Wubi should work with Vista.

Wubi will not run windows software natively. You have to use a special program called wine to emulate/implement the Windows environment that programs need to run in. Once you get ubuntu running, go to Applications > Add/Remove Programs, show all available applications, and search for wine windows emulator.

---

### Post by ELD on 2008-07-11
Same problem here for me avast thinks its a trojan/virus.

---

