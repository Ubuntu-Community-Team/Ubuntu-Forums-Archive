---
title: "Rarring and parring a whole directory"
date: 2013-04-08
forum: General Help
---

### Post by chuckie86 on 2013-04-08
[COLOR=#333333][FONT=Ubuntu Beta]Ok, so heres my question, i was wondering if it's possible, with a command or a script, to rar and par a directory full of files. But i want the rar and par to be separted for every file.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]For example: I have a dir /home/upload with file1, file2, file, ... etc.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]I want to rar and par file1 than rar and par file2 and than file3. So i don't want them in one big archive.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Is that possible in one way?[/FONT][/COLOR]

---

### Post by cortman on 2013-04-08
Rar is proprietary. Why would you use it instead of tar?
Copy this into a text file in your main directory and set it to executable.

```

#!/bin/sh


echo "Enter full path of target dir:"
read workdir
while [ ! -d $workdir ]; do
    echo "That directory does not exist. Please enter path."
    read workdir
done
cd $workdir
for i in *; do
        par2 create -qq $i
        tar -czf $i.tar.gz $i $i*.par2
done
rm *.par2

```

Invoke it by running

```
./script_name
```

It will create .tar.gz archives containing the original file and the parity files. It cleans up the parity files created in the main dir, but leaves the original files intact.
Run it on a test directory first, of course.

---

### Post by chuckie86 on 2013-04-08
I'm trying to upload some files to usenet, that why i want to use winrar :) But i'll try your script, thx for that!

```
#!/bin/sh



echo "Enter full path of target dir:"
read workdir
while [ ! -d $workdir ]; do
    echo "That directory does not exist. Please enter path."
    read workdir
done
cd $workdir
for i in *; do
        par2 create -qq $i
        rar a $i.rar -v50m -m0 $i $i*.par2
done
rm $workdir/*.par2
```

Works with rar, thx for it!

---

### Post by cortman on 2013-04-08
You'll need to install par2 and rar, but the script then would be:

```

#!/bin/sh


echo "Enter full path of target dir:"
read workdir
while [ ! -d $workdir ]; do
    echo "That directory does not exist. Please enter path."
    read workdir
done
cd $workdir
for i in *; do
        par2 create -qq $i
        rar a $i.rar $i $i*.par2
done
rm *.par2

```

EDIT: Missed your reply- glad it works. Mark the thread [SOLVED] by editing the first post, and changing the title.
Good luck!

---

