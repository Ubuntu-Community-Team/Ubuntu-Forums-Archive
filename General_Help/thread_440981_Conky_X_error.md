---
title: "Conky X error"
date: 2007-05-12
forum: General Help
---

### Post by GSF1200S on 2007-05-12
Just did a fresh install of Kubuntu 7.04, and im trying to get conly working. 

I already made a startup script, placed it in my autostart folder, etc.

It doesnt load at bootup, but thats not the problem.. it wont load at all- I get this error message when trying to run it from the terminal...

xlinux@xlinux-laptop:~$ conky
Conky: can't parse X color '#lightgrey'
Conky: forked to background, pid is 6003
xlinux@xlinux-laptop:~$
Conky: desktop window (140000f) is subwindow of root window (10e)
Conky: window type - override
Conky: drawing to created window (2c00002)
Conky: drawing to double buffer
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  91 (X_QueryColors)
  Value in failed request:  0xff00ff
  Serial number of failed request:  644
  Current serial number in output stream:  644

Any ideas?

---

### Post by reclusivemonkey on 2007-05-12
Try adding

```

Load    "dbe"

```

to /etc/X11/xorg.conf in the "Module" section. Also, its clear conky doesn't like "#lightgrey". Try either "lightgrey" or only use the # with a vaild hex colour number, like #bababa

---

### Post by GSF1200S on 2007-05-12
> **reclusivemonkey said:**
> Try adding

```

Load    "dbe"

```

to /etc/X11/xorg.conf in the "Module" section. Also, its clear conky doesn't like "#lightgrey". Try either "lightgrey" or only use the # with a vaild hex colour number, like #bababa

Thanks man.. worked like a charm...

I never really thought about changing anything in conkyrc, as I copied conkyrc to my windows partition before reinstall. Conky worked perfect on Kubuntu before, so I looked elsewhere for the problem. I changed everything from lightgrey to white, and removed the # sign from one entry and it worked great.. weird!

Thanks for the help :)

---

