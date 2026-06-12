---
title: "batch script for ubuntu and debian: command for files in (sub)directorys"
date: 2013-02-24
forum: General Help
---

### Post by il pepe on 2013-02-24
Hi,
My picture data base is ordered as follows: year/month/event

These pictures are quiet large and not easily streamable.

The idea is the next:
I want to keep my database intact.
I want to copy the database, and resize all pictures in this database so that they become streamable. ImageMagick has the command.

Problem statement:
First:
I want to keep the file structure of my original database. I just want to change the top level folder name (e.g. pictures in the original database) to /name_resized/ (e.g. pictures_resized). The rest of the folder structure I would like to keep intact (so /year/month/event) in the new database.
I already started with this:
```

#!/bin/bash

for d in * .[!.]* ..?*; 
    do
    test -d "${d}"; echo ${d}
     
    
    done
```But it doesn't print only the folders, but everything that is in the original folder. I don't know why...

Second (but minor):
I would like that the script works on ubuntu and debian. Is writing in bash clever then?

---

### Post by sudodus on 2013-02-24
Yes, bash will work in ubuntu and debian :-)

-Append _resized to the name of the copy and save it in the same subdirectory as its original picture

- Afterwards use rsync to copy the whole directory tree but only the resized copies

```
"*_resized*"
```

The manual for rsync is well written and contains several examples ```
man rsync
``` for example something like this example

```
rsync -avmn --include="*_resized*" --include="*/" --exclude="*" /source-dir-path**[COLOR="Red"]/[/COLOR]** /target-dir-path
```

---

### Post by Kansasguy on 2013-02-25
Hi, I might be totally off base here, but I had a problem in that I had over 7000 pictures that I took with a camera that started the numbering over each time I downloaded the pictures (DSCF0001, DSCF0002, etc). When transfering pictures from one file to another, they would overwrite, and I could lose the older picture.  I solved the problem when I learned to use the program IrfanView, and learned to batch renumber.  I believe they have a batch resize.

   Like I said, I may be off base and out of my league, but you might want to copy your database and give it a try.  If you need help with the learning curve, get back to me.

---

### Post by lmarmisa on 2013-02-25
I recommend to use a language like python for your script. bash is quite good script language but python could be more advisable for non-trivial programs.  

I think that ImageMagick is a good choice with many options availabe.

---

### Post by schragge on 2013-02-25
> **il pepe said:**
> But it doesn't print only the folders, but everything that is in the original folder. I don't know why...Because this
```
test -d "${d}"[color=red];[/color] echo ${d}
``` should be
```
test -d "${d}" [color=red]&&[/color] echo ${d}
```

And yes, if you don't mind having a trailing slash attached to each directory name, the same could be achieved with
```

#!/bin/bash
shopt -s nullglob
printf "%s\n" */ .[!.]*/ ..?*/

```

---

### Post by prodigy_ on 2013-02-25
> **lmarmisa said:**
> I recommend to use a language like python for your script. bash is quite good script language but python could be more advisable for non-trivial programs.  

I think that ImageMagick is a good choice with many options availabe.

+1

Basically (not thoroughly tested but seems to work):

```
#!/urs/bin/env python

import os
import errno
from wand.image import Image
from wand.exceptions import MissingDelegateError


# User defined vars
source_folder = "/path/to/source" # replace with actual path
target_folder = "/path/to/target" # replace with actual path
width_height = "500x600" # max widthXheight after resize, aspect ratio is preserved


try:
    os.makedirs(target_folder)
except OSError as exc:
    if exc.errno == errno.EEXIST and os.path.isdir(target_folder):
        pass
    else: raise

for root, folders, files in os.walk(source_folder):
    for file_name in files:
        file_path = os.path.join(root, file_name)
        try:
            with Image(filename=file_path) as img:
                with img.clone() as img_clone:
                    img_clone.transform(resize=width_height)
                    img_clone.save(filename="{0}/{1}".format(target_folder,
                                                             file_name))
        except MissingDelegateError:
            continue
```

Execution:
```
sudo apt-get install imagemagick pypy python-stdeb
sudo easy_install wand
python /path/to/script # replace with actual path and script name
```

---

### Post by Vaphell on 2013-02-25
if you don't mind huge copy why don't you simply
1. copy everything recursively
2. rename the root dir
3. proceed to process copied files in place with imagemagick?

if you do mind wasteful copy you can easily recreate the dir structure with something like this

```
#!/bin/bash

src="$PWD"
dest="/some/dir"
while read -rd $'\0' d
do
  *echo* mkdir -p "$dest/${d#$src/}"
done < <( find "$src" -type d -print0 )
```
and then generate output file paths in similar way

```
while read -rd $'\0' f
do
  *echo* imgmagicwhatever -input "$f" -output "$dest/${f#$src/}"
done < <( find "$src" -type f -print0 )
```

---

