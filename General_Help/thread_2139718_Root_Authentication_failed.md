---
title: "Root: Authentication failed"
date: 2013-04-27
forum: General Help
---

### Post by lukapez on 2013-04-27
I have a problem. When I type in my root password, i get the message: authentication failed. I am 100% sure that I type the correct password, which works when I use it for log in. I am the only user of the device. Can you help me?

---

### Post by Bashing-om on 2013-04-27
lukapez; Hi !

Here is one possibility:
1. At the login screen, press Ctrl+Alt+F1 to get to the console.
2. Log in there.
3. Check if ".ICEauthority" is owned by you:
```

ls -al .ICEauthority
```
4. If it isn't (but possibly by root), change it to you:
```

sudo chown USERNAME:USERNAME .ICEauthority
```
5. Switch back to the login screen by pressing Ctrl+Alt+F7 or F8
6. Better take a look at the permissions on ~/.Xauthority, too. It often gets changed when ~/.ICEauthority gets changed. The same fix applies.
7. Try again to log in.


If it worked, see here about a possible cause:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by lukapez on 2013-04-27
i cant log in from there, it says login incorrect.

---

### Post by steeldriver on 2013-04-27
What exactly do you mean by your "root password"? The root account is not enabled by default in Ubuntu - have you enabled it? or are you referring to the primary 'sudo' account that you created at install time?

What version of Ubuntu are you running? What are you trying to do when you get prompted for the password? There has been a change in gksu with the latest version, which may be what you are experiencing here.

---

