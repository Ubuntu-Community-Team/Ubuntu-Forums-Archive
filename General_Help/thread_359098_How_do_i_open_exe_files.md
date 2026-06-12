---
title: "How do i open exe files?"
date: 2007-02-11
forum: General Help
---

### Post by Deathflame on 2007-02-11
how do i open exe files?

---

### Post by Arisna on 2007-02-11
Generally, you won't be using .exe files on a GNU/Linux system such as Ubuntu.  Such files are generally designed for Microsoft Windows.  However, some .exe files can be run correctly using the Wine program, a compatibility layer that allows some Windows applications to function under Ubuntu and other Unix-like operating systems.

What program are you trying to run?  There may be a version available for GNU/Linux, or a work-alike program.

---

### Post by llamakc on 2007-02-11
With Wine if you absolutely must but most likely you do not want to open them. Give an example, please.

---

### Post by Deathflame on 2007-02-11
im trying to install this file called scorpio xp [http://desi-underground.com/index.php?showtopic=12704&hl=SiCoXP-SP3](http://desi-underground.com/index.php?showtopic=12704&hl=SiCoXP-SP3)

---

### Post by llamakc on 2007-02-11
**```
The error returned was:**

  		Sorry, but you do not have permission to use this feature. If you are not logged in, you may do so using the form below if available.
```



Linking to a closed forum isn't going to help. What does the program do? You do realize that most *.exe files aren't made for Linux and will not work? Even the ones that run through Wine there is usually an alternative to it.

---

### Post by Deathflame on 2007-02-11
its like windows

---

### Post by bionnaki on 2007-02-11
sudo apt-get install wine
winecfg

and then
cd into the directory of the file
and do
wine "filename"

---

### Post by Ramses de Norre on 2007-02-11
> **Deathflame said:**
> its like windows

What do you mean by that??

And what is the functionality of the program you're trying to use?? (as already asked before)
How can we help you if you don't give us information...

---

### Post by nickoli_02 on 2007-02-11
Yea... you're going to have to include more information if you want any sort of useful response around here.

---

### Post by nalioth on 2007-02-11
Windows Executables can be several things.

Self-extracting zip file.  Open this with unzip in the console, or Ark 

Self-extracting rar file.  Make sure you have unrar-nonfree (just unrar in newer releases) and use unrar from the console or Ark

Microsoft Cabinet file.  Install 'cabextract' and use cabextract from the console to open it.

Installshield Cabinet file.  Install 'unshield' and use unshield from the console to open it.

Compiled binary file.  Have fun opening this one.  To attempt to run this, use Wine as previously mentioned

---

### Post by llamakc on 2007-02-11
The link the OP posted is this:

[http://albddl.com/2006/10/15/new_fast_windows_sicoxpsp3_full_2006.html](http://albddl.com/2006/10/15/new_fast_windows_sicoxpsp3_full_2006.html)

I think they are trying to install Windows and this doesn't appear to be a legal copy.

---

### Post by Ramses de Norre on 2007-02-12
So you're asking on a linux distro forum how to run some kind of home made windows installer? Good luck finding answers here...
And it doesn't look legal to me neither, as the forum policy states, illegal activities are not to be explained here.

---

