---
title: "Listing recently installed packages"
date: 2007-06-24
forum: General Help
---

### Post by doctapeppa on 2007-06-24
Hello. I'm running Ubuntu server 7.04 on a box in a closet. It is lots of fun and has been a great learning experience. 

How do I get a list of recently installed packages? Better yet, is there a way to list all packages installed and sort them by date?  I have used aptitude and it is a very nice program, but I cann't find a way to find recently installed packages that i do not remember names to.  I have a installed quite a few things recently trying out this and that and now I wish to find them and remove them because I'm not using them.

doctapeppa

---

### Post by r0ck80y on 2007-06-24
In console, type:```

aptitude search ~i 
```
Or send the output to a file by:
```
aptitude search ~i > file
```

---

### Post by doctapeppa on 2007-06-24
Awesome! 

Now, is there a way to sort that by install date/time? The default shows them in alphabetical order.

---

### Post by r0ck80y on 2007-06-24
Not sure how that is done by aptitude. But the /var/lib/dpkg/status file stores the package names (and other details) in the order that they have been installed. Again the date/time of installation is not listed here. Hope this file suffices your inquiry till then. I'll try to find out how the sorting is done.

---

### Post by hfw on 2007-06-26
I was just getting ready to post this question, glad to see it had already been answered.   Wondering if anybody had figured out how to list by install date.  I did 

man aptitude

and it says that you can add sort order to your search parameters, but I couldn't figure out how to get it to sort by install date.

Also I was curious about the option to create a file.  I assume it just creates a text file?

Thanks,
Hal

---

### Post by stylishpants on 2007-06-27
This is the best approximation I've found:

```
ls -lrt /var/lib/dpkg/info/*.list
```

It appears that every time you install or upgrade a package, a file named <packagename>.list is created in this directory or has its timestamp updated if it already exists.

If you delete a package, the file is not removed, it just has its timestamp updated again.  The file only gets deleted if you remove the package using the --purge option (apt-get --purge remove <packagename>)

---

### Post by MasterAslan on 2008-02-03
Thanks so much...just saved me doing a clean install

---

### Post by TyrosCenva on 2008-02-06
Okay, I got a little carried away here and came up with a big one-liner:
```

echo -e "State     \tLast change \t \tName" > PkgLog && ls -lsrt /var/lib/dpkg/info/*.list | awk '{print $6"\t"$7"  "$8"\t"$9}' | sed -e "s/\/var\/lib\/dpkg\/info\///" -e "s/.list//" -e "s/^0\t/Removed \t/" -e "s/^[0-9]*\t/Installed\t/" >> PkgLog
```
Put this into the command line and you'll get a file called "PkgLog".
This file contains a list with the current package state (either installed or removed), the date and time the package state was last changed, and the package name itself.
Beware that the date will most likely change with package updates too.

It's probably not the most efficient piece of code, but it gets the job done :)

Enjoy.

---

### Post by disturbedite on 2008-02-06
synaptic is a much better package manager imo, i use it on kubuntu.  it has a history that is prolly exactly what you're looking for.  just go to "File --> History" & every operation is listed by date.

---

### Post by DrMega on 2008-02-06
Just expanding on this, I guess if you did this periodically, and used one of the many text file compare tools, you could identify what's changed between dates to some extent, which might come in useful if you have Synaptic frenzy and manage to bust your setup.

---

