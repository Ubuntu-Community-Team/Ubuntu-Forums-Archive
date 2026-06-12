---
title: "How to install Electrum Wallet on Lubuntu 16.04?"
date: 2019-06-13
forum: General Help
---

### Post by rbscebu on 2019-06-13
I am trying to install Electrum 3.3.6 on my desktop with Lubuntu 16.04. I previously tried using the python installation method for Electrum but gave up after 8 hours of trying. I now want to try with the Electrum Appimage (which I have been told is the easy way).

I have downloaded the Electrum Appimage and now have the folder Electrum-3.3.6 in my home folder. The Electrum-3.3.6 folder contains-

Folders:[INDENT]contrib
electrum
Electrum.egg-info
PACKAGES

[/INDENT]
Files:[INDENT]AUTHORS
Electrum Bitcoin Wallet
LICENCE
MANIFESAT.in
PKG-INFO
README.rst
RELEASE-NOTES
run_electrun
setup.cfg
setup.py

[/INDENT]

I have read the README file but that only seems to cover the python installation.

What do I now do to get the Electrum wallet to work on my desktop?

---

### Post by again? on 2019-06-13
If you downloaded the appimage you should have a file **electrum-3.3.6-x86_64.AppImage** or similar in your downloads directory.
[https://electrum.org/#download](https://electrum.org/#download)

_To run via GUI_
Right click on the .AppImage file..... *properties > permissions* and make executable.
Then double click on file to launch.

_To run via terminal_
[LIST=1]
[*]Change to the directory (cd) containing the AppImage.
[*]Make the AppImage executable.
[*]Run the AppImage.
[/LIST]

eg
```
cd ~/Downloads
chmod +x [COLOR="#FF0000"]elect[/COLOR]rum-3.3.6-x86_64.AppImage
./[COLOR="#FF0000"]elect[/COLOR]rum-3.3.6-x86_64.AppImage
```

When typing in the name of the appimage file, type in "[COLOR="#FF0000"]elect[/COLOR]" then hit the Tab key to autocomplete.

---

### Post by rbscairns on 2019-07-21
Thank you guber2 for your guidance, however I am still having problems.

I downloaded electrum-3.3.8-x86_64.AppImage into my Downloads folder. In that file's Properties>Permissions under Access Control I set Execute: to Only owner and group (followed by OK). I then double clicked on electrum-3.3.8-x86_64.AppImage and got a file in my Downloads folder named &#65533;F@@&#65533;&#65533;@8@

All very strange.

I then tried to run via Terminal and got the following error:

```
richard@CEBPC01:~$ cd ~/Downloads
richard@CEBPC01:~/Downloads$ chmod +x electrum-3.3.8-x86_64.AppImage
richard@CEBPC01:~/Downloads$ ./electrum-3.3.8-x86_64.AppImage
bash: ./electrum-3.3.8-x86_64.AppImage: cannot execute binary file: Exec format error
richard@CEBPC01:~/Downloads$ 
```

What should I try next?

---

### Post by again? on 2019-07-22
Are you running a 32bit Ubuntu...
```
uname -a
```

---

