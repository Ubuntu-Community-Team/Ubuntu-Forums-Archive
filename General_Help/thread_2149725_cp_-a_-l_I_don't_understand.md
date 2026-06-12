---
title: "cp -a -l I don't understand"
date: 2013-05-29
forum: General Help
---

### Post by Ready2DropWin on 2013-05-29
I am very confused by this command. Let me explain what am doing with this command to help you understand my confusion. I have a root folder, lets call it root. In this root folder I have four folders. Three folders are numbers 1,2,3. Right now the number folders are empty. The last folder is the data folder. Inside the data folder I have three files A,B,C. Now if I run 

```
cp -a -l data 1
```

Then the files A, B, C are copied to folder 1. now if I delete file A from the data folder, and rerun the command on folder 2, it will copy just B and C

If I go back to folder 1 the A file is still there, and this is where I am confused. If I created a link by using -l, why is the file still accessible in the 1 folder? These are 1 GB files we will say. If I copy my data folder 20 times, and check the disk space, the size doesn't change. So I know it is creating links, I am just confused of how this works.

Thanks for the help in advance.

---

### Post by Impavidus on 2013-05-29
It's creating hard links. They don't use disk space, contrary to a normal copy, but when you delete the original, the copy stays. That's because the data isn't really copied, but you make a second file name refering to the same block of data on your disk

---

### Post by Ready2DropWin on 2013-05-29
Thanks, that makes since.

---

### Post by HiImTye on 2013-05-29
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
if you just want symlinks, use
```
ln -s /path/to/folderOrFile /path/to/link
```

---

