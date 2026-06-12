---
title: "Activate Google Chrome Dark Mode on 18.04"
date: 2019-05-16
forum: General Help
---

### Post by Erdem on 2019-05-16
Hello,

I would like to share how to activate google chrome dark mode on ubuntu 18.04. 
To do that you need to edit **google-chrome.desktop** file in **/usr/share/applications** folder.

In terminal 
```
sudo nano /usr/share/applications/google-chrome.desktop
```

if you have gnome desktop even better
```
sudo gedit /usr/share/applications/google-chrome.desktop
```

Now you should make some change in two lines.

Find this line
```
Exec=/usr/bin/google-chrome-stable %U
```
and change it like
```
Exec=/usr/bin/google-chrome-stable %U --force-dark-mode
```

Another line is
```
Exec=/usr/bin/google-chrome-stable
```
and change it 
```
Exec=/usr/bin/google-chrome-stable --force-dark-mode
```

You should totally close chrome and when you open it again you will see the dark theme activated.
If it is not working you can try to reboot your ubuntu.

Please keep in mind chrome over-write on this file every time it's updated.

---

### Post by deadflowr on 2019-05-16
Just copy the file to the user's .local/share/applications directory.
That way it won't get overwritten on updates.

This also is beneficial in allowing editing without root.

And never run sudo on graphical apps like gedit.
If need be use admin:// like
```
gedit admin:///usr/share/applications/google-chrome.desktop
```
or use sudo -H
like
```
 sudo -H /usr/share/applications/google-chrome.desktop
```
More here:
[https://help.ubuntu.com/community/RootSudo#Graphical_sudo]("https://help.ubuntu.com/community/RootSudo#Graphical_sudo")

---

