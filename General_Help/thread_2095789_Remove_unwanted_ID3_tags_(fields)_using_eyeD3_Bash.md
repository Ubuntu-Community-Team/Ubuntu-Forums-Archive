---
title: "Remove unwanted ID3 tags (fields) using eyeD3 Bash Script Error"
date: 2012-12-17
forum: General Help
---

### Post by jaguare22 on 2012-12-17
I have Ubuntu 12.04 Server on a no head system so I am working over SSH.  I found what looks like the perfect script for stripping unwanted tags via cli with eyeD3.  There were a couple of comments from others having trouble running this script on Ubuntu.  Same error.  One reply suggested adding single quotes to -F option but that failed too.  Added more errors in fact.  

I am getting this error when running the script with ./script.sh -

```
awk: line 0: regular expression compile failed (missing '(') ):
``` 
```
awk: line 0: regular expression compile failed (missing '(') )>
```

The following tags have been found in the mp3s:

These tags are to be stripped:

(end of error report)

Here is a the script obtained from savvyadmin

```
!/bin/bash
Script name: strip-tags.sh
Original Author: Ian of DarkStarShout Blog
Site: [http://darkstarshout.blogspot.com/](http://darkstarshout.blogspot.com/)
Options slightly modified to liking of SavvyAdmin.com

oktags="TALB APIC TCON TPE1 TPE2 TPE3 TIT2 TRCK TYER TCOM TPOS"

indexfile='mktemp'

Determine tags present:
find . -iname "*.mp3" -exec eyeD3 --no-color -v {} \; > $indexfile tagspresent=sort -u $indexfile | awk -F\): '/^<.*$/ {print $1}' \ | uniq | awk -F\)\> '{print $1}' | awk -F\( '{print $(NF)}' \ | awk 'BEGIN {ORS=" "} {print $0}'

rm $indexfile

Determine tags to strip:
tostrip=echo -n $tagspresent $oktags $oktags \ | awk 'BEGIN {RS=" "; ORS="\n"} {print $0}' | sort | uniq -u \ | awk 'BEGIN {ORS=" "} {print $0}'

Confirm action:

echo echo The following tags have been found in the mp3s: echo $tagspresent echo These tags are to be stripped: echo $tostrip echo echo -n Press enter to confirm, or Ctrl+C to cancel... read dummy

Strip 'em
stripstring=echo $tostrip \ | awk 'BEGIN {FS="\n"; RS=" "} {print "--set-text-frame=" $1 ": "}'

First pass copies any v1.x tags to v2.3 and strips unwanted tag data.
Second pass removes v1.x tags, since I don't like to use them.
Without --no-tagging-time-frame, a new unwanted tag is added. :-)
find . -iname "*.mp3" \ -exec eyeD3 --to-v2.3 --no-tagging-time-frame $stripstring {} \; \ -exec eyeD3 --remove-v1 --no-tagging-time-frame {} \;

echo "Script complete!"
```


Thanks to all who consider aid.

---

### Post by jaguare22 on 2012-12-18
After many, many hours trying to debug a language I can't write...it works.  Installing gawk seems to be what worked.  Using the original code as shown on savvyadmin.com.  

I've just realized, above did not paste with line breaks in correct places.  Have to be more observant. 

This is a beautiful thing.  Seriously, I wouldn't have believed it if I hadn't seen it, but running this shaved off 4 of the 17 gigs.  Wow!  I kept typing tags but that's not right.  That should be "frames".

EyeD3 doesn't remove the entire tag, just certain frames.  These frames were not even visible in any of the gui's I tried.  Be careful pasting into editor.

---

