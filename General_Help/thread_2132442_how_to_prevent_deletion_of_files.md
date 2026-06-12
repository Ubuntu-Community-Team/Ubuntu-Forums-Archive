---
title: "how to prevent deletion of files"
date: 2013-04-04
forum: General Help
---

### Post by faust99 on 2013-04-04
I have a number of valuable directories on my system whose accidental deletion I prevent by setting permissions to 'access only'. However, this method does not seem to work for individual files, which can still be sent to the trash despite having their permissions set to 'access only'. Would somebody please explain why setting the permissions of individual files in this way does not prevent their deletion?

---

### Post by Slim Odds on 2013-04-04
> **faust99 said:**
> I have a number of valuable directories on my system whose accidental deletion I prevent by setting permissions to 'access only'. However, this method does not seem to work for individual files, which can still be sent to the trash despite having their permissions set to 'access only'. Would somebody please explain why setting the permissions of individual files in this way does not prevent their deletion?
What do you mean by 'access only'? How did you set this?

---

### Post by papibe on 2013-04-04
Hi  faust99.

To avoid a file being delete, set 'access only' to the parent directory where the file lives (not the file itself).

Let us know how it goes.
Regards.

---

### Post by faust99 on 2013-04-22
Thank you papibe-your method with directories works fine. 

But it's not possible to do this for individual files?

---

### Post by faust99 on 2013-04-22
> **Slim Odds said:**
> What do you mean by 'access only'? How did you set this?

Right click on a dir then adjust its permissions...

---

### Post by dino99 on 2013-04-22
everything is possible, using the desired rights: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
and even hidding the files/folders themselves

---

### Post by Vaphell on 2013-04-22
you can also create hardlinks to the files you want to protect though it's more about prevention of accidental deletion than making sure file X exists in dir Y.

hardlink is another filesystem handle for a file that can be created in some other directory (that means the same file can exist in N places with no duplication). The file is deleted only when the last handle is removed.



and file permissions don't work because you don't change the content of the file, you change the content of the directory. Analogy time: when you tear out the page from the book, you modify the book, not the contents of the page ;-)

---

### Post by faust99 on 2013-04-22
Thanks guys. From dino99's link, it says that: 

"write restricts or allows creating new files or deleting files in the directory. (Caution: write access for a directory allows deleting of files in the directory even if the user does not have write permissions for the file!)"

This seems to imply that a it is not possible to protect individual files within a directory; i.e. that either the entire directory's permissions are affected, or none.

---

### Post by papibe on 2013-04-22
> **faust99 said:**
> This seems to imply that a it is not possible to protect individual files within a directory.
There is a way, but it is not available through the GUI interface.

If you feel comfortable using the terminal, take a look at the command:
```
chattr
```
[Here]("http://www.cyberciti.biz/faq/linux-write-protecting-a-file/")'s an example on how to use it.
Regards.

---

### Post by faust99 on 2013-04-22
Thanks papibe-that's easy enough and exactly what I was trying to do.

---

