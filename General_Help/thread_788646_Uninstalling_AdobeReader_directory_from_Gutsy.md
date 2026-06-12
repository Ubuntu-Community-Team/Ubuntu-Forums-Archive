---
title: "Uninstalling AdobeReader directory from Gutsy"
date: 2008-05-09
forum: General Help
---

### Post by rtrdom on 2008-05-09
I have downloaded AdobeReader 8.1.2 as a directory only. Have not inintentionally installed
it in Gutsy. Would like to remove it from computer but Gutsy says I do not
have permission, even when trying with sudo or su. Help appreciated.

---

### Post by Patb on 2008-05-10
Sounds strange, Rtrdom.  

In a terminal, try going to the directory it is in and check the output of:
```
ls -l
```
If that gives you no further clues, perhaps you could post the output here.  

Cheers, Pat.

---

### Post by rtrdom on 2008-05-10
drwxr-xr-x  5 root root      4096 2008-04-28 18:42 AdobeReader_enu-8.1.2
Above is the applicable listing for the problem directory. I have tried su, sudo,
aptitude, apt-get with both and the result is still...I don't have authority to
remove it.

---

### Post by Patb on 2008-05-11
Rtrdom. By the looks of it, you should be able to delete that directory and all files and subdirectories under it using this command in a terminal from that same directory:
```
sudo rm -r AdobeReader_enu-8.1.2
```
That will require that you confirm each directory and file deletion.  Check the details with "man rm".  If you have lots of files you can force deletion without prompts (take care!) with the option -rf instead of just -r.

If it doesn't work, there may be some other problem.  If you get any errors in the terminal, please post the output.  

Cheers, Pat.

---

