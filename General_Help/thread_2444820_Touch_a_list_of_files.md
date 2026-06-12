---
title: "Touch a list of files"
date: 2020-06-04
forum: General Help
---

### Post by raleigh3 on 2020-06-04
I often touch a file so it shows up at the top of the file manager.

Is there a way to touch a list of files instead of touching each one individually?

Thanks.

---

### Post by Holger_Gehrke on 2020-06-04
The 'touch' command line tool will accept a list of files (for example 'touch firstfile secondfile thirdfile'). How you can do this in a file manager depends on the program you're using. On XUbuntu in Thunar there is something called 'user-defined actions' which gives you the ability to define commands to run on selected files from the context menu. A short look at 'apt search caja' shows a plugin for caja named 'caja-actions' which seems to do something similar in Mate's file manager.

Holger

---

### Post by raleigh3 on 2020-06-04
touch test1 test2 works, but I have to manually specify each file.

Looking for  something automated.

---

### Post by lvm on 2020-06-05
Define automated, and keep in mind that automated does not mean mind reading. You want to touch a list of files, so you have to pass this list to a program somehow, and one way of doing it by listing files on the command line. If you have a list of files in a text file you may pass it to touch by running " touch `cat filelist` " or better still " xargs touch <filelist ". If by 'automated' you mean 'integrated with my favourite file manager' it depends on the file manager e.g. in mc you can run a program for selected files by using macro substitution e.g. " touch %t " or %T, %u, %U.

---

### Post by ActionParsnip on 2020-06-05
Something like

```

#!/bin/bash
for file in filename1 filename2 filename3
do
touch $file
done
exit 0

```

---

### Post by HermanAB on 2020-06-05
Here are some ideas:

Touch everything:
$ touch *

Make a list of filenames:
$ ls | tr '\n' '\n' > filelist

Now you can edit the list and remove filenames you don't want to touch.

Use cat to pass the filenames to touch:
$ cat filelist | touch

Use redirection to pass the filenames to touch:
$ touch < filelist

---

### Post by lvm on 2020-06-06
> **HermanAB said:**
> 
Use cat to pass the filenames to touch:
$ cat filelist | touch

Use redirection to pass the filenames to touch:
$ touch < filelist

touch cannot read filenames from stdin

---

### Post by raleigh3 on 2020-06-06
#!/bin/bash
# 
#----------------------------------------------------------------------------
# 
# If I make a list of files I want to touch in files.txt, this
#  will touch all the files in that list.
# The files must be in a text file with each on it's own line
#----------------------------------------------------------------------------
<files.txt xargs -d'\n' touch

---

