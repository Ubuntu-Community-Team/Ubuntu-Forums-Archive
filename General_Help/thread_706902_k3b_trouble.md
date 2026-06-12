---
title: "k3b trouble"
date: 2008-02-24
forum: General Help
---

### Post by bigearl on 2008-02-24
Im trying to burn a iso to a CDRW and i set it up and such and it gets to about 30% until it says "cdrecord has no permission to open the device" and then it stops , id really like some help asap as I need this CD for tomorrow thanks

---

### Post by ENB on 2008-02-24
Maybe this will work:

sudo chmod 777 /dev/xxx

Where xxx is the device for your cdrom. (Not sure what it would be called, I'm not on Ubuntu right now)

---

### Post by bigearl on 2008-02-24
i dont understand what i would put XXX too.

---

### Post by ENB on 2008-02-24
Try: sudo chmod 777 /dev/cdrom

If it doesn't work here is a google search: [http://www.google.com/search?q=k3b+cdrecord+has+no+permission+to+open+the+device&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=k3b+cdrecord+has+no+permission+to+open+the+device&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

Maybe you'll find some info there.

---

### Post by bigearl on 2008-02-24
when i put it in the terminal nothing happens.

---

### Post by ENB on 2008-02-24
Does it ask you for a password?

---

### Post by bigearl on 2008-02-24
nope

---

### Post by ENB on 2008-02-24
Odd...

Can you open a new terminal and type it in again **sudo chmod 777 /dev/cdrom**

And post what happens.

If you don't get this problem solved, and need your CD for tomorrow you can install **brasero** which should work. It may just install a lot of gnome files. I'm assuming you are using KDE?

---

### Post by bigearl on 2008-02-24
lol yeah i just installed brasero like 2 minutes ago im giving it a try

---

### Post by ENB on 2008-02-24
Wait actually try burning your iso now... I just forgot, nothing will actually happen.

Edit: Okay. K3b might work now though.

---

### Post by bigearl on 2008-02-24
oh lol w/e its burning right now if anything goes wrong its highspeed one so i can erase it :P

---

### Post by ENB on 2008-02-24
Okay. You might also try **sudo chmod 777 /dev/cdrw**.

Good luck with the problem though.

---

