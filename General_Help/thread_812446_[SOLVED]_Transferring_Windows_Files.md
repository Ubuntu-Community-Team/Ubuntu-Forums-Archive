---
title: "[SOLVED] Transferring Windows Files"
date: 2008-05-29
forum: General Help
---

### Post by dstein on 2008-05-29
I would like to transfer all my personal files from my Windows partition to Ubuntu. Both operating systems are installed on the same machine as a dual boot. The Windows partition is mounted in Ubuntu.

I would like to know if there is any way to transfer these files in such a way that all the ASCII text files will have the CRLFs converted to LF, and so that all files will not be automatically marked as executable, which seems to be the case when dragging-and-dropping with Nautilus.

Any help would be greatly appreciated. A method using the terminal would be preferred, as I always like to learn new tricks from the terminal. However, I am really just looking for any way to transfer my files in this way. Thanks.

---

### Post by dstein on 2008-05-29
Ah, in addition to the non-executable setting, I would like all permissions to be set as if the files and directories had been created in Ubuntu - that is, I do not want the files to be set as read-only. I would like each file's permissions to mimic the permissions that would have been set by default had the file been created in Ubuntu, now Windows.

Thanks again.

---

### Post by tamoneya on 2008-05-29
i dont have a method for CRLF but the easiest way to deal with the permissions/executableness would be to just you chmod:```
sudo chmod -R 644 /directory/with/my/files
```This sets all the files to have no execute and to be read write for the owner and just read for everyone else.

---

### Post by dstein on 2008-05-29
Ah, thanks tamoneya. I considered something similar, but I first created an empty directory on my desktop to check the default permissions, and there was a dash in the 'executable' category. I was worried that a recursive usage of chmod would not set directories this way. However, I am beginning to think that it would not matter. Please let me know otherwise, or if you are aware of any differences between the default permissions for files versus directories (especially regarding that dash in the exexutable option).

Thanks

---

### Post by mike2357 on 2008-05-30
To convert CRLF to LF:

tr -d '\r' < inputfile > outputfile

Where "inputfile" is the name of the txt file you copied from Windows, and outputfile is the name of the converted file.  This works by removing all occurances of CR, which in unix is '\r'.

You can type "man tr" to learn more.

There is a program you can try called "dos2unix".  It can be installed with the following command:

sudo apt-get install tofrodos

---

### Post by dstein on 2008-05-30
Is there any type of find feature that I can use to isolate all the .txt files that were transferred (they are scattered) and then use dos2unix to convert them? Thanks.

---

### Post by clong83 on 2008-05-30
dos2unix doesn't work recursively that I know of.  Beyond writing a small script to check recursive directories yourself (which is one option...), there is another way...

cd into your root directory that was transferred, say for example, /usr/home/user/TRANSFERREDDIRECTORY.

Then just do the following commands:
```
dos2unix -fb ./*.txt
dos2unix -fb ./*/*.txt
dos2unix -fb ./*/*/*.txt
dos2unix -fb ./*/*/*/*.txt
```

And so on and so forth until you run out of subdirectories.  Hope that helps.

---

