---
title: "Cleaning up Ubuntu"
date: 2008-01-06
forum: General Help
---

### Post by pikaia on 2008-01-06
Hi.

I've been (almost) exclusively Ubuntu now for about 3-4 months and love it.  But have heard of some cleaning options to remove partially installed packages and unnecessary files.  I do the autoclean and clean commands, and downloaded gtkorphan and Kleansweep, but I'm a bit worried since I'm not as familiar with what is necessary and what is not (as I was with XP) so how trustworthy is the list of files these programs provide and if they're not, what are my options for determining which files to get rid of.  I like keeping a streamlined machine and would like to maintain that with linux...

I ran gtkorphan and got about 15 files (mostly lib files) and Kleansweep found somewhere along the lines of 25000 files... after 3 months?  What should I do?

I saw the HOWTO: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920), but this doesn't list any sort of reliability issues.  I don't want to go uninstalling packages or libraries that are going to upset the running of my machine, even if I reinstall.

Thanks

---

### Post by gsiliceo on 2008-01-06
I installed kleansweep and i would say the safests options are:
Empty files
Empty directories
Broken symlinks
Dead menu entries
Obsolete thumbnails
Duplicate files.

The others may kill programs i compiled my self and other binaries, libraries.

---

### Post by erfahren on 2008-01-06
> **pikaia said:**
> 
I saw the HOWTO: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920), but this doesn't list any sort of reliability issues.  I don't want to go uninstalling packages or libraries that are going to upset the running of my machine, even if I reinstall.

you can use 
```

sudo apt-get install -f

```
to repair broken dependencies afterwards

You could also use that "deborphan in Synaptic" tip in that howto - remove the ophaned packages in there (without *completely* removing them) - then run the above command. If you do find someting non-fuctioning later you'll have them there. 

I think some packages might pull in a dependency (of a library package for example) and then another package might require a newer version so the older one isn't really needed.  The package manager is excellent but probably not perfect.

The other thing to consider is the total size of whatever orphans you decide to keep. They probably don't take up too much space. This isn't like Windows where programs (especially retail ones) leave remnants of themselves all over the place. Afew orphans isn't going to hurt anything.

I'm kind of the same way though (a perfectionist?) - I found that using aptitude gives you much more information. You can use it to see reverse dependencies of a package (see what packages depend on a particular package). You just have to familiarize yourself with it.
[https://help.ubuntu.com/7.10/server/C/aptitude.html](https://help.ubuntu.com/7.10/server/C/aptitude.html)
[https://help.ubuntu.com/community/AptitudeSurvivalGuide](https://help.ubuntu.com/community/AptitudeSurvivalGuide)

---

### Post by jis on 2008-02-14
> **erfahren said:**
> 
I'm kind of the same way though (a perfectionist?) - I found that using aptitude gives you much more information. You can use it to see reverse dependencies of a package (see what packages depend on a particular package). You just have to familiarize yourself with it.
[https://help.ubuntu.com/7.10/server/C/aptitude.html](https://help.ubuntu.com/7.10/server/C/aptitude.html)
[https://help.ubuntu.com/community/AptitudeSurvivalGuide](https://help.ubuntu.com/community/AptitudeSurvivalGuide)

How can you use it to see reverse dependencies of a package?

---

### Post by seventhc on 2008-02-14
doesn't this clean unnecessary files?
```

sudo apt-get autoclean

```
[B]
Edit:[/B] sorry, I see now that you did that. I didn't notice that before I posted.

---

### Post by erfahren on 2008-02-17
> **jis said:**
> How can you use it to see reverse dependencies of a package?
under the package entry (in the attached screenshot example it is "gthumb" - the Ubuntu image viewer) and use the arrow keys to scroll down to where it says "Packages which depend on gthumb" - 

with it highlightd hit "enter" to expand the tree

it will list the packages that have gthumb listed as a dependency - (it also lists packages that suggests it and recommends it, etc.).

(the "---" and "--/" denote expandable and collaspable trees)

like I say though, you kind of have to mess around with Aptitude to familiarize yourself with it (the interface is a little "old-school"). It's good though.

---

### Post by jis on 2008-02-17
erfahren, thanks for the instructions. I have used the command line mode of aptitude to get information about packages and didn't find an option in that. Good that there is a way to get reserve dpendencies in the other user interface.

---

### Post by jis on 2008-02-17
aptitude seems to install recommended packages so it generates more packages to clean than apt-get in Gutsy.

---

