---
title: "A way to search and delete doubles?"
date: 2007-11-11
forum: General Help
---

### Post by honeydew on 2007-11-11
I have a growing selection of data and research for school.. at one point I had to commit/use my backups and seemed to created doubles in a few different spots.. I am trying to relieve some space does anyone know how I can search for and delete doubles in a specified folder or file system?

---

### Post by cwaldbieser on 2007-11-11
> **honeydew said:**
> I have a growing selection of data and research for school.. at one point I had to commit/use my backups and seemed to created doubles in a few different spots.. I am trying to relieve some space does anyone know how I can search for and delete doubles in a specified folder or file system?

You could look for files with similar names and run them through md5sum.  If the hashes are identical, it is a pretty good bet the files are the same.  If the files are just text files, you could probably use diff or cmp.

---

### Post by AlexThomson_NZ on 2007-11-11
I do something similar to find duplicate files in 2 directories occasionally using a basic Perl script (could fairly easily do using bash)...

find <directory1> -name *.mp3 > list_1.txt
find <directory2> -name *.mp3 > list_2.txt

Then do some string trickery to remove everything before the last "/" on each line (use "sed")

Merge the two lists:
cat list_1.txt list_2.txt > list.txt

Show the duplicates:
uniq -d list.txt

You can then either delete them manually, or pipe then using xargs to delete them automatically.

---

### Post by honeydew on 2007-11-11
> **AlexThomson_NZ said:**
> I do something similar to find duplicate files in 2 directories occasionally using a basic Perl script (could fairly easily do using bash)...

find <directory1> -name *.mp3 > list_1.txt
find <directory2> -name *.mp3 > list_2.txt

Then do some string trickery to remove everything before the last "/" on each line (use "sed")

Merge the two lists:
cat list_1.txt list_2.txt > list.txt

Show the duplicates:
uniq -d list.txt

You can then either delete them manually, or pipe then using xargs to delete them automatically.

Thanks for the quick help!  Ill test and possibly implement this tonight =].

---

### Post by stalker145 on 2007-11-12
> **honeydew said:**
> I have a growing selection of data and research for school.. at one point I had to commit/use my backups and seemed to created doubles in a few different spots.. I am trying to relieve some space does anyone know how I can search for and delete doubles in a specified folder or file system?

Personally, I use [fslint]("http://www.pixelbeat.org/fslint/"). > sudo aptitude install fslint This app uses the aforementioned md5 sums for scanning files and seeing is they *actually are* different regardless of filename.

I'm all about the GUI ;)

---

### Post by honeydew on 2007-11-14
> **stalker145 said:**
> Personally, I use [fslint]("http://www.pixelbeat.org/fslint/").  This app uses the aforementioned md5 sums for scanning files and seeing is they *actually are* different regardless of filename.

I'm all about the GUI ;)

hrmm fslint looks good.. though I would like something I can run from the CLI..  I want to run this as a weekly cron for my archive project.

---

### Post by calldrin on 2007-11-14
> **stalker145 said:**
> Personally, I use [fslint]("http://www.pixelbeat.org/fslint/").  This app uses the aforementioned md5 sums for scanning files and seeing is they *actually are* different regardless of filename.

I'm all about the GUI ;)

I find this very interesting..
Will "fslint" work on pictures?
I have many duplicates and it takes forever to track them down!!

Thanks, 
Chuck

---

### Post by stalker145 on 2007-11-15
> **calldrin said:**
> I find this very interesting..
Will "fslint" work on pictures?
I have many duplicates and it takes forever to track them down!!

Thanks, 
Chuck

Yes, fslint works for pictures. In fact, that was my reason for hunting it down in the first place. I was paranoid on the first folder that I ran it on, checking every single "duplicate", but it was accurate.

There *are* CLI versions of these programs. I saw them when I was searching, but I don't recall them now. I chose fsling because it wasn't CLI... call me lazy, but I like my GUI ;)

---

### Post by Justin Trouble on 2007-11-19
I've just found a CLI program named 'fdupes'.

It's available as a package in Gutsy.

---

### Post by honeydew on 2007-11-19
cool, thanks justin this looks like what Im looking for.   Also.. I appreciate GUIs as well but, I need to run this from cron, or another script.. thanks for the help guys!

---

