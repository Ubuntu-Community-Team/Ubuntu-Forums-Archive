---
title: "Installing FULL Lamp  help"
date: 2007-12-10
forum: General Help
---

### Post by pundip on 2007-12-10
My computer has been persistently disobedient so I am going to take it out back and shot it like a red army POW. In its place there will be a brand new shinny machine ready to receive my love and adoration. One of the things important to me is a fully functional LAMP server with all the little php perl and phyton extensions ImageMagik and all. Is there a simple method of installing the whole lot in one go. What I am looking for is something like a script that I can leave to run go have lunch and come back to a fully functional lamp stack. One thing that was suggested to me was to install the server edition and then put the desktop on after. I have tried that and not fully happy with the desktop it gave me. Also I may install linux mint. Falling short of a fire and forget script I am prepared to write one myself but i have no idea how to implement the "force yes" Can anyone provide me with an example of an aptitude command with force yes which i can use to set up all my little bits. When this new and great machine will arrive I will be too excited to go about installing all the little things so i have to have the script ready before the machine is built. Any advice will be appreciated.  Also I have tried to install via sudo tasksel in the past and it has ended in tears unintalling my desktop (my bad) but i havent the heart to use it again

---

### Post by geirha on 2007-12-10
Just install the packages you need manually. do ```
aptitude search libapache2-mod
``` and figure out which modules you want (like libapache2-mod-python). Then append them to this, which should get your lamp up and running: ```
sudo aptitude install mysql-server-5.0 mysql-client-5.0 php5-mysql libapache2-mod-php5
```

---

### Post by LaRoza on 2007-12-10
```

sudo tasksel

```

Choose "Lampp"

-EDIT I see you did that, just select the "Lampp" don't unselect anything.

---

### Post by pundip on 2007-12-11
thanks geirha the search command is pretty handy. You wouldnt happen to know how to use the force yes option with apptitude?

---

### Post by geirha on 2007-12-11
```
$ aptitude --help
...
 -y             Assume that the answer to simple yes/no questions is 'yes'
...

```

---

### Post by fragos on 2007-12-11
> **LaRoza said:**
> ```

sudo tasksel

```

Choose "Lampp"

-EDIT I see you did that, just select the "Lampp" don't unselect anything.

You can also use the synaptic GUI.  Click the edit text menu and select "Mark packages by Task.."

---

