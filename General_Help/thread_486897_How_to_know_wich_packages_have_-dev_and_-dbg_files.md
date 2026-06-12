---
title: "How to know wich packages have -dev and -dbg files"
date: 2007-06-28
forum: General Help
---

### Post by hecato on 2007-06-28
Hi people, I will like to know if there is a possible way to analyze which of the only the installed packages have -dev and -dbg files, and get a report and perhaps a way to download or some like that.

---

### Post by dreadlord_chris on 2007-06-28
> **hecato said:**
> Hi people, I will like to know if there is a possible way to analyze which of the only the installed packages have -dev and -dbg files, and get a report and perhaps a way to download or some like that.

If you use one of the GUI package managers - Synaptic or Adept - you'll be able to see right on the screen in front of you what the **dev**elopment and **deb**ug packages are...

---

### Post by hecato on 2007-06-28
I mean, I want to get a list of the packages actually installed that have -dev and -dbg is a little cumbersome searching them graphically, not all the installed packages have -dev or -dbg.


Tought a screenshoot would be nice.

---

### Post by stylishpants on 2007-06-30
I find your description unclear -- where do files and downloading come into it?

If what you want is a list of all currently installed packages whose names end in -debug or -dev, you could do this: 
```
dpkg -l | grep ^ii | awk '{print $2}' | egrep '\-(dev|debug)$'
```

If you want a list of all currently installed packages for which a -dev version of the package also exists, then you could do this:

```

# Generate a list of dev package names
# (some of these may already be installed)
# (this would probably take a while to run)
dpkg -l | grep ^ii | awk '{print $2}' | egrep -v '\-dev$' | while read p; do devpkg="$p-dev"; if apt-cache show $devpkg > /dev/null 2>&1; then echo $devpkg; fi; done  > packages.txt;

# install the found dev packages
cat packages.txt | while read p; do sudo aptitude install $p; done

```

It should be said that while this is possible, I can't see why you would want to do this and it probably will not help you in any way.

---

### Post by hecato on 2007-06-30
> If you want a list of all currently installed packages for which a -dev version of the package also exists, then you could do this:Yes this is what I want...

That is because some times when i compile something or in the configure step, I need to be checking the errors for see which thing isn't there, also when debugging (thought I'm not good at it) is nice to have the -dbg for see where the error is "more easily".

Havent checked it, but it only display the -dev files of the archives I have installed?? I mean

```
 package1 _____________________ **installed**
package1-dev _______________________ **not installed**
package2 ___________________________ **not installed**
package2-dev  ______________________ **not installed**
package2-dbg  ______________________ **not installed**
package3  __________________________ **installed**
package4  __________________________ **not installed**
package5  __________________________ **installed**
package5-dev  ______________________ **not installed**
package5-dgb  ______________________ **not installed**

```after the script

```
 package1  ____________________ **installed**
package1-dev _______________________ **installed**
package2  ___________________________ **not installed**
package2-dev  _______________________ **not installed**
package2-dbg  _______________________ **not installed**
package3  ___________________________ **installed**
package4  ___________________________ **not installed**
package5  ___________________________ **installed**
package5-dev  _______________________ **installed**
package5-dgb  _______________________ **installed**

```

---

