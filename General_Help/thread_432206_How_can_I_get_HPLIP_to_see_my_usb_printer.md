---
title: "How can I get HPLIP to see my usb printer?"
date: 2007-05-03
forum: General Help
---

### Post by shultzjr on 2007-05-03
Hi all,

I plug in my new HP D1420 into the first usb port on my motherboard.  Then I go into System -> HPLIP and it says there are no HP devices connected.  I just plugged one in so how do I get it to see my usb printer?  Other usb devices work fine with the connection.

thanks,
charles....

---

### Post by fragos on 2007-05-03
I assume you're talking about HPLIP Toolbox.  I had to edit the menu changing the startup command to "hp-toolbox" without the quotes.  For the meantime, open a termial window and try running "hp-toolbox".   The toolbox will help you get things setup properly.

---

### Post by ramjet_1953 on 2007-05-03
Firstly, make sure that [COLOR="Blue"]python-qt3[/COLOR] is installed.

You check this out by using Synaptic and doing a search for it. If the box in front is green, all is OK. If not right click on it and select it for installation.

Once this is done, type in [COLOR="Red"]hp-toolbox[/COLOR]

I have also found that if you go into a terminal and type in [COLOR="Red"]sudo hp-setup[/COLOR], this often overcomes difficult installations of HP printers.

Regards,
Roger 8)

---

