---
title: "Vivaldi/package mgr update fail"
date: 2017-04-27
forum: General Help
---

### Post by kithrup on 2017-04-27
Using Vivaldi, on Ubuntu 16.04.2, Gnome compiz flashback. Getting this message after latest update, wonder if anyone else has this. 

E: Malformed line 3 in source list /etc/apt/sources.list.d/vivaldi.list (type)
E: the list of sources could not be read.

Keep getting nags about it, otherwise I probably wouldn't notice, much less be bothered to do anything about it. 

Thanks for looking.

ETA: some packages may have unmet dependencies message also, but not specific enough for me to figure out...

---

### Post by Xian on 2017-04-27
Can you show us the output of:

```
$ cat -n /etc/apt/sources.list.d/vivaldi.list
```

---

### Post by kithrup on 2017-04-27
Please excuse my ignorance; $: command not found

?

eliminate the $ ?

   1	### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2	# You may comment out this entry, but any other modifications may be lost.
$

---

### Post by howefield on 2017-04-28
The file should look like this..

```
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://repo.vivaldi.com/stable/deb/ stable main
```

So if you do..

```
sudo nano /etc/apt/sources.list.d/vivaldi.list
```

you'll can change to make it so...

That is using the nano text editor but if you are more comfortable with a gui text editor you can also use gedit..

```
sudo -H gedit /etc/apt/sources.list.d/vivaldi.list
```

---

### Post by kithrup on 2017-04-30
Marked as solved, problem seems to have resolved itself actually, that is, at least the nag disappeared.


Thanks for the helpful hints, anyway, folks.

---

