---
title: "apt-get update errors in hardy 64-bit"
date: 2008-05-17
forum: General Help
---

### Post by jniebles on 2008-05-17
Hi all,

When I do an 
```

me@my_machine$ apt-get update

```

I get the following error
```

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/Release  Unable to find expected entry  main/debian-installer/source/Sources in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```


I tried this
```

me@my_machine$ sudo apt-get -f clean
me@my_machine$ sudo apt-get update

```

and still get the same error.

Then I tried cleaning up my sources.list file, that is, I erased "all contents" in sources.list. I was hoping that running the apt-get update would produce no errors, but instead, got the following:

```

me@my_machine$ sudo apt-get -f clean
me@my_machine$ sudo apt-get update
Hit http://us.archive.ubuntu.com hardy-backports Release.gpg
Hit http://us.archive.ubuntu.com hardy-backports Release
Hit http://us.archive.ubuntu.com hardy-backports/main/debian-installer Packages
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/Release  Unable to find expected entry  main/debian-installer/source/Sources in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Does anyone have any clue of what is going on here? Apparently, the 'backports' repo is sticked somewhere. Is there any other file, or maybe a cache where apt-get is taking this info from?

I'm running Hardy 64 bits.

Thanks!

---

### Post by ibuclaw on 2008-05-17
check your sources.list file.

```
gksu gedit /etc/apt/sources.list
```

Find the lines with "hardy-backports" on:
Make sure that it looks like this:

[PHP]
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
[/PHP]

Regards
Iain

---

### Post by jniebles on 2008-05-17
Hi,

I tried that before posting, without luck.
I have in fact erased all contents in my sources.list file. So there are no lines referring to the 'backports'.

Any other thoughts?

thanks

---

### Post by ibuclaw on 2008-05-17
```

cd /etc/apt
ls -1

```

Follow the blue directories with the word "source" in them.
And read the files that are contained within them.

See where it might lead you!

[EDIT]
If your still stuck.
Try:
```
cd /var/lib/apt/lists
```
And remove all files with the word "hardy-backports" in their filename.


Regards
Iain

---

### Post by jniebles on 2008-05-17
hi,

the file /etc/apt/sources.list.d/prerequists-sources.list had pointers to the backports repo. I commented out this lines, and finally got my problem solved.

I had in fact cleaned up /var/lib/apt/lists before my first posting, so I am not sure if I had to do this by hand or not to get my problem fixed.

Thanks!

---

