---
title: "reinstall default packages?"
date: 2007-07-27
forum: General Help
---

### Post by Jacks0n on 2007-07-27
Hi. I was mucking around with deborphan to free up some space (I know I know... I was warned), and I made a for loop to remove every one. and now when I login, the desktop doesn't properly load. the panels, and nautilus are fine. but the background and icons don't show. it freezes up too. I'm guessing it removed some essential libraries too...

so is there anyway I can make sure all the default packages are installed? or is there a list of them somewhere? or maybe apt-get has a log file of what it's removed...

thanks!

---

### Post by tombott on 2007-07-27
If you press Alt-F2 after logging in do you get the 'Run Application' box?

If so you could try running the following:

```
gksu "update-manager -c"
```

That should load the Update Manager, maybe doing a Check will reload broken apps?

I'll keep looking around for other solutions for you, but let us know how you get on.

Tom.

---

### Post by tombott on 2007-07-27
You could also try pressing Alt-F2 then typing:
```

sudo apt-get dselect-upgrade -su
```

Tick the 'Run in terminal' box then clicj Run

Tom.

---

### Post by az on 2007-07-27
> **Jacks0n said:**
> 
so is there anyway I can make sure all the default packages are installed? or is there a list of them somewhere? or maybe apt-get has a log file of what it's removed...
!

sudo apt-get install ubuntu-desktop

---

### Post by Jacks0n on 2007-07-27
ahh... works fine now. thanks! :)

---

