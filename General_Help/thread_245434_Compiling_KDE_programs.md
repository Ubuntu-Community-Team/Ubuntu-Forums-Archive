---
title: "Compiling KDE programs?"
date: 2006-08-27
forum: General Help
---

### Post by Castar on 2006-08-27
Hi,

I'm trying to install [this cool applet]("http://www.kde-look.org/content/show.php?content=22605") for kicker (KDE) and when I do

./configure

I get this error

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

I tried to install kde-devel but Adept claims it will break everything, so it doesn't install it. 

Any ideas? :confused: 

Thanks

---

### Post by taurus on 2006-08-27
I assume you know by now that if you want to build something from source, you need to install all the necessary files, developing, before you can compile anything.  Therefore, use synaptic and search for kde-dev...  So, back up your personal files or important files and go for it!

---

### Post by Anonii on 2006-08-27
> **Castar said:**
> Hi,

I'm trying to install [this cool applet]("http://www.kde-look.org/content/show.php?content=22605") for kicker (KDE) and when I do

./configure

I get this error

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

I tried to install kde-devel but Adept claims it will break everything, so it doesn't install it. 

Any ideas? :confused: 

Thanks

I guess you are using GNOME. Its logical that you dont have the KDE libs, and KDE headers installed, so its better to use APT that will download ALL the dependencies. (Its always better to use APT, in an APT based system like Ubuntu, so get used to it :] ).
You can easily do this by executing this:
sudo apt-get install kicker
in a terminal. It will _easily_ download everything you need, and you will have it working in no time :3

Finally, you _MUST_ read this:
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

### Post by Castar on 2006-08-28
I am using KDE and kubuntu. I have successfully installed the X includes and headers but as I said, when I try to install the kde-devel headers, I cannot since it will break the installation.

I'm using KDE 3.5.4 btw. I will try synaptic.

---

### Post by elettronicha on 2006-08-28
> **Castar said:**
> when I try to install the kde-devel headers, I cannot since it will break the installation.

I'm using KDE 3.5.4 btw. I will try synaptic.
Strange... If I try to install "kde-devel" I get no errors. By the way that's a meta-package, try to install only "kdebase-dev".

---

### Post by Castar on 2006-08-28
This is what I get when

sudo apt-get install kdebase-dev

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  kdebase-dev: Depends: kate (= 4:3.5.2-0ubuntu27) but 4:3.5.4-0ubuntu1~dapper2 is to be installed
               Depends: kdesktop (= 4:3.5.2-0ubuntu27) but 4:3.5.4-0ubuntu1~dapper2 is to be installed
               Depends: kicker (= 4:3.5.2-0ubuntu27) but 4:3.5.4-0ubuntu1~dapper2 is to be installed
               Depends: konqueror-nsplugins (= 4:3.5.2-0ubuntu27) but 4:3.5.4-0ubuntu1~dapper2 is to be installed
               Depends: konqueror (= 4:3.5.2-0ubuntu27) but 4:3.5.4-0ubuntu1~dapper2 is to be installed
               Depends: ksysguard (= 4:3.5.2-0ubuntu27) but 4:3.5.4-0ubuntu1~dapper2 is to be installed
               Depends: kwin (= 4:3.5.2-0ubuntu27) but 4:3.5.4-0ubuntu1~dapper2 is to be installed
               Depends: kdelibs4-dev (>= 4:3.5-rc1) but it is not going to be installed
E: Broken packages

---

### Post by Castar on 2006-08-28
I have found the problem I think. Automatix changed my repositories and disabled the kubuntu repos for KDE 3.5.4. apt could not get the updated packages so it refused installation. 

Sorry for the trouble...:oops:

---

