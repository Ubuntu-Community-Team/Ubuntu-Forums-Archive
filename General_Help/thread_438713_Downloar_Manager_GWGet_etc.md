---
title: "Downloar Manager GWGet etc"
date: 2007-05-10
forum: General Help
---

### Post by sefs on 2007-05-10
Hey all.

Slight problem here, when I download with these managers they seem to clog the network.  By that I mean that for instance I cant browse when makeing a huge downlad.  I would have to pause the download to browse.  Alternatively if i were to use Getright for instance on a windows machine this does not happen.  So I am guessing there is a setting somewhere in linux that I could stop this from happening.

Any ideas?

Thanks

---

### Post by MoLE on 2007-05-15
sefs,

Having had a quick look at Gwget and the back-end program wget, I'm sure it would be possible to  tweak the wget configuration file to a maximum download speed.

Go to the help menu and type wget into the search bar.  From the list of hits, click on wget info page.  This will show you how to configure the .wgetrc file with configuration options.
The parameter you probaby want is:
```

limit_rate = RATE
     Limit the download speed to no more than RATE bytes per second.
     The same as `--limit-rate=RATE'.

```

I haven't tried this myself, but it's where I would start if I had the same problem.

Good luck.

---

### Post by Marsolin on 2007-05-15
You could also try [KGet]("http://linuxappfinder.com/package/kget"), [D4x]("http://linuxappfinder.com/package/d4x"), or [doKa]("http://linuxappfinder.com/package/doka") and see if any of them work better for you.

---

