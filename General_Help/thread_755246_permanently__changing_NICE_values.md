---
title: "permanently  changing NICE values"
date: 2008-04-14
forum: General Help
---

### Post by FAJALOU on 2008-04-14
Is there a way to permanently change the nice values for a program.  I know about 'renice' and 'nice' in terminal, but those only work for one session.  Is there a way to permanently change the values so, say firefox, starts at -4 instead of 0?  Thanks.

---

### Post by bodhi.zazen on 2008-04-14
Add a function in .bashrc or write a short script. Run nice as root for values of <0

```
sudo nice -n -4 sudo -u user "/usr/bin/firefox"
```

where user = your log in name

---

### Post by FAJALOU on 2008-04-19
Ok... but will this make firefox run at a nice value of -4 every time I start up?  I just plugged that in and it started a new ff window...

---

### Post by bodhi.zazen on 2008-04-19
As long as you start firefox with that command. You can edit your menu or make a new launcher.

If you start firefox with just "firefox" it will not start with a nice value of -4.

You can check this with 

ps aux | grep firefox

That command will show your the nice value of firefox.

---

### Post by FAJALOU on 2008-04-20
Ok, that works, but what about compiz?  I want it to start at -5, but it automatically starts on startup.  I'm kind of confused as to how to edit the bashrc and I would love to be able just to make the system defaults for different programs -4, -5 and so on.  Is there a file that can be created or edited to have the programs default to a certain nice value?

---

### Post by kerry_s on 2008-04-20
i was just looking at a similar thing, i been trying to find info on a program called " reniced " ( [http://www.digipedia.pl/man/reniced.1.html](http://www.digipedia.pl/man/reniced.1.html) ), it's in the repo's. the man page tells jack about exactly how to use it or i just don't understand. :(

---

### Post by kerry_s on 2008-04-20
yeap, try reniced, it's actually very simple. you just set your value and when that process is found running it's reniced to the new value.
example:
-10 ^Xorg
15 ^conky
etc...

very simple. after you make your first changes to /etc/reniced.conf, run->
sudo reniced

to have it scan the config file.

my bag " sudo reniced " has to be run manually, that sucks, the search go's on. :)

---

### Post by gnivler on 2008-05-24
> **bodhi.zazen said:**
> Add a function in .bashrc or write a short script. Run nice as root for values of <0

```
sudo nice -n -4 sudo -u user "/usr/bin/firefox"
```

where user = your log in name


I'd like to try and get this working with nautilus, but my experimentation is failing.  I'd like to be able to double click on a file type which normally launches mplayer or VLC, but have that instance of the player started at a negative nice level.  Running it from the command line isn't really an attractive option, but it does work when done manually.  Anyone know how/if it can be done?  Thanks.

---

### Post by FAJALOU on 2008-05-31
> **kerry_s said:**
> 

my bag " sudo reniced " has to be run manually, that sucks, the search go's on. :)

Sorry for not responding forever, I determined that reniced is automatically added int /etc/init.d/ so it should, in theory run at startup.

---

