---
title: "ABANDONED! Where to put new program"
date: 2021-11-02
forum: General Help
---

### Post by Enigma12 on 2021-11-02
I have installed Image Scan! for Linux in the past for use with my Epson scanner and want to install it on my current computers, since it gives me many more options than any included scanner program. Always before this, as well as I can recall, the .deb or tar.gz file extracted everything without my giving it any input as to where to put things. This time, the default location shows as my Downloads folder, where the tar.gz file is located. That's NOT where I want things put. But where should I install it?

I could put it in /Home, but I think somewhere in / would be tidier, if the program would work there [COLOR=#b22222]**and **[/COLOR]show up in my Graphics menu. Would /usr be a good place? Or is somewhere else in / better? Should I create a folder for it in /? Obviously, the location for the files may (almost) be irrelevent, but I'd prefer to install it where it would be best.

I had hoped that after 7 1/2 years of using Linux, I would no longer have any questions, but Reality let me know otherwise.  :-({|=

Thanks in advance for any advice.[COLOR=#00ffff][/COLOR][COLOR=#00ffff][/COLOR][COLOR=#00ffff][/COLOR]

---

### Post by Dennis N on 2021-11-03
I'd choose a folder under /opt if given a choice. So you may have to first create a folder such as /opt/ImageScan to contain the program files.

---

### Post by ActionParsnip on 2021-11-03
Everyone is learning. Even many more years later you'll more than likely still have questions.
Is there no deb file to install it with?

---

### Post by Impavidus on 2021-11-03
If they offer both a .deb and a .tar.gz, try the .deb first. That tells the package manager about the software you install, so it can prevent conflicts with other software and cleanly remove it later or replace it with a new version. A .deb doesn't ask you where to install files. That's all stored in the .deb, just like all (well, most) other software on Ubuntu. It will be installed in the appropriate place automatically (if the .deb is appropriately built, but the epson imagescan package on my computer is).

---

### Post by grahammechanical on 2021-11-03
If these two files are important to your use of the scanner then I suggest that you keep copies in a safe place under /home. Then if you need to re-install Ubuntu you will not need to download these files again. This will be all the better if you have a separate /home partition or a partition used for Data.

Regards

---

### Post by HermanAB on 2021-11-03
Note that the directories /usr/local and /opt are customarily used for user installed programs and these directories will not be messed up by a system update.

---

### Post by TheFu on 2021-11-03
There are standards for where different files should go.  The major Linux distros mostly follow those standards - with the exception of what snaps do. They don't follow any standards that I can figure out.

Anyway, [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) has a table with descriptions.
Package manager installed software puts files in specific locations.  Non-package (i.e. .deb files) on Ubuntu should never be placed in those same places.  Commercial packages can be put into /opt/ or /usr/local/.  I use a vague "did this come with an installer and binary code" as the delimiter for what goes into /opt/.  Stuff I compile or that is using a scripting language (not compiled), belong in /usr/local/ if system-wide use is desired.  For a single user, I'd put the program under my $HOME somewhere, usually keeping a setup like this:
```
Program
|____bin
|____etc
|____lib
|____doc
|____db
|____data

```
That way, the entire program, settings and everything else are stored together. This works for /opt/ too.

/usr/local/ can be either self-contained like the directory structure I show above or mixed together. I let the "installer" decide and let the "PREFIX" for the source package decide.  If they keep the program self contained, I will either add the bin/ directory to my PATH or create a symlink to it in the /usr/local/bin/ directory.

So ... it depends is the only answer. ;)

---

### Post by Enigma12 on 2021-11-12
First, thank you to each of you guys for your advice and assistance. All familiar and known-helpful members. You are appreciated. 

Second, I had to abandon this project for a few days to tend to pre-winter home and vehicle matters. 

Lastly, although I was aware of tarball files, I had never encountered one before, but that file contained the old familiar .deb within it. When I attempted to install the program using the .deb, I got only a partial install. With that being useless to me, I deleted it, then did some online research and got a list of recommended programs. I chose to have old trusty Synaptic install Xsane, and it seems to do what I need, so I'll stick with that for now at least. 

If I can figure out how, I will mark this thread as "Abandoned" or other appropriate term.

---

### Post by TheFu on 2021-11-13
Actually, it would be better to mark **SOLVED** using the thread tools button, and update the first post saying that an alternative installation method was used - the normal package manager with xsane.  There are fancier GUIs for scanning available in the normal repos, BTW.

The preferred order of installation methods:
[LIST=1]
[*]Always start with using the Canonical packaged solutions first.
[*]Next, look for a trusted PPA and use that.  PPAs integrate into the normal OS patching and a trusted PPA would provide updates as needed when dependent packages are updated.
[*]Next would be a Snap/Flatpak package. There are some downsides and upsides to using these. Canonical seems to think our computers are smartphones with 1 storage device and I suppose for that situation, Snaps aren't THAT bad.  But they don't allow local control and people using more storage are likely to bang their head's into storage access restrictions.
[*]Next would be a .deb file.  This will most likely break package dependencies and in 3-6 months, 1 package can prevent other important core packages from being updated.  This is commonly known as "RPM Hell", but "APT Hell" would better fit on Ubuntu.  There are 2 solutions for APT Hell.  Remove the original .deb file that was manually installed OR do a fresh - clear-field - nuked-from-orbit - OS install.  
[*]Next would be using source code.  This assumes it is a compiled language.  For some small script programs (python/GoLang/Perl/Bash), that work in highly dynamic ways and need updating weekly, it would be preferred to use the original script install/update method and not the .deb file or snap or PPA or even Canonical Repos.  But for larger projects with multiple dependencies and compiles, best to avoid manually installation, since this means you've just accepted the need to redo this at least monthly for as long as the system uses that program. All to stay patched and current.
[/LIST]
I think that list handles most situations. There can be exceptions, but those really need to be avoided by people who cannot fully commit to maintaining their systems.

---

