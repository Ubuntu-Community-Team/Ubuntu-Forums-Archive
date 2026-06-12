---
title: "Firefox bookmarks"
date: 2019-07-30
forum: General Help
---

### Post by newboy19 on 2019-07-30
As a newboy who has never used Linux os before i need a bit of help with a couple of questions a friend has given me his old laptop as my windows 10 has crashed and will be out of action for a while .but have to say this old free laptop is good  what i would like to know can i put bookmarks on firefox or pages i use mostly Facebook,Outlook BBC player etc etc and how can i see what version of os i am using  . All advice welcome

---

### Post by TheFu on 2019-07-30
Firefox profiles are cross platform.  Just copy the entire profile from your Windows machine to the Linux machine.  Put it into the "expected location" and it will work.  Same for OSX.  Firefox stores bookmarks as html.  Binary 'plugins' dont work, obviously. I haven't tried this in a few years and I've never touched Win10, so YMMV.

Google "Ubuntu Users guide" for answers to many of your questions. Of course, not all will be answered and it is absolutely fine to ask here. I just did that and found 6 semi-official guides from reputable places at the top.

---

### Post by oldfred on 2019-07-30
Since XP I have copied my Firefox & Thunderbird profile from Windows & Linux back & forth. But for first time when loaded into 19.10 test install, it worked, but loading with my main working install 18.04 gave errors on older Firefox version. (both were same version, supposedly). I ended up restoring from backup.
       Firefox
[https://support.mozilla.org/en-US/products/firefox](https://support.mozilla.org/en-US/products/firefox)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles](https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles)
Firefox files:
[https://support.mozilla.org/en-US/kb/recovering-important-data-from-an-old-profile](https://support.mozilla.org/en-US/kb/recovering-important-data-from-an-old-profile)
[https://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data?redirectlocale=en-US&redirectslug=Profiles](https://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data?redirectlocale=en-US&redirectslug=Profiles)

This will show Ubuntu version:
```
fred@bionic-z97:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:    bionic
fred@bionic-z97:~$ echo $DESKTOP_SESSION
gnome-flashback-metacity
fred@bionic-z97:~$ gnome-shell --version
GNOME Shell 3.28.4

```

---

### Post by SeijiSensei on 2019-07-30
If you just want to move the bookmarks, go to

Bookmarks > Show All Bookmarks > Import and Backup > Export Bookmarks to HTML

Copy the bookmarks.html it creates to the other machine, then use the Import Bookmarks from HTML option.

---

### Post by mastablasta on 2019-07-31
or just use firefox sync.

---

### Post by newboy19 on 2019-07-31
Thanks for all reply before i posted my question i had a look on on YouTube for info and user guide and what i saw was nothing like the desktop layout i have on my laptop i will att some photos if you look at firefox on the Win 10 pc you van see 4 vertical lines ontop right hand side that gives you you bookmarks etc on my ubuntu firefox they are not there  i also post layout of desktop . I am thinking of buying a ready made usb with the latest version and give that a test run.

---

### Post by ajgreeny on 2019-07-31
I am not sure if this works in all platforms but when I press the left Alt key the menu bar appears in my Firefox; click that and you can click "Show all bookmarks" to see the bookmarks library window.

You can also hit **Ctrl+Shift+O** and the same bookmarks library window will appear.

---

### Post by howefield on 2019-07-31
> **newboy19 said:**
> ...on my ubuntu firefox they are not there ...

Try clicking on the hamburger menu on the very right hand side and select *Library > Bookmarks*.

---

### Post by mastablasta on 2019-07-31
old version of Xubuntu OS and Firefox is an old version as well. as others said hamburger icon has bookmarks menu as well as the alt key brings the text menues.

---

### Post by walts48 on 2019-07-31
> **newboy19 said:**
> Thanks for all reply before i posted my question i had a look on on YouTube for info and user guide and what i saw was nothing like the desktop layout i have on my laptop i will att some photos if you look at firefox on the Win 10 pc you van see 4 vertical lines ontop right hand side that gives you you bookmarks etc on my ubuntu firefox they are not there  i also post layout of desktop . I am thinking of buying a ready made usb with the latest version and give that a test run.

Right click in the Tab bar, select Customize, look for the Library icon you show in the first screen shot and move it to the Toolbar.

---

### Post by newboy19 on 2019-07-31
Thank you for swift replies and you have sorted it out i have bookmarks and home icon now so thank you , mastablasta points  out i have old version of OS & Firefox so i will get the latest one so stand by for more questions to come later.  I have downloaded the help guide for beginners for future education.

---

