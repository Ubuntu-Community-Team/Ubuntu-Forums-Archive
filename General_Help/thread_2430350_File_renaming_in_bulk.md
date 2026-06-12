---
title: "File renaming in bulk"
date: 2019-10-31
forum: General Help
---

### Post by linux123as on 2019-10-31
Recently I have formated my hard drive that had a lot of important files on it. I used a data recovery software and recovered that files but the folder directories got corrupted and I got double folders and double files. One file/folder has no data in it and the other has the same name with _000 and it has all the data. My problem is that I havent thound a way to merge/rename files in bulk. I would need something like this: find -type f -not -name '*_000*' -delete. But this command works only on the directory that Im inand it only works on files and when I change -type to d it says directory not empty.

Thanks for helping

---

### Post by Skaperen on 2019-10-31
the "[COLOR=#800080][FONT=courier new]**rename**[/FONT][/COLOR]" command can do this.  it uses _Perl compatible regular expressions_.  to get all the details, do this:  [COLOR=#0000cd][FONT=courier new]**man rename**[/FONT][/COLOR]

---

### Post by linux123as on 2019-10-31
I know that but I cant write the command myself because I dont have the knowledge.

---

### Post by cmcanulty on 2019-10-31
Pyrenamer does what you want with an easy interface

[https://launchpad.net/ubuntu/+source/pyrenamer/0.6.0-1.2/+build/8439869]("https://launchpad.net/ubuntu/+source/pyrenamer/0.6.0-1.2/+build/8439869")

---

### Post by uRock on 2019-10-31
Pyrenamer is no longer available in the repos. If using gnome, then you can highlight multiple files, right-click select rename and it  will give you options.

---

### Post by cmcanulty on 2019-10-31
It is available at the link I gave and it successfully installed on my 18.04 computer. Post 18.04 I don't know.The last link on bottom of page.

---

### Post by TheFu on 2019-10-31
Learning simple regex is a basic skill for anyone using Linux.  Very worthwhile to know.  
You can also make a little script that builds a script.  

I don't understand why you don't just restore everything from backups. Seems much easier.

---

