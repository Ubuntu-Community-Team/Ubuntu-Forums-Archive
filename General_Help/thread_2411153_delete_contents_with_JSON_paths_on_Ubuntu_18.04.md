---
title: "delete contents with JSON paths on Ubuntu 18.04"
date: 2019-01-25
forum: General Help
---

### Post by idkwhatimdoing1.0 on 2019-01-25
Hi, I have an external hard drive full of pictures. Basically I ran lots of scans on it and I copied the JSON format of all the paths of the duplicated pictures. So now I have a JSON file with paths and photo id and stuff like that. I was wondering if there was a Linux command or function to completely delete the pictures to the path? I was wondering if there was something like rm -filepath Links.JSON? Something like that. Thank you

---

### Post by TheFu on 2019-01-25
json is just text.  Text processing tools are part of all Unix-like OSes.  grep, cut, sed, head, tail, awk, perl, python are the basic tools to be used. These mostly use the regex language, so mastering that is important.

So, depending on the actual pattern for the text you want (the list of files), it can be really easy to get just the lines you care about, then remove everything to the left of the file-path and everything to the right of the file-path.

Many of these can be accomplished in 1 line of awk or perl.

---

### Post by idkwhatimdoing1.0 on 2019-01-28
oh that is perfect then. Thank you so much

---

