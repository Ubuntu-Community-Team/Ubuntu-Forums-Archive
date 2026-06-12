---
title: "Changed whole user folder permisions to 755"
date: 2017-04-26
forum: General Help
---

### Post by pepe-aravaca on 2017-04-26
Hi,

in a moment of complete stupidity, instead of typing
chown -R user1 /home/user1

I typed automatically
chmod -R 755 /home/user1

So now I have the whole user tree files excutable and writable to anyone... 
Is there a way to restore the right permissions to files and folders to solve this mess?

Thanks.

---

### Post by Dennis N on 2017-04-26
There are no write permissions given by 755 except to the owner. 5 means you can read and execute only - with a directory, read means you can list the contents. execute means you can open the directory. With a file, read means you can open and read it;  excute is permission to run a script or program.

755 is normal for folders, To fix the files, in the terminal change directory to  /home/user1 and use this terminal command:
```
find ./ -type f -exec chmod -c 644 {} \;
```
which will change only files back to 644.

---

### Post by pepe-aravaca on 2017-04-27
Thanks for your quick and detailed answer, but aren't there scripts in user's subfolders or are they stored outside this tree?

---

### Post by Dennis N on 2017-04-27
Most if not all of the files in your home folder are non-executable. Many configuration files are there, but those are not executable files. All operating system and other software installed by the package manager would not go into your home folder. 

Some game or app that you might have downloaded yourself and put in your home folder would have executable files in its folder. You also may have put some of your own scripts there. If any of this is the case, you have to find those files and change them back to executable one at a time.

---

### Post by pepe-aravaca on 2017-05-10
Thank you again. I used your tips and everything is running wonderfully :D

---

