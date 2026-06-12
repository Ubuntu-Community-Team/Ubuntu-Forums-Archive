---
title: "Terminal code to turn off log in password upon boot up?"
date: 2015-10-15
forum: General Help
---

### Post by michael-piziak on 2015-10-15
Terminal code to turn off log in password upon boot up?

---

### Post by Bucky Ball on 2015-10-15
Any reason you specifically want to use the terminal? It is easy to do without. 

[http://www.liberiangeek.net/2012/11/turn-off-disable-automatic-logon-in-ubuntu-12-10-quantal-quetzal/](http://www.liberiangeek.net/2012/11/turn-off-disable-automatic-logon-in-ubuntu-12-10-quantal-quetzal/)

Best to do a search prior to posting. If the above doesn't work, one of [these]("https://duckduckgo.com/?q=turn+on+auto+login+ubuntu") should. :)

---

### Post by michael-piziak on 2015-10-15
> **Bucky Ball said:**
> Any reason you specifically want to use the terminal? It is easy to do without. 

[http://www.liberiangeek.net/2012/11/turn-off-disable-automatic-logon-in-ubuntu-12-10-quantal-quetzal/](http://www.liberiangeek.net/2012/11/turn-off-disable-automatic-logon-in-ubuntu-12-10-quantal-quetzal/)

Best to do a search prior to posting. If the above doesn't work, one of [these]("https://duckduckgo.com/?q=turn+on+auto+login+ubuntu") should. :)

ok tell me how to do it in Ubuntu settings - i just couldn't find it.

---

### Post by deadflowr on 2015-10-15
Boot? or login?
Those are two different things and have different settings.
A password at boot is the usual way for full-disk-encryption, and I don't know if there is any real way to disable that.

But a password at login has several ways to change it, here is one and most likely the easiest:

Open System settings, then go into User Accounts, highlight your username in the right and then look to see if a line in the main window says Automatic Login, with a toggle box and "off" written in it.
To toggle you will need to click the "unlock" box in the top right corner. The toggle the "off" box and the next tijme you reboot, you'll autologin.

**Point of note**, DO NOT do anything to the password box field. Which should be right above the automatic login box in the User Accounts page.
Some users have taken it upon themselves to think that you can set the password field to nothing or disabled and then never have to use a password, but that really disables the user and causes nothing but problems. 


Hope it helps.

---

### Post by michael-piziak on 2015-10-16
> **deadflowr said:**
> Boot? or login?
Those are two different things and have different settings.
A password at boot is the usual way for full-disk-encryption, and I don't know if there is any real way to disable that.

But a password at login has several ways to change it, here is one and most likely the easiest:

Open System settings, then go into User Accounts, highlight your username in the right and then look to see if a line in the main window says Automatic Login, with a toggle box and "off" written in it.
To toggle you will need to click the "unlock" box in the top right corner. The toggle the "off" box and the next tijme you reboot, you'll autologin.

**Point of note**, DO NOT do anything to the password box field. Which should be right above the automatic login box in the User Accounts page.
Some users have taken it upon themselves to think that you can set the password field to nothing or disabled and then never have to use a password, but that really disables the user and causes nothing but problems. 


Hope it helps.

My login password is turned off - see attached.

Yet I still have to login with password when booting up


?

---

### Post by deadflowr on 2015-10-16
Yeah, I should have stated is you need to toggle the automatic login box from off to on.

What I did was murder the English language:
[COLOR=#000000] > The toggle the "off" box and the next tijme you reboot, you'll autologin.[/COLOR]
which probably made no sense to anyone but me.

---

### Post by michael-piziak on 2015-10-16
oh shucks, i should have understood what to do

it's a bit confusing to me, but yes i need to toggle it to ON

it's like it got stuck in my mind that it being off meant it should NOT require auto login - but quite the opposite!

---

