---
title: "Opera Won't Open Maximized"
date: 2017-09-02
forum: General Help
---

### Post by sasafrass452 on 2017-09-02
I decided to try the Opera browser, so I downloaded the .deb file from the official website. I want to open it maximized, but it doesn't "stick". This seems to be a long-standing bug that others have encountered. Is there some way to make this work? Help!

---

### Post by again? on 2017-09-02
Add "--start-maximized" option to the Exec command.

Copy system launcher to your local user directory.
```
cp /usr/share/applications/opera.desktop ~/.local/share/applications
```

Edit local file.
```
gedit ~/.local/share/applications/opera.desktop
```

Change
```
Exec=opera %U
```

to
```
Exec=opera --start-maximized %U
```
Logout.

---

### Post by sasafrass452 on 2017-09-03
Thankyou!!!

---

