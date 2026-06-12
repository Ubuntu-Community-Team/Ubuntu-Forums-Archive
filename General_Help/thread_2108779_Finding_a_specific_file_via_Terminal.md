---
title: "Finding a specific file via Terminal"
date: 2013-01-25
forum: General Help
---

### Post by slooksterpsv on 2013-01-25
All,

I had a question, I was able to do this today, but I was wondering if there's an easier way to do this via terminal.

I was looking for a Gimp file I had worked on some time ago and couldn't remember what folder I had put it in. So I ran an ls -R | grep .xcf to find the gimp file, but that didn't give me the full working directory.

I then tried to use find (which is what worked) on the directory where I had limited it down to being:

find | grep shattered

Is there a way I could have used find to find the file in the first place giving me the full directory path instead of having it go through countless folders in the root of my home folder to find the file. ls -R | grep xcf gave me an idea of where it was at due to the other files that were grouped together that I knew were in the pictures folder.

I'm new with find specifically, but I don't mind using it as I have a general area of where it's located. I just feel I can use it more efficiently in my searches.

Thanks,



Slook

---

### Post by Double.J on 2013-01-25
Hi there, I think [this resource]("http://http://content.hccfl.edu/pollock/unix/findcmd.htm") will help. 

Limiting the search to just the directory should just be a case of 
```
 
Find /[COLOR="Red"]path\ to\ chosen\ directory[/COLOR] -name [COLOR="Blue"]name.of.file[/COLOR]
```

Hope it helps! 

Personally I find the 

```
 mtime 0 
``` argument very useful for finding files, particularly documents, test files and images that I forgot where I put them as it only includes files modified in the last day .. Not helpful here, but I do use it a fair bit!

Edit: don't forget, if you're sure it's in the directory you're in, no need to specify a directory as it defaults to your current location not /

---

### Post by Habitual on 2013-01-25
```
find `pwd`~ -iname "*.xcf" -type f
```

---

### Post by andrew.46 on 2013-01-25
There is a *find* resource a little closer to home:

[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

A quick read should show the way...

---

