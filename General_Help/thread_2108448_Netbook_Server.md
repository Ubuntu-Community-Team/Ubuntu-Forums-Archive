---
title: "Netbook Server"
date: 2013-01-24
forum: General Help
---

### Post by divergex on 2013-01-24
I currently have an old tower PC that serves as a print server for my family. It is attached to a Canon MP280 via USB and allows everyone to print wirelessly (it's connected via Ethernet to our router). It runs Windows XP Home. From time to time, I use Remmina to log in and scan a document or photo.

I would like to replace this server as it is quite old and takes up too much space, and I am considering a netbook running Ubuntu (or Zentyal) to take its place.

My question is, is there a way to disable sleep when the netbook display is closed? I would only need to open it when I need to scan something or perform some other rare task. I can keep it open if needed, but would prefer to keep it closed to keep out dust and prevent accidental key presses.

---

### Post by tgalati4 on 2013-01-24
Laptops/netbooks go to sleep when the "lid" switch is activated.  So you want to search the forums for redefining the lid switch action or ignore it all together.

How this is done depends on what version of Ubuntu you are considering.  A netbook will probably need a slimmed-down version of Ubuntu or just the server/console version.

---

### Post by Double.J on 2013-01-24
Hi there!

A netbook can even run full kubuntu and a light vm... I should know! 

Just have a look see if you can set lid to do nothing in the power settings first and foremost 

Not had a chance to look properly yet, but [this]("http://http://ubuntuforums.org/showthread.php?t=1443534") thread may be of use if the option is not given by default, though it is from gnome and kernel 2.

Also remember that you'd be wanting to remove the battery and disable screen saver, lock screen... Anything scheduled to happen after a set time of inactivity.

---

### Post by matt_symes on 2013-01-24
Hi

You can create a script to disable sleeping and hibernation.

Press alt + F2 and type...

```
gksudo gedit /etc/pm/sleep.d/inhibit-pm-utils
```Copy and paste this text into it.

```
#!/bin/sh

. "$PM_FUNCTIONS"

case $1 in
  suspend|hibernate)
    inhibit
    ;;
  resume|thaw)
    ;;
esac
```Save the script.

Make the script executable. From the terminal

```
sudo chmod 755 /etc/pm/sleep.d/inhibit-pm-utils
```That should disable sleep.

Check to see if you lose network connectivity when sleep tries to be activated and post back if you do.

You can also disable it using policy kit as well.

Kind regards

---

