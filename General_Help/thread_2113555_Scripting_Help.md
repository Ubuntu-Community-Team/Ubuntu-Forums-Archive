---
title: "Scripting Help"
date: 2013-02-07
forum: General Help
---

### Post by doppel.ganger on 2013-02-07
Hey all,
I need help writing a simple bash script that will archive a few folders, rename the archive with the date, and move that archive to my DropBox folder. So, I'm pretty much asking you to write the script for me. :P

Thanks,
Thomas

---

### Post by Habitual on 2013-02-08
That's not "help" IMO.
That's work.

I get paid for work.

---

### Post by Stonecold1995 on 2013-02-08
> **doppel.ganger said:**
> Hey all,
I need help writing a simple bash script that will archive a few folders, rename the archive with the date, and move that archive to my DropBox folder. So, I'm pretty much asking you to write the script for me. :P

Thanks,
Thomas

You'll probably have more luck if you try to make the script yourself, and then come here and ask for help if you're having any problems.

---

### Post by Impavidus on 2013-02-09
Start your script with **#!**, use **date** to get the date in a string, use **tar** or any other archiver to create the archive and then move it to wherever you want.

---

### Post by CaptainMark on 2013-02-09
try this```
#!/bin/bash
for j in $jobs; do
    if [ $effort -gt $laziness ]; then
        wget "http://someone/else/to/do/it.com"
    else
        echo "$j cancelled"
        exit
    fi
done
```

---

### Post by prodigy_ on 2013-02-09
```
#!/bin/bash
shopt -s dotglob # to match filenames starting with "."

cur_date="$(date +%F)"

tar -cvjf "${cur_date}.tar.bz2" "/path/to/source_folder1" "/path/to/source_folder2" # etc., replace with actual paths and folder names
mv "${cur_date}.tar.bz2" "/path/to/dropbox_folder" # replace with actual path and folder name
```

---

### Post by Stonecold1995 on 2013-02-10
> **CaptainMark said:**
> try this```
#!/bin/bash
for j in $jobs; do
    if [ $effort -gt $laziness ]; then
        wget "http://someone/else/to/do/it.com"
    else
        echo "$j cancelled"
        exit
    fi
done
```
:lol:

---

