---
title: "No such file or directory"
date: 2017-12-28
forum: General Help
---

### Post by frepie on 2017-12-28
Need help on a very simple shell script to convert video from wmv to mp4 format.

```

#!/bin/bash

for i in *.wmv;
do
    name=`echo $i | cut -d'.' -f1`;
    avconv -i "$i" -vcodec libx264 -acodec aac -strict experimental  -threads 3 "$name.mp4";
done
```


The folder only contains wmv video but when I run it, I get the error :
```
*.wmv: No such file or directory
```
yet there are dozens of wmv files, that show up when I do ```
ls -l *.wmv
```

but somehow, *.wmv fails to work in the script.

---

### Post by slickymaster on 2017-12-28
Something like this, perhaps;```
#!/bin/bash

FILES=/path/to/files

for f in $FILES
do
  # take action on each file
done
```

---

### Post by frepie on 2017-12-28
I appreciate your quick reply but I would like to know why *.wmv is not recognized in the script while it works on the command line.

---

### Post by sisco311 on 2017-12-28
Not sure why your script does not work. Are you in the right directory when you run it?


Linux is very permissive with file names. To prevent any unexpected behaviour, I would try something like:
```

#!/bin/bash

#with this option *.wmv will also match .WMV .Wmv .wmV ... 
shopt -s nocaseglob

#don't run the for loop if there are no wmv files in the current working directory
shopt -s nullglob

for file in ./*.wmv
do
    name=${file%.*}
    echo "$name" "$file"
done

```

---

### Post by frepie on 2017-12-28
I am puzzled....
The complete  script that failed was as follows (I just didn't copy the commented lines in the first post):
```
#!/bin/bash

#for %%f in {*.avi} do {
#avconv -i "%%~nxf" -c:v libx264 "%%~nf.mp4"
#}

for i in *.wmv;
do
    name=`echo $i | cut -d'.' -f1`;
    avconv -i "$i" -vcodec libx264 -acodec aac -strict experimental  -threads 3 "$name.mp4";
done
```

Now the script is 
```
#!/bin/bash

for i in *.wmv;
do
    name=`echo $i | cut -d'.' -f1`;
    avconv -i "$i" -vcodec libx264 -acodec aac -strict experimental  -threads 3 "$name.mp4";
done


```

The only thing I did was delete the comment lines. And now, it works.....

---

