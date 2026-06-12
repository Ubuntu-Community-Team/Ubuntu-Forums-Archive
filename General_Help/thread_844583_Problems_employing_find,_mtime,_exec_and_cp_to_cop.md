---
title: "Problems employing find, mtime, exec and cp to copy files newer than a certain date"
date: 2008-06-29
forum: General Help
---

### Post by RudeIota on 2008-06-29
I have a directory with many sub directories, often nested several levels deep. I add files on a regular basis. I would like to copy files that are newer than 160 days and retain the directory structure on the new copy so I can share the newest ones with my family.

It sounds like a simple enough job to use find, mtime and cp for, but the issues I'm having caught me by surprise. :) I'm betting the answer is simple, so I'm hoping someone can improve my (or has a different) approach. 

Here are some things I've tried (path name is simplified)

[INDENT]_find /photos -mtime -160 -exec cp -r {} /newphotos \;_
The above didn't work because it includes the 'photos' directory itself in the output from 'find because its modified date is very recent. Because of this, it copies every single file in the directory. 

_find /photos/* -mtime -160 -exec cp -r {} /newphotos \;_
Although this avoided the parent 'photos' folder and copies the new files and directories, it makes a mess of the structure, copying nested directories and deeper files into the root of /newphotos

_find /photos/* -mtime -160 -type d -exec mkdir -p /newphotos{} \;_
_find /photos/* -mtime -160 -exec cp {} /newphotos{} \;_
This *almost* worked, but many of the files themselves are newer than the directories they are in. Since cp won't make directories, none of the newer files contained within a directory older than 160 days are copied.[/INDENT]

I've tried some other things too, but I'm really not sure how to approach this outside of a script. I feel like this should be doable in a line or two at the shell though. :\ 

Thanks for any ideas.

---

### Post by nick_h on 2008-06-29
I think you are almost there.  You could find all the files that are less the 160 days old and then call a script rather than use *cp* and *mkdir* directly in the *find* command.

```
find /photos -type f -mtime -160 -exec myscript.sh '{}' \;
```
This will give you more control.  The script could check that the destination directory exists and if not create it before copying the file.

My only other idea would be to use *find* to build a *tar* archive.
```
find /photos -type f -mtime -160 -exec tar rvf newphotos.tar '{}' \;
```

---

### Post by ghostdog74 on 2008-06-29
the GNU tar utility has some options you can try, like -N and -u. check the man page for more.

---

### Post by RudeIota on 2008-06-30
I didn't have the will or focus to come up with a more elegant method, but here's the (sloppy) method I used, thanks to your inspiration:

# First, I tarballed all of stuff I wanted from /photos to photos.tar.
tar -cvf /photos.tar /photos/* --newer-mtime "2008-01-01"

***This is probably my fault, but the tarball contained the *entire* /photos directory hierarchy; however, it copied *only* the files I wanted - the ones modified after the first of the year. Progress!*

# Second, I extracted the tarball into the /newphotos directory
tar -xzvf /photos.tar /newphotos/

# Finally, I removed all of the empty directories.
sudo find /newphotos -type d -print0 | xargs -0 rmdir --ignore-fail-on-non-empty --parents


So, this method isn't very good because it required twice the free space and took some time to process. But it DID get the job done, so that works for now. :) 

I think ultimately I'd have to write a (short) script to achieve what I wanted to do in a straight forward fashion. I can't really see how it would  be possible using bash commands without conditions or a utility.

---

### Post by nick_h on 2008-06-30
> I think ultimately I'd have to write a (short) script to achieve what I wanted to do in a straight forward fashion.

You could go back to my first idea and use the following script:
```
#!/bin/bash

# $1 = file
# $2 = source directory
# $3 = destination directory

FILE=`basename "$1"`
SRC_DIR=`dirname "$1"`
DEST_DIR=`echo "$SRC_DIR" | sed "s#$2#$3#"`

if ! [ -d "$DEST_DIR" ]; then
    mkdir -p "$DEST_DIR"
fi

cp "$1" "${DEST_DIR}/${FILE}"
```

Then call it with:
```
find /photos -type f -mtime -160 -exec myscript.sh '{}' '/photos' '/newphotos' \;
```

---

### Post by soldersplash on 2008-08-27
Thanks nick_h, I have just used a slightly modified version of your script to copy all foo.flac files from my mixed mp3/m4p/m4a/flac music library to my iPod whilst retaining the folder structure of the original library (which suites RockBox). 
:guitar:

```
#!/bin/bash

# $1 = file
# $2 = source directory
# $3 = destination directory

FILE=`basename "$1"`
SRC_DIR=`dirname "$1"`
DEST_DIR=`echo "$SRC_DIR" | sed "s#$2#$3#"`

if ! [ -d "$DEST_DIR" ]; then
    mkdir -p "$DEST_DIR"
fi

cp -v "$1" "${DEST_DIR}/${FILE}"
```

(just added -v option to cp so I get verbose output.)

```
find /music -type f -name *.flac -exec myscript.sh '{}' '/music' '/media/ipod' \;
```

(changed search for file oder than ** to file with ext .flac)

---

