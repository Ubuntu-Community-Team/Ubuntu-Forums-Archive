---
title: "GNU Xnee - can't find Gnee, Cnee, etc."
date: 2008-03-31
forum: General Help
---

### Post by kristjans on 2008-03-31
> GNU Xnee is **a suite of programs** that can record, replay and distribute user actions under the X11 environment. Think of it as a robot that can imitate the job you just did.

I downloaded Xnee from Synaptic Package Manager, and since it said that it is a suite of programs, I expected all the programs to be installed: cnee, gnee (GUI!), and pnee. However, I can only use xnee and the programs aren't installed. Are they already installed under xnee, do I have to download them separately... what is going on??

---

### Post by kristjans on 2008-04-03
**B**ring **U**p **M**y **P**ost, thanks.

---

### Post by mrodent on 2008-04-12
hi,

sorry, not an answer....!  I have the same question...

want to move over to Linux but 2 or 3 apps in the Windows environment are vital... one is autohotkey... want to find whether xnee/cnee is an adequate substitute.

so I went to Synaptic, found xnee in the list... installed this package... looking at the "getting started" section in the manual found here: [http://www.sandklef.com/xnee/?q=node/13](http://www.sandklef.com/xnee/?q=node/13)

but bash tells me "cnee" is not a command
did whois cnee and locate cnee... no joy
cnee is not listed in the Synaptic package list

I'm struggling... help!  Does this mean I have to download & install a package or sthg?  

Thanks

---

### Post by kristjans on 2008-04-16
Found out that Ubuntu's version is **very** outdated. I compiled a (rather sloppy) package for **64-bit** architecture myself, if you want it, then you can find it at [http://kaurism.com/xnee_3.02-1_amd64.deb](http://kaurism.com/xnee_3.02-1_amd64.deb). I make no guarantees though. And it doesn't have any requirements set up, so make sure that you do have GTK and libxtst6 installed. Also, I suggest you make a backup copy of the package, case the server should go down. You will need it to uninstall later. ;)

---

### Post by aouie on 2008-07-23
Installing latest xnee.
Download the latest xnee from [the Xnee site http://savannah.gnu.org/projects/xnee/]("http://savannah.gnu.org/projects/xnee/").
Extract the archive to some folder.
Go over to the folder and then type:
```
./configure --enable-gnome-applet --prefix=/usr

```
Unless you had all the necessary files in place you will not succeed in the previous step.
Try installing from synaptic: libpanel-applet2-dev, build-essential, libxtst-dev, and libgtk2.0-dev (this will also install several dependencies).
Now try the configure step again and it should succeed.
Then type:
```
make
sudo make install
sudo gedit /etc/X11/xorg.conf

```
Add the following line in the module section
```
Load "record"

```
Restart X. (If you don't know how, then simply restart the computer (or logout (and just to be sure CTRL+ALT+BACKSPACE) and log back in)).
You could learn to use GNEE, but I stuck to CNEE.

I created two bash scripts (which you can put in /usr/local/bin if you don't know how else to set it up) (Make them executables. (In Nautilus file manager right click on file then set to executable on the permissions tab.)
Script 1 is MacRec
```
sleep 0.3s
cnee --record -o /tmp/cnee_$1.xns --events-to-record 10000 --keyboard  --stop-key Shift_R

```

Script 2 is MacPlay
```
sleep 0.3s
cnee --replay --keyboard --file /tmp/cnee_$1.xns --stop-key Shift_R -sp 10

```

On any terminal (command prompt) type MacRec 1 (or any other value "Val" to create a tmp macro file /tmp/cnee_Val.xns).
Hit the right shift key to stop recording the events.

MacPlay 1 (or whatever "Val" you used) should play back the file.

You should just have to add --mouse to the cnee arguments to record and play back mouse events, but I didn't test that.

Now setup your keyboard shortcuts for your desktop (On XFCE it is under Settings->Settings Manager->Keyboard, for gnome it is probably under System->Preferences->Keyboard), I setup shortcuts for the commands "MacRec 1", "MacPlay 1", "MacRec 2" and "MacPlay 2".

Either look up the documentation on the site or "man cnee" to check what other options you may find useful in cnee.

Sincerely,
Aouie

---

