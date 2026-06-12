---
title: "Where does wget download files to?"
date: 2007-04-03
forum: General Help
---

### Post by 67GTA on 2007-04-03
I am going to try to install Lacie lightscribe for my new cd/dvd writer. I was using instructions that used wget to get the two files needed. Where is the default location that wget downloads to? Can I tell it which directory to use?

---

### Post by kerry_s on 2007-04-03
It puts it in your home folder.
settings are in /etc/wgetrc, you need root privaleges to modify( gksu gedit /etc/wgetrc )

---

### Post by aysiu on 2007-04-03
Actually, I think *wget* downloads to whatever directory you're in, not necessarily your home folder.

---

### Post by bashologist on 2007-04-03
The -O option maybe? Wget saves files to the working directory by default.
[QUOTE=man wget]       -O file
       --output-document=file
           The documents will not be written to the appropriate files, but all will be concatenated together and written to file.  If - is used as file,
           documents will be printed to standard output, disabling link conversion.  (Use ./- to print to a file literally named -.)

           Note that a combination with -k is only well-defined for downloading a single document.[/QUOTE]
Example saving to home directory:```
wget [http://ubuntuforums.org/imagesorig/ub2/ubuntulogo.png](http://ubuntuforums.org/imagesorig/ub2/ubuntulogo.png) -O ~/logo.png
```

---

### Post by 67GTA on 2007-04-03
I downloaded the first file while in my desktop dir and it put it there. Just for kicks I ran wget for the second file without specifying a dir and it went to my /home dir. I am guessing that is for security reasons. Thanks for the info. Now I get to play with my new lightscriber.

---

### Post by enchance on 2007-12-05
> **bashologist said:**
> 
Example saving to home directory:```
wget [http://ubuntuforums.org/imagesorig/ub2/ubuntulogo.png](http://ubuntuforums.org/imagesorig/ub2/ubuntulogo.png) -O ~/logo.png
```
What if I want to download a whole site instead of just a single file? Do I go
```
$ wget -r http://ubuntuforums.org/ -o ~/sitefolder/
```
Is this the right way to do it?

---

