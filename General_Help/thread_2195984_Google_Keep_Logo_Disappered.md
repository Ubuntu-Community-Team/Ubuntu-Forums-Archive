---
title: "Google Keep Logo Disappered"
date: 2013-12-27
forum: General Help
---

### Post by willzhigaylo on 2013-12-27
The logo for google keep has changed into a question mark. Looks like this: [ATTACH=CONFIG]248938[/ATTACH] I think this happened after a reboot. Though the program still works fine it is still annoying. Any help is appreciated.

---

### Post by willzhigaylo on 2013-12-31
Help?

---

### Post by deadflowr on 2013-12-31
I'm guessing this a shortcut?

Were you following this guide
[http://www.omgubuntu.co.uk/2013/05/add-google-keep-to-unity](http://www.omgubuntu.co.uk/2013/05/add-google-keep-to-unity)
or some similar method?

---

### Post by willzhigaylo on 2014-01-01
no, I installed it via chrome web store and it was automatically locked to launcher

---

### Post by willzhigaylo on 2014-01-11
Help?

---

### Post by deadflowr on 2014-01-11
Then it's most likely the icon is misplaced.

Open the app "gedit' and then click Open, go to your username in the leftside panel, and then go to the folder .local.
If it isn't showing folder/files with a dot, right-click in that main area and select show hidden files/folders.
inside the .local folder go to share, then inside share go to applications.
There should be an entry for the app here, probably marked as google-keep.desktop
Open it and look for the entry Icons=
look at the name of the icon.
If you want post it here.
You might also try running a locate on the icon.
```
locate <icon-name-here>
```

---

### Post by willzhigaylo on 2014-01-11
Not sure what the problem was, but it was automatically fixed after a couple of reboots.

---

