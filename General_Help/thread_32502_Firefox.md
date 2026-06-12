---
title: "Firefox"
date: 2005-05-08
forum: General Help
---

### Post by g77s80 on 2005-05-08
I'm new to linux and know very little about the os and its workings
I'm trying to install the latest version of mozilla firefox and does'nt come in an rpm package
How do I do this

---

### Post by Hokputooy on 2005-05-08
Open a terminal and type
$  tar -xzvf firefox-1.0.3.installer.tar.gz
to decompress it, then
$  cd firefox-installer
and
$  ./firefox-installer

---

### Post by clb137 on 2005-05-08
[QUOTE=g77s80]I'm new to linux and know very little about the os and its workings
I'm trying to install the latest version of mozilla firefox and does'nt come in an rpm package
How do I do this[/QUOTE]

Hi there,

From a terminal window (In Applications/system tools) type the following

sudo apt-get update  (press enter; you will be asked for your password)

then 

sudo apt-get upgrade

the other way is to run "synaptic pakage manager" this is found in 'system/administration' 

once the program is open you can search for firefox and install the latest version that is stable and tested

good luck

clinton

---

### Post by Professor X on 2005-05-08
You need to enable the backports repositories to get the latest stable version of firefox.  If your talking a about a nightly build, then you'll need to install it using another method.

---

### Post by strawberry on 2005-05-08
I installed firefox 1.0.3 from the *.installer.tar.gz file.
Now I would like to go back to the ubuntu repository and install it from deb package.
Is it possible uninstall the current version of firefox (come from *.tar.gz) simple delete firefox-installer folder?  :roll:

---

### Post by clb137 on 2005-05-08
[QUOTE=strawberry]I installed firefox 1.0.3 from the *.installer.tar.gz file.
Now I would like to go back to the ubuntu repository and install it from deb package.
Is it possible uninstall the current version of firefox (come from *.tar.gz) simple delete firefox-installer folder?  :roll:[/QUOTE]

Delete the Firefox-installer, where did you install the package?

---

### Post by edou on 2005-05-08
Hi, i am a newbie and i recently succeded in installing ubuntu on my hd. My problem is that since i did it, i am unable to have the internet what ever navigator i use. If i start my computer with the cable swicthed to the computer, the connection of the entire building fails. the verry common message 'server not found' is shown. after a whole month without internet i abandonned to try it from ubuntu. So i am obliged to use ubuntu offline.
I am under a toshiba A30p4 with 512 ram, 2.3ghza and 40 Go.
Could some body tell me what to do.
PS: i am not a champion in the commanline. ](*,)

---

### Post by Psquared on 2005-05-08
[QUOTE=edou]Hi, i am a newbie and i recently succeded in installing ubuntu on my hd. My problem is that since i did it, i am unable to have the internet what ever navigator i use. If i start my computer with the cable swicthed to the computer, the connection of the entire building fails. the verry common message 'server not found' is shown. after a whole month without internet i abandonned to try it from ubuntu. So i am obliged to use ubuntu offline.
I am under a toshiba A30p4 with 512 ram, 2.3ghza and 40 Go.
Could some body tell me what to do.
PS: i am not a champion in the commanline. ](*,)[/QUOTE]

Sounds like you are using a "wired" connection instead of wireless.

Go to network settings (I am in Xfce and you are probably using Gnome) and enable your ethernet. If you are using Hoary you just highlight it and click activate. If it is more than that you will have to write more details.

---

### Post by strawberry on 2005-05-08
[QUOTE=clb137]Delete the Firefox-installer, where did you install the package?[/QUOTE]
I installed firefox to a sub-folder in firefox-installer folder so I would delete it also when delete firefox-installer.

---

### Post by clb137 on 2005-05-08
[QUOTE=strawberry]I installed firefox to a sub-folder in firefox-installer folder so I would delete it also when delete firefox-installer.[/QUOTE]


no problem go ahead

---

### Post by strawberry on 2005-05-08
[QUOTE=clb137]no problem go ahead[/QUOTE]
Thanks, I'll do this way.  ;-)

---

### Post by edou on 2005-05-15
[QUOTE=Psquared]Sounds like you are using a "wired" connection instead of wireless.

Go to network settings (I am in Xfce and you are probably using Gnome) and enable your ethernet. If you are using Hoary you just highlight it and click activate. If it is more than that you will have to write more details.[/QUOTE]
 Thanks,
i effectively use a wired connection. I already tried what you recommended me. My connection is eth0. In addition after an Ubuntu session, when i go back to win, there is a clock problem and i have Brussels time -1. I'll still try.

---

