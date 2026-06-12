---
title: "tar command not working correctly"
date: 2007-04-12
forum: General Help
---

### Post by Joespower on 2007-04-12
Hi all, I have a problem...

I'm using 6.06.1 LTS Server, and I installed the LAMP stack.  My hope is to use this machine as a joomla webserver.  Trouble is, when I downloaded the Joomla_1.0.12-Stable-Full_Package.tar.gz file and tried to extract it, tar doesn't create a directory of Joomla_1.0.12-Stable-Full_Package but instead just extracts everything into the folder that I'm in.  This has happened to me now on 2 similarly configured servers.  What's the deal?!?

Here's the exact command I'm using:

tar -zxvf Joomla_1.0.12-Stable-Full_Package.tar.gz

... but no directory is created.  I have to create it manually, copy in my tar.gz file, extract it, then delete the tar.gz file.  Its not hard, but it SUX!!

Help please...

---

### Post by bashologist on 2007-04-12
If you wanted to unpack all tar.gz in the cd; then you could do the following; fi
```
for i in *tar.gz; do mkdir "${i%.tar.gz}"; cd "${i%.tar.gz}"; tar -xvvzf "../$i"; cd ..; done
```

Edit: Made a little mistake there; it wasn't tested. This should work.

---

### Post by girishv on 2007-04-12
Hi,

tar will create the files as they were seen when you tarred them. If you go into a directory and make a tar file of all the files, you will NOT get back the directory name
when you untar it. You can check this by just listing the contents of the file
tar -ztvf file.tar

You need not copy the tar file into the directory where you want to extract it. You can directly extract it into the directory where you are working by giving the full path.

mkdir test
cd test
tar -zxvf ../file.tar

will untar the files in the directory test

Girish

---

### Post by WW on 2007-04-12
In other words, this is not a problem with the tar command.  That is how the Joomla tar file was created.

```

$ tar tzf Joomla_1.0.12-Stable-Full_Package.tar.gz 
administrator/
administrator/components/
administrator/components/com_trash/
administrator/components/com_trash/admin.trash.php
administrator/components/com_trash/trash.xml
administrator/components/com_trash/index.html
administrator/components/com_trash/admin.trash.html.php
administrator/components/com_trash/toolbar.trash.php
administrator/components/com_trash/toolbar.trash.html.php
administrator/components/com_newsfeeds/
administrator/components/com_newsfeeds/admin.newsfeeds.html.php
administrator/components/com_newsfeeds/admin.newsfeeds.php
...snip...
templates/rhuk_solarflare_ii/index.php
templates/css/
templates/css/offline.css
templates/css/index.html
templates/index.html
templates/404.php
$

```
The files that you see in the list are the files that will be extracted with the 'x' option. Note that they are not put into a Joomla subdirectory.

---

### Post by Joespower on 2007-04-12
Okay, I get it now... Thanks everyone!  I knew it had to be something like that since it was happening on both machines.

You guys ROCK! :guitar:

---

