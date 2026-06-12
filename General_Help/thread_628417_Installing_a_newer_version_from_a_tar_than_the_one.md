---
title: "Installing a newer version from a tar than the one in the repositories"
date: 2007-12-01
forum: General Help
---

### Post by lightstream on 2007-12-01
Hi

The version of an application I'm using (Eclipse) is significantly behind the latest release.

I have downloaded the tar file of the latest version, but already have the repository version installed.

Is it necessary to uninstall the repository version first before I install the tar?

Also can anyone tell me what the best location is for installing apps from tar files? I generally just do it from wherever they were downloaded to, which might not always be the most appropriate place!

Thanks for any help

---

### Post by mysticrider92 on 2007-12-01
I think you will probably need to remove the repository version first, just to solve any file conflicts, but you might not. You could try with it still installed, but I doubt it will work.

The place you have the untarred source in isn't always the place it will be installed (the install path is easily changeable when running ./configure), but /usr/local is probably the best place. It all depends on what you are installing, some apps need different locations, but will most likely install to a certain place set in the configure script.

---

### Post by lightstream on 2007-12-01
Thanks buddy, I'll do the uninstall first. Eclipse is a java app, so no compilation is necessary. I think it's just a case of extract and go!

If I install to 'usr/local' would it then be available for all users?

I will try to find where the current version is installed before I uninstall, although I've found tracking down where an app is installed rather difficult in the past ..

---

### Post by mysticrider92 on 2007-12-01
Hmm, I forgot about that... There should still be some kind of installer to put the .jar files (I assume that is what they use) and documentation in the right places.

Apps are scattered all around your hard drive. Binaries are typically in /usr/bin, configuration files go in /etc/, documentation goes in /usr/share/doc, personal configuration files in /home/<user>, and some other files in different places depending on the program. There is sometimes just a single directory for the application, it depends on who wrote and packaged it. 

You can open Synaptic and find the app you are going to install, then click the more information (something similar) in the right-click menu and it will give a new window. Click the "installed files" tab and you will see a listing of any files from that package and where they are on your system.

---

### Post by bodhi.zazen on 2007-12-01
You will need to do some reading as it varies by paclkage and it depends on how the developers went about it :

Look first on the website where you got the package.

Then look for a README within the package.

You can also look at this :

[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by lightstream on 2007-12-01
> **mysticrider92 said:**
> You can open Synaptic and find the app you are going to install, then click the more information (something similar) in the right-click menu and it will give a new window. Click the "installed files" tab and you will see a listing of any files from that package and where they are on your system.
Ahh, v useful, that will save me a lot of trouble! You're right about being scattered all over though - eclipse has loads of files listed in all different places, mostly under 'usr' but a couple in 'etc'. I can see no installation file in the tar either, and the file structure doesn't really correspond with the current one.

I think the best way is definitely to uninstall the existing one first, and then I suspect I will just need to extract the tar to where I want it, and run it from there. I will have a good check for more specific eclipse info on the web first though. Strangely the supplied readme makes no mention of installation, apart from a little mention that I missed initially that eclipse must be installed into a new, fresh directory.

Drat, a bit more involved than I'd been expecting! Thanks so much for your help though, it could've gone messy if I'd gone ahead with my initial assumptions.

---

### Post by lightstream on 2007-12-01
> **bodhi.zazen said:**
> You will need to do some reading as it varies by paclkage and it depends on how the developers went about it :

Look first on the website where you got the package.

Then look for a README within the package.

You can also look at this :

[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

Thanks for the link, I'm going to have a good read through that as I have a few grey areas in this subject!

Strangely the readme is clearly focused on Windows users, with only a few mentions of Linux, which I find odd for a Sun product. I will start by checking out the eclipse web site, more info must be found there.

---

