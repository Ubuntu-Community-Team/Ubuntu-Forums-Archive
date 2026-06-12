---
title: "Script that can copy a directory if a specific file is in it"
date: 2006-09-13
forum: General Help
---

### Post by andersl on 2006-09-13
Hi

I was wondering if any of you know how to make a script that searches through  folders for at specific filename and when that filename is found the script should copy the directory that the file is in to another location. Ive used the following line 

```

find /home/user/ -name "*IMG.JPG" | xargs -i cp {} /home/user/images

```

this finds all my images from my digital camera that I have lying around in my homedir. The problem is that it dumps all files in the same folder and I would like my images still to be sorted in the original fonders. So if I have /home/user/folder1/folder2/folder3/file_IMG.JPG then I want all files from folder3 to be copied to /home/user/images/folder3.

hope you know what I mean :)

Anders

---

### Post by Tomosaur on 2006-09-13
```
if [ $(find $HOME/folder1/folder2/folder3/ -name *IMG.JPG) ]
then
  cp -r $HOME/folder1/folder2/folder3/ $HOME/images/
else echo "file not found"
fi

```

This will search the /home/user/folder1/folder2/folder3 directory for files ending with IMG.JPG, and if any are present, copies that folder into /home/images (so you will end up with /home/images/folder3

---

### Post by mbeierl on 2006-09-13
The previous post is close, but will copy all files, not just images from the specified subdirectory.

What I *think* you might want is the --parent option to cp, like so:

```
find /home/user/ -name "*IMG.JPG" | xargs -i cp --parent {} /home/user/images
```

That tells cp to append the source directory to the target directory path.

You can also do it without the use of xargs (useful if there is going to be a large number of files) like so:

```
find /home/user/ -name "*IMG.JPG" -exec cp --parent {} /home/user/images \;
```

---

### Post by andersl on 2006-09-14
when I run the last one that you suggested mbeieri I get this 

```

cp: cannot make directory `/home/user/images/folder3': Permission denied

```

(I havent tried any of the others that was suggested yet)

---

### Post by DoctorMO on 2006-09-14
replace [user] with your username.

---

### Post by andersl on 2006-09-14
ah yes I know that could be a problem! :)

Im changing the path when I post in the forum! The real error is

```

cp: cannot make directory `/home/anderslaursen/billeder_fra_kamera/windows/c/Documents and Settings': Permission denied

```

---

### Post by Ramses de Norre on 2006-09-14
Do you have write permissions? Can you do
```
mkdir -p /home/anderslaursen/billeder_fra_kamera/windows/c/Documents\ and\ Settings
```

---

### Post by Tomosaur on 2006-09-14
Are you trying to write to a mounted NTFS drive by any chance?

---

### Post by andersl on 2006-10-13
I was trying to copy from a mounted NTFS drive. That gave me permissionproblems. Ive fixed that now.

My problem now is that the command

```
find /home/user/ -name "*IMG.JPG" | xargs -i cp --parent {} /home/user/images
```

only copies the files with names containing IMG.JPG. But what I want is to copy ALL files in the folders where a file which name contains IMG.JPG is found.

---

### Post by andersl on 2006-10-13
I've been thinking

is it possible the to get a list of directories that contain files which filename contains IMG.JPG and then take that list and give it to cp which copies all the directories and underlaying directives and files?

---

