---
title: "Zip multiple files in a directory"
date: 2015-07-28
forum: General Help
---

### Post by pradeep15 on 2015-07-28
Hi all,

I was looking on how to zip multiple files in a directory and stumbled on this thread [http://ubuntuforums.org/showthread.php?t=1060130](http://ubuntuforums.org/showthread.php?t=1060130) and i was able to zip it. Now i was wondering if this command  for i in `ls`; do zip -r $i.zip $i ;done can be modified to ignore already zipped files and zip only newly created folder.

Thanks in advance

---

### Post by nerdtron on 2015-07-28
so you want to ignore the files already having the .zip extension right? Try the quick exclude .zip
```
 for i in `ls | grep -v .zip`; do zip -r $i.zip $i; done 
```

---

### Post by Lars Noodén on 2015-07-28
In general, is better to [avoid parsing "ls"](http://mywiki.wooledge.org/ParsingLs) and use [find](http://manpages.ubuntu.com/manpages/trusty/en/man1/find.1.html) instead.  In this case it can be used to exclude filenames that end in .zip too.  

```

find . -not -name '*.zip' -print0 | xargs --null zip -u foo.zip

```

There, [find](http://manpages.ubuntu.com/manpages/trusty/en/man1/find.1.html) looks in the current directory which is always represented by a dot (.)
It looks for anything not named .zip and prints out the filename delimited with a null.  The null allows it to handle files with spaces in the names.  

The output from [find](http://manpages.ubuntu.com/manpages/trusty/en/man1/find.1.html) is passed via a pipe over to [xargs](http://manpages.ubuntu.com/manpages/trusty/en/man1/xargs.1.html), which is set to watch for the null separators, and feeds the file names to [zip](http://manpages.ubuntu.com/manpages/trusty/en/man1/zip.1.html) as [s]input[/s] options.  [zip](http://manpages.ubuntu.com/manpages/trusty/en/man1/zip.1.html) is set to update its archive, in this case *foo.zip*.

---

### Post by sudodus on 2015-07-28
Thanks for teaching about the -not option for find :-)

---

### Post by pradeep15 on 2015-07-28
sorry iam not much into scripting. but when i look into your find option it looks like foo.zip gets rewritten every time. so if i run the command in a directory which has 800 folders, it keeps updating foo.zip. I was looking for  command in bash which creates individual zip files for all 800 folders and skip already existing zip files.

---

### Post by Lars Noodén on 2015-07-29
> **pradeep15 said:**
> sorry iam not much into scripting. but when i look into your find option it looks like foo.zip gets rewritten every time. so if i run the command in a directory which has 800 folders, it keeps updating foo.zip. I was looking for  command in bash which creates individual zip files for all 800 folders and skip already existing zip files.

Yes, the above writes just one zip file.  The following makes one per subdirectory, and anything inside the subdirectory, including other directories, goes into the zip file.  

```

for dir in $(find . -maxdepth 1 -not -name '.' -not -name '*.zip' -type d -printf "%f\n"); \
  do find "$dir" -not -name '*.zip' -print0 | xargs --null zip -u "$dir.zip" ; done

```

The first line finds all subdirectories in the current directory and loads them one at a time into the variable $dir and you need to run it from the directory containing the subdirectories you wish to zip.

Is that a step closer?

---

### Post by nerdtron on 2015-07-29
why zip -u ? from the man page (rhel 7 at the moment) it says -u option is used to update the zip file. And also don't you need -r option to zip the folders?

**i don't have much testing with zip at it seems pre-historic to me, I'm more comfortable with gzip and tar

---

### Post by Lars Noodén on 2015-07-29
> **nerdtron said:**
> why zip -u ? from the man page (rhel 7 at the moment) it says -u option is used to update the zip file. And also don't you need -r option to zip the folders?

**i don't have much testing with zip at it seems pre-historic to me, I'm more comfortable with gzip and tar

But in this case with zip the desire was stated as avoiding any files with names ending in zip.  If they are scattered in the hierarchy then then only way to avoid them is to use find to skip them.  If -r is used with zip it will get the wrong files, if they exist.  At least that's how it turns out in my small tests.  

** I don't really condone zip either and normally use only GNU tar.

---

### Post by pradeep15 on 2015-07-30
fantastic. it looks what i wanted but the problem is it display all 800 folders info like this:
zip warning: name not matched: abc1/raw_files/devices_data_full
zip warning: name not matched: abc2/raw_files/devices_data_full 

I just dont want it to display all 800 folders just show the one which is newly created. Can it be achieved with is for command

---

### Post by nerdtron on 2015-07-30
It can be achieved with the for command. My original post is still applicable. Though "ls | grep" combination is not efficient, it will still do the job.
```
for i in `ls | grep -v .zip`; do zip -r -m "$i.zip: "$i"; done
```
**note: Since you used the -m on the zip command, the source folder will be deleted and be replaced with the zipped file, therefore, if the folder is successfully zipped, the original folder is removed.

---

### Post by pradeep15 on 2015-08-03
great this worked...thanks guys it was really really helpful and my issue was solved. thanks a ton.

---

