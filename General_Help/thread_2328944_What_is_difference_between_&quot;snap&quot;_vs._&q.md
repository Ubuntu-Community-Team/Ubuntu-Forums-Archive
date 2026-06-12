---
title: "What is difference between &quot;snap&quot; vs. &quot;snappy&quot;?"
date: 2016-06-26
forum: General Help
---

### Post by abcuser on 2016-06-26
Hi,
I am little bit confuse. I am looking into official Ubuntu help:
[https://developer.ubuntu.com/en/snappy/start/using-snappy/](https://developer.ubuntu.com/en/snappy/start/using-snappy/)

and another help about snap:
[https://itsfoss.com/use-snap-packages-ubuntu-16-04/](https://itsfoss.com/use-snap-packages-ubuntu-16-04/)
[http://www.howtogeek.com/252047/how-to-install-and-manage-snap-packages-on-ubuntu-16.04-lts/](http://www.howtogeek.com/252047/how-to-install-and-manage-snap-packages-on-ubuntu-16.04-lts/)

Are "snap" and "snappy" the same thing or what is difference between them?
Regards

---

### Post by banceu_sergiu_ione on 2016-06-26
As I get it is that Snappy is the system and snaps are the apps. You have to install snappy in order to use it, and i mean for a new device like phone/notebook/table/pc. You can [lunch snappy on a VM if you want to see how it is]("https://developer.ubuntu.com/en/snappy/start/").
Meanwhile snap are the aps. Ubuntu 16.04 came with snap package management already installed, which mean that let you install any apps is on snappy platform.
Lets say you call snappy, windows phone, meanwhile you have all apps in your phone. But you want to have that app on your computer too,  here is where snap come for us.
Correct me if I am wrong.

---

### Post by abcuser on 2016-06-26
> You have to install snappy in order to use it, and i mean for a new device like phone/notebook
No Ubuntu Touch does not use snappy it uses Click. Click packages where specially developed for phone. Then development started to think how to install on IoT devices and server and they thought they will have similar (the same) mechanism, but Clicks have evolved into Snappy. It looks to me that Snappy is actually Click version 2, but they decided to change a name, probably some marketing think to do. It is planned to have the same system of snappy on all of the platforms: phone/tabled/IoT/server/cloud/desktop some day, like convergence. We don't know when this will happen, we are waiting for convergence to get into the light for years now. Like it looks now, we will need to wait some years. Some debate about this: [https://askubuntu.com/questions/583076/difference-between-snappy-and-click](https://askubuntu.com/questions/583076/difference-between-snappy-and-click)

But according to what I have read it looks like "Ubuntu Core" = snappy. What confuses me is this:
sudo snappy install docker
and
sudo snap install <some package>

---

### Post by banceu_sergiu_ione on 2016-06-26
It look like snappy is intended to replace not only Click but deb packages too. Will need to pass time for that but this is the intention.

The fact of snappy install or snap install. At the moment i can use the snap command in terminal, invoke help and what ever option I chose. But i can not invoke snappy, which say its not installed. 
So, it may be that snap command is just a package made to interact with snappy platform without snappy been installed. And the use of snappy commands only on snappy platform? What I am curious now, is that if it can be run snap commands inside snappy platform or will ask only for snappy.

---

### Post by mc4man on 2016-06-26
snap's are the new packaging installed from the command of snap via snapd
snappy is  " a media player that gathers the power and flexibility of GStreamer inside the ease of a minimalistic Clutter interface"  & runs from the command of "snappy".
No relationship between the two.

---

### Post by grahammechanical on 2016-06-26
Apart from other uses of the words "snap" and "snappy," we have Click packaging which is a development of Debian packaging (debs) and is used at present on Ubuntu phones & tablets. These applications are called click apps. Then, click packaging evolves into snap packaging and the applications that are snap packaged are called snap apps.

Snappy Ubuntu Core is Ubuntu core where the kernel is a snap and Ubuntu core is a snap and any applications would also need to be snaps. In fact everything is or will be snap packaged and tightly confined and restricted.

[https://developer.ubuntu.com/en/snappy/](https://developer.ubuntu.com/en/snappy/)

Snappy Ubuntu core is built on Ubuntu 15.04 code. It does not have a desktop environment and the user interface is the command line. For a few months there existed an installable image called personal_x86.img. It was Snappy Ubunty Desktop Next. It was build on Ubuntu 15.10 code and had Mir and Unity 8. And transactional updates worked as did the roll back feature if an upgrade to the OS failed in some way. The personal_x86 images are no longer being built. So, it did not transition on to Ubuntu 16.04 code. But it did show one possible future for Ubuntu desktop as well as server editions.

Snap packaged application will run on Ubuntu 16.04 and the flavours if a package called snapd is installed. In a terminal run snap find to see a list of installable snaps or snap apps. At the moment there are not many snap apps that are useful on desktop Ubuntu. But there is a snapped version of Libreoffice 5.2 beta that works very well.

[https://skyfromme.wordpress.com/2016/06/16/a-third-of-a-libreoffice-snap/](https://skyfromme.wordpress.com/2016/06/16/a-third-of-a-libreoffice-snap/)

Regards

---

### Post by banceu_sergiu_ione on 2016-06-26
> **mc4man said:**
> No relationship between the two.

snap help output

The snap tool interacts with the snapd daemon to control the snappy software platform.

---

### Post by mc4man on 2016-06-26
> **banceu_sergiu_ione said:**
> snap help output

The snap tool interacts with the snapd daemon to control the snappy software platform.
Again - there is no relationship between snap (the command) & snappy (the command
One manages snap packages, the other plays media

(- you're the one that tried to run a snappy command...

---

### Post by mikodo on 2016-06-26
I am glad you asked abcuser. 

Every once in a while, I come in from being out in left-field picking daisies and have trouble with the present flow of conversation. I remain perpetually confused.

Thanks, to the responders.

---

### Post by pota on 2016-08-25
> **mc4man said:**
> Again - there is no relationship between snap (the command) & snappy (the command
One manages snap packages, the other plays media

(- you're the one that tried to run a snappy command...

mc4man I think we are talking about this [snappy]("https://en.wikipedia.org/wiki/Snappy_(package_manager)") and not this [snappy]("https://wiki.gnome.org/Apps/Snappy")!

---

### Post by nu2one on 2016-10-30
The question seems to relay to one ambiguity for "snappy" in ubuntu 16.04 packages.
See the result of the try to aditional install the mediaplayer snappy.

# apt install snappy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  snapd
The following NEW packages will be installed:
  snappy
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 59,2 kB of archives.
After this operation, 26,1 MB disk space will be freed.
Do you want to continue? [Y/n] 

Here you must decide to use the snap platform or the snappy mediaplayer.
The resulting question - who will fixes this?

---

