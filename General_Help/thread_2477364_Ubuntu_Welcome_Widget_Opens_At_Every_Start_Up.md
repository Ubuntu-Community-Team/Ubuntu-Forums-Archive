---
title: "Ubuntu Welcome Widget Opens At Every Start Up"
date: 2022-07-22
forum: General Help
---

### Post by jpvetter on 2022-07-22
As the title states, my Ubuntu Welcome Widget window continues to open after every start up and I'm not sure if I'm just not seeing a way to stop it from opening or if I need to complete something specific. Been having trouble finding an answer.

Thanks in advance!

---

### Post by #&amp;thj^% on 2022-07-22
Which DE??? Gnome and Mate are the only two that have this behavior. Details please...

---

### Post by grahammechanical on 2022-07-22
If you are asking about Automatic Login, then open System Setting>Users. Your password will unlock the utility and then you can move the Automatic Login slider.

Other than that, I do not know what a Ubuntu welcome widget is. I have never seen one in all the years I have been using Ubuntu. Except when using Ubuntu from a DVD disc or USB memory stick. If this is what you are doing then I think that you are stuck with it.

Regards

---

### Post by mIk3_08 on 2022-07-23
> **jpvetter said:**
> As the title states, my Ubuntu Welcome Widget window continues to open after every start up and I'm not sure if I'm just not seeing a way to stop it from opening or if I need to complete something specific. Been having trouble finding an answer.
Thanks in advance!
Please run this command below in your terminal, To access terminal in your Linux Ubuntu Desktop, just press ctrl and alt + t or just find it under your Linux Ubuntu installed applications. Regards and cheers.
```
hostnamectl status 
```

---

### Post by #&amp;thj^% on 2022-07-23
I'm *guessing* the OP is after this, "**gnome-initial-setup**"
A one liner to disable it
```

sudo bash -c 'echo "X-GNOME-Autostart-enabled=false" >> /etc/xdg/autostart/gnome-initial-setup-first-login.desktop'
```
Or if you feel you will need it at some point, use this:
Edit /etc/gdm3/custom.conf and add the following:
```

[daemon]


/usr/lib/gnome-initial-setup/gnome-initial-setup --existing-user
```

---

### Post by jpvetter on 2022-07-25
> **grahammechanical said:**
> If you are asking about Automatic Login, then open System Setting>Users. Your password will unlock the utility and then you can move the Automatic Login slider.

Other than that, I do not know what a Ubuntu welcome widget is. I have never seen one in all the years I have been using Ubuntu. Except when using Ubuntu from a DVD disc or USB memory stick. If this is what you are doing then I think that you are stuck with it.

Regards

Ubuntu 22.04 LTS

The screen/widget/app I'm referring to is the one that asks to sign in to Google/Microsoft/Canonical accounts, turn on location services and also brings up recommended applications to install. It opens on every boot.

---

### Post by #&amp;thj^% on 2022-07-25
> **jpvetter said:**
> Ubuntu 22.04 LTS

The screen/widget/app I'm referring to is the one that asks to sign in to Google/Microsoft/Canonical accounts, turn on location services and also brings up recommended applications to install. It opens on every boot.
Ok Thats different and a bit more complex but this should work:
```
sudo sed -i 5d /etc/xdg/autostart/gnome-initial-setup-first-login.desktop && sudo sed -i '5i#Exec=/usr/libexec/gnome-initial-setup --existing-user' /etc/xdg/autostart/gnome-initial-setup-first-login.desktop
[sudo] password for me: 

```
This is why it's a little complex:
```

me@me-Standard-PC-Q35-ICH9-2009:~$ apt show gnome-initial-setup
Package: gnome-initial-setup
Version: 42.0.1-1ubuntu2
Priority: optional
Section: gnome
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 1,749 kB
Depends: libaccountsservice0 (>= 0.6.24), libc6 (>= 2.34), libcairo2 (>= 1.2.4), libcheese-gtk25 (>= 3.28), libcheese8 (>= 3.18.0), libfontconfig1 (>= 2.12.6), libgdk-pixbuf-2.0-0 (>= 2.25.2), libgdm1 (>= 3.8.3), libgeoclue-2-0 (>= 2.4.0), libglib2.0-0 (>= 2.63.1), libgnome-desktop-4-1 (>= 3.17.92), libgoa-1.0-0b (>= 3.5.90), libgoa-backend-1.0-1 (>= 3.10.0), libgtk-3-0 (>= 3.22.29), libgweather-3-16 (>= 3.13.91), libhandy-1-0 (>= 1.5.90), libibus-1.0-5 (>= 1.5.2), libjson-glib-1.0-0 (>= 1.5.2), libkrb5-3 (>= 1.8+dfsg), libnm0 (>= 1.2), libnma0 (>= 1.1.90), libpango-1.0-0 (>= 1.32.5), libpangocairo-1.0-0 (>= 1.32.5), libpolkit-gobject-1-0 (>= 0.103), libpwquality1 (>= 1.1.0), librest-0.7-0 (>= 0.7), libsecret-1-0 (>= 0.18.8), libsnapd-glib1 (>= 1.42), libsoup2.4-1 (>= 2.41.90), libsysmetrics1 (>= 1.0.5), libwebkit2gtk-4.0-37 (>= 2.26), policykit-1 (>= 0.103), adduser, gnome-settings-daemon (>= 3.24), gnome-control-center-data
Recommends: accountsservice, geoclue-2.0 (>= 2.3.1), gnome-keyring
Suggests: gdm3
Homepage: https://git.gnome.org/browse/gnome-initial-setup/
Task: ubuntu-desktop-minimal, ubuntu-desktop
Download-Size: 987 kB
APT-Manual-Installed: no
APT-Sources: http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
Description: Initial GNOME system setup helper
 After acquiring or installing a new system there are a few essential things
 to set up before use. GNOME Initial Setup aims to provide a simple, easy,
 and safe way to prepare a new system.
 .
 GNOME Initial Setup runs the first time you log in to the GNOME desktop
 and lets you easily configure your language, keyboard layout, online accounts
 integration, and more.
 .
 If you want to configure these things at any other time, run the Settings app.
```

Now if you want to revert this at some point;
```
sudo sed -i 5d /etc/xdg/autostart/gnome-initial-setup-first-login.desktop && sudo sed -i '5iExec=/usr/libexec/gnome-initial-setup --existing-user' /etc/xdg/autostart/gnome-initial-setup-first-login.desktop
```
You will se a change in:
```
nano /etc/xdg/autostart/gnome-initial-setup-first-login.desktop
```
**You'll notice this is no longer used: "StartupNotify=true"**

---

### Post by jpvetter on 2022-08-15
Still getting the popup on start up. It's the "welcome to ubuntu" app.

---

### Post by #&amp;thj^% on 2022-08-15
> **jpvetter said:**
> Still getting the popup on start up. It's the "welcome to ubuntu" app.

Nor have you told us what you have followed, from our reply's or suggestions.
One more time, Note: This is for a **single user only**, 
```
mkdir /home/<yourusername>/.config
echo "yes" >> /home/<yourusername>/.config/gnome-initial-setup-done
```
If you desire to disable for ***all users*** use,
oneliner:
```
sudo bash -c 'echo "X-GNOME-Autostart-enabled=false" >> /etc/xdg/autostart/gnome-initial-setup-first-login.desktop'
```

---

### Post by jpvetter on 2022-08-15
I tried this:
sudo sed -i 5d /etc/xdg/autostart/gnome-initial-setup-first-login.desktop && sudo sed -i '5i#Exec=/usr/libexec/gnome-initial-setup --existing-user' /etc/xdg/autostart/gnome-initial-setup-first-login.desktop






I will try the suggestions above, thank you!

---

### Post by jpvetter on 2022-08-15
> **1fallen said:**
> 
If you desire to disable for ***all users*** use,
oneliner:
```
sudo bash -c 'echo "X-GNOME-Autostart-enabled=false" >> /etc/xdg/autostart/gnome-initial-setup-first-login.desktop'
```

I just tried this and I still get the application on boot. I'm confused why this application would pop up more than once after setup.

---

### Post by #&amp;thj^% on 2022-08-15
That makes two of us??
What show in your autostatrt:
Post back the return of:
```
find / -name "*autostart*" /

ls -1 "/etc/xdg/autostart" "/home/$USER/.config/autostart" "/usr/share/gdm/autostart"  "/usr/share/gnome/autostart"
```

---

