---
title: "Copy n files from directory"
date: 2014-10-19
forum: General Help
---

### Post by guber90 on 2014-10-19
Hi guys I lost some pics and  I tryed to recover them. 
After recovering has been finished I can't see them cus there is almost 100 000 pics in folder and laptop just get frozen when I open it, so I would like to copy lets say first 10 000 pics to other folder, then take look are they pics I was looking for, if not then I would like to copy from 10 000 to 20 000 and take look at them ect. So is there simple way to get this done?

---

### Post by O9aIevckc0 on 2014-10-19
1 first create a file called script.sh and paste this into it 

#!/bin/bash
find -type f >file
split -l 10000 file file2
cat file2aa|xargs mv -t '/home/testuser/testfolder' 2>/dev/null

changing /home/testuser/testfolder to wherever the folder you want to move files to

2 then chmod +x for that file to make it executable

3 cd to the directory with your pictures

4 next run the script 

e.g ./file.sh

 if the files aren’t the files you want 

5 then cd to the folder with the unwanted files and run rm *

and repeat from step 3 however many times

please mark this thread solved if this solves your problem

---

### Post by nerdtron on 2014-10-19
Move the first 10000 files of the "allpics" folder to "folder1"
```
mv -v `ls -1 /folder/with/allpics/ | head -n 10000` /destination/folder1/
```

Now you can view your pictures in /destination/folder1 and do your sorting/deleting.
Re-run the command to transfer the next batch.

Edit: added -v option on the move command to see the progress of moving

---

### Post by guber90 on 2014-10-19
> **abpabp said:**
> 1 first create a file called script.sh and paste this into it 

#!/bin/bash
find -type f >file
split -l 10000 file file2
cat file2aa|xargs mv -t '/home/testuser/testfolder' 2>/dev/null

changing /home/testuser/testfolder to wherever the folder you want to move files to

2 then chmod +x for that file to make it executable

3 cd to the directory with your pictures

4 next run the script 

e.g ./file.sh

 if the files aren’t the files you want 

5 then cd to the folder with the unwanted files and run rm *

and repeat from step 3 however many times

please mark this thread solved if this solves your problem
This didn't work, I got 0 pictures in destination folder.

---

### Post by O9aIevckc0 on 2014-10-19
can you remove the 2>/dev/null from the script and post some of the error messages if any ?

---

### Post by steeldriver on 2014-10-19
Do the filenames have any structure? for example if they are sequentially numbered you can do something like

```

mkdir newdir{0..9}

echo olddir/file{00000..09999} | xargs cp -t newdir0/
echo olddir/file{10000..19999} | xargs cp -t newdir1/
.
.
echo olddir/file{90000..99999} | xargs cp -t newdir9/

```

---

### Post by guber90 on 2014-10-19
> **nerdtron said:**
> Move the first 10000 files of the "allpics" folder to "folder1"
```
mv -v `ls -1 /folder/with/allpics/ | head -n 10000` /destination/folder1/
```

Now you can view your pictures in /destination/folder1 and do your sorting/deleting.
Re-run the command to transfer the next batch.

Edit: added -v option on the move command to see the progress of moving
I get tons of lines like this:
mv: cannot stat ‘f404055896.png’: No such file or directory

Just part with .png is changing its name.

I used this line:
mv  `ls -1 ~/recovered_output/Images | head -n 10000` ~/Desktop/test

Folder is located in home/recovered_output/Images and I want to copy on Desktop/test.

---

### Post by guber90 on 2014-10-19
> **steeldriver said:**
> Do the filenames have any structure? for example if they are sequentially numbered you can do something like

```

mkdir newdir{0..9}

echo olddir/file{00000..09999} | xargs cp -t newdir0/
echo olddir/file{10000..19999} | xargs cp -t newdir1/
.
.
echo olddir/file{90000..99999} | xargs cp -t newdir9/

```
No it is crazly random.

---

### Post by nerdtron on 2014-10-19
> I get tons of lines like this:
mv: cannot stat &#8216;f404055896.png&#8217;: No such file or directory 

Oh yeah. sorry, you should cd on the directory first, then run the mv command
```
 cd /home/recovered_output/Images
mv  `ls -1 /home/recovered_output/Images | head -n 10000` ~/Desktop/test 

```

---

### Post by guber90 on 2014-10-19
> **abpabp said:**
> can you remove the 2>/dev/null from the script and post some of the error messages if any ?
After runing script 3 or 4 times it just started working, I really don't get it but I'm happy :D, thx a lot mate I will mark topic as solved.

Thank you everyone for great help wish u best guys :).

---

