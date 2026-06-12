---
title: "App Installs Result in Failed to Fetch + 404 Error"
date: 2014-03-13
forum: General Help
---

### Post by zecharixs on 2014-03-13
I got a .deb file for Adobe Reader and tried to install with gdebi package manager. I got this error when it started downloading additional files.

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnutls26/libgnutls26_2.12.14-5ubuntu3.5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnutls26/libgnutls26_2.12.14-5ubuntu3.5_i386.deb) 404  Not Found [IP: 91.189.91.14 80]

I also tried it with Steam.deb and got a similar error.

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/curl/curl_7.22.0-3ubuntu4.6_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/curl/curl_7.22.0-3ubuntu4.6_amd64.deb) 404  Not Found [IP: 91.189.92.200 80]

The web browser is working perfectly so I don't understand why there would be a connection error. BTW, I'm running Ubuntu through Crouton on the Chromebook Pixel. How do I fix this?

---

### Post by deadflowr on 2014-03-13
I think your package list is out of date.
You can simply update it with
```
sudo apt-get update
```
which will bring the list of packages you can install up to date

or, better yet
open the program "Update Manager", or as it is called for newer versions such as 13.10,
"Software Updater" and install all the updates.
(If you are on 12.04, then when you start the update manager, click on the button Check first. This runs the apt-get update command.
12.10 and newer automatically runs this when the updater starts, so...)


The only thing is I haven't a clue on what happens to crouton setups when installing updates, so
buyer beware.

(I don't think anything bad will happen, but you never know)

---

### Post by zecharixs on 2014-03-14
I tried to update and I got an error that said check your internet connection, followed by an error message:
E: The method driver /usr/lib/apt/methods/https could not be found.
I've never had a problem downloading updates before on Crouton before.
Edit: Wait nvm. I looked for the file on the web and installed it and now the update works and steam installs correctly.

---

