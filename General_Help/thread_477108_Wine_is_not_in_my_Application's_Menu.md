---
title: "Wine is not in my Application's Menu"
date: 2007-06-18
forum: General Help
---

### Post by thomasaaron on 2007-06-18
I had wine on my laptop and several windows apps installed.
They all automatically (i.e. no configuration on my part) appeared under Applications > Wine > (..programs...).

I uninstalled wine via 'sudo apt-get --purge remove wine' and deleted the .wine directory.
I noticed that, after a reboot, those programs were STILL in my Applications menu, so I went
into alacarte and deleted the wine entry.

Now, I'd like to re-install wine. So I went to Applications > Addremove and loaded it up.
I installed a couple of windows apps (the same ones I had before) with wine, but nothing shows up in my applications Window.

I tried a 'sudo updatedb' and then rebooted, but still no dice.

I thought about going back into alacarte and adding wine, but that wouldn't bring up all of the sub-programs.

Any ideas on how to get everything to appear again in my applications menu?

Best,
Tom

---

### Post by thomasaaron on 2007-06-18
*bump*

---

### Post by Brucevdk on 2007-06-18
The command *updatedb* builds an index you can use to search for files on your hard disk using the command *locate*, so I don't think that would help in this case.

Anyways the following should solve your problem.

Open *~/.config/menus/applications.menu* in your favorite text editor and search for the following:
```

<Name>wine-wine</Name>
<Deleted/>

```

Remove the <Deleted/> tag and the wine menu should reappear in your applications menu.

---

### Post by thomasaaron on 2007-06-18
That worked perfectly.
Thank you.

---

