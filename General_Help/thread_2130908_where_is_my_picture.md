---
title: "where is my picture?"
date: 2013-03-30
forum: General Help
---

### Post by ihatetryingtopickaloginna on 2013-03-30
I saved a pic off the web to my desktop and it never showed up. So I saved it again and got the message asking if I wanted to overwrite the file that was on the desktop. I looked again and it's not showing. Then I did a search and it's supposed to be on the desktop. So I clicked the .jpg file and it loaded up in the viewer. Then I clicked image properties and it shows it being on the desktop. I'm just confused now lol.

---

### Post by Frogs Hair on 2013-03-30
Open the file manager and select desktop from the side pane and it should appear.

---

### Post by ihatetryingtopickaloginna on 2013-03-31
I tried that but it won't show. I'm thinking it might be marked hidden for some reason.

---

### Post by lisati on 2013-03-31
Did you save the file with the name ".jpg" (without the quotes, and with nothing before the dot) by any chance? If so, it will be considered "hidden".

---

### Post by ihatetryingtopickaloginna on 2013-03-31
I looked at properties of the image and it shows filename.jpg and it shows Desktop in the folder tab. If I click the tab it brings up the desktop but the file doesn't show.

---

### Post by ihatetryingtopickaloginna on 2013-03-31
Also I clicked show hidden files and it doesn't show.

---

### Post by alladnsane on 2013-04-01
When you found the file with search, right click on it and select ' open folder'.  That should take you to the folder the file is in to verify that it is saved in 'home/*username*/Desktop

---

### Post by ihatetryingtopickaloginna on 2013-04-01
I opened that folder and set it to show hidden files also. The only extra file is one called 'Untitled Document~'. The .jpg isn't there.

---

### Post by ihatetryingtopickaloginna on 2013-04-01
I rebooted after having a problem in another program and now the pic is showing on the desktop.

---

### Post by coldcritter64 on 2013-04-02
> **ihatetryingtopickaloginna said:**
> I rebooted after having a problem in another program and now the pic is showing on the desktop.

If a file fails to show on the desktop, try clicking the desktop (left) to ensure selected and press F5 on the keyboard. I mimick F5 on the keyboard with a mouse stroke ("easystroke") and regularly "draw" a 5 on my desktop to get a file to appear on the desktop. I think it may either be a failure of Nautilus in refreshing or possibly nautilus crashing (**do you notice any open nautilus windows "dropping out"?**); nautilus handles displaying the desktop in Ubuntu. 

If crashing or seizing of nautilus occurs you can use command box, ALT + F2 from the keyboard makes it available, and the codes.

```
nautilus -q
``` to quit any open nautilus windows, desktop icons will "dissapear" when this is used.

```
nautilus -n
``` opens nautilus, thus desktop icons appear, but with no open nautilus window.

Or try stringing the 2 together to form a reset command (if nautilus is already crashed a reset **won't** work, but "nautilus -n" will),

```
nautilus -q && nautilus -n
``` should quit any nautilus windows, including showing the desktop, then restarting just the desktop, showing it's icons etc.

Your rebooting seems to have reset nautilus.

Hope this helps in future, Cheers.

---

### Post by jackclarck on 2013-04-02
I think it's happened due to Corrupted file. so its doesn't appears now.

---

