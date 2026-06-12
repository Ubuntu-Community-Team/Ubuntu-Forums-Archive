---
title: "Dictionary with Definitions, please?"
date: 2008-04-17
forum: General Help
---

### Post by sidewalkcynic on 2008-04-17
I'm looking for an English dictionary with definitions I can use offline. I have checked the Universal Repository, and all I see are spell checkers for various langauges.

---

### Post by JimmyBEng on 2008-04-17
Applications->Accesories->Dictionary

-or-

```
$ gnome-dictionary 
```

its pat of the gnome-utils package if you happened to uninstall it

---

### Post by phidia on 2008-04-17
The gnome-dictionary is an online tool. Check the thread [here]("http://ubuntuforums.org/showthread.php?t=131719") for a offline dictionary.

---

### Post by angry_johnnie on 2008-04-18
You could use Stardict.  It's very good, and should be available in your repositories.

The downside is that you'll have to download the dictionaries yourself, but it's not all that difficult.

Look for it in synaptic.  Somewhere in the package's description it will give you a webpage where you can download dictionaries.

---

### Post by sidewalkcynic on 2008-04-20
Hey, thanks,

I'm having some trouble putting the Tarball or extracted files into the stardict/dic directory though.

---

### Post by JimmyBEng on 2008-04-21
> **phidia said:**
> The gnome-dictionary is an online tool. Check the thread [here]("http://ubuntuforums.org/showthread.php?t=131719") for a offline dictionary.

opps.  My mistake.  sorry.

---

### Post by angry_johnnie on 2008-04-21
> **sidewalkcynic said:**
> Hey, thanks,

I'm having some trouble putting the Tarball or extracted files into the stardict/dic directory though.

Hit alt+f2 and then type:

```
gksu nautilus
```

Then you shoudln't have any problem moving files around.

Or, you could do this in terminal:

```
sudo mv /path/to/files /new/path/to/files
```

Where /path/to/files is where they are now, and /new/path/to/files is where you want them to be.

---

