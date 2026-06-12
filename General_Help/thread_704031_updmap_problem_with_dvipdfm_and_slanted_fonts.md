---
title: "updmap problem with dvipdfm and slanted fonts"
date: 2008-02-21
forum: General Help
---

### Post by Demogorge on 2008-02-21
Hello all,

I just spent a couple hours tracking this bug down so I wanted to post it here so other people can find it. I could not find a solution to this problem anywhere else (though I did find other people posting with the same issue, but with no solution). I also downloaded the tetex-3.0 distro and it still has this issue.

Problem: When using dvipdfm and certain fonts, slanted fonts will not display in the produced pdf. Dvipdfm will not generate any errors, and the text will be set in normal roman font. The dvi will show a slanted font, as will the output from pdflatex. This is reproducible with the Times and New Century Schoolbook fonts and others (Utopia, Garamond, Palatino, etc). 

Cause: Dvipdfm uses a fontmap file when producing pdf output. In tetex on Ubuntu, this file is created by the **updmap** program, which is actually just a large shell script which translates the dvips formatted fontmap files for use by dvipdfm, pdflatex, etc. Since the above fonts do not come with slanted shapes, pdflatex and dvipdfm are supposed to create them on the fly by following commands in the fontmap file such as "0.167 SlantFont".

Updmap translates fontmap files from standard dvips (or psfonts.map) format into dvipdfm format. The input maps contain the correct SlantFont commands on my system. However, updmap does not create a correct fontmap file for dvipdfm. In particular, it should output "-s 0.167" at the end of the line for any font when it sees "0.167 SlantFont" in the input map.

Solution: Updmap has the capability to do this, but seems to have a small bug that messes up the process. Luckily, it can be very easily fixed.

1) Edit updmap with
```
gksudo gedit /usr/bin/updmap
```
This is the location of updmap on my system (Feisty).

2) Find the dvips2dvipdfm() subroutine. Click find and search for: **dvips2dvipdfm** or, alternatively, **SlantFont** .

3) Edit the sed script which translates the fontmap format for use by dvipdfm. It will be 8 lines below the start of the subroutine.

Change:
```
-e 's@\(.* \([.0-9-][.0-9-]*\) *ExtendFont.*\)@\1 -e \2@' \
-e 's@\(.* \([.0-9-][.0-9-]*\) *SlantFont.*\)@\1 -s \2@' \
```

To:
```
-e 's@\(.*[ "]\([.0-9-][.0-9-]*\) *ExtendFont.*\)@\1 -e \2@' \
-e 's@\(.*[ "]\([.0-9-][.0-9-]*\) *SlantFont.*\)@\1 -s \2@' \
```

The input map contains '..."0.167 SlantFont...', but the sed script is not expecting the quotation mark before the number. The script is now modified to accept this.

4) Save the file and quit gedit. 

5) Now run updmap to apply the new script to the input maps and create the new map. In a terminal type:
```
sudo updmap
updmap
```

This will update the global updmap, and then the local copy. Now you can run dvipdfm on your dvi file, and the slanted fonts should now be correct.

Done!

---

