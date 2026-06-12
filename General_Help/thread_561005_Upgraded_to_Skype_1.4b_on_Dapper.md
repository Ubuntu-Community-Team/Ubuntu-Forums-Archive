---
title: "Upgraded to Skype 1.4b on Dapper?"
date: 2007-09-27
forum: General Help
---

### Post by stillingen on 2007-09-27
I'm running Dapper with 2.6.15-29-686 kernel. The problem I'm having is that my Skype client (v 1.3.0.53) is causing my system to hang. This issue is described [ here ](http://forum.skype.com/lofiversion/index.php/t42232.html)

It seams like the workaround is to upgrade to Skype 1.4b, which has the following dependencies;

# Qt 4.2.1+
# D-Bus 1.0.0
# libsigc++ 2.0.2
# libasound2 1.0.12 

I'm using this [sources.list](http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories) and non of the packages above are available for Dapper from these sites. Are there other Dapper repos that these packages could be installed from? Are there limitations to installing these packages manually, and what would that be?

---

### Post by lisati on 2007-09-27
i don't know about dapper, but I haven't had any problems with skype 1.4 on Feisty using the package downloaded from [www.skype.com](www.skype.com) - the only catch was that you might have to use the "download" link in the menu and choose an appropriate package rather than the green download button.

---

### Post by mivo on 2007-09-27
They have repositories, too, so using apt-get/etc. is an option as well:

[http://skype.com/download/skype/linux/repositories.html](http://skype.com/download/skype/linux/repositories.html)

PS. The required libraries are in the Ubuntu core repositories (well, at least for Feisty). I had those already installed when I got Skype.

---

### Post by stillingen on 2007-09-27
> **mivo said:**
> They have repositories, too, so using apt-get/etc. is an option as well:

[http://skype.com/download/skype/linux/repositories.html](http://skype.com/download/skype/linux/repositories.html)

PS. The required libraries are in the Ubuntu core repositories (well, at least for Feisty). I had those already installed when I got Skype.

I aware of the application downloads and repo install, I have this in my sources.list. It's the libraries/package dependencies I can't figure out. It don't seam to be available in the Ubuntu Dapper repos
Searching [this page](http://packages.ubuntu.com/) it look like Dapper only has e.g Qt 4.2.1, wile Feisty has Qt 4.2.3 
Same for the other packages, the new onces are not supported on Dapper. Any experience one installing Feisty packages on Dapper?

---

### Post by notoriousdbp on 2007-10-05
Goes back to the difference in interpretation of "long term support".
Users interpretation "will have the most up to date packages for three years"
Developers interpretation "will have set packages and any security updates over the next three years".

I guess it's the down side of free software - you get what you're given.

---

