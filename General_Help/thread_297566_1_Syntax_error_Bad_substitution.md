---
title: "1: Syntax error: Bad substitution"
date: 2006-11-11
forum: General Help
---

### Post by jasplund on 2006-11-11
I have a script for transferring images from my camera to my harddrive and changing folder name rotatint images and so on. It worked great in dapper but when I try to execute it in edgy I get 1: Syntax error: Bad substitution

Why is that? what should I do?

```
DU="/usr/bin/du"

SRC="/media/usbdisk/DCIM"
DEST="/home/johan/Bilder/2006"

if [ -x /usr/bin/jhead ]
then
  ROTATE=TRUE
else
  ROTATE=FALSE
  echo "Hittar inte /usr/bin/jhead"
fi

if [ ! -d "$SRC" ]
then
  echo "$SRC finns inte!"
  exit
elif [ ! -d "$DEST" ]
then
  echo "$DEST finns inte!"
  exit
fi

cd $SRC
for i in *
do
  if [ -d $i ]
  then

    NEWDIR=`echo ${DEST}/0${i:3}`
    if [ ! -d "$NEWDIR" ]
    then
      mkdir "$NEWDIR"
    fi

    DS=`$DU $i | awk '{print $1}'`
    if [ "$DS" -gt 0 ]
    then
      # cp -v $i/* "$NEWDIR"
      mv $i/* "$NEWDIR"
    fi

    cd $NEWDIR
    for j in *.JPE
    do
      FN=`basename $j .JPE`
      NEWFN="$FN.JPG"
      mv $j $NEWFN
      rm -f $FN.THM
    done
    if [ $ROTATE=TRUE ]
    then
      /usr/bin/jhead -autorot *.*
    fi
    cd $SRC

    rmdir $i
  fi

done
```

---

### Post by DaveBorealis on 2006-11-11
Hello,
Did you check to see if any of the paths changed?
Dave

---

### Post by jasplund on 2006-11-11
Thanks, but yes that was the first thing and nothing has changed

---

### Post by kidders on 2006-11-11
Yeah, that might be what happened... I wonder if some unescaped special characters are turning up in **awk '{print $1}'**. Something about your environment has changed that has uncovered a flaw in the script :-(

---

### Post by jasplund on 2006-11-11
> **kidders said:**
> Yeah, that might be what happened... I wonder if some unescaped special characters are turning up in **awk '{print $1}'**. Something about your environment has changed that has uncovered a flaw in the script :-(

ok any suggests on how to change the script? I'm not very good at these things and someone made the script for me

---

### Post by kidders on 2006-11-11
Hi there,

I'm no expert, but since you didn't write the script yourself, I will *try* to explain...

```

	DS=`$DU $i | awk '{print $1}'`
	if [ "$DS" -gt 0 ]
	then
		# cp -v $i/* "$NEWDIR"
		mv $i/* "$NEWDIR"
	fi

```

This seems designed to try to establish whether a given directory actually contains any files, before doing a move. Executing "mv source/* dest" on a source with nothing in it causes the error "cannot stat `source/*': No such file or directory" to appear, which is ugly, so your friend probably wanted to stop it happening.

Unfortunately his trick won't always work anyway. On many filesystems, du reports nonzero disk usage for empty directories (because the directory itself is often considered to take up a little space). As a result, the test **[ "$DS" -gt 0 ]** *may* sometimes be true, even if there's nothing to move. So, now that a second problem has cropped up (which is most likely being caused by directory names that contain unexpected characters), you should tweak this block of code.

This is a very nice little script :cool: but you might ask your friend to take a quick look at it. I wonder if it would be worth redesigning it along the lines of **find source/ -exec action_1 \; -exec action_2 \; ... ** rather than the current **cd source/; for i in *** approach. Maybe, maybe not!

**Edit:** Better still, replacing **for i in *** with **for i in `find source/`** might work quite nicely, with some additional tweaking. If you really want me to, I can pollute your script with the appropriate changes (in my own poor style) and post it back.

---

### Post by jasplund on 2006-11-11
That would be great
With an early version of the script I had some problems if my memorycard wasn't mounted that's why it checks if the source is present. Otherwise it moved files on my desktop for some mysterious reason



thanks

---

### Post by kidders on 2006-11-11
Hmm...

Well in that case, I'll play around and post back. Can I ask about the **NEWDIR=`echo ${DEST}/0${i:3}`** substitution though ... this line seems to turn "./whatever" into "/path/to/destination/0atever". Am i interpreting that correctly?

I'm just wondering what the reason is, out of curiosity.

---

### Post by jasplund on 2006-11-12
Well that is because the folders in my camera is called 101YMMDD or 102YMMDD and I want 101, 102, 103 etc to be replaced by 0 so that I get YYMMDD which of course is the date the pics's been taken.

Also the script is supposed to delete the .THM files associated with JPE-files but not the ones that are associated with .MRW-files. 


Johan

---

### Post by jasplund on 2006-11-14
Have you looked into yet?

---

### Post by JoelP on 2006-11-20
Edgy uses 'dash' instead of 'bash'. Try running your script through bash. eg /bin/bash /your/script

Joel.

---

### Post by jasplund on 2006-11-22
> **JoelP said:**
> Edgy uses 'dash' instead of 'bash'. Try running your script through bash. eg /bin/bash /your/script

Joel.

Thanks that made it work

---

### Post by byenary on 2008-02-07
Hello,

Got same problem moving to gutsy , but since the script is an eventhandler for an sms module i can't call it using /bin/bash caus the script is defined in the sms daemon file.
This piece is not working anymore, anybody knows how to alter

 if [ "${TEXT:1:4}" = "Code" ]; then

it says bad substitution ....

Grts

---

### Post by hunt.topher on 2008-04-07
Hey, just a comment: Jasplund, if you run the following simple script, does it generate the same error?

[B][INDENT]# small-script

string1="test text"
echo ${string1:2}[/INDENT][/B]

For me, even that doesn't work, when run as a script; something about my environment doesn't like the use of ${string:position} to grab part of a string. I don't know much about scripting either so I don't know if this is an outdated way of manipulating strings, or if I'm missing something... The command works fine in terminal - just not when run as a script. Also, the error doesn't appear when I run the script on Suse; only on Ubuntu.

---

### Post by ghostdog74 on 2008-04-07
> **hunt.topher said:**
> Also, the error doesn't appear when I run the script on Suse; only on Ubuntu.

try running it as
```

# bash script.sh

```
or

put shebang
```

#!/bin/bash
string1="test text"
echo ${string1:2}

```
make sure its executaable, then run it like ./script.sh

---

### Post by hunt.topher on 2008-04-08
Yes, that was the answer, I actually figured that out from a Launchpad bug report last night. Any idea why dash is different? Is it *meant* to be broken like this?

Whatever, bash instead of sh works pretty well.

---

