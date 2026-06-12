---
title: "Wine is not opening in Lubuntu"
date: 2018-05-15
forum: General Help
---

### Post by heedbusiness on 2018-05-15
Hello!

I have used Ubuntu and Zorin OS in the past.  In each of those, Wine was a very useful thing being I came from a Windows background.  I recently installed Lubuntu on my machine but can't seem to get Wine to work.

I am using the most current version on Lubuntu and have installed both Wine & its development version. Neither will actually launch though.  I don't know how to fix this and don't want to uninstall the os for a heavier version.

Any thoughts?

---

### Post by Autodave on 2018-05-15
I am running Xubuntu 18.04 and having the same problem. I am assuming that somethin g got changed that the WINE developers haven't figured out yet.

---

### Post by monkeybrain20122 on 2018-05-15
Wine.desktop has been moved so wine windows programs loader doesn't appear as an option in the "open with menu". To restore it by copying/linking wine.desktop to /usr/share/applications

Do either

```
sudo cp /usr/share/doc/wine-stable/examples/wine.desktop /usr/share/applications/
```

or
```

sudo ln -s /usr/share/doc/wine-stable/examples/wine.desktop /usr/share/applications/
```

Then wine windows program loader will show up in the nautilus' "open with" list.

---

### Post by nodesire00 on 2019-01-08
Many Thanks, it worked for me. Ubuntu 18.04. With wine 3.0.
It's not directly shown up on the "open with" list, but it's necessary to pick it from the "View All Application Button" first.

---

