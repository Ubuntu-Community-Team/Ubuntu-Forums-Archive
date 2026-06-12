---
title: "Lubuntu 17.10 fresh install no sudo functionality"
date: 2017-10-27
forum: General Help
---

### Post by cdoublejj on 2017-10-27
"xhost +si:localuser:root" isn't working. is there by chance a work around for lubuntu?

---

### Post by monkeybrain20122 on 2017-10-27
Log into xorg instead of using wayland.

---

### Post by cdoublejj on 2017-10-27
> **monkeybrain20122 said:**
> Log into xorg instead of using wayland. is lubuntu using wayland? if i may ask, like whats the deal how'd this get looked over? wouldn't using x cause issues if i switch back over to wayland once it's fixed?

---

### Post by monkeybrain20122 on 2017-10-27
> **cdoublejj said:**
> is lubuntu using wayland? if i may ask, like whats the deal how'd this get looked over? wouldn't using x cause issues if i switch back over to wayland once it's fixed?

I don't know about lubuntu, but the work around you posted is for Wayland. If you can log into xorg why do you want wayland except for testing and bug hunting? It is beta and missing in functionalities (for Ubuntu you can choose to login to wayland or xorg)

---

### Post by cdoublejj on 2017-10-27
> **monkeybrain20122 said:**
> I don't know about lubuntu, but the work around you posted is for Wayland. If you can log into xorg why do you want wayland? It is beta and missing in functionalities (for Ubuntu you can choose to login to wayland or xorg)

I just want the default stable setup and for it to work like it i would generally speaking expect it to. is there a command ot check if i'm logged in via "x"?

---

### Post by monkeybrain20122 on 2017-10-27
> **cdoublejj said:**
> I just want the default stable setup and for it to work like it i would generally speaking expect it to. is there a command ot check if i'm logged in via "x"?

The default setup is not stable if it is wayland and 17.10 is not a stable release. If you want something that works reliably you should use 16.04.

To check if you are using X, in the terminal
```
echo $XDG_SESSION_TYPE
```

It should say X11 if you are in X

---

### Post by cdoublejj on 2017-10-27
> **monkeybrain20122 said:**
> The default setup is not stable if it is wayland and 17.10 is not a stable release. If you want something that works reliably you should use 16.04.

To check if you are using X, in the terminal
```
echo $XDG_SESSION_TYPE
```

It should say X11 if you are in X

It indeed outputs; "X11"

so i wonder what that cause is then.

---

### Post by sudodus on 2017-10-27
@cdoublejj,

Please tell us what you want to do! And tell us exactly what is happening instead of what you want to do. Tell us as many details as possible. Then it will be easier to help.

---

### Post by vasa1 on 2017-10-27
Lubuntu 17.10 doesn't have Wayland, AFAIK.

In what way is there no sudo functionality?

---

### Post by cdoublejj on 2017-10-27
it would appears few things are going on. i tried running some sudo commands and was getting no output when running them. HOWEVER one of which was "sudo dpkg --add-architecture i386" my emulator doens't run without out it as of the past several LTS version of Lubuntu. well funnily enough i formatted and installed the emulator figuring i'd find a fix eventually, for giggle i tried to to run said emulator and funnily enough, it runs without me having to enter "sudo dpkg --add-architecture i386" so maybe that never output anything cause it already has that package?

i'm also having problems installing a VPN client. the first time yielded no icons, i should not have closed it out without reading the output, usually it works however after closing i found no icons! i tried running the commands from the clients installation instructions again and the output was spewing lines of "permissions denied"

if i try to "su" it rejects my password. i also noticed other sudo commands prompted no output other than the default idle user@hostname:$

EDIT: i'm hesitant to try again. i'm on a fresh install (again) so no chance of it trying to overwrite it's own stuff
[https://www.privateinternetaccess.com/installer/download_installer_linux](https://www.privateinternetaccess.com/installer/download_installer_linux)

EDIT: tried installing wine, seems to be working with the sudo commands but, it ultimately failed with...

Unpacking libosmesa6:amd64 (17.2.2-0ubuntu1) ...
Errors were encountered while processing:
 /tmp/apt-dpkg-install-P0BNVh/80-libsane1_1.0.27-1~experimental2ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


EDIT: it tried to report a bug and redirected to this when trying to submit: [URL="https://bugs.launchpad.net/ubuntu/+source/sane-backends/+filebug/40f245f2-bb0e-11e7-b34a-002481e7f48a?field.title=package+libsane1+1.0.27-1~experimental2ubuntu1+failed+to+install%2Fupgrade%3A+trying+to+overwrite+shared+%27%2Flib%2Fudev%2Fhwdb.d%2F20-sane.hwdb%27%2C+which+is+different+from+other+instances+of+package+libsane1%3Ai386"]https://bugs.launchpad.net/ubuntu/+source/sane-backends/+filebug/40f245f2-bb0e-11e7-b34a-002481e7f48a?field.title=package+libsane1+1.0.27-1~experimental2ubuntu1+failed+to+install%2Fupgrade%3A+trying+to+overwrite+shared+%27%2Flib%2Fudev%2Fhwdb.d%2F20-sane.hwdb%27%2C+which+is+different+from+other+instances+of+package+libsane1%3Ai386

this one is ls listed as happening during wine install,  [/URL][https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1727108](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1727108)

not sure if it's python versions mismatching or if it's something to do with i386 package, which is odd as prior versions required manual installation of said package, it's welcome change for sure to have 32 bit app support again!

EDIT: re ran "sudo apt-get install --install-recommends winehq-staging" it installed some more packages, and then went back to the user prompt $, no icons, rebooted, no icons, can't tell if it's installed or not.

EDIT: wine --version outputs 2.19 staging and 'wine launch" seems to have started it up but, i still have no icons, what gives? why are my apps half way installing with no icons?

---

### Post by sudodus on 2017-10-27
> **cdoublejj said:**
> it would appears few things are going on. i tried running some sudo commands and was getting no output when running them. HOWEVER one of which was "sudo dpkg --add-architecture i386" my emulator doens't run without out it as of the past several LTS version of Lubuntu. well funnily enough i formatted and installed the emulator figuring i'd find a fix eventually, for giggle i tried to to run said emulator and funnily enough, it runs without me having to enter "sudo dpkg --add-architecture i386" so maybe that never output anything cause it already has that package?

What emulator is this?
> 
i'm also having problems installing a VPN client. the first time yielded no icons, i should not have closed it out without reading the output, usually it works however after closing i found no icons! i tried running the commands from the clients installation instructions again and the output was spewing lines of "permissions denied"

Is this the VPN client in the link of your edit?
> 
if i try to "su" it rejects my password. i also noticed other sudo commands prompted no output other than the default idle user@hostname:$

How do you try to "su"? Please give us the exact command line and what happens.
> 
EDIT: i'm hesitant to try again. i'm on a fresh install (again) so no chance of it trying to overwrite it's own stuff
[https://www.privateinternetaccess.com/installer/download_installer_linux](https://www.privateinternetaccess.com/installer/download_installer_linux)

What happens when you run the following command lines?

```
sudo apt update
sudo apt full-upgrade
```

Is there some other particular program package, that you want to install? In that case, try to install it with

```
sudo apt install program-package-name
```

for example htop which is a small program (similar to top, and I think better).

```
sudo apt install htop
```

---

### Post by cdoublejj on 2017-10-27
> **sudodus said:**
> What emulator is this?

Is this the VPN client in the link of your edit?

How do you try to "su"? Please give us the exact command line and what happens.


What happens when you run the following command lines?

```
sudo apt update
sudo apt full-upgrade
```

Is there some other particular program package, that you want to install? In that case, try to install it with

```
sudo apt install program-package-name
```

for example htop which is a small program (similar to top, and I think better).

```
sudo apt install htop
```

oh snap i dind't see the second page, ive been playing around some more.

EDIT: tried installing wine, seems to be working with the sudo commands but, it ultimately failed with...

Unpacking libosmesa6:amd64 (17.2.2-0ubuntu1) ...
Errors were encountered while processing:
 /tmp/apt-dpkg-install-P0BNVh/80-libsane1_1.0.27-1~experimental2ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


EDIT: it tried to report a bug and redirected to this when trying to submit: [URL="https://bugs.launchpad.net/ubuntu/+source/sane-backends/+filebug/40f245f2-bb0e-11e7-b34a-002481e7f48a?field.title=package+libsane1+1.0.27-1~experimental2ubuntu1+failed+to+install%2Fupgrade%3A+trying+to+overwrite+shared+%27%2Flib%2Fudev%2Fhwdb.d%2F20-sane.hwdb%27%2C+which+is+different+from+other+instances+of+package+libsane1%3Ai386"]https://bugs.launchpad.net/ubuntu/+source/sane-backends/+filebug/40f245f2-bb0e-11e7-b34a-002481e7f48a?field.title=package+libsane1+1.0.27-1~experimental2ubuntu1+failed+to+install%2Fupgrade   %3A+trying+to+overwrite+shared+%27%2Flib%2Fudev%2F   hwdb.d%2F20-sane.hwdb%27%2C+which+is+different+from+other+inst   ances+of+package+libsane1%3Ai386

this one is ls listed as happening during wine install,  [/URL][https://bugs.launchpad.net/ubuntu/+s...s/+bug/1727108]("https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1727108")

not sure if it's python versions mismatching or if it's something to do  with i386 package, which is odd as prior versions required manual  installation of said package, it's welcome change for sure to have 32  bit app support again!

EDIT: re ran "sudo apt-get install --install-recommends winehq-staging"  it installed some more packages, and then went back to the user prompt  $, no icons, rebooted, no icons, can't tell if it's installed or not.

EDIT: wine --version outputs 2.19 staging and 'wine launch" seems to  have started it up but, i still have no icons, what gives? why are my  apps half way installing with no icons?[INDENT]                                      [Last edited by cdoublejj]("https://ubuntuforums.org/posthistory.php?p=13703779"); 19 Minutes Ago at 07:14 AM.                                               


---------------------------

I was just typed in "su" and it asks for a password but, rejects my password. i know for a fact i set the user name and all passwords to "user".

it's installing htop

yes i linked the client in the edit

sorry this post is all jumbled up



EDIT: i installed play on linux from the appstore and it too is missing icons form the start menu as well. i'n prior version of lubuntu I've always had icons added to the menu after install of software

EDIT: other apps from the app store like blender or wesnoth and libre office installed icons no problem

EDIT: app store = ubuntu/lubuntu software center.
[/INDENT]

---

### Post by sudodus on 2017-10-27
Well, the main answer must be that there ***is*** sudo functionality, which kind of finishes this thread.

I think it is better to **create new threads for each of the other problems** (with Wine, with VPN etc), because it will be very confusing to try to discuss and solve several problems in the same thread.

---

### Post by cdoublejj on 2017-10-27
i'm starting to think it's denying permissions for the icons in the menu, why it denying permissions if sudo is used?

EDIT: su and su root, still reject my password, is this default behavior?

---

### Post by sudodus on 2017-10-27
In Ubuntu you are not supposed to log in as the user **root**. You can use **su** to log in as another user like so (if there would be a user **sudodus** in your computer),

```
cdoublejj@yourbuntu ~ $ su - sudodus
Password:
sudodus@yourbuntu ~ $

```

You are supposed to use

```
sudo text-mode-application-program
```

or

```
gksudo graphical-mode-application-program
```

to run programs with elevated permissions. This descreases the risk, that you run with elevated permissions, when you need not do it. (It is easy to cause damage to the system, when you run with elevated permissions.)

---

### Post by cdoublejj on 2017-10-27
gksudo outputs as unrecognized, i might assume this is a change with 17.10?

---

### Post by sudodus on 2017-10-27
Install the package that contains it with the following commands

```
sudo add-apt-repository universe
sudo apt update
sudo apt install gksu
```

---

