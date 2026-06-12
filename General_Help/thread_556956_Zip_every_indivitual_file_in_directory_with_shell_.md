---
title: "Zip every indivitual file in directory with shell script?"
date: 2007-09-22
forum: General Help
---

### Post by Githlar on 2007-09-22
I'm trying to make a shell script that will get all files of a certain extension, we'll use .txt in this example, cut off the .txt and zip it with [base name].zip.

This seems pretty simple at first glance, but it kind of hard to find answers for.

Here's what I have:
for file in `ls /my/path | grep *.txt`
do
 TEMP=`sed 's/\*.txt/""/'`
 //zip command
done

However, the script is not doing the `ls /my/path | grep *.txt` part. The files are in a different directory than the script.

I also tried to cd over the directory in the script using both

`cd /my/path`
cd /my/path

in the script and neither seemed to work. 

The second part causes it to go into some kind of infinite loop I think.

Any ideas?

---

### Post by Githlar on 2007-09-22
Oh, I was stupid, I didn't put the grep expression in quotes.

However, now I'm running into new problems. In my "for file in..." loop, my files has spaces in the names. So, $file ends up only being one part of the name, then the next part, then the next part with the space being the delimiter. Is there any way I can take that grep output line-by-line instead of word-by-word?

---

### Post by dcstar on 2007-09-22
> **Githlar said:**
> Oh, I was stupid, I didn't put the grep expression in quotes.

However, now I'm running into new problems. In my "for file in..." loop, my files has spaces in the names. So, $file ends up only being one part of the name, then the next part, then the next part with the space being the delimiter. Is there any way I can take that grep output line-by-line instead of word-by-word?

"ls -1" will list one file per line, and "ls -1 *.txt" should just return the matching filenames on single lines, does this help?

---

### Post by Githlar on 2007-09-22
I eventually figured it out. Here's my final script:

```
for file in /my/path/*.txt
do
  #Replaces spaces with underscores
  TEMP=`echo $file | sed 's/ /_/g'`
  #Removes known file extension (.txt)
  TEMP=`echo $TEMP | sed 's/\.txt//'`
  #Zip file and delete orginal
  zip -9mj $TEMP".zip" "$file"
done
```

---

