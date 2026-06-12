---
title: "Failure to download extra data files (flash &amp; mscorefonts)"
date: 2016-12-15
forum: General Help
---

### Post by Macamba on 2016-12-15
My new installed Ubuntu (16.04) is trying to install the > flashplugin-installer and ttf-mscorefonts-installer The installation however fails every time. There is a button labeled "Run this action now", after entering the root password this results in a terminal opening, a list of actions flashing by and closing of the terminal. I do not see any success message. But the next day the dialog is shown again. What are my options?

---

### Post by howefield on 2016-12-15
Have you got the ms fonts downloaded, you should have Andale Mono, Arial Black, Arial, Comic Sans MS, Courier New, Georgia, Impact, Times New Roman, Trebuchet, Verdana and Webdings ?

Try..

```
sudo touch /var/lib/update-notifier/package-data-downloads/ttf-mscorefonts-installer
```

---

### Post by Macamba on 2016-12-16
I looked in ```
/usr/share/fonts
``` And I found no Arial. In that directory I followed up with a ```
find . -name arial
``` I got the same result: nothing. Lastly I tried your suggested 
```
sudo touch /var/lib/update-notifier/package-data-downloads/ttf-mscorefonts-installer
```
and nothing seemed to happen. Should anything have happened?

---

### Post by howefield on 2016-12-16
> **Macamba said:**
> I looked in ```
/usr/share/fonts
``` And I found no Arial. In that directory I followed up with a ```
find . -name arial
``` I got the same result: nothing.

You can double check by loading up LibreOffice, is Arial there ?

Lastly I tried your suggested 
```
sudo touch /var/lib/update-notifier/package-data-downloads/ttf-mscorefonts-installer
```
and nothing seemed to happen. Should anything have happened?[/QUOTE]

You wouldn't have gotten any feedback in the terminal, it is a fix reported by some users as preventing the pop up you describe in the OP.

---

