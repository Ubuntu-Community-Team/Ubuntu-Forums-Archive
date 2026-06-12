---
title: "Cping off of a RW"
date: 2008-02-01
forum: General Help
---

### Post by deltaandroid on 2008-02-01
Hello, I recently set up an Ubuntu PC as a media center device. videos and the like.

That computer doesn't have an internet connection, so I download media on my main PC then copy it over using DVDRW's or my ipod, however, last night when I burned some videos, I tried to copy them over. It gave me a read error on the second (out of 3) file, and so I hit retry, as I did I noticed the total transfered MB's increased after I pressed retry, so after I hit retry a few times, it the gave no more errors and copied over fine.

The third file is more stubborn, as  I keep hitting retry, and while it increases the total transfered, it still kept error'ing.

So I am writing a bash script, to copy over media, and since it mainly uses the "cp" command, I looked in the help and couldn't find an "ignore errors" extension for it. I would like to know if one exists, and if at all possible I would like to do it with a built in command, or else I have to carry my pc upstairs, download the stuff and etc.

It is running 6.06 LTS btw and here is my script:

#!/bin/bash
cd /media/cdrom*
cp *.avi /home/owner/Desktop/Movies
cp *.jpg *.jpeg /home/owner

---

### Post by Nycticorax on 2008-02-01
I'm not sure if I understood, but do you want a script that goes through a bunch of files and tries to copy each one, moving on to the next if it has a problem? If so, how about using a for loop:

(You might have to change /media/cdrom to the correct name)

```
#!/bin/bash

for file in /media/cdrom/*.avi ; do
cp $file /home/owner/Desktop/Movies/ || echo failed to copy $file error code $?
done

for file in /media/cdrom/*.jpg /media/cdrom/*.jpeg ; do
cp $file /home/owner || echo failed to copy $file error code $?
done
```

p.s. The first line of your script is
```
cd /media/cdrom*

```
but if there are multiple mountpoints in /media that match /media/cdrom*
(e.g. /media/cdrom0, /media/cdrom1) then it will just cd into the first one and ignore the others. Why do you need the *?

---

