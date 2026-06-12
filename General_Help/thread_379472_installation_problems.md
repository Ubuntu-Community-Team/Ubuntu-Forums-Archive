---
title: "installation problems"
date: 2007-03-08
forum: General Help
---

### Post by toastN on 2007-03-08
After trying to remove the package **gambas**, using *aptitude remove* through the command line, I ran into the following problem: (verbatim error message follows):

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  gambas 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 2277kB will be freed.
Writing extended state information... Done
(Reading database ... dpkg: error processing gambas (--remove):
 files list file for package `gambas' contains empty filename
Errors were encountered while processing:
 gambas
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:"

At first I was not bothered by it, BUT THE SAME MESSAGE APPERED WHEN TRYING TO INSTALL UPDATES (verbatim error message follows:

"E: /var/cache/apt/archives/tcpdump_3.9.4-4ubuntu0.1_i386.deb: files list file for package `gambas' contains empty filename"

Also, any attempt to install **gnutella** were unssucessful, too, for the same reason. 

Any installation procedure gets interrupted because *gambas contains empty filename*.

I kindly ask for help with the following:

1. Explanation of the error message: "**files list file for package `gambas' contains empty filename**". What is the meaning of "file list for package", and what is the meaning of "empty filename"?

2. Procedure how to fix this problem.

3. Why is it not possible to install completely unrelated package like gnutella if the problem is with gambas?

Any help is greatly appreciated. Thank you.

---

### Post by waldschm on 2007-03-08
There is one other post on the forums regarding this issue [here]("http://ubuntuforums.org/showthread.php?t=343424") in which one user had a similar error corrected by entering the following in the terminal

```
apt-get -f install
dpkg --configure -a
```

however it appears as if it did not work for the the author of the thread. I think the problematic file is /var/lib/dpkg/info/gambas
so I would try examining that file for any extra newlines or obvious corruptions.

```
gedit /var/lib/dpkg/info/gambas
```

if that fails the following [web page]("http://www.finkproject.org/faq/usage-fink.php") has commands for addressing the issue under the header **Q5.19: I can't install or remove anything, because of a problem with a "files list file". ** This method works if you still have the .deb package file however make sure to modify the path appropriately. If you don't have the .deb perhaps you could download it again.

I don't really know what causes this error, perhaps someone more knowledgeable about package management could comment but hopefully one of these methods will work.

---

### Post by toastN on 2007-03-10
Thx 4 your suggestions. 

You are right - everything posted so far did not help. I researched all the forums for 3 days before asking for help.

The stuff posted on **fink** website helped but now I have the following problem:

**files list file for package `libglibmm-2.4-1c2a' is missing final newline**. 

Unfortunately, fink-website suggestions do not help here. I'll try to learn more about the package management since I do not even understand words like "files list file", "empty filename", or "missing final newline".

In the meantime it seem I'll have to deal with this problem as I used on Win - formatting and reinstalling :(

---

