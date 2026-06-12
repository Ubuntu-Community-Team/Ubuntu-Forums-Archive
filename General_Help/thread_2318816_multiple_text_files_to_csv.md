---
title: "multiple text files to csv"
date: 2016-03-29
forum: General Help
---

### Post by lp.descamps on 2016-03-29
hi

i need to extract lines from multiple files to a csv file.
for example, i have these 3 files

file1.txt
date:29dec1980
caller:91245824255
called:8127766

file2.txt
date:11apr2014
caller:9155584558
called:8115478

file3.txt
date:25jun2015
caller:445225552
called:8117485

i need grep/awk to read these files and create a csv like this

output.csv
file,date,caller,called
file1.txt,29dec1980,91245824255,8127766
file2.txt,11apr2014,9155584558,8115478
file3.txt,25jun2015,445225552,8117485

any idea?
thanks

---

### Post by lp.descamps on 2016-03-29
i got this so far

test$ awk '/date/ || /called/ || /caller/' *
date:29dec1980
caller:91245824255
called:8127766
date:11apr2014
caller:9155584558
called:8115478
date:25jun2015
caller:445225552
called:8117485

---

### Post by mcgess on 2016-03-30
Hi

The first line of output.csv can be created using BEGIN{ command } a search for "awk begin" gives [http://www.linuxnix.com/awk-scripting-10-begin-and-end-block-examples/](http://www.linuxnix.com/awk-scripting-10-begin-and-end-block-examples/) 

Your desired output.csv contains the file names, a quick search for "awk filename" comes up with [http://www.thegeekstuff.com/2010/01/8-powerful-awk-built-in-variables-fs-ofs-rs-ors-nr-nf-filename-fnr/](http://www.thegeekstuff.com/2010/01/8-powerful-awk-built-in-variables-fs-ofs-rs-ors-nr-nf-filename-fnr/) which gives a useful built in awk variable

You need to separate date caller and called from the useful information, the same web page also shows how to set the input field separator. 

The last bit is that awk processes one line after another so you have to store the useful information from each line until you have enough to output a complete line, googling "awk variables" gives [http://www.linuxnix.com/awk-scripting-how-to-define-awk-variables/](http://www.linuxnix.com/awk-scripting-how-to-define-awk-variables/)

```

/date/ {dt=$2}
/caller/ {cr=$2}
/called/ {command to print a line}

```

This sets dt to the second field of a line containing date, ditto cr for a line containing caller, these two variables can be used in a print statement when a line containing called is processed

---

