---
title: "bashscript help"
date: 2007-12-05
forum: General Help
---

### Post by enchance on 2007-12-05
I got this bash script which downloads images from xkcd.com. It works great but the files aren't downloaded in the order they were presented and instead come out alphabetically in nautilus since there aren't any numbers signifying their order. 

I've never done bash scripting so I can't edit it myself, can anyone check this out and see how to add numbers before the actual file name? Script goes like so
```
#!/bin/bash

for i in `seq 1 352`
do
	wget http://xkcd.com/$i/
	wget `grep http://imgs.xkcd.com/comics/ index.html | head -1 | cut -d\" -f2`
	rm index.html
done
```

---

### Post by cmnorton on 2007-12-05
I don't think you can get there from here, at least not directly, and you will probably need to edit a bash script.

Your iteration number is contained in $i. If you started in a clean directory, and then did a listing for the file that was downloaded, you could probably assign a number to each picture that way. 

DOWNLOADED_FILE=`ls *.jpg`

mv ${DOWNLOADED_FILE} ../a_new_directory/$i_${DOWNLOADED_FILE}
rm index.html

I believe wget is iterating the default page of this web site -- index.html --  to see what pictures are there and then downloading them for you. Look at the documentation for wget and see what else it does. Maybe you can assign a unique file name on the fetch.

---

### Post by Nameless_one on 2007-12-05
There is no need for a bash script. Try to download [this page](http://xkcd.com/archive/) and all its links, and the images will be placed in folders named with the corresponding number, and you will have a nice index for them (and get to keep the hover text). Just read ```
$ man wget
```.

---

### Post by enchance on 2007-12-05
> **cmnorton said:**
> I don't think you can get there from here, at least not directly, and you will probably need to edit a bash script.

Actually, all the webpages are named like this: **xkcd.com/1**, **xkcd.com/2** all the way to **xkcd.com/n**, "n" being the last number. Is it possible instead to name the file with the folder name (1, 2, etc...) then append the filename and extension at the end? That way they would be listed in nautilus in the right order instead of alphabetically.

---

