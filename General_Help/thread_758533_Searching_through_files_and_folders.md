---
title: "Searching through files and folders"
date: 2008-04-18
forum: General Help
---

### Post by stomm on 2008-04-18
Hi, I'm running Ubuntu 7.10 and I'm new to Linux overall.

I have a selection of files in a folder that are separated by region (E), (US) and (JP).
I've used the search function to search for files that have (JP) in the title but it doesn't seem to bring any results.

Basically there are around 1000 files in each folder, i'd like to be able to delete just the (JP) files.

i.e.

Document 1 (JP).doc
Document 1 (E).doc
Document 55 (US).doc

Please could someone recommend a program to use or the proper syntax of how to just delete those particular files. 

Thanks very much

---

### Post by kpkeerthi on 2008-04-18
First run this command and make sure it is finding the right files
```

find /path/to/search -name "*(JP).doc"

```

When you are sure, run this command
```

find /path/to/search -name "*(JP).doc" -exec rm '{}' ';'

```

Replace /path/to/search to the actual path to the folder where you want the search to begin. (Could be your home directory)

---

### Post by jeffus_il on 2008-04-18
This should do it for you in the current directory and below:
```
find -name "*JP*" -exec rm \{\} \;
```

First test the find to see that it is selecting what you intended using:
```
find -name "*JP*"
```

then afterwards execute the full command, the rm acts on the output of the "find".

---

### Post by stomm on 2008-04-20
Thanks to you both for your help, the files in question are on another partition on another drive though so I can't seem to get to the folder to find the files lol. Please could you tell me how to access the drive using the terminal first - i'm used to using DOS but this is a whole new territory for me.

---

### Post by happyhamster on 2008-04-20
- When the partition is mounted, is there an icon for it on your desktop? In that case, you can right-click that icon and choose Properties-->Volume. It will show where the disk is mounted (for example at /media/disk).

- Or from a terminal, type: 

mount

- to see where everything is mounted at. BTW, an easy way of navigating a terminal (when using regular Ubuntu, meaning the one with the nautilus file browser) is installing the package "nautilus-open-terminal" which allows you to right-click a folder and start a terminal from there. To install:

sudo apt-get install nautilus-open-terminal

- And to let it take effect, you'll probably have to restart nautilus (close all nautilus windows). If that doesn't help, just issue:

killall nautilus

- And you should be good to go. Good luck.

---

### Post by stomm on 2008-04-20
> **happyhamster said:**
> - When the partition is mounted, is there an icon for it on your desktop? In that case, you can right-click that icon and choose Properties-->Volume. It will show where the disk is mounted (for example at /media/disk).

- Or from a terminal, type: 

mount

- to see where everything is mounted at. BTW, an easy way of navigating a terminal (when using regular Ubuntu, meaning the one with the nautilus file browser) is installing the package "nautilus-open-terminal" which allows you to right-click a folder and start a terminal from there. To install:

sudo apt-get install nautilus-open-terminal

- And to let it take effect, you'll probably have to restart nautilus (close all nautilus windows). If that doesn't help, just issue:

killall nautilus

- And you should be good to go. Good luck.

That did the trick thanks, the search button seems to be weird on my machine and just comes up blank or with results that are nothing to do with what I put in.

The terminal commands worked perfectly once nautlius opened the terminal in the window.

Thanks to everyone, I've freed up about 25gb now :)

---

