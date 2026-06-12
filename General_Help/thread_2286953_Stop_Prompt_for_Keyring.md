---
title: "Stop Prompt for Keyring?"
date: 2015-07-15
forum: General Help
---

### Post by Camilia on 2015-07-15
Since I started using Google Chrome I when I got to some forums which require logging in I get prompt:
An Application wants to create a nw keyring called default keyring. Choose the password you want to use for it. 
How do I stop this prompt?

---

### Post by NoWayWin8 on 2015-07-15
Did you use the Software Center to install the downloaded Chrome package?

---

### Post by monkeybrain20122 on 2015-07-16
Is this Xubuntu? Just leave it blank and confirm.

---

### Post by Camilia on 2015-07-16
> **NoWayWin8 said:**
> Did you use the Software Center to install the downloaded Chrome package?
Yes!
> **monkeybrain20122 said:**
> Is this Xubuntu? Just leave it blank and confirm.
Only have option to cancel or continue. I have Ubuntu 15.04

---

### Post by monkeybrain20122 on 2015-07-16
Close Chrome. Open the file manager, press ctrl+H or choose show hidden files from menu, go to .local/share/keyrings, move the content to some backup place. Then logout and log back in. Open Chrome, there will be a pop up asking you to set a keyring password, leave it blank, confirm, then it shouldn't bother you anymore. If everything works, you can delete the backup you saved earlier.

---

### Post by NoWayWin8 on 2015-07-16
Open "Passwords and Keys" application and see what it shows under "Login" (see attachment for example).

---

### Post by Camilia on 2015-07-17
Well I decided to not put a password in and clicked continue. It doesn't show up now. I don't need it for I don't save any of my passwords.

---

