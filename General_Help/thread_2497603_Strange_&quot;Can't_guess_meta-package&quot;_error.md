---
title: "Strange &quot;Can't guess meta-package&quot; error message when run Software Updater"
date: 2024-05-12
forum: General Help
---

### Post by goodstuff9 on 2024-05-12
Ubuntu 22.04.4, GNOME 42.9, Wayland.  

When I run the Software Updater, I started getting the series of three error messages as shown in the three attached screenshots:  

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293755&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293756&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293757&stc=1[/IMG]

When I run sudo apt update, it reports no errors, but does end by saying this:  "4 packages can be upgraded. Run 'apt list --upgradable' to see them."

When I run sudo apt upgrade, it reports no errors, but does end by saying this:  "The following packages have been kept back:  libglib2.0-0 libglib2.0-bin libglib2.0-dev libglib2.0-dev-bin"

When I run sudo apt-get upgrade --with-new-pkgs for those four packages, here is the result:  

```
main1@system1:~$ sudo apt-get upgrade --with-new-pkgs libglib2.0-0 libglib2.0-bin libglib2.0-dev libglib2.0-dev-bin
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 chrome-gnome-shell : Depends: gnome-shell but it is not installable
 gdm3 : Depends: gnome-shell (>= 3.37.90) but it is not installable
 gnome-shell-extension-appindicator : Depends: gnome-shell (>= 3.33) but it is not installable
                                      Depends: gnome-shell (< 43~) but it is not installable
 gnome-shell-extension-desktop-icons-ng : Depends: gnome-shell (>= 3.38) but it is not installable
 gnome-shell-extension-prefs : Depends: gnome-shell (= 42.5-0ubuntu1pop1~1675984688~22.04~f574f54~dev) but it is not installable
 gnome-shell-extension-ubuntu-dock : Depends: gnome-shell (< 43) but it is not installable
                                     Depends: gnome-shell (>= 40) but it is not installable
 ubuntu-desktop : Depends: gnome-shell but it is not installable
 ubuntu-desktop-minimal : Depends: gnome-shell but it is not installable
 ubuntu-session : Depends: gnome-shell (>= 3.37.91) but it is not installable
E: Broken packages
```

But, chrome-gnome-shell, gnome-shell, ubuntu-desktop, etc., are all already installed and running just fine.  

When I run Synaptic, it reports no broken packages.  

Questions:  

1)  What are these Software Updater error messages shown in the screenshots above trying to tell me?  
2)  Are those Software Updater error messages related to the four libglib packages that are being held back?  
3)  Why does tyring to install those four libglib packages report that I have broken packages?  
4)  What should I be doing to fix whatever is wrong?  (And, I do realize that one of the error messages above suggested using ppa-purge on some offending application, but I have no idea which application it is referring to.)  

Thanks in advance for any help.

---

### Post by gezzer2 on 2024-05-12
you can check via synaptic and see if you have any broken packages.
fix broken packages is in the edit menu.

or in a terminal try ..

sudo dpkg --configure -a

sudo apt-get install -f

then try the updates and see if that corrects the problem ..

---

### Post by goodstuff9 on 2024-05-12
Thanks gezzer2 for the help.  

I'm not following your logic.  In my original post I pointed out that I had already checked via Synaptic and saw that it reported that there are no broken packages.  Is there something else in Synaptic you're suggesting that I check?  

I did try your two terminal commands, they didn't produce any output in the terminal.  The same problems remain.

---

### Post by gezzer2 on 2024-05-13
it maybe worth while posting your software PPA lists
you can check in software and updates just to see what you have in them ..

note. in synaptic menu/edit there is 'fix broken packages' i was just checking that you had used it ..

---

