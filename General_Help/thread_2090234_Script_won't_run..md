---
title: "Script won't run."
date: 2012-12-01
forum: General Help
---

### Post by Kidwell on 2012-12-01
So I found this script to remove MP3 tags some time ago and it works flawlessly on my ubuntu 11.04 32bit desktop and CentOs server, however it will not execute on my Lubuntu 12.04 32bit desktop.  Any help is appreciated.

```
#!/bin/bash
# Script name: strip-tags.sh
# Original Author: Ian of DarkStarShout Blog
# Site: http://darkstarshout.blogspot.com/
# Options slightly modified to liking of SavvyAdmin.com
 
oktags="TIT2 TPE1 TALB TYER TDRC TRCK TCON COMM APIC"
 
indexfile=`mktemp`
 
#Determine tags present:
find . -iname "*.mp3" -exec eyeD3 --no-color -v {} \; > $indexfile
tagspresent=`sort -u $indexfile | awk -F\): '/^<.*$/ {print $1}' \
| uniq | awk -F\)\> '{print $1}' | awk -F\( '{print $(NF)}' \
| awk 'BEGIN {ORS=" "} {print $0}'`
 
rm $indexfile
 
#Determine tags to strip:
tostrip=`echo -n $tagspresent $oktags $oktags \
| awk 'BEGIN {RS=" "; ORS="\n"} {print $0}' | sort | uniq -u \
| awk 'BEGIN {ORS=" "} {print $0}'`
 
#Confirm action:
echo
echo The following tags have been found in the mp3s:
echo $tagspresent
echo These tags are to be stripped:
echo $tostrip
echo
echo -n Press enter to confirm, or Ctrl+C to cancel...
read dummy
 
#Strip 'em
stripstring=`echo $tostrip \
| awk 'BEGIN {FS="\n"; RS=" "} {print "--set-text-frame=" $1 ": "}'`
 
# First pass copies any v1.x tags to v2.3 and strips unwanted tag data.
# Second pass removes v1.x tags, since I don't like to use them.
# Without --no-tagging-time-frame, a new unwanted tag is added.  :-)
 
find . -iname "*.mp3" \
-exec eyeD3 --to-v2.3 --no-tagging-time-frame $stripstring {} \; \
-exec eyeD3 --remove-v1 --no-tagging-time-frame {} \; 
 
echo "Script complete!"
```

This is the output on Lubuntu:
> awk: line 0: regular expression compile failed (missing '(')
)>
awk: line 0: regular expression compile failed (missing '(')
):

The following tags have been found in the mp3s:

These tags are to be stripped:


Press enter to confirm, or Ctrl+C to cancel...

I've tried modifying the script at those lines, but it makes the script not work properly.

Thanks for looking! :guitar:

---

### Post by ohnonot on 2012-12-03
i'm not familiar with awk, but generally with shell scripts i have noticed:

- different shells treat " and ' and possibly all sorts of brackets differently.
- copy pasting a script, simple single quotes (') sometimes are replaced to (`).
- maybe also this one \ causes trouble? it's there for your convenience anyway, make one long line out of it, like this:
"one\
long\
line"
becomes "one long line"
...

edit: the error message seems to point to awk being the culprit, not the shell script itself.
since awk is called several times you have to find out which one exactly.

---

### Post by zealibib slaughter on 2012-12-03
edit the script to read this on the first line
```
#! /bin/bash -x
```
this will cause it to print all the debugging info to your terminal.
Run the script and post output.

---

### Post by jaguare22 on 2012-12-20
Had the same script.  Got it working after doing two things.  The one I think fixed it was installing gawk, gnome version of awk from what I understand.  Anyway I am fairly certain that's what fixed the problem.  If you got it from savvyadmin you may have seen someone there suggesting in the comments that you change a couple of lines.  With mine, Ubuntu 12.04 server, neither the original or the alternate code worked.  Once I installed gawk I tried it with the the alternate code, still failed.  Once I changed the script back to the original code, it ran perfectly.  

So, install gawk and use original code from savvyadmin and give it a try.  

If it still doesn't work check the script for green blocks on blank lines between code sections.  I think they were from cutting and pasting improperly so I removed them.

I have a thread in this forum too, just search eyeD3.  Good luck.

---

