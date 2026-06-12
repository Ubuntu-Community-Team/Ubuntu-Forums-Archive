---
title: "Need help getting windows share working in 20.04.1 LTS"
date: 2020-12-02
forum: General Help
---

### Post by watson5242 on 2020-12-02
Hi all,

I brought my old linux box back online and given I was on 14.whatever, I decided on a totally clean install to get me to 20.04.1 LTS vs going through all the iterations one by one. 

Install went fine but I'm having an issue being able to allow sharing a /media drive to windows. Go to the drive, right click, go to properties, local network share, click off "share this folder", give it the name I want. click on "share this folder" and it pops up and says sharing service is not installed, you need to install the windows networks sharing service in order to share your folders. So I hit "install service". Immediately pops up and says "install additional software? do you want to install package 'samba'?". So then I click on install for that.

Fails out and says package dependencies cannot be resolved and then gives this in the details

The following packages have unmet dependencies:

samba: Depends: python3 (< 3.9) but 3.8.2-0ubuntu2 is to be installed
       Depends: samba-common (= 2:4.11.6+dfsg-0ubuntu1.6) but 2:4.11.6+dfsg-0ubuntu1.6 is to be installed
       Depends: samba-common-bin (= 2:4.11.6+dfsg-0ubuntu1.6) but 2:4.11.6+dfsg-0ubuntu1.6 is to be installed
       Depends: python3:any but it is a virtual package
       Depends: libwbclient0 (= 2:4.11.6+dfsg-0ubuntu1.6) but 2:4.11.6+dfsg-0ubuntu1.6 is to be installed
       Depends: samba-libs (= 2:4.11.6+dfsg-0ubuntu1.6) but 2:4.11.6+dfsg-0ubuntu1.6 is to be installed

so....... how does one go about resolving this? I'm not new to ubuntu but it's been a LONG time and I used it more as just that, a user, so if things don't just work, I get stuck.

thanks in advance!

---

### Post by watson5242 on 2020-12-02
Installed samba through the terminal (sudo apt install samba) and I seem to be making progress because now when I click on "share this folder", I don't get a popup, just this:

'net usershare' returned error 255: net usershare add: cannot share path /media/michele/2tbext as we are restricted to only sharing directories we own.
    Ask the administrator to add the line "usershare owner only = false" 
    to the [global] section of the smb.conf to allow this.

Why it doesn't know I'm the administrator is being me (or why it had dependencies it couldn't overcome the first time around) but I guess I'll edit the smb.conf file if I can track it down.

---

### Post by rsteinmetz70112 on 2020-12-03
The file you need to edit is /etc/smb.conf

---

### Post by SeijiSensei on 2020-12-04
Or you could fix the permissions on that directory so that you own it.

---

