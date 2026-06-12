---
title: "Desktop Firewall Tool?"
date: 2013-06-11
forum: General Help
---

### Post by hra on 2013-06-11
I've tried to install a "Firewall Desktop Tool" program from the Ubuntu Software Center and I've got problem.  After I download the thing and click on the icon it will say "Enter Administrative Password."  Now the only password I know is my password but when enter it will come back "Incorrect Password Try again."  Is there another password that I don't know?

---

### Post by slickymaster on 2013-06-11
I'm assuming that when you refer to Firewall Desktop Tool, you're meaning Firestarter. Normally when you start Firestarter by clicking an icon or manually from a terminal, the system will prompt you for your root user's password.

---

### Post by hra on 2013-06-11
No not Firestarter but it is "Firewall Desktop Tool" that the name of program.  It is in Ubuntu Software Center.  If you put the word "firewall" in the search bar on the right, there will be a list of firewall program.

---

### Post by Frogs Hair on 2013-06-11
Do you have a user and administrative account ? Firewall Configuration or GUFW is unlocked the by selecting the unlock dialog under the rules box and after entering the password can be enabled.

---

### Post by slickymaster on 2013-06-11
> **hra said:**
> No not Firestarter but it is "Firewall Desktop Tool" that the name of program.  It is in Ubuntu Software Center.  If you put the word "firewall" in the search bar on the right, there will be a list of firewall program.

To which one are you referring:
[ATTACH=CONFIG]243729[/ATTACH]

---

### Post by HiImTye on 2013-06-11
> **slickymaster said:**
> To which one are you referring:
[ATTACH=CONFIG]243729[/ATTACH]

Firestarter, it says right underneath 'desktop firewall tool' ;)

use UFW in the command line, it's much simpler to set up and it's installed by default
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW) [CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by slickymaster on 2013-06-11
> **HiImTye said:**
> Firestarter, it says right underneath 'desktop firewall tool' ;)

use UFW in the command line, it's much simpler to set up and it's installed by default
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW) 

I thought that, but apparently that's not what the OP is mentioning. See my [post #2]("http://ubuntuforums.org/showthread.php?t=2153477&p=12686763&viewfull=1#post12686763") and his reply, [post #3]("http://ubuntuforums.org/showthread.php?t=2153477&p=12686768&viewfull=1#post12686768").

---

### Post by HiImTye on 2013-06-11
I think mayhaps it's listed as 'desktop firewall tool' in the lens if you search for firewall and he just doesn't know the command behind it (but I could be wrong too, it's happened once before)

---

### Post by hra on 2013-06-11
The UFW worked, thanks alot.

---

### Post by sammiev on 2013-06-11
Here's a very good [read]("http://ubuntuforums.org/showthread.php?t=1876124") you may enjoy.

---

