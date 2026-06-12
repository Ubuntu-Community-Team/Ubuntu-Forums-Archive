---
title: "[SOLVED] question about beryl"
date: 2008-02-19
forum: General Help
---

### Post by psfelgate on 2008-02-19
First off, I apologize if this has been asked before.

I would like to find out if beryl has to be run on a fast machine or not. I have a IBM r50e laptop and it has a onboard intel display card. I've installed beryl using synaptics but when I try to run it, it hangs on "reloading options".

I found a few posts of people having similar problems but that had better 3d display cards, so I wonder if my issue is simply because my laptop sucks.

---

### Post by kpkeerthi on 2008-02-19
You don't need beryl if you are running gutsy. Gutsy has compiz (fusion), which has superseded beryl, installed by default. You just have to enable it from System -> Preference -> Appearance -> Visual Effects

---

### Post by psfelgate on 2008-02-19
Sorry, I guess I shoud have mentioned that I was using feisty.

Is it complicated to upgrade the laptop to gutsy? Can I just update it through the synaptics manager or is it more work than that?

---

### Post by cwgannon on 2008-02-19
> **psfelgate said:**
> Sorry, I guess I shoud have mentioned that I was using feisty.

Is it complicated to upgrade the laptop to gutsy? Can I just update it through the synaptics manager or is it more work than that?

It isn't complicated at all.

There are guides everywhere (try Google), or you can just use the following commands sequentially:

In a terminal:
```
sudo sed -e 's/\sfeisty/ gutsy/g' -i /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade
```

Make sure you have some time to spare--it can take a few hours.

---

### Post by billgoldberg on 2008-02-19
It is preffered to install from disk instead of upgrading.

In gutsy you'll still need to add "compizconfig" from synaptic to get the most out of compiz fusion.

---

### Post by psfelgate on 2008-02-19
Will my laptop be fast enough to run this compiz if I do upgrade?

---

### Post by Sukarn on 2008-02-19
> **psfelgate said:**
> Will my laptop be fast enough to run this compiz if I do upgrade?

That question cannot be answered without knowing what's inside your laptop (the hardware)

---

### Post by psfelgate on 2008-02-19
Oops, blonde moment...

Ok, I have a IBM R50e laptop and I it has a 8 or 16 mb intel card, 768 mb RAM and 1.5 ghz celeron cpu.

Will it just hang and not say that it is too slow or will it actually say it is too slow before running?

---

### Post by psfelgate on 2008-02-20
Ok, I just found a small program in one of the menus that does change the window effects etc. so I'm sorted. Thanks for the help guys.

Oh and BTW I see you can change the themes of the windows etc. and the login screens as well, but do you get themes for the screen that shows JUST after you put in your password? (the one that shows loading... nautilus etc.)

---

### Post by Sukarn on 2008-02-20
For changing the splash theme, go to *System -> Preferences -> Splash Screen*

To get new splash themes for GNOME, you can try installing [gnome-art](apt:gnome-art) from synaptic. This application gets the required theme files from art.gnome.org

Your laptop specs seem to be good enough to run Ubuntu, except for like compiz and beryl. I think the graphic card might be too weak for those.
My desktop which runs ubuntu without any problems has a 1.8 GHz processor, 512 MB ram and a 512 MB graphics card (though my graphics card only runs at 256 MB. It wants the system to have 1 GB ram before it runs at its full 512 MB.)

---

### Post by psfelgate on 2008-02-20
Oh well, I guess I will have to live without the fancy effects... sigh. Thanks for the help though!

---

