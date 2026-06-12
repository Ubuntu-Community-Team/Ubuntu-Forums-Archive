---
title: "Java File Permissions"
date: 2008-03-09
forum: General Help
---

### Post by Maxcore on 2008-03-09
Hey, I am having trouble with a game called "Runescape" If you don't know, RS is a Java based game that can be accessed through a web browser. My problem is when I run the game I get this error message: 
> Error_loader_nocache - Unable to create cache directory.
Runescape was unable to find a suitable place to store its temporary files. To solve this please either:

# Login to your computer as an 'administator' user, and then try loading RuneScape again. This should give it sufficient access to create its temporary cache.

# Or, create a new directory called c:/rscache or /rscache. If possible, set that directory to have full read+write permissions so that all users can write to it. Runescape should then detect that directory and use it for its files.

# If you are unable to do either of the above, then as a last resort you can tell RuneScape not to store any files on the harddisk. When entering the site and choosing between high-detail/low-detail also select 'Unsigned Applet Using Default Java' from the dropdown scroll at the bottom of the detail select page. You will need to do this everytime you load the game. The disadvantage of this is the game will load slower, so if possible use one of the top two solutions instead. 

I have tried editing the file permissions using nautilus and I created a folder at "/rscache" with these permissions:

Owner: max (me)
Folder Access: Create and Delete Files
File Access: --- (Whenever I change it to read + write it always goes back to this).

Group: max (me)
Folder Access: Create and Delete Files
File Access: --- (Whenever I change it to read + write it always goes back to this).

Others
Folder Access: Create and Delete Files
File Access: --- (Whenever I change it to read + write it always goes back to this).

How can I solve this?

---

### Post by tzulberti on 2008-03-10
Have you tried using "sudo" before the command you use?
NOTE: this you give you admin rights while executing the file.

---

### Post by Rocket2DMn on 2008-03-10
Try
```
sudo chmod 777 /rscache
```

---

