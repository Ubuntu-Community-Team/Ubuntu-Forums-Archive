---
title: "File names in alphabetical order"
date: 2016-12-01
forum: General Help
---

### Post by tech291083 on 2016-12-01
Hi Friends,

I have one big folder named Subjects in Downloads folder, which contains other folders namely History, Maths etc. How can I get the name of all files in each sub-folder in alphabetical order sorted by their type ie image, text etc.

Thanks.

```

[john@localhost ~]$ cd Downloads/
[john@localhost Downloads]$ ll
total 8
drwxr-xr-x. 5 john john 4096 Dec  1 11:01 Subjects
-rw-r--r--. 1 john john  235 Dec  1 11:08 Ubu Forums

[john@localhost Downloads]$ ls
Subjects  Ubu Forums

[john@localhost Downloads]$ cd Subjects/

[john@localhost Subjects]$ ls
History  Maths  Science

[john@localhost Subjects]$ cd History/

[john@localhost History]$ ls
Lesson 1  Lesson 2  World Map.jpg

[john@localhost History]$ ll
total 32
-rw-r--r--. 1 john john    50 Dec  1 11:01 Lesson 1
-rw-r--r--. 1 john john    48 Dec  1 11:02 Lesson 2
-rw-rw-r--. 1 john john 23295 Dec  1 11:03 World Map.jpg

[john@localhost History]$ 

```

I want file names (with their extensions if possible), that too in alphabetical order. The ls command seems to be the right choice, but I want to put all the files names in each folder in a separate column in a sheet (Excel/Calc etc) in alphabetical order sorted by type as shown in my attached screenshot (Sheet.png). If I copy the output to ls command manually, it will be very difficult for me to paste them into a sheet. This is just an example. I have more than 2000 files in different sub-folders in total in an actual folder named Subjects. Can you please help?

Thanks.

---

### Post by sudodus on 2016-12-01
If you pipe the list through ***tr***, you can remove one or more adjacent spaces with a tab, and a file with tabs can be imported to columns automatically in the spreadsheet.

```
... | tr -s ' ' '\t' > file.txt
```

---

### Post by vasa1 on 2016-12-01
It seems that parsing `ls` isn't advisable. `find` maybe more suitable: > ls is only intended for human consumption: it has a loose, non-standard format and may "clean up" filenames to make output easier to read.from [https://github.com/koalaman/shellcheck/wiki/SC2012](https://github.com/koalaman/shellcheck/wiki/SC2012)

Also, it may help to ensure that filenames are Linux-friendly: [http://pclosmag.com/html/Issues/201607/page03.html](http://pclosmag.com/html/Issues/201607/page03.html). I'm just throwing that in because, in your image, you seem to be using the .xlsx format ;)

---

### Post by tech291083 on 2016-12-01
> **sudodus said:**
> If you pipe the list through ***tr***, you can remove one or more adjacent spaces with a tab, and a file with tabs can be imported to columns automatically in the spreadsheet.

```
... | tr -s ' ' '\t' > file.txt
```

Thanks.


```

[john@localhost History]$ ls|tr -s '''\t' > ListOfFiles.xlsx

```


The above command works for me perfectly, but that is after doing cd into each of the sub-folders in the main folder "Subjects". Is there a way I can just avoid cd into each sub-folder and have a list of all files right from the parent folder to each of the sub-folders in it? 

Thanks.

May be the below one works, right? Thanks.

```

[john@localhost Downloads]$ ls -R |tr -s '''\t' > ListOfFiles.xlsx

```

---

### Post by sudodus on 2016-12-01
I think there should be two spaces between the single quote characters:

```
$ ls -R |tr -s ' ' '\t' > ListOfFiles.xlsx
```

But it is worth considering the advice by *vasa1*, and use find

```
$ find > ListOfFiles.xlsx
```

Where the whole directory path will be written.

Notice that converting spaces to tabs will cause problems, if there are spaces in some of the file names. On the other hand, find will write one file per line by default, so you need not use ***tr*** unless you modify that output.

---

### Post by Keith_Helms on 2016-12-02
Hah, no way you're going to get the ls command to output a 2-dimensional spreadsheet consisting of directory names as the heading and file names sorted by extension, then name, under each column.  This was a fun challenge.  My solution is probably way over-engineered, but here it is.  You could save this in a script if you want or just paste it to the command line.
```
(
ridx=0
cidx=0
maxrows=0
maxcols=0
delim=","
declare -A table
while IFS='' read -r -d $'\0' file; do
  subdirs[$cidx]="$file"
  table[$cidx,0]="$file"
  ((cidx++))
done < <(find ./ -mindepth 1 -maxdepth 1 -type d -printf "%P\0" | sort -z)
maxcols=$cidx
for ((i=0; i<$maxcols; i++));
do
  ridx=0
  while IFS='' read -r -d $'\0' file; do
    name[$ridx]="${file##*.}::$file"
    ((ridx++))
  done < <(find "${subdirs[i]}" -mindepth 1 -maxdepth 1 -type f -printf "%P\0")
  ridx=1
  while IFS='' read -r -d $'\0' file; do
    table[$i,$ridx]="${file#*::}"
    ((ridx++))
    if [ $ridx -gt $maxrows ]
    then
      maxrows=$ridx
    fi
  done < <(printf '%s\0' "${name[@]}" | sort -z)
done
maxcomma=$((maxcols-1))
for ((j=0; j<$maxrows; j++));
do
  line=""
  for ((i=0; i<$maxcols; i++));
  do
    line="$line${table[$i,$j]}"
    if [ $i -lt $maxcomma ]
    then
      line="$line$delim"
    fi
  done
  echo "$line"
done
) > dummy.csv
```

Assumptions:
* The code will be run in the parent directory of the subdirectories you want to list.
* Only directory names from the parent directory will be used, not any regular files.
* Only regular files will be captured from the subdirectories, not any sub-subdirectories.
* The code will only go down one level.  If you have files that are several levels deep, they will be ignored.  If you want files from several levels, you can change the 2nd maxdepth value to something greater than 1.
* The output will be a comma delimited text file.  You can change the delim value to something else if you want and change the output file from dummy.csv to something else.

In general, here's what it's doing:
* Capture the top-level directory names and sort them then save in an associative array
* For each top-level directory, capture the file names under it and sort them by extension first, then name and then save those in the same associative array
* Loop through the array that was built from the results and output a line for each row

---

### Post by tech291083 on 2016-12-14
Friends,

The below command did the trick for me, thanks a lot for so many wonderful replies and sorry for the delayed response.

```
ls -R |tr -s '''\t' > ListOfFiles.xlsx
```

[**[COLOR=#000000]Keith_Helms[/COLOR]**]("https://ubuntuforums.org/member.php?u=1871481") 	 ,

You have given such a fine-tuned reply and I am ashamed to say that I know nothing about scripting, sorry, but I have saved it in a safe place for any future use and I salute your effort that has gone into ensuring that I get the best possible help. Thanks a lot. Appreciated.

---

