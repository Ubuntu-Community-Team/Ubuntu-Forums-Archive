---
title: "Unable to locate package xev (what do I do now?)"
date: 2014-10-18
forum: General Help
---

### Post by Gottier on 2014-10-18
I have a Logitech mouse. It's an old one, LX7. I love this mouse. It has two extra buttons on the top, and one (on Windows) I set up to close the window (ctrl+q).

I've done this in Ubuntu in the past too, but today it does not seem like xev no longer exists. I was following instructions on this page:

[http://askubuntu.com/questions/152297/how-to-configure-extra-buttons-in-logitech-mouse](http://askubuntu.com/questions/152297/how-to-configure-extra-buttons-in-logitech-mouse)

```

sudo apt-get install xbindkeys xautomation xev
[sudo] password for gottier: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xev

```

So what can I do now?

---

### Post by steeldriver on 2014-10-18
What version of Ubuntu are you using? xev should be part of the x11-utils package I think

```

$ dpkg -L x11-utils | grep xev
/usr/share/man/man1/xev.1.gz
/usr/bin/xev

```

---

### Post by Gottier on 2014-10-18
Yes, it turns out it was already installed. So all I had to do was:

```

sudo apt-get install xbindkeys xautomation
xbindkeys --defaults > $HOME/.xbindkeysrc

```

And then add the following to .xbindkeysrc (because my mouse button was #9):

```

# Close Window
"xte 'keydown Control_L' 'key w' 'keyup Control_L'"
  b:9

```

---

