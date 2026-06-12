---
title: "Adding Chromium as default browser adds --disable-web-security setting"
date: 2018-10-01
forum: General Help
---

### Post by alkarinv on 2018-10-01
Today I went to open up my chromium browser and I noticed something odd.

The Chromium browser is being titled as Estimator5 - Chromium

> [IMG]https://i.imgur.com/JysCpJU.png[/IMG]

Now I know Estimator5 happens to be the title of an angular app project I have on my machine, and I previously had to test something with it by opening a new chrome instance in a terminal with
```

chromium-browser --disable-web-security --user-data-dir="USR_DIR]"
```
However I haven't had issues with this for weeks.

When I go to Details > Default Applications I see the chromium option named as `Estimator5 - Chromium`. If I select another option like firefox, and then populate the dropdown again, I do NOT see the estimator titled browser, and I do not see a normal `chromium` browser option either.

I can successfully open chromium via the terminal
```
chromium-browser
```

When this browser opens, it asks me to set the browser as my default, which I click "set as default". But when viewing my default browser option, it is again set to `Estimator5 - Chromium`, and if I click any links it populates with a chromium browser that is warning I have `--disable-web-security` enabled.

I've attempted multiple times to reinstall chromium by doing the following:

```
sudo apt-get purge chromium-browser
rm ~/.config/chromium/ -rf
rm ~/.cache/chromium/ -rf
#Restarting PC
sudo apt-get install chromium-browser
```

However, this issue keeps happening. This is fairly frustrating as any links I attempt to open with this as a default browser, do not actually open the links, and just opens a new browser window set to the url of 'directory'

If anyone has any ideas or advice I greatly appreciate it.

Sorry in advance of any formatting issues or if this is the wrong place to post.

Thanks!

---

### Post by deadflowr on 2018-10-01
Look in ~/.local/share/applications for any chromium related .desktop files.
Any .desktop file in this directory overrides any in the main system desktop file directory and will never get removed when the related program is removed; 
you must manually delete the .desktop files in here.
(unlike those in the main system directory, which will get removed if the related program is removed)
This can cause a sort of time loop (or fruit loop, or something; probably a better analogy out there for it) of rinse and repeating the same thing over and over again.

---

### Post by alkarinv on 2018-10-03
Thank you deadflowr! I knew there had to be something somewhere that was being brought back from the dead.

I'll add my final steps in case anyone else ever runs into a similar issue:

```
sudo apt-get purge chromium-browser
rm ~/.config/chromium/ -rf
rm ~/.cache/chromium/ -rf
rm ~/.local/share/applications/{chromium/chrome related .desktop files}
#Restarting PC
sudo apt-get install chromium-browser
```


From here I was able to confirm the desktop icon was no longer being named differently, the default browser option was showing the correct name now, and when opening links they now properly open in my default browser.  :)

Thanks again!

---

