---
title: "[SOLVED] A way to use shred to securely delete FOLDERS"
date: 2014-08-07
forum: General Help
---

### Post by pine508 on 2014-08-07
Here's my (way-suboptimal) situation:


[LIST]
[*]I need to securely delete ~10 GB of files that are in folders.  (Overwriting once with zeroes would be sufficient) 
[*]Everything that needs to be deleted is organized under one big "delete this" folder. 
[*]My Ubuntu install is messed up such that **I can't apt-get or install anything.**  (So, no, I can't install secure-delete) 
[*]I have shred on there, but I only know how to use it for files, not folders. 
[*]I am supposed to have this done in 2.5 hours. (!) 
[/LIST]

So, is there a way I could write some script or something that COULD use shred to do this?

Or is there some other way I could (fairly) securely delete all this stuff fast?

Thanks!
_________________________________________

** EDIT:**  OK, found a solution that worked for me:

**[FONT=courier new]find <directory> -depth -type f -exec shred -v -n 1 -z -u {} \;[/FONT]**

(Found on this answer: [http://unix.stackexchange.com/a/117848](http://unix.stackexchange.com/a/117848) )

10 GB took a while (this was doing one random pass and one pass with zeroes).. (> 30 min?), but it seemed to do the trick.  The computer is returned.

Thanks again!

---

### Post by Rob Sayer on 2014-08-07
[COLOR=#444444][FONT=Arial]I think if you opened the terminal and then navigated to your "delete this" folder and ran shred it should work.  Be careful, and here's a wee guide ...

[/FONT][/COLOR]http://askubuntu.com/questions/57572/how-to-delete-files-in-secure-manner[COLOR=#444444][FONT=Arial]

I think the fact you can't install anything is probably more serious.  You should start another thread on the subject and post the output of this from terminal:

```
sudo apt-get -f install[/FONT][/COLOR][COLOR=#444444][FONT=Arial]
```

wrapped in [CODE] tags.  This command will try and fix broken packages.[/FONT][/COLOR]

---

### Post by pine508 on 2014-08-07
Thanks. I found a solution online that worked for my needs (and edited my post to reflect that). 

As far as the install issues go, I've returned this computer now so it is a moot point.  (It was a WUBI install of Ubuntu 10.04 anyway, so if I dabble with Ubuntu in the future, I'll start from a regular install of the latest version and hope to have better luck with it...I think WUBI never quite worked well enough and that's why it is not an option any longer).

---

