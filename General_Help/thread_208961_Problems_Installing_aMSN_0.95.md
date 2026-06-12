---
title: "Problems Installing aMSN 0.95"
date: 2006-07-04
forum: General Help
---

### Post by TWIXMIX on 2006-07-04
Hello, I'm having a few problems installing aMSN. I'm trying to install the newest version off of amsn.sourceforge.net but I'm getting a few errors.

I type:  **sudo dpkg -i amsn_0.95-3.unbuntu.deb** n the terminal and I get this.

> 
dpkg: error processing amsn_0.95-3.unbuntu.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 amsn_0.95-3.unbuntu.deb

The installation package is in that directory, therefore I'm not sure what the problem is.

Thanks in Advance.

---

### Post by Jagot on 2006-07-04
You have spelt the filename wrong which is why it's not recognising the file.

It should be:

```
amsn_0.95-3.ubuntu.deb
``` 
Whereas you have 

```
amsn_0.95-3.u**n**buntu.deb
```

You've put an extra n in ubuntu.

---

### Post by TWIXMIX on 2006-07-04
Oh geeze, I'm an idiot. I swear I looked over that like 5 times haha. 

Thanks :neutral:

---

### Post by Jagot on 2006-07-04
Something which can help with long file names is the use of the tab key to autocomplete, so for example if you go to the same directory that the amsn .deb is in, in Terminal type:

```
sudo dpkg -i a
```

Then press the tab key and, providing it is the only .deb in the directory beginning with an 'a', it will autocomplete the file name for you.  If it isn't the only .deb in the directory beginning with an 'a', then just add then just add a couple more letters to make it unique and tab again.

---

### Post by TWIXMIX on 2006-07-04
Okay, thanks for the tip.

---

### Post by newbie2 on 2006-07-04
[QUOTE=Jagot]You have spelt the filename wrong which is why it's not recognising the file.

It should be:

```
amsn_0.95-3.ubuntu.deb
``` 
Whereas you have 

```
amsn_0.95-3.u**n**buntu.deb
```

You've put an extra n in ubuntu.[/QUOTE]

amsn_0.95-3.ubuntu.deb isn't in my repositories ....only 0.95-1  :?

---

### Post by aysiu on 2006-07-04
That's why you have to manually install aMSN 0.95-3. Paste these two commands in the terminal: ```
wget -c http://internap.dl.sourceforge.net/sourceforge/amsn/amsn_0.95-3.ubuntu.deb
sudo dpkg -i amsn_0.95-3.ubuntu.deb
```

---

### Post by krazykirk on 2006-07-05
this is a bit unrelated, but I tried aMSN, and I didn't really like it, so i switched to KMess and It works like a charm! =)

---

### Post by newbie2 on 2006-07-06
[QUOTE=aysiu]That's why you have to manually install aMSN 0.95-3. Paste these two commands in the terminal: ```
wget -c http://internap.dl.sourceforge.net/sourceforge/amsn/amsn_0.95-3.ubuntu.deb
sudo dpkg -i amsn_0.95-3.ubuntu.deb
```[/QUOTE]
tnx aysiu....i must say i did it in a more 'grafical' way....i downloaded from 
[http://amsn.sourceforge.net/linux-downloads.php](http://amsn.sourceforge.net/linux-downloads.php) to my desktop , then i did have to install tcltls in adept , and then i rightclicked on the aMSN 0.95-3 - deb package .....i got then a window with 'Kubuntu Package Menu' ---> 'Install Package'...and it was installed .....

---

