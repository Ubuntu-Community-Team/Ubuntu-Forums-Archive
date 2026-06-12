---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2016-01-08
forum: General Help
---

### Post by jakr2 on 2016-01-08
I get this error on nearly every command I run, I tried re-installing Ubuntu but it wont let me re-install because I just get this error - ACPI PCC Probe Failed
also I cant connect via ssh on other operating systems. Everything was fine a few hours ago im not very good with linux so any help would be appreciated.

---

### Post by v3.xx on 2016-01-08
Hi jakr2

> error - ACPI PCC Probe Failed
This seems to be going around
[https://www.google.com/search?q=error+-+ACPI+PCC+Probe+Failed&ie=utf-8&oe=utf-8](https://www.google.com/search?q=error+-+ACPI+PCC+Probe+Failed&ie=utf-8&oe=utf-8)
and from what I'm reading, not a concern for you since you can still boot (?).

> Sub-process /usr/bin/dpkg returned an error code (1)
Is a general error code and needs to be narrowed down.  If you still have a working system please run the following commands in terminal and post any errors you get.

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

---

### Post by jakr2 on 2016-01-08
I was looking around for more fixes and im not getting the below error no more[B]
E: Sub-process /usr/bin/dpkg returned an error code (1)

[/B]But now I cant install any packages and im not getting no error from the above commands you told me to issue. 

Im trying to install htop and I get this
```
# sudo apt-get install htop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package htop
```

Still cant connect via SSH and error - ACPI PCC Probe Failed is sort of a problem as I cant re-install ubutnu

---

### Post by v3.xx on 2016-01-08
> Unable to locate package htop
Weird

Lets see what you got.  Please post the output of
```
inxi -b
```

---

### Post by jakr2 on 2016-01-08
I get universe must be enabled so I did
sudo add-apt-repository universe

Now I try to install htop and get the same error but if I do inxi - b again and I get
The program 'inxi' is currently not installed. You can install it by typing:
apt-get install inxi

I try to install it and I get
# apt-get install inxi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package inxi

Okay now I can install htop but I cant connect via SSH on other machines.

---

### Post by v3.xx on 2016-01-08
Ok, please post the output of

```
lsb_release -a
```

Edit:
Just seen your last post

Again, weird

---

### Post by jakr2 on 2016-01-08
```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty
```

No solution?

---

### Post by v3.xx on 2016-01-08
Ok, thats good.

Lets take a look at your sources.

```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
```

---

### Post by jakr2 on 2016-01-08
```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
deb http://archive.ubuntu.com/ubuntu trusty main universe
/etc/apt/sources.list.d/ajenti.list[
/etc/apt/sources.list.d/ispsystem-base.list
/etc/apt/sources.list.d/ispsystem.list
/etc/apt/sources.list.d/nginx.list
/etc/apt/sources.list.d/vesta.list
/etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list
```

---

### Post by v3.xx on 2016-01-08
Bingo

Your sources list is missing.  But there is a backup, lets see what shape its in.  Please post the output of..

```
cat /etc/apt/sources.list.save
```

---

### Post by jakr2 on 2016-01-08
```
# cat /etc/apt/sources.list.save
deb mirror://mirrors.ubuntu.com/mirrors.txt trusty main restricted
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty-updates main restricted

deb mirror://mirrors.ubuntu.com/mirrors.txt trusty universe
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty universe

deb mirror://mirrors.ubuntu.com/mirrors.txt trusty-updates universe
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty-updates universe

deb mirror://mirrors.ubuntu.com/mirrors.txt trusty multiverse
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty multiverse

deb mirror://mirrors.ubuntu.com/mirrors.txt trusty-updates multiverse
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty-updates multiverse

deb mirror://mirrors.ubuntu.com/mirrors.txt trusty-backports main restricted universe multiverse
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty-backports main restricted universe multiverse

deb mirror://mirrors.ubuntu.com/mirrors.txt trusty-security main restricted
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty-security main restricted

deb mirror://mirrors.ubuntu.com/mirrors.txt trusty-security universe
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty-security universe 
```

---

### Post by v3.xx on 2016-01-08
Run this code
```
sudo mv /etc/apt/sources.list.save /etc/apt/sources.list
```

Then do another update and upgrade in terminal and see what happens.

---

### Post by jakr2 on 2016-01-08
Nope still cant connect

---

### Post by v3.xx on 2016-01-08
Check your sources.list again.
```
cat /etc/apt/sources.list
```
also
```
gksudo software-properties-gtk
```
In your case, all boxes in "Downloadable from inet" should be checked.  What are you seeing for "Download from"?

And CDrom/DVD should be unchecked.

Here's mine as a example
[ATTACH=CONFIG]266617[/ATTACH]

---

### Post by jakr2 on 2016-01-08
```
cat /etc/apt/sources.list
deb mirror://mirrors.ubuntu.com/mirrors.txt trusty main restricted
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty-updates main restricted

deb mirror://mirrors.ubuntu.com/mirrors.txt trusty universe
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty universe

deb mirror://mirrors.ubuntu.com/mirrors.txt trusty-updates universe
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty-updates universe

deb mirror://mirrors.ubuntu.com/mirrors.txt trusty multiverse
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty multiverse

deb mirror://mirrors.ubuntu.com/mirrors.txt trusty-updates multiverse
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty-updates multiverse

deb mirror://mirrors.ubuntu.com/mirrors.txt trusty-backports main restricted universe multiverse
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty-backports main restricted universe multiverse

deb mirror://mirrors.ubuntu.com/mirrors.txt trusty-security main restricted
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty-security main restricted

deb mirror://mirrors.ubuntu.com/mirrors.txt trusty-security universe
deb-src mirror://mirrors.ubuntu.com/mirrors.txt trusty-security universe
```

And for gksudo I get
```
kup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_cascade_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_style_provider_get_style_property: assertion 'GTK_IS_STYLE_PROVIDER (provider)' failed

(software-properties-gtk:4778): Gdk-CRITICAL **: gdk_pango_context_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Pango-CRITICAL **: pango_context_set_font_description: assertion 'context != NULL' failed

(software-properties-gtk:4778): Pango-CRITICAL **: pango_context_set_base_dir: assertion 'context != NULL' failed

(software-properties-gtk:4778): Pango-CRITICAL **: pango_context_set_language: assertion 'context != NULL' failed

(software-properties-gtk:4778): Pango-CRITICAL **: pango_context_set_base_dir: assertion 'context != NULL' failed

(software-properties-gtk:4778): Gdk-CRITICAL **: gdk_pango_context_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Pango-CRITICAL **: pango_context_set_font_description: assertion 'context != NULL' failed

(software-properties-gtk:4778): Pango-CRITICAL **: pango_context_set_base_dir: assertion 'context != NULL' failed

(software-properties-gtk:4778): Pango-CRITICAL **: pango_context_set_language: assertion 'context != NULL' failed

(software-properties-gtk:4778): Pango-CRITICAL **: pango_context_set_base_dir: assertion 'context != NULL' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gdk-CRITICAL **: gdk_screen_get_display: assertion 'GDK_IS_SCREEN (screen)' failed

(software-properties-gtk:4778): Gdk-CRITICAL **: gdk_keymap_get_for_display: assertion 'GDK_IS_DISPLAY (display)' failed

(software-properties-gtk:4778): Gdk-CRITICAL **: gdk_keymap_get_direction: assertion 'GDK_IS_KEYMAP (keymap)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIVATE (provider)' failed

(software-properties-gtk:4778): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_CSS_VALUE_RGBA' failed
  
```

---

### Post by v3.xx on 2016-01-08
Ok, now I'm stuck.  Need to research this, be back :)

---

### Post by jakr2 on 2016-01-08
Do you know a way of re installing ubuntu would save a lot of hassle. Also thanks for the help

---

### Post by Bashing-om on 2016-01-08
jakr2; 
v3.xx' Ole buddy !

Have not looked closely at the thread, but
Internet connectivity ?
what returns:
```

ping -c3 ubuntu.com

```

[INDENT]where do we have a failure
[INDENT][INDENT][INDENT][INDENT]to communicate
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by v3.xx on 2016-01-08
Hey Bashing :D

Please do

I'm busy looking at kup

---

### Post by jakr2 on 2016-01-08
```
ping -c3 ubuntu.com
PING ubuntu.com (91.189.94.40) 56(84) bytes of data.
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=1 ttl=52 time=26.3 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=2 ttl=52 time=23.1 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=3 ttl=52 time=24.5 ms

--- ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 23.180/24.697/26.397/1.325 ms
```

Fixed, I had to flush iptables and add them again. Thank you for the help.

---

### Post by v3.xx on 2016-01-08
Wow, nice :D

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Happy trails

And see ya later Bashing :)

---

