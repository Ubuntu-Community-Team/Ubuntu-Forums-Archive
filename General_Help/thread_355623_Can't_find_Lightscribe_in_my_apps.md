---
title: "Can't find Lightscribe in my apps"
date: 2007-02-07
forum: General Help
---

### Post by SirPaPa on 2007-02-07
Hello, I wonder if someone can help me. I just installed Lightscribe for Linux using Automatix 2, but I can' find the app. Can someone help me plz? Thank,you 
](*,)

---

### Post by jackrobinson on 2007-02-07
> **SirPaPa said:**
> Hello, I wonder if someone can help me. I just installed Lightscribe for Linux using Automatix 2, but I can' find the app. Can someone help me plz? Thank,you 
](*,)

Look under Applications --> Accessories

---

### Post by nereid on 2007-02-07
Just open a terminal and be so kind and post the result of

```

which lightscribe

```

returns (if lightscribe is the name of the executable). Or do the following

```

sudo updatedb

```

this could take a while depending on your harddrive as it updates the search database manually (there should be a cron job on your pc doing this once everyday in the background). After updatedb has finished, just type

```

sudo locate lightscribe

```

which will give you a listing of everything on your harddrive with the name lightscribe.

Hope I could help you.

---

### Post by SirPaPa on 2007-02-07
> **nereid said:**
> Just open a terminal and be so kind and post the result of

```

which lightscribe

```

returns (if lightscribe is the name of the executable). Or do the following

```

sudo updatedb

```

this could take a while depending on your harddrive as it updates the search database manually (there should be a cron job on your pc doing this once everyday in the background). After updatedb has finished, just type

```

sudo locate lightscribe

```

which will give you a listing of everything on your harddrive with the name lightscribe.

Hope I could help you.
Thank,you jackrobinson I had already done that with zero results.
Also nereid , I got bunches of places lightscribe is in, but not one that lets me run the app.
The Gdebi  Package Installer indicates that is installed but I can't access it. Could it be tha it just does'nt work with Samsung dvd- burners even though it's a lightscribe drive?
Anyone? Thank,you.](*,)

---

### Post by jackrobinson on 2007-02-07
> **SirPaPa said:**
> Thank,you jackrobinson I had already done that with zero results.
Also nereid , I got bunches of places lightscribe is in, but not one that lets me run the app.
The Gdebi  Package Installer indicates that is installed but I can't access it. Could it be tha it just does'nt work with Samsung dvd- burners even though it's a lightscribe drive?
Anyone? Thank,you.](*,)

The executable can be run from terminal as follows. Lightscribe only works correctly on Dapper (has known bugs on Edgy)
```
4L-gui
```

---

### Post by SirPaPa on 2007-02-07
> **jackrobinson said:**
> The executable can be run from terminal as follows. Lightscribe only works correctly on Dapper (has known bugs on Edgy)
```
4L-gui
```

Thank,you jackrobinson thank you very much. Now I like to know if there's a way of runny it from the applications menu with an icon. That would be great.
          Thank,you all for help.:)

---

### Post by Maestro23 on 2007-02-07
> **SirPaPa said:**
> Thank,you jackrobinson thank you very much. Now I like to know if there's a way of runny it from the applications menu with an icon. That would be great.
          Thank,you all for help.:)

Should be able to go up to your menu editor and create an entry for it.  Can specify Type, Name, Command(path to execute), and Icon.  Don't know what Desktop you are using, but I use Xfce and this is under Applications...Settings....Menu Editor for me.  

Hope that points you in the right direction.

---

### Post by jackrobinson on 2007-02-07
> **SirPaPa said:**
> Thank,you jackrobinson thank you very much. Now I like to know if there's a way of runny it from the applications menu with an icon. That would be great.
          Thank,you all for help.:)

```
sudo apt-get install alacarte
```
now run 
```
alacarte
```
and make sure the lightscribe menu item under accessories is NOT hidden

---

### Post by SirPaPa on 2007-02-08
Thank, you all for your suggestions.I'm using gnome. It's not available in alacarte and don't know how to set it up.

---

