---
title: "Xorg Error after Updates"
date: 2006-08-22
forum: General Help
---

### Post by ahaslam on 2006-08-22
Hello,

This morning I had two Xorg updates. In their description it mentioned that it addressed certain bugs for intel chipsets. I don't have an intel chipset but thaught that it wouldn't do any harm in keeping up to date, afterall it's offering this update for a reason, right?

I installed as prompted and continued to use the machine as usual & shut down. When starting back up, I got a familiar message (setting up via unichrome on Breezy wasn't exactly breezy) "Failed to start the Xserver".

I checked my xorg.conf and it was fine, completly unchanged. I then looked at the Xorg.0.log file, at the end it shows:

[B](II) Via: Driver for Via chipsets ....*(list of chipsets)*....
(EE) No devices detected
 
Fatal server error:
No screens found[/B]

I find this a little weird, sa my xorg.conf file remained untouched. :-k 

Any help would be greatly appreciated,

Thank you,

Tony.

---

### Post by Metacarpal on 2006-08-22
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

There was a problem with the xorg update 10.3
You should be able to fix this now (update 10.4 is out) by entering in the command line:

```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by ghansel on 2006-08-22
I had the same problem, on an nVidia Geforce card. I tried 'nvidia-glx-config enable' 'dpkg-reconfigure xserver-xorg' and 'nvidia-xconfig', all to no avail. Anyone know what's going on?

EDIT: the above advice completely fixed my problem.

---

### Post by ahaslam on 2006-08-22
> **Metacarpal said:**
> [http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

There was a problem with the xorg update 10.3
You should be able to fix this now (update 10.4 is out) by entering in the command line:

```
sudo aptitude update
sudo aptitude dist-upgrade
```
Thank you, I'll try that in a minuite and report back.

It really annoys me when 'updates' break my system.  This is the third time that it's happened in as many months.

Cheers,

Tony.

---

### Post by ahaslam on 2006-08-22
> **Metacarpal said:**
> [http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

There was a problem with the xorg update 10.3
You should be able to fix this now (update 10.4 is out) by entering in the command line:

```
sudo aptitude update
sudo aptitude dist-upgrade
```
That worked perfectly ;)
Your help was greatly appreciated :)

Thank you,

Tony.

PS. The dev's really should test things a little more prior to release, updates should not create problems, they're supposed to fix them :rolleyes:

---

### Post by Zalbor on 2006-08-22
> **Metacarpal said:**
> [http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

There was a problem with the xorg update 10.3
You should be able to fix this now (update 10.4 is out) by entering in the command line:

```
sudo aptitude update
sudo aptitude dist-upgrade
```
Thanks, that worked for me too. :)

> **Anthony Haslam said:**
> PS. The dev's really should test things a little more prior to release, updates should not create problems, they're supposed to fix them :rolleyes:
I'll have to second this though...

---

### Post by Metacarpal on 2006-08-22
> **Anthony Haslam said:**
> That worked perfectly ;)
Your help was greatly appreciated :)

Glad I could help!  I'm just glad I wasn't home and online to catch the broken update, myself.

> PS. The dev's really should test things a little more prior to release, updates should not create problems, they're supposed to fix them :rolleyes:

There's been an [interesting proposal]("http://www.ubuntuforums.org/showthread.php?t=241473") put forward by another Ubuntu user that I think bears further discussion.

---

### Post by MattPalmer on 2006-08-22
> **Metacarpal said:**
> [http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

There was a problem with the xorg update 10.3
You should be able to fix this now (update 10.4 is out) by entering in the command line:

```
sudo aptitude update
sudo aptitude dist-upgrade
```

Perfect - thank you so much for posting that.  I had exactly this problem - I have to say, the first back-to-the-command-line problem I've had since I started using Ubuntu over a year ago (and linux in general a few years before that, but not as my main system).

I wasn't terribly happy about it, as I have a big meeting tomorrow, and I needed the files I'd been working on.  It got a bit hairy when I discovered the network wasn't working - as I use wireless with wpa2 encryption, and rely on the gnome nm-applet to load wpa-supplicant - so I was lost on the command line to get that going.  I got the wired interface going, and then I could upgrade and fix the problem.  Phew...

Anyway, it all seems to be back with a bit of digging and your help, but I have years of experience with computers, and I don't tend to panic.  This would be a complete show-stopper for Aunty Mabel. So there's a lesson here for us - it's reasonably OK if you muck the GUI up in such a way that it defaults to a more basic, but workable configuration - like only being able to run it at a low resolution or color depth - but it's a total no-no these days to have no graphical system at all, barring complete hardware failure.  This doesn't bother linux geeks much, but it's a show stopper for anyone else, and a pain for those of us who love linux, but want to use it to do something else.

---

### Post by VoodooChile on 2006-08-22
I typed in those commands, but now instead of getting the xserver error, and then the command prompt, I just get a blank screen, I cant do anything at that point but hit the restart button. It looks as if its going to load to the login screen but then does nothing... frustrating... I thought I had a fix... any ideas???

---

### Post by spockrock on 2006-08-22
some people have had to reinstall the driver, or reconfigure the xorg package.

---

### Post by VoodooChile on 2006-08-22
Hmm, I dont remember what I used for the ATI driver, I have a 9800 pro, what would I have to type at the command prompt for either opiton?

---

### Post by VoodooChile on 2006-08-23
Has anyone come up with a working solution to this?

---

