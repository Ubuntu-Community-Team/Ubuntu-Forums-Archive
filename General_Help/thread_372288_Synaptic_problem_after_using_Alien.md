---
title: "Synaptic problem after using Alien"
date: 2007-02-28
forum: General Help
---

### Post by ramjet_1953 on 2007-02-28
Hi, Guys!

I have encountered an interesting problem after using [COLOR="Red"]alien[/COLOR] to convert an RPM package to a DEB package.

The package is called [COLOR="Red"]kastrolog[/COLOR], which is a KDE version of astrolog.

After downloading the RPM, I issued the following command:

sudo alien -c -k kastrolog-5.4-1.1.i386.rpm

It successfully converted the package to a DEB, with no errors.

I then changed the permissions of the DEB package, to allow myself read and write priveleges.

I then right clicked on the DEB package and selected to open it with GDebi Package Installer.

The installation proceeded and then stoped, with what I think was an error 1 .

I then tried a re-install, but it said the package could not be opened, as it was either corrupted, or I didn't have the correct priveleges [COLOR="Blue"](see attached screen shot).[/COLOR]

I then tried re converting the RPM again, but the same error came up.

It gets better, as now Synaptic comes up with an error [COLOR="Blue"](see attached screen shot).[/COLOR] And all of the repositories appear to have been hosed. Even when I click on re-load in Synaptic, it goes through the motions of downloading the repositories, but it is still blank when it finishes.

Any suggestions on where I go from here?

Regards,
Roger 8)

---

### Post by Johan! on 2007-02-28
Try this in a terminal:

```

sudo apt-get remove kastrolog
```

---

### Post by ramjet_1953 on 2007-02-28
Hi, thanks for the suggestion.
I was considering trying it before you replied, but unfortunately, the same problem persists.

See the attached screen shot.

Regards,
Roger :cool:

---

### Post by ramjet_1953 on 2007-02-28
I've just encountered another problem.

Even though I get the indicator in the panel that there are updates available, when I try to update it won't.

So it looks like this problem has well and truly hosed Synaptic for me.

Regards,
Roger :cool:

---

### Post by Johan! on 2007-02-28
Try this then:
```
 sudo apt-get --purge --force-yes remove kastralog
```

If this doesn't work, re-download the .rpm.
Convert it to a .deb with alien, don't use sudo.
Then you can try to reinstall it.

You could also try to remove it with synaptic.
There's an option to remove a package completely. (Instead of normal removal)
You can also try to repair it by clicking on Edit>Fix broken packages.

---

### Post by ramjet_1953 on 2007-02-28
Hi, Johan!

Thanks again, for the advice, but again, no success.

Please see the attached screen shots.

There is something consistent here, in that it keeps saying that it can't find an archive for it.

I also tried sudo apt-get -f install and dpkg --configure -a (see the screen shot)

By the way you can't run alien without sudo.

I can't uninstall it with Synaptic, as it is totally empty and won't allow me to re-load the package info. See screen shot on first post. 

I've already tried to repair it using Synaptic, but as it is empty, there is nothing to repair.

Regards,
Roger 8)

---

### Post by Johan! on 2007-02-28
You could try to copy the .deb file to /var/cache/apt
I hope apt can find the archive then.

---

### Post by ramjet_1953 on 2007-02-28
> **Johan! said:**
> You could try to copy the .deb file to /var/cache/apt
I hope apt can find the archive then.

Sorry, I forget to meantion that I had tried that move earlier, to no avail.

Regards,
Roger :cool:

---

### Post by ramjet_1953 on 2007-02-28
Here's another bit of information.

I no longer have an [COLOR="Red"]/etc/sources.lst[/COLOR] file!

Regards,
Roger :cool:

---

### Post by Johan! on 2007-02-28
> **ramjet_1953 said:**
> 
I no longer have an [COLOR="Red"]/etc/sources.lst[/COLOR] file!


I hope that's a typo :o
It's /etc/apt/sources.list

If you're sure there's no sources.list, your system is b0rked.
Reinstall Ubuntu and start again :(

I'm sorry


PS: [Maybe this is an interesting link]("http://ubuntuforums.org/showthread.php?t=355571")

---

### Post by ramjet_1953 on 2007-02-28
Sorry, Johan!

I had brain fade there!

I do have an etc/apt/sources.list file , including backups.

Still no go on the original problem, though.

Regards,
Roger 8)

---

### Post by hikaricore on 2007-02-28
> **Johan! said:**
> your system is b0rked.
Reinstall Ubuntu and start again :(

Now that's the Microsoft spirit I like to see alive and well. :lolflag:

---

### Post by hikaricore on 2007-02-28
(you may want to backup */var/lib/dpkg/status* before trying my advice)

As a last resort try this from a terminal:

```
sudo kate /var/lib/dpkg/status
```

Do a search for "kastrolog" and CAREFULLY manually remove the entry.  Save the file and run:

```
sudo apt-get update
```

And your problem should be "resolved", though I use this term lightly as the files will still be installed, just your package managers won't complain about it.

Also from now on you may consider compiling software on your own instead of converting packages >.<

---

### Post by Johan! on 2007-02-28
> **hikaricore said:**
> Now that's the Microsoft spirit I like to see alive and well. :lolflag:
If apt is broken, then I consider my Ubuntu installation is broken.
If I can repair it 100%, my system is not broken. (I also hate "the Microsoft spirit" :) )
Since we don't know how to repair it in a normal way, I think the system is borked.



> **hikaricore said:**
> (you may want to backup */var/lib/dpkg/status* before trying my advice)

As a last resort try this from a terminal:

```
sudo kate /var/lib/dpkg/status
```

Do a search for "kastrolog" and CAREFULLY manually remove the entry.  Save the file and run:

```
sudo apt-get update
```

And your problem should be "resolved", though I use this term lightly as the files will still be installed, just your package managers won't complain about it.

Also from now on you may consider compiling software on your own instead of converting packages >.<

Since you don't know what damage the converted rpm package has done (which files are affected?, apt may be unstable after the "repairs" and some unknown files are still installed) I would recommend a full reinstall.
After the "repairs" the system might work again, but what will happen when you try to update or install other applications?

---

### Post by ramjet_1953 on 2007-02-28
Hikaricore, you're a star ***************************!!!!!

Thanks for that, it worked a treat!

And yes, this was the first and LAST time that I use Alien!

And thanks to you, too Johan for the tips, also.

If I could do it, I would email both of you a beer!

Regards,
Roger 8)

---

### Post by hikaricore on 2007-02-28
> **ramjet_1953 said:**
> Hikaricore, you're a star ***************************!!!!!

Thanks for that, it worked a treat!

And yes, this was the first and LAST time that I use Alien!

And thanks to you, too Johan for the tips, also.

If I could do it, I would email both of you a beer!

Regards,
Roger 8)

Glad I could help, I've had to fix many a system this way in an emergancy.  It's definately not the end all be all solution to broken packages, but it will save you some headaches when you know what you'er doing and nothing else will work.  Good luck to you in the future.  :)

---

### Post by hikaricore on 2007-02-28
> **Johan! said:**
> 
Since you don't know what damage the converted rpm package has done (which files are affected?, apt may be unstable after the "repairs" and some unknown files are still installed) I would recommend a full reinstall.

It's a kde app, trust me the system will be fine.  :)

> **Johan! said:**
> 
After the "repairs" the system might work again, but what will happen when you try to update or install other applications?

Nothing will happen when other applications are updated or installed.  The pacakage manager will happily overwrite any files installed by the messed up alien package and go anong it's merry way.  If the system is running still I'm just going to assume that a simple kde application didn't destroy libc6 or anything silly like that.

All in all it worked and that's the important thing.  This is no different than telling someone to remove a messed up registry entry via regedit.  I'm sure you would tell a windows user than editing the registry is dangerous and they should just reinstall everything "just in case".  I realize my examples are a little strong, but you get my point.

---

