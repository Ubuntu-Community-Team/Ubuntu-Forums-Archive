---
title: "no default browser"
date: 2004-11-05
forum: General Help
---

### Post by Verlager on 2004-11-05
I uninstalled my Firefox 0.93 with Synaptic because I wanted a newer version

I untarred **firefox-1.0PR-i686-linux-gtk2+xft-installer.tar.gz**; **cd firefox-installer**; ran: **firefox-installer**; -which generated firefox, fine! I then modified the application menu Firefox entry to point to /home/verlager/firefox-installer/firefox -a Hell of a place to put a system-wide web browser, but I'm getting desparate.

It all looked fine, just peachy-keen _until I clicked a hyperlink in an email and nothing happened_. I conclude that the system doesn't recognizes the new Firefox 1.0PR as the default browser. 

**[SIZE=3]Any suggestions?[/SIZE]**

---

### Post by im_ka on 2004-11-05
try computer/desktop preferences/preferred applications and add "mozilla-firefox" to web-browser

hth

---

### Post by FLeiXiuS on 2004-11-05
> **Verlager]I uninstalled my Firefox 0.93 with Synaptic because I wanted a newer version

I untarred **firefox-1.0PR-i686-linux-gtk2+xft-installer.tar.gz** said:**
> Any suggestions?[/SIZE]**


Where was the email located?  I believe thunderbird has its own option for which browser to open.

---

### Post by Verlager on 2004-11-05
That didn't work. I changed the preferred browser to _mozilla-firefox_ and to _firefox_ and neither worked. But thanks, that showed where to look for interesting things. Any other ideas?

---

### Post by im_ka on 2004-11-05
[QUOTE=Verlager]That didn't work. I changed the preferred browser to _mozilla-firefox_ and to _firefox_ and neither worked. But thanks, that showed where to look for interesting things. Any other ideas?[/QUOTE]

try to add the path to the installed firefox starter.

---

### Post by Verlager on 2004-11-05
[QUOTE=FLeiXiuS]Where was the email located?  I believe thunderbird has its own option for which browser to open.[/QUOTE]The email data is located in a directory /home/rmack/.thunderbird/gwdqmrjz.default/Mail/Local Folders

Do you mean "where was the email sourced from?"

**I don't see any option in Thunderbird for selecting a web browser.  **

---

### Post by allen on 2004-11-05
slightly off-topic but.... 

why is 0.93 the latest in the repository ?

---

### Post by FLeiXiuS on 2004-11-05
[QUOTE=Verlager]**I don't see any option in Thunderbird for selecting a web browser.  **[/QUOTE]

I haven't used thunderbird in a while, perhaps they deleted the selection of a default browser.  Have you tried what was said above, with the prefered applications?

[QUOTE=allen]slightly off-topic but.... 

why is 0.93 the latest in the repository ?[/QUOTE]

If its not current/up to date then its the latest stable version.

---

### Post by Verlager on 2004-11-06
I reinstalled ubuntu.  :-|

---

### Post by Julius on 2004-11-06
You should've run mozilla-firefox from the console to check what the problem was.

Anyway, the problem at least for me was that firefox-bin didn't exist in the firefox folder. Instead, there was mozilla-firefox-bin. I just renamed it to firefox-bin and evertyhing went fine.

---

### Post by Julius on 2004-11-06
1) Download Firefox, not the installer version, and untar it somewhere.
2) Rename the old link to firefox.orig and then make a new link to the place you have installed firefox onto. 

sudo mv /usr/bin/firefox /usr/bin/firefox.orig
sudo ln -s /home/username/firefox/firefox /usr/bin/firefox

3) run mozilla-firefox from the console. It if says it cannot find firefox-bin or mozilla-firefox-bin, go to the folder your firefox is, and rename the existing mozilla-firefox-bin to firefox-bin (you can also have both)

4) Voila! That should work

---

### Post by az on 2004-11-06
Whatever you do, you should remove the old version first!

This is easy - remember that you are using a Debian-based system?

Go into synaptic and remove the package.

Then go and bugger about your home directory...

---

