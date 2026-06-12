---
title: "Can't Get Gnome Shell to Work"
date: 2019-03-23
forum: General Help
---

### Post by Quarkrad on 2019-03-23
Running Mate 18.04, Gnome Shell 3.28.3.   I need help getting gnome shell working with pref Firefox 66 or Chromium 73.  I have spent many hours going through solutions and attempting to reinstall but nothing seems to work.  When I go to [https://extensions.gnome.org/](https://extensions.gnome.org/)  I am presented at the top of the page with **Unable to locate GNOME Shell settings or version. Make sure it is installed and running** - as per attached.  I can get everything working OK in a VBox environment - I'm guessing, despite everything being up to date there is some config somewhere causing this problem.  Any help appreciated.

---

### Post by kc1di on 2019-03-23
if your using ubuntu-mate why would you want gnome-shell involved.  If you want to run gnome - switch to ubuntu That already has gnome installed as the default desktop.  Sounds like your trying to mix desktops and that is always a problem.

---

### Post by Quarkrad on 2019-03-23
I'm trying to get my Desktop to communicate/transfer a file to my Android phone via wifi.  I've tried a number of FTP solutions but they have not worked.  The latest solution I would like to try involves installing GSConnect via gnome shell. (source: [https://www.omgubuntu.co.uk/2018/11/connect-android-ubuntu-gsconnect](https://www.omgubuntu.co.uk/2018/11/connect-android-ubuntu-gsconnect)).

---

### Post by kc1di on 2019-03-23
I do think you'll have to install ubuntu and not mate to make it work.  But I could be wrong. That is I believe you'll need a gnome desktop to run it.

---

### Post by deadflowr on 2019-03-23
To install the extensions from the website you need 
1)to be running gnome-shell.
2)have the package chrome-gnome-shell installed on your system; installable through apt/apt-get/synaptic/probably software store.
3)have the chrome-gnome-shell enabled in the browsers add-ons/extensions settings.
(The extension is called Gnome Shell Integration inside the browser)

---

### Post by Quarkrad on 2019-03-23
Thank you all for your help. I got it working in the end using gnome Desktop in Vbox.

---

### Post by kc1di on 2019-03-23
Glad you got is sorted out :)

---

