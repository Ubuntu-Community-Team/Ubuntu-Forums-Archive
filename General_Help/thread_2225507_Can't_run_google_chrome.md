---
title: "Can't run google chrome"
date: 2014-05-21
forum: General Help
---

### Post by eduarda2 on 2014-05-21
I can only run google chrome from terminal. I doesn't run from launcher. Does anyone know how to fix this? I'm using ubuntu 14.04

---

### Post by deadflowr on 2014-05-21
Maybe, right-click on the launcher select unlock from launcher.
Then hit super(the windows-logo button on keyboard) and type chrome.
Then select the google chrome icon and try launching it.
If it launches, look over at the launcher bar, and a new chrome icon should be there.
Right-click on that new one and select lock to launcher.

---

### Post by eduarda2 on 2014-05-21
I tried this but the icon doesn't run from laucher...

---

### Post by deadflowr on 2014-05-21
Does it launch from the dash(the menu/the super menu)?

---

### Post by monkeybrain20122 on 2014-05-21
In the terminal type
```
gedit /usr/share/applications/google-chrome.desktop
```

What does the line "Exec=.." say?

In mine it says 

```
Exec=/usr/bin/google-chrome-stable %U
```
This is a symbolic link actually as the binary is /opt/google/chrome/google-chrome

So in your case maybe somehow the symlink was not created
in that case do
```
sudo ln -s /opt/google/chrome/google-chrome /usr/bin/google-chrome-stable

```

You can alternatively change the Exec line in the .desktop file to point to the actual location of the chrome binary but in that case a chrome upgrade will wipe it out.

---

### Post by deadflowr on 2014-05-22
I would think, if running google-chrome from the browser, that the link to the /opt folder is intact.
However, yes, a post of the Exec line(s) would give us a better understand if there is a flaw.
There are three Exec commands for chrome in that file.
A simple way to easily post all three without having to search the long string of Name= lines is this command
```
cat /usr/share/applications/google-chrome.desktop | grep Exec
```
or in gedit, use the word search feature.
(It is the magnifying glass in the gedit toolbar)

---

