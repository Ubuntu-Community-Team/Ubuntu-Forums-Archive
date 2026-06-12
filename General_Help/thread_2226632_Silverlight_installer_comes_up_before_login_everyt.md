---
title: "Silverlight installer comes up before login everytime"
date: 2014-05-28
forum: General Help
---

### Post by qaissi on 2014-05-28
Installed Netflix Desktop on 14.04 and it works fine.

```
sudo apt-add-repository ppa:ehoover/compholio

sudo apt-get update

sudo apt-get install netflix-desktop

```
However every time I turn on the computer the process goes like this.

Reaches Grub Boot Menu fine

Pick the Ubuntu OS and before it get to the log in screen i get a small white window in the middle of a black screen with a message that says "Downlaoding Wine-Silverlight5.1-Installer (6M).

It eventually goes away but is annoying and slows down the boot process of course.

As a side not I have noticed that randomly starting the Software Centre will start the Message Box "Creating Wine Profile" though none of the wine programs installed seem to be having issues.

Any thoughts?

---

### Post by majk2 on 2014-08-21
[COLOR=#333333][FONT=UbuntuRegular]I had a problem with the netflix browser asking me to install Silverlight all the time I checked the Netflix browser "Firefox" for plugin errors and found one with Pipelight[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]when I tried to apply your fix I got an error ....gnupg/pubring.gpg~: Permission denied[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]which I fixed with[/FONT][/COLOR]
sudo chown -R {your-user-name}.{your-user-name} ~/.gnupg
[COLOR=#333333][FONT=UbuntuRegular]and then I ran[/FONT][/COLOR]
sudo pipelight-plugin --update
pipelight-plugin --update
[COLOR=#333333][FONT=UbuntuRegular]For some reason the first command was not enough, I have started wine-browser before ran it, and I had to remove the .wine-browser folder with:[/FONT][/COLOR]
rm -rf .wine-browser
[COLOR=#333333][FONT=UbuntuRegular]and then[/FONT][/COLOR]
sudo apt-add-repository ppa:ehoover/compholio
sudo apt-get update
sudo apt-get install netflix-desktop
[COLOR=#333333][FONT=UbuntuRegular]and that sorted my problem out[/FONT][/COLOR]

---

