---
title: "Lucid &gt; Precise via do-release-upgrade worked BUT having a few repo issues."
date: 2012-10-25
forum: General Help
---

### Post by jtwdyp on 2012-10-25
Last night I ran do-release-upgrade on my desktop. 

I was mostly happy with the results. Though I'm disappointed by a few evidently "obsoleted" items that I surely wish were still there.

And one item I'm a bit frustrated with that IS in the repo but which is not installable due to dependency problems.

I should mention that my desktop of choice is Enlightenment. I usually use E17. Which is occasionally unstable. So I like being able to fall back on the very stable E16. Which is also fun to play with now and again even when E17 is working perfectly. 

The E17 repo that I used to use with Lucid hasn't been updated for Precise however so I added:

```
deb http://ppa.launchpad.net/hannes-janetzek/enlightenment-svn/ubuntu precise main
```

to my sources. I noticed that a "calender" module/gadget disappeared from the available modules list. That would be fine if the "clock" module/gadget had been updated to the version with a pop-up calender function. But it hasn't...

So I fired up synaptic and went looking for the calender module/gadget.  There were some dependency problems. The part of the error pop-up that I could copy and paste said: 
```

emodule-calendar:
 Depends: libecore1 but it is not going to be installed
 Depends: libedje1 but it is not going to be installed
 Depends: libeina1 but it is not going to be installed
 Depends: libevas1 but it is not going to be installed

```
[SIZE="2"]**[COLOR="Blue"]Are there any Enlightenment users out there who have managed to get the calender module working in precise???[/COLOR]**[/SIZE]

BTW, when I tried to restore E16 I got:
```

e16:

Package e16 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never
uploaded, has been obsoleted or is not available with the contents of sources.list

```
I was also disappointed to lose a nice stand-alone desktop-independent scriptable screen snapshot utility named emprint. When I tried to find that, synaptic simply displayed an empty package selection window.

[COLOR="blue"][B]Can anybody tell me if e16 and emprint are missing because somebody decided they were obsolete??? Or if it could be just that nobody has had time to add them to the 12.04 repo(s)???
[/B][/COLOR]
-- 
JtWdyP

---

### Post by pqwoerituytrueiwoq on 2012-10-26
try ```
sudo apt-get dist-upgrade
```
or just go manual
```
sudo apt-get install libecore1 libedje1 libeina1 libevas1
```

---

### Post by jtwdyp on 2012-10-26
> **pqwoerituytrueiwoq said:**
> try ```
sudo apt-get dist-upgrade
```or just go manual
```
sudo apt-get install libecore1 libedje1 libeina1 libevas1
```
Opened a root shell and:
```
/home/jtwdyp 
UnderTree=-> apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libedje-bin libeet1 libembryo0
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
/home/jtwdyp 
UnderTree=-> apt-get install libecore1 libedje1 libeina1 libevas1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libedje-bin libeet1 libeio0 libembryo0
The following packages will be REMOVED:
  e17 libecore-con-svn-05 libecore-evas-svn-05 libecore-fb-svn-05 libecore-file-svn-05
  libecore-imf-svn-05 libecore-input-svn-05 libecore-ipc-svn-05 libecore-job-svn-05
  libecore-svn-05 libecore-txt-svn-05 libecore-x-svn-05 libedbus-svn-05 libedje-svn-05
  libefreet-svn-05 libeina-svn-05 libembryo-bin libevas-svn-05
  libevas-svn-05-engines-core libevas-svn-05-engines-x
The following NEW packages will be installed:
  libecore1 libedje1 libeina1 libeio0 libevas1
The following packages will be upgraded:
  libedje-bin libeet1 libembryo0
3 upgraded, 5 newly installed, 20 to remove and 0 not upgraded.
Need to get 1,820 kB of archives.
After this operation, 7,698 kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
/home/jtwdyp
UnderTree=-> 

```{sigh}

[SIZE=1][COLOR=Sienna]-- 
JtWdyP
[/COLOR][/SIZE]

---

### Post by dino99 on 2012-10-26
is that better now ? dont hesitate to clean the system: clean/autoclean/autoremove/deborphan/bleachbit

and of course be sure that some oldish ppa(s) are not still activated before updating

---

### Post by jtwdyp on 2012-10-29
> **dino99 said:**
> is that better now ? dont hesitate to clean the system: clean/autoclean/autoremove/deborphan/bleachbit

and of course be sure that some oldish ppa(s) are not still activated before updating

Better????

The dist-upgrade did NOTHING and the attempted manual install wanted to throw away a LOT of e17 packages, hence I said NO...

---

### Post by grahammechanical on 2012-10-29
You should understand that Lucid is based upon the Gnome 2 desktop environment and Precise is based on the Gnome 3 desktop environment.

So, you should not be surprised that stuff that worked on Gnome 2 does not work on Gnome 3. They are completely different libraries.

The stuff you want to use needs to be compatible with Gnome 3.

Regards.

---

### Post by jtwdyp on 2012-10-30
> **grahammechanical said:**
> You should understand that Lucid is based upon the Gnome 2 desktop environment and Precise is based on the Gnome 3 desktop environment.

So, you should not be surprised that stuff that worked on Gnome 2 does not work on Gnome 3. They are completely different libraries.

The stuff you want to use needs to be compatible with Gnome 3.

Regards.

I would expect that if the ubuntu.desktop metafile had been installed when I did the do-release-upgrade from Lucid to Precise. How much upon gnome3 does the xubuntu.desktop metafile configuration depend?? I don't actually use xfce BTW, But I needed to select an *buntu flavor when I first installed, and since there isn't an enlightenment.desktop metafile, and as far as I know the Xubuntu configuration would install less stuff that I'd never use then either the ububtu,desktop or the kubuntu desktop would, {Given that since kde4, I wouldn't be caught dead using the user interface supplied by kde, and I never could stand gnome}

I'm actually not sure though how much the E17 desktop envitonment itself depends on gnome? But I know it can be added to a kde system without installing the whole gnome environment...

-- 
JtWdyP

{sigh}

---

