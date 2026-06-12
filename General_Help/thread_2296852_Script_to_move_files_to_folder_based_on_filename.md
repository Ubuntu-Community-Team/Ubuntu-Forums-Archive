---
title: "Script to move files to folder based on filename"
date: 2015-09-29
forum: General Help
---

### Post by Ross-C on 2015-09-29
Hi,

Can anyone help me to write a script that I can add as a crontask.  I am running asterisk with call recording and the recordings are saved in the following format:

OUT202-20150928-191328-6376544008.588.wav

I have lots of these files in a folder called /var/spool/asterisk/monitor

can anyone help me to write a script to move these to folders based on the date (including auto creating the destination folders) 

so in this example id end up with

/home/recordings/2015/09/28/OUT202-20150928-191328-6376544008.588.wav

Any help is very much appreciated I am reading to try and figure out myself but I have an urgent requirement to archive some off and need to store them logically.

Many Thanks in advance

---

### Post by tristan16 on 2015-09-29
Try using
```
 mv *.wav ~/FilePath/
``` 

From [https://askubuntu.com/questions/214560/how-to-move-multiple-files-at-once-to-a-specific-destination-directory](https://askubuntu.com/questions/214560/how-to-move-multiple-files-at-once-to-a-specific-destination-directory)

---

### Post by sisco311 on 2015-09-29
You have to write a [for loop]("http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Loops_.28while.2C_until_and_for.29") to iterate through the .wav files. Then you can use [parameter expansion]("http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion") to get the year, month and day from the file name.  From there, creating the destination directory and moving the file shouldn't be hard at all.

Not sure how much help do you need or want. If you wish, I can post a script which should work with some minor adjustments.

---

### Post by Ross-C on 2015-09-29
Thanks for the reply but I need to learn how to seperate out into different folders if possible.

---

### Post by Ross-C on 2015-09-29
@sisco311 Sorry I didn't see your reply, that's what I'm talking about thanks.  I'm not familiar with bash scripting logic / syntax if you could get me started with a sample script that would be great and really helpful.

---

### Post by sisco311 on 2015-09-29
A very basic approach to get the date from the file names would be something like:
```

#!/bin/bash

for file in *.wav;
do
    date="${file#*-}"
    date="${date%%-*}"

    echo "$date"
done

```

In a similar way you can get the year, month and day from the `date' variable. 

Here is a more elaborated script:
```

#!/bin/bash

# specify the source and destination directories
source="$HOME/xtmp/foo"
dest="$HOME/xtmp/foo/dest"

# exit if source is invalid
cd "$source" || exit 1

shopt -s nullglob
for file in ./*-[[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]]-*-*.wav
do
    # skip if $file is not a regular file
    [ -f "$file" ] || continue
    # get the date from the filename
    date="${file#*-}"
    date="${date%%-*}"
    # get the year, month and day
    year="${date:0:4}"
    month="${date:4:2}"
    day="${date:6:2}"
    # check if the date is valid
    # you can omit this part if only asterisk craetes the files in $source
    if (( ${month##0} > 12 )) || (( ${day##0} > 31 ));
    then
        printf '%s\n' "invalid date: $date" >&2
        continue
    fi
    #added for testing :)
    echo $date $year $month $day
    #create the directory and  move the file
    mkdir -p "$dest/$year/$month/$day" || continue
    mv "$file" "$dest/$year/$month/$day"
done

```

I didn't tested it on sensitive data, so use it at your own risk.

---

### Post by Ross-C on 2015-09-29
This is great thank you,  I will have a play around with it and post back a copy of what I end up using.

---

### Post by Ross-C on 2015-09-29
Hi,

I am just trying it now and I am getting a syntax error on line 12

line 12: syntax error near unexpected token `./*-[[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]]-*-*.wav'

please could you explain the expression to me, thanks for all your help

---

### Post by Ross-C on 2015-09-29
Sorry ignore me the script works perfectly :) , it was just line spacing causing the error, it would be good to understand the script though.

I understand the program flow just not the expression and also the bits in curly brackets.:D

---

### Post by sisco311 on 2015-10-02
> **Ross-C said:**
> Sorry ignore me the script works perfectly :) , it was just line spacing causing the error, it would be good to understand the script though.

I understand the program flow just not the expression and also the bits in curly brackets.:D

The expression is a[ glob ]("http://mywiki.wooledge.org/glob")and the bits in curly brackets are [parameter expansions]("http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion").

---

