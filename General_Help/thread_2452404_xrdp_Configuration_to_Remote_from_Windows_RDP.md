---
title: "xrdp Configuration to Remote from Windows RDP"
date: 2020-10-21
forum: General Help
---

### Post by giobaxx on 2020-10-21
Hello Guys

I'm trying to configure *xrdp* to use Windows RDP to Remote connect to an Ubuntu Workstation using the Gnome-Session. More or less it is working but i would like to ask some clarification


[LIST]
[*]I have installed ** xrdp** and ***xorgxrdp-hwe-18.04*** because with the only xrdp it didn't worked. which is the difference abiout the two packages i really need to install oth?
[*]to get a gnome session open i have added the two line:
[/LIST]


[LIST=1|INDENT=3]
[*]***echo 'gnome-session' > ~/.xsession***
[*]***chmod +x ~/.xsession***
[/LIST]

        to the file ***etc/xrdp/startwm.sh   ***Franklyi found this trick in an Centos Guide but until i put these two lines i couldn't connect to my session. There is an alternative way to do it?


[LIST]
[*]to remove the annoyng pop up with xrdp i have added the following lines
[/LIST]
> [INDENT=3]
***polkit.addRule(function(action, subject) {***[/INDENT]
[INDENT=3]***if ((action.id == "org.freedesktop.color-manager.create-device" ||***[/INDENT]
[INDENT=3]***action.id == "org.freedesktop.color-manager.create-profile" ||***[/INDENT]
[INDENT=3]***action.id == "org.freedesktop.color-manager.delete-device" ||***[/INDENT]
[INDENT=3]***action.id == "org.freedesktop.color-manager.delete-profile" ||***[/INDENT]
[INDENT=3]***action.id == "org.freedesktop.color-manager.modify-device" ||***[/INDENT]
[INDENT=3]***action.id == "org.freedesktop.color-manager.modify-profile") &&***[/INDENT]
[INDENT=3]***subject.isInGroup("{group}")) {***[/INDENT]
[INDENT=3]***return polkit.Result.YES;***[/INDENT]
[INDENT=3]***}***[/INDENT]
[INDENT=3]***});***[/INDENT]

to the following file [I][B]/etc/polkit-1/localauthority.conf.d/02-allow-colord-conf

[/B][/I]
[LIST]
[*]to have the remote session similar to the local session, basically adding the Bar on the left and  fixing the look and feel issue for all the users i have added
[/LIST]
> [B][INDENT=3]*[SIZE=2]gnome-shell-extension-tool -e [EMAIL="ubuntu-dock@ubuntu.com"]ubuntu-dock@ubuntu.com[/EMAIL][/SIZE]*[/INDENT]
[INDENT=3]*[SIZE=2]gnome-shell-extension-tool -e [EMAIL="ubuntu-appindicators@ubuntu.com"]ubuntu-appindicators@ubuntu.com[/EMAIL][/SIZE]*[/INDENT]
[INDENT=3]*[SIZE=2]gsettings set org.gnome.desktop.interface gtk-theme 'Ambiance'[/SIZE]*[/INDENT]
[INDENT=3]*[SIZE=2]gsettings set org.gnome.desktop.interface icon-theme 'Humanity'[/SIZE]*[/INDENT]
[/B]
 at the beginning of the /[I][B]etc/xrdp/startwm.sh

[/B][/I]There is something different that i have to do ?

i'm just only testing and for the moment the major issue is that if i'm connected via RDP i cannot login locally, there is a way to disconnect the session if i try to login locally?

Thanks A.

---

### Post by HermanAB on 2020-10-22
Linux is a multi-user system, so add another user account to the Linux machine.

---

### Post by giobaxx on 2020-10-27
With xrdp the problems is that if you are logged locally you have no access remotely and vice versa. and it is impossible remotely to have access to your  Local Session like happend using RDP in Windows.

So the question is, there is a way to do it?

---

### Post by TheFu on 2020-11-02
Maybe not using RDP would be smart? 
[https://arstechnica.com/features/2020/11/future-of-collaboration-03/](https://arstechnica.com/features/2020/11/future-of-collaboration-03/)

x2go works using ssh authentication over an ssh-tunnel. Usually considered secure enough to use over the internet, from anywhere, assuming ssh-keys are used, never passwords.

---

