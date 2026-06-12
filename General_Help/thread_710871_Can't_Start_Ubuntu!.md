---
title: "Can't Start Ubuntu!"
date: 2008-02-28
forum: General Help
---

### Post by AbsentHarvest on 2008-02-28
Well, I just finished re-installing Ubuntu. All was well, untill i had to install the 191 updates. It downloaded all of them, and installed every one except the last bit at the end. The computer froze at "Configuring comsys" or something relative to that. Anyway, I start up Ubuntu, Enter the log in screen, after i log in, it doesn't go anywhere. Just a blank screen, and i still have control over my mouse, but that's it. Lmao what can i possibily do to regain control of this completely useless state.

i'm really irked about this, this is the 5th time i re-installed this operating system, each one causing different problems.  Finally i have my graphics and wireless drives working properly! and of course this happens!

What can i do? lol seriously

---

### Post by Rocket2DMn on 2008-02-28
Before you login, hit CTRL+ALT+F1 to do get to a tty and run
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```
Then do CTRL+ALT+F7 to get back to the GUI and login.  Let me know if that works.

---

### Post by pointone on 2008-02-29
Try rebooting into recovery mode and run the following commands:

```
apt-get update
apt-get -f install
apt-get upgrade
```

If all goes well, reboot and see if this fixes anything.

*EDIT: Bah, beaten to the punch!

---

### Post by AbsentHarvest on 2008-02-29
Ok pointone, i tried it your way.
However, i get the following errors.

- Cannot Fetch (then the url)
- Something about needing DPKG (something like that) configure - a ... 

what must i do?

[currently trying rocket's instruction]

---

### Post by AbsentHarvest on 2008-02-29
Ok. Rocket's method doesn't work either, just a black screen, waited for 5 min... and quit it instantly to the log in screen with the described keys.

i'm tired, and frusterated.
i'm going to bed.
i hope someone knows that answer.
thanks.

---

### Post by Rocket2DMn on 2008-02-29
Why don't you try reconfiguring the X server, if you fiddled with your video card, you probably know what this is, but here's a guide - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
If you installed proprietary drivers, you may need to redo those.  Awhile back some updates broke X for some people, so choose the open source drivers then enable the restricted ones once you have a GUI.

---

### Post by kesman on 2008-02-29
what's the exact url that cannot be fetched within apt? Maybe there's a typo in your source.list that makes it try to connect to an url that doesn't exist.

> - Something about needing DPKG (something like that) configure - a ... 

Maybe it tells you to run a "dpkg-reconfigure" command to manually configure some package?

Read trough the output carefully and also check out these commands:
```

cat /var/log/Xorg.0.log | grep EE
cat /var/log/Xorg.0.log | grep WW

```

They give you every error and warning that xorg(the graphical interface) gives when it's started.

Good luck!

---

### Post by zvacet on 2008-02-29
> Cannot Fetch (then the url)

Which url?

```
cat /etc/apt/sources.list
```

Post it here.

---

### Post by AbsentHarvest on 2008-02-29
(on a another computer at the moment)
Well, i know the graphics driver didn't cause any problems. It worked fine after I restarted, this problem only occured after freezing at the very end of installing the 191 updates.

Rocket,
[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
1A) do you mean go into Options at the log in screen and log in through the GNOME?
1B) requires you to do CTRL+ALT+F1 to get to a tty. which i cannot access. (just an idle blank screen)
Also, i'd like to add the people with that problem describe freezing while booting the OS. However, in my case, it makes it to the log in screen, after which, i'm stuck at that peach/brown background screen. i can move my mouse around but the desktop is not loading.

kesman, zvacet
after typing in the following code.
"apt-get update" in recovery mode.
I got a list of "Cannot Fetch" links. (Guessing these are the source locations for the updates.) I will take a picture when I return home.

After that I get the list of source locations that cannot be fetched, at the very end it states.
needing to dpkg --configure -a

I will take a picture of the problem when I get home. However, I'm thinking I should attempt to try Rocket's command, but in Recovery Mode.
> sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

---

### Post by Rocket2DMn on 2008-02-29
Can't get to a tty eh?  Reboot into the recovery kernel instead (the option at the GRUB screen just below your normal boot kernel).  This will bring up a root terminal.  From there run the reconfiguration.  What is your video card and which driver did you select?  Did you setup proprietary drivers before?
The reason you got "Cannot Fetch" link is because the internet is disabled in recovery mode, so it can't look for the URLs in your sources.list file.
If you can't get your normal video drivers to work, see what happens when you use "vesa".  We can troubleshoot from inside the GUI from there.

---

### Post by pointone on 2008-02-29
My network works fine in recovery mode... 0_o

---

