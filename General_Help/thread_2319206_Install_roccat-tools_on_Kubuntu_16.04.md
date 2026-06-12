---
title: "Install roccat-tools on Kubuntu 16.04"
date: 2016-04-01
forum: General Help
---

### Post by Aydos on 2016-04-01
Hello I just purchased a Roccat Ryos TKL Pro mechanical keyboard after seeing they had Linux support.

I have it hooked up and it works, but I want to use the software to manage all of the features.

There is a ppa for the software. [https://launchpad.net/~berfenger/+archive/ubuntu/roccat](https://launchpad.net/~berfenger/+archive/ubuntu/roccat)

I have the PPA installed and I can see it in my repository list and I can see it update when I sudo apt-get update.

However, when I sudo apt-get install roccat-tools it responds with unable to locate package.

I believe it is because there is not a folder past Wily yet.

What are my options for installing via this PPA?

Is there away to make it install the Wily version of the software and if so would this break anything?

There is a down loadable installer from sourceforge found at [http://roccat.sourceforge.net/](http://roccat.sourceforge.net/) , but when I use that it says it cant find GTK packages. I am on KDE so I did not know if I wanted to install of those packages.

Any help would be much appreciated. Thank you.

---

### Post by Aydos on 2016-04-02
as an update if I sudo apt-get install roccat-tools-3.9.0 I get 
[FONT=monospace][COLOR=#000000]E: Couldn't find any package by glob 'roccat-tools-3.9.0'[/COLOR]
E: Couldn't find any package by regex [/FONT][COLOR=#000000][FONT=monospace]'roccat-tools-3.9.0' 

I am not sure what that means.[/FONT][/COLOR]

---

### Post by ppjdd on 2016-04-27
There is a newer version of roccat-tools on sourceforge. That might help.

---

