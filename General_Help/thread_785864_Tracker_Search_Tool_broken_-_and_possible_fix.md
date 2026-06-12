---
title: "Tracker Search Tool broken - and possible fix?"
date: 2008-05-07
forum: General Help
---

### Post by riskbreaker927 on 2008-05-07
Hey guys. I noticed something very disturbing on my fresh install of Hardy.

Tracker-Search-Tool is installed, but unusable. After I dug around, I found that trackerd and tracker-applet are running, so I couldn't understand the problem. Then I looked at /.config/tracker/tracker.cfg and noticed it had disabled indexing, and also forced the applet icon to disappear if the daemon wasn't indexing.

Rather than question the monolithic failure of judgment that led someone to make this behavior the default for an LTS release of Ubuntu, I'll post what I did to fix it.

First, edit the configuration file:
```
gedit ~/.config/
```

Find the section labeled **[Indexing]** and under it should be an option that says **EnableIndexing=false**. Change "false" to "true". Save and exit.

Now stop the tracker daemon and restart it:```
sudo killall trackerd
trackerd
```

You should get a notification in your tray that it's indexing, and the icon will probably be there too. You can then use the icon to configure any other tracker preferences you want, without mucking about with the configuration files.

Please let me know if this worked for you, and maybe a package will be released that doesn't have this problem?

---

### Post by shankariyer on 2008-05-08
I can't get the icon back, I changed 'Indexing' as how its mentioned here and also, AutoHideIcon=false in my tracker-applet.cfg.

Any pointer as how I can get the applet back ? Thanks.

---

### Post by shankariyer on 2008-05-08
I killed them all again and went to 'preferences -> search and indexing', restarted indexing/watches. But that didn't start...then logged out & logged back in the applet is back...

---

### Post by gOOglEy03 on 2008-11-15
Yeah I noticed the same thing. If you use close in the preferences, it closes the tray. If you log in and out, it is back. I have never gotten the thing to work even in Hardy when the icon was always there, but nonetheless, it still seems fishy...

---

