---
title: "Compare Files in Directories"
date: 2012-11-08
forum: General Help
---

### Post by Quarkrad on 2012-11-08
I am consolidating my photo collection from multiple directories into one big folder.  I am using the command

find /home/(A) -type f -exec cp {} /home/ (B)/ \;

to extract all the pictures in the multiple folders in parent folder (A) into the single folder (B).  This appears to work very well, after the command has run (B) just contains jpeg files, no files within sub directories.  To check everything has gone accross I looked at the Properties of (A) and then (B) - I would have thought that as a folder is not big the size of the folders would be almost the same. However, (A) is 874 items totalling 1.4 GB and (B) is 687 items totalling 1.1 GB.  I was hoping to use Meld Diff Veiwer to compare the files in (A) and (B) but it appears Meld does not like binary files.  Is there a gui type program I could use to see what is missing?  All that should be missing are the sub folders but I can't see they would account for the 0.3 GB difference.

---

### Post by Vaphell on 2012-11-08
i suspect there are files with the same name, 2nd file overwrites the 1st
path1/filename -> /dest/filename
path2/filename -> /dest/filename

---

### Post by Quarkrad on 2012-11-08
I don't think so.  Before I ran the command to cp all the files into the single folder I selected the multi-directory top level folder in FSlint and made sure there were no duplicate files within the multi folder structure.  There were some and I deleted them - so when I ran the Terminal command all the individual files should have been unique.

---

### Post by steeldriver on 2012-11-08
well I guess you could do something like

```
$ while read -r -d $'\0' file; do [ -f /home/*B*/"$file" ] || echo "$file" : not found; done < <(find /home/*A* -type f -printf '%f\0')

```

---

### Post by Habitual on 2012-11-08
```
diff --brief --recursive --report-identical-files /folder1 /folder2
```Alternate:
```
diff -qr /somedir/ /someotherdir/
```HTH.

---

### Post by gordintoronto on 2012-11-08
See Full Circle Magazine, issue 58, page 42.

---

### Post by hwttdz on 2012-11-08
Or count how many unique filenames there are in (A):
find ~/(A) -type f -exec basename {} \; | sort | uniq | wc -l

and compare that to how many filenames there are in (A):
find ~/(A) -type f | wc -l

@gordintoronto - could you post a link to the pdf since not all of us have that copy, thanks.

---

### Post by gordintoronto on 2012-11-08
Full Circle Magazine, issue 58:

[http://fullcirclemagazine.org/issue-58/](http://fullcirclemagazine.org/issue-58/)

Page 42 has a story on finding duplicate files. Right-click on the image and select "save as" to get the PDF.

---

### Post by Quarkrad on 2012-11-10
thank you all - I now have many options.

---

