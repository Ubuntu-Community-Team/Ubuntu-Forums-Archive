---
title: "listing files in uninstalled packges"
date: 2017-03-18
forum: General Help
---

### Post by Skaperen on 2017-03-18
i can list the files in an installed package with:  ```
dpkg -L $packagename
```

how can i get the list of files in a package that i have *not* installed?

---

### Post by howefield on 2017-03-19
The -c option ?

Eg.

```
dpkg -c $packagename
```

```
dpkg -c /home/hugh/Downloads/ttf-mscorefonts-installer_3.6_all.deb 
drwxr-xr-x root/root         0 2014-10-16 07:01 ./
drwxr-xr-x root/root         0 2014-10-16 07:01 ./var/
drwxr-xr-x root/root         0 2014-10-16 07:01 ./var/lib/
drwxr-xr-x root/root         0 2014-10-16 07:01 ./var/lib/msttcorefonts/
-rw-r--r-- root/root       866 2014-10-16 06:52 ./var/lib/msttcorefonts/cabfiles.sha256sums
drwxr-xr-x root/root         0 2014-10-16 07:01 ./usr/
drwxr-xr-x root/root         0 2014-10-16 07:01 ./usr/share/
drwxr-xr-x root/root         0 2014-10-16 07:01 ./usr/share/lintian/
drwxr-xr-x root/root         0 2014-10-16 07:01 ./usr/share/lintian/overrides/
-rw-r--r-- root/root        86 2014-10-16 06:52 ./usr/share/lintian/overrides/ttf-mscorefonts-installer
drwxr-xr-x root/root         0 2014-10-16 07:01 ./usr/share/fonts/
drwxr-xr-x root/root         0 2014-10-16 07:01 ./usr/share/fonts/truetype/
drwxr-xr-x root/root         0 2014-10-16 07:01 ./usr/share/doc/
drwxr-xr-x root/root         0 2014-10-16 07:01 ./usr/share/doc/ttf-mscorefonts-installer/
-rw-r--r-- root/root       746 2014-10-16 06:52 ./usr/share/doc/ttf-mscorefonts-installer/copyright
-rw-r--r-- root/root      7606 2014-10-16 07:00 ./usr/share/doc/ttf-mscorefonts-installer/changelog.gz
-rw-r--r-- root/root       231 2014-10-16 06:52 ./usr/share/doc/ttf-mscorefonts-installer/README.Debian
```

---

### Post by Skaperen on 2017-03-19
how can i do that *without* having the .deb file?  the package is only on the repository at this moment.  if i wanted to install it i would do **apt-get install**.  i looked through the man page of apt-get and apt but i didn't see a way to get a listing.

or how can i get the .deb file of a package if all i have is the name, without installing it?

---

### Post by howefield on 2017-03-19
I'm not sure if there is a way of querying your package sources for that level of detail without installing an extra application,  but apt-file seems to do what you want.

```
sudo apt install apt-file
```
```
apt-file update
```

allow it to do its thing and then (using a package not installed on my system as an example)...

```
apt-file list cowsay
``` 

```
apt-file list cowsay
cowsay: /usr/games/cowsay
cowsay: /usr/games/cowthink
cowsay: /usr/share/cowsay/cows/apt.cow
cowsay: /usr/share/cowsay/cows/bud-frogs.cow
cowsay: /usr/share/cowsay/cows/bunny.cow
cowsay: /usr/share/cowsay/cows/calvin.cow
cowsay: /usr/share/cowsay/cows/cheese.cow
cowsay: /usr/share/cowsay/cows/****.cow
cowsay: /usr/share/cowsay/cows/cower.cow
cowsay: /usr/share/cowsay/cows/daemon.cow
cowsay: /usr/share/cowsay/cows/default.cow
cowsay: /usr/share/cowsay/cows/dragon-and-cow.cow
cowsay: /usr/share/cowsay/cows/dragon.cow
cowsay: /usr/share/cowsay/cows/duck.cow
cowsay: /usr/share/cowsay/cows/elephant-in-snake.cow
cowsay: /usr/share/cowsay/cows/elephant.cow
cowsay: /usr/share/cowsay/cows/eyes.cow
cowsay: /usr/share/cowsay/cows/flaming-sheep.cow
cowsay: /usr/share/cowsay/cows/ghostbusters.cow
cowsay: /usr/share/cowsay/cows/gnu.cow
cowsay: /usr/share/cowsay/cows/hellokitty.cow
cowsay: /usr/share/cowsay/cows/kiss.cow
cowsay: /usr/share/cowsay/cows/koala.cow
cowsay: /usr/share/cowsay/cows/kosh.cow
cowsay: /usr/share/cowsay/cows/luke-koala.cow
cowsay: /usr/share/cowsay/cows/mech-and-cow.cow
cowsay: /usr/share/cowsay/cows/milk.cow
cowsay: /usr/share/cowsay/cows/moofasa.cow
cowsay: /usr/share/cowsay/cows/moose.cow
cowsay: /usr/share/cowsay/cows/pony-smaller.cow
cowsay: /usr/share/cowsay/cows/pony.cow
cowsay: /usr/share/cowsay/cows/ren.cow
cowsay: /usr/share/cowsay/cows/sheep.cow
cowsay: /usr/share/cowsay/cows/skeleton.cow
cowsay: /usr/share/cowsay/cows/snowman.cow
cowsay: /usr/share/cowsay/cows/stegosaurus.cow
cowsay: /usr/share/cowsay/cows/stimpy.cow
cowsay: /usr/share/cowsay/cows/suse.cow
cowsay: /usr/share/cowsay/cows/three-eyes.cow
cowsay: /usr/share/cowsay/cows/turkey.cow
cowsay: /usr/share/cowsay/cows/turtle.cow
cowsay: /usr/share/cowsay/cows/tux.cow
cowsay: /usr/share/cowsay/cows/unipony-smaller.cow
cowsay: /usr/share/cowsay/cows/unipony.cow
cowsay: /usr/share/cowsay/cows/vader-koala.cow
cowsay: /usr/share/cowsay/cows/vader.cow
cowsay: /usr/share/cowsay/cows/www.cow
cowsay: /usr/share/doc/cowsay/NEWS.Debian.gz
cowsay: /usr/share/doc/cowsay/README
cowsay: /usr/share/doc/cowsay/changelog.Debian.gz
cowsay: /usr/share/doc/cowsay/copyright
cowsay: /usr/share/doc/cowsay/examples/cowsay_random
cowsay: /usr/share/man/man6/cowsay.6.gz
cowsay: /usr/share/man/man6/cowthink.6.gz
cowsay-off: /usr/share/cowsay/cows/beavis.zen.cow
cowsay-off: /usr/share/cowsay/cows/bong.cow
cowsay-off: /usr/share/cowsay/cows/head-in.cow
cowsay-off: /usr/share/cowsay/cows/mutilated.cow
cowsay-off: /usr/share/cowsay/cows/sodomized-sheep.cow
cowsay-off: /usr/share/doc/cowsay-off/NEWS.Debian.gz
cowsay-off: /usr/share/doc/cowsay-off/changelog.Debian.gz
cowsay-off: /usr/share/doc/cowsay-off/copyright
xcowsay: /usr/games/xcowdream
xcowsay: /usr/games/xcowfortune
xcowsay: /usr/games/xcowsay
xcowsay: /usr/games/xcowthink
xcowsay: /usr/share/doc/xcowsay/NEWS.gz
xcowsay: /usr/share/doc/xcowsay/changelog.Debian.gz
xcowsay: /usr/share/doc/xcowsay/copyright
xcowsay: /usr/share/locale/pt_BR/LC_MESSAGES/xcowsay.mo
xcowsay: /usr/share/locale/ru/LC_MESSAGES/xcowsay.mo
xcowsay: /usr/share/man/man6/xcowdream.6.gz
xcowsay: /usr/share/man/man6/xcowfortune.6.gz
xcowsay: /usr/share/man/man6/xcowsay.6.gz
xcowsay: /usr/share/man/man6/xcowthink.6.gz
xcowsay: /usr/share/xcowsay/cow_large.png
xcowsay: /usr/share/xcowsay/cow_med.png
xcowsay: /usr/share/xcowsay/cow_small.png
```

The alternative is to go to packages.ubuntu.com, search for the package you want and you'll find a link to listing all files.

---

### Post by Dennis N on 2017-03-19
> how can i get the .deb file of a package if all i have is the name, without installing it?

**apt-get download xxx**

gets you the deb file for xxx.

Example:
```
dmn@Zotac:~$ apt-get download htop
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/universe htop amd64 1.0.2-3 [68.0 kB]
Fetched 68.0 kB in 0s (180 kB/s)

```

Use archive manager to examine the package, which reveals the files it installs.

---

### Post by oldos2er on 2017-03-19
> **Skaperen said:**
> how can i get the list of files in a package that i have *not* installed?

In addition to the other answers, you can also visit packages.ubuntu.com

---

### Post by Skaperen on 2017-04-14
> **howefield said:**
> I'm not sure if there is a way of querying your package sources for that level of detail without installing an extra application,  but apt-file seems to do what you want.

```
sudo apt install apt-file
```
```
apt-file update
```

allow it to do its thing ...

this looks like it does what i need.  other features of apt-file include things i was going to try to implement.  thanks for letting me know about this:P  btw, apt-file update took about 1m11s for anyone else who needs to know.

---

### Post by vasa1 on 2017-04-15
> **Skaperen said:**
> this looks like it does what i need. ...
If you're sure, please mark the thread [SOLVED]: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
Thanks!

---

