---
title: "Compiling additional Compiz Fusion plugins from GIT"
date: 2008-04-29
forum: General Help
---

### Post by jsully1 on 2008-04-29
Hi all, 

After scratching my head a bit this morning I figured I'd share my experiences about compiling additional plugins from source.

To start with, we need to install some dependencies and packages.

```
sudo apt-get install git-core automake build-essential intltool libtool python-pyrex python2.5-dev xsltproc compiz-dev compiz-bcop
```

Next up we'll want to make a directory to compile things in.  If you want to make a directory called git in your home directory, do this:
```
sudo mkdir ~/git
```

Next we'll want to grab the code from git.  **[Here](http://gitweb.opencompositing.org/)** is where I found sources.  Search for the plugin you want, and then click on summary.  In my case I wanted to install the tile plugin, **[found here](http://gitweb.opencompositing.org/?p=fusion/plugins/tile;a=summary)**.  This page indicates that the git url is git://anongit.compiz-fusion.org/fusion/plugins/tile

In your newly created directory, do the following to pull down the source:
```
git clone git://anongit.compiz-fusion.org/fusion/plugins/tile
```

Now cd to the directory that it just pulled down (in my case tile) and do:
```
sudo make
```
If that's successful then proceed to:
```
sudo make install
```
You'll see you now have a build directory and a .libs directory beneath it.  Head to the libs directory and you'll find a series of lib[pluginname].*
We'll want to move them to the Compiz plugins directory - in my case with the tile plugin:
```
sudo mv libtile.* /usr/lib/compiz/
```

That should be all there is to it.  At this point you'll want to install the Compizconfig settings manager if you haven't already.
```
sudo apt-get install compizconfig-settings-manager
```
Your new plugin should now show up int he settings manager and be ready for configuration and use.  Please let me know if I missed anything, as I wrote this little guide after the fact.

Sully

---

### Post by makajawanjack on 2008-06-22
Thanks for the guide, it worked flawlessly! I've been missing this functionality in Compiz ever since I switched over from Beryl. It makes window management boatloads simpler.

---

### Post by 71CH on 2008-06-23
I get this error.

[PHP]sudo make
compiling : snow.c -> build/snow.losnow.c: In function ‘snowInitScreen’:
snow.c:545: error: incompatible type for argument 2 of ‘compAddTimeout’
snow.c:545: error: too many arguments to function ‘compAddTimeout’
snow.c: In function ‘snowDisplayOptionChanged’:
snow.c:613: error: incompatible type for argument 2 of ‘compAddTimeout’
snow.c:613: error: too many arguments to function ‘compAddTimeout’
make: *** [build/snow.lo] Error 1
[/PHP]

a little help please

---

### Post by 71CH on 2008-06-23
One more thing
I successfully installed the screensaver plugin.  Can I delete the git folder now or will that mess up the install?  Thanks.

---

### Post by isaacj87 on 2008-06-23
When I install additional Compiz-Fusion plugins I don't run a "sudo make install." I just do a "make install" that way the plugins install locally and I can delete them myself with little effort.

> **71CH said:**
> One more thing
I successfully installed the screensaver plugin.  Can I delete the git folder now or will that mess up the install?  Thanks.

and I wouldn't delete the source folder, just in case you want to update the plugin (git pull) or if you want to uninstall it.

---

### Post by 71CH on 2008-06-24
that doesn't seem to help
anything else i can try?

---

### Post by 71CH on 2008-06-25
bump

---

### Post by Techrocket9 on 2008-07-04
[SIZE=7]Bra*vo*![/SIZE]

---

### Post by Jebtrix on 2008-07-05
**THANK YOU!!!**\\:D/

I absolutely cannot believe the tile plugin is not standard issue.. this is borderline usability treason [-(

---

### Post by feeshy on 2008-08-20
Thank You!  Appreciate this!

---

### Post by fyjpm on 2008-08-20
Tile is working for me, but it tiles across both monitors...I'm sure that the fix is in the code, but i'm not a C programmer.

I realize that X sees one big display, but perhaps there is a way to determine what Twinview is using to calculate the display sizes and go off this # for tiling dimensions instead of using both displays......

-John

---

### Post by robatron on 2009-01-07
Thank you SO much, jsully1!!! It worked FLAWLESSLY!! \\:D/

---

### Post by jsully1 on 2009-04-24
Note that if you want to compile one of these plugins in 9.04 Jaunty Jackelope, you want to grab the unsupported plugins from here rather than git:
[http://releases.compiz-fusion.org/0.8.2/](http://releases.compiz-fusion.org/0.8.2/)

---

### Post by Godly on 2009-04-24
Great post! +1

---

### Post by Lota on 2011-03-22
I keep getting a fatal: The remote end hung up unexpectedly... any help? It occurs after git clone...

---

