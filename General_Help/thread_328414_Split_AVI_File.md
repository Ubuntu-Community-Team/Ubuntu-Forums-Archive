---
title: "Split AVI File"
date: 2006-12-30
forum: General Help
---

### Post by taekwondodogoof on 2006-12-30
Hi,
     I have a split avi file, meaning the name is moviename.avi.001 then moviename.avi.002. How do I put these back together? I've heard of HJ split program, but I can't get it to work with Ubuntu. Any help would be greatly appreciated!! Thanks in advance! :-D :-D

---

### Post by taurus on 2006-12-30
```
sudo aptitude update
sudo aptitude install avimerge
avimerge -o filename.avi -i first_file.avi second_file.avi
```

---

### Post by 0MG on 2006-12-30
nm

---

### Post by taekwondodogoof on 2006-12-30
Wait... it says cannot find file or package with name avimerge..

---

### Post by tagra123 on 2006-12-30
> **taekwondodogoof said:**
> Hi,
     I have a split avi file, meaning the name is moviename.avi.001 then moviename.avi.002. How do I put these back together? I've heard of HJ split program, but I can't get it to work with Ubuntu. Any help would be greatly appreciated!! Thanks in advance! :-D :-D


SPLIT APART into 1 GB files = 1000m , a 10MB file would be 10m
```
split -b 1000m "FileToSplit.EXT" SplitFileName-EXT-
```


JOIN THEM TOGETHER (Assume 3 Segments
```

cat SplitFileName-EXT-ab >> SplitFileName-EXT-aa
cat SplitFileName-EXT-ac >> SplitFileName-EXT-aa

```


Rename the file to a normal name again.

```

mv SplitFileName-EXT-aa NewFileName.EXT
```


Your Example

Make a backup in case something goes wrong
```
cp  moviename.avi.001  moviename.avi.001.bak
cp  moviename.avi.002  moviename.avi.002.bak
```

Combine the files
```
cat moviename.avi.002 >> moviename.avi.001

```

Rename the joined file

```
mv moviename.avi.001 moviename.avi
```

---

### Post by taekwondodogoof on 2006-12-30
I know I'm going to sound like a total noob, but where do I put the files? it says cannot find the file? Thanks for dealing with me

---

