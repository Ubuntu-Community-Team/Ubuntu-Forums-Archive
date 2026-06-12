---
title: "I can't link java to firefox"
date: 2006-10-13
forum: General Help
---

### Post by FuturePilot on 2006-10-13
Can someone help me out? I can't seem to create a symbolic link to the java plugin for firefox. In the terminal I put ```
ln -s /usr/java/jre1.5.0/plugin/i386/ns7
/libjavaplugin_oji.so .
```
But it tells me Permission denied. Am I doing something wrong?:confused:

---

### Post by christhemonkey on 2006-10-13
You probably need to do:
```
sudo ln -s /usr/java/jre1.5.0/plugin/i386/ns7/libjavaplugin_oji.so ./
```

---

### Post by divague on 2006-10-13
try doing it as root

sudo ln -s /usr/java/jre1.5.0/plugin/i386/ns7/libjavaplugin_oji.so

---

### Post by FuturePilot on 2006-10-13
Ok, that sort of worked. The link was created but nothing java woks in firefox. It still says click to install missing plugin.

---

### Post by dannyboy79 on 2006-10-13
> **FuturePilot said:**
> Ok, that sort of worked. The link was created but nothing java woks in firefox. It still says click to install missing plugin.

I don't think by creating a symlink from java to firefox is the way to get Java to work within Firefox. If you want an easy way out, find out how to install Automatix, then you simply run it, and you'll see a whole list of apps and things you can install into your system. Java for Firefox being one of them.

The hard way would be to go to firefox help website and find out how to install java for linux. It does tell you how to do it. I can confess that I used Automatix however so I can't tell you for sure how to install it into Firefox. Good luck and I wish I could help more.

---

### Post by Aranel on 2006-10-13
It depends on where you're putting it. If it's in /usr/lib/firefox/plugins/ or something, then yes, you'll need to use sudo. But you can also create the symbolic link without root privileges if you do it in ~/.mozilla/plugins/ (you can create the folder if it doesn't exist). Putting it in the former folder will make it accessible throughout the entire system; in the latter, it'd just be for your account.

---

### Post by FuturePilot on 2006-10-13
> **dannyboy79 said:**
> I don't think by creating a symlink from java to firefox is the way to get Java to work within Firefox. If you want an easy way out, find out how to install Automatix, then you simply run it, and you'll see a whole list of apps and things you can install into your system. Java for Firefox being one of them.

The hard way would be to go to firefox help website and find out how to install java for linux. It does tell you how to do it. I can confess that I used Automatix however so I can't tell you for sure how to install it into Firefox. Good luck and I wish I could help more.

Thank you! I installed Automatix and installed the Java for Firefox and it worked. Thank you again!:D

---

### Post by dannyboy79 on 2006-10-13
> **FuturePilot said:**
> Thank you! I installed Automatix and installed the Java for Firefox and it worked. Thank you again!:D


You're welcome, did you install any of the other goodies that automatix allows you to install? Just to point out, you should try to understand exactly what automatix did by doing a search on your computer, maybe sudo find / -name java* or something like that so you can understand how automatix did it so you can learn from it cause there isn't always gonna be a automatix for everything you want to install when it's not in synaptic. or you could check out firefox help website and just look over the instructions and see if you could've done it on your own. heres the link to the instructions, [http://www.mozilla.org/support/firefox/faq#q2.2](http://www.mozilla.org/support/firefox/faq#q2.2).
just a suggestion though.  :)

---

### Post by FuturePilot on 2006-10-13
Thanks for the info. Yeah, I did install some other goodies too:)

---

