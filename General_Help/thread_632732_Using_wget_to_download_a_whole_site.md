---
title: "Using wget to download a whole site"
date: 2007-12-05
forum: General Help
---

### Post by enchance on 2007-12-05
How do I download a whole site using wget and have it saved to a specific folder on my desktop for offline viewing? I'm looking at only getting the files/links within the domain and not those going out. Does anyone know this?

---

### Post by Matt Yun on 2007-12-05
You have to use the recursive options for wget.

I usually do: **wget -r -p -l 2 [http://website.com](http://website.com)**

-r = wget recursively
-p = download all files (incl. images) necessary to render the html pages
-l 2 = descend maximum 2 levels (default is 5)

Another useful option is "-np" or "--no-parent".  This will prevent wget from ascending to the parent directory, such as when you want to download [http://website.com/subdirectory](http://website.com/subdirectory), but not everything on [http://website.com](http://website.com)

Look at the man page ('man wget') for more info.

---

### Post by BLTicklemonster on 2007-12-05
[http://linuxreviews.org/quicktips/wget/](http://linuxreviews.org/quicktips/wget/)

---

### Post by Brindled on 2007-12-05
where exactly does this save the website?


edit: nevermind, i found it in my home/username folder.

---

### Post by enchance on 2007-12-06
> **Matt Yun said:**
> You have to use the recursive options for wget.

I usually do: **wget -r -p -l 2 [http://website.com](http://website.com)**

-r = wget recursively
-p = download all files (incl. images) necessary to render the html pages
-l 2 = descend maximum 2 levels (default is 5)

Another useful option is "-np" or "--no-parent".  This will prevent wget from ascending to the parent directory, such as when you want to download [http://website.com/subdirectory](http://website.com/subdirectory), but not everything on [http://website.com](http://website.com)

Look at the man page ('man wget') for more info.

How do I specify which folder it should download the files to?

---

### Post by FakeOutdoorsman on 2007-12-07
I usually just do a wget mirror:
```
wget -m http://website.com
```

It will then create a folder "website.com" in your current directory.

---

### Post by enchance on 2007-12-07
> **FakeOutdoorsman said:**
> I usually just do a wget mirror:
```
wget -m http://website.com
```

It will then create a folder "website.com" in your current directory.
What happens if it's a mirror? I used
```
wget -r -p -U Mozilla http://www.site.com/
``` Is this different from "-m" ?

---

### Post by FakeOutdoorsman on 2007-12-07
> **enchance said:**
> What happens if it's a mirror? I used
```
wget -r -p -U Mozilla http://www.site.com/
``` Is this different from "-m" ?

From **man wget**:
[I]-m or --mirror
Turn on options suitable for mirroring [a web site].  This option turns on recursion and time-stamping, sets infinite recursion depth and keeps FTP directory listings.  It is currently equivalent to -r -N -l inf --no-remove-listing.[/I]

Some differences between using -m and what you use:
-m doesn't use -U so "wget" is passed as the user agent instead of "Mozilla".
-m will check timestamps of the files and only download what is new (if you've mirrored the site before with -m)
-m uses -l inf with -r, so will handle an infinite level of folders, while your version just uses -r which has a default 5 levels of recursion (it will download up to five levels of folders).

You can use **man wget** or **wget --help** for more details on those options.

---

### Post by enchance on 2007-12-08
> **FakeOutdoorsman said:**
> From **man wget**:
[I]-m or --mirror
Turn on options suitable for mirroring [a web site].  This option turns on recursion and time-stamping, sets infinite recursion depth and keeps FTP directory listings.  It is currently equivalent to -r -N -l inf --no-remove-listing.[/I]

Some differences between using -m and what you use:
-m doesn't use -U so "wget" is passed as the user agent instead of "Mozilla".
-m will check timestamps of the files and only download what is new (if you've mirrored the site before with -m)
-m uses -l inf with -r, so will handle an infinite level of folders, while your version just uses -r which has a default 5 levels of recursion (it will download up to five levels of folders).

You can use **man wget** or **wget --help** for more details on those options.
So it is better since it can find out which file to download and which to not! I guess I'll use this next time. You *do* suggest it right? I mean, other than the one I used...

Any chance I can also target a folder where it would be saved?

---

### Post by oliv66 on 2007-12-19
Hi all,

I tried all the described options 

wget -r -p -l5 ftp.myname.com

I gather all the folders but inside those folders, i have just  an index.html file (i.e ;  just a link to get the files but not the files themselves.)

Why ? What could I do more ?

I tried with -E -m and so on.

Thanks for your help.

Olivier

---

