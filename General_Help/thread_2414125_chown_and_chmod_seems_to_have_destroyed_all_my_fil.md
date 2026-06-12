---
title: "chown and chmod seems to have destroyed all my files"
date: 2019-03-06
forum: General Help
---

### Post by artist-wavenet on 2019-03-06
My hard drive failed, but the data on it was recoverable. Only the boot sector failed. I copied all my website mirror files from the failed disk to my new hard drive. And form there copied again again into a working directory so I would have a backup on the new drive. Used the command "sudo cp" to do the recursively copy all files and directory.

In the working directory I found all I was not able to edit my websites because all directories and files were owned by root. So I executed this sequence of commands:

```
sudo chown -R me:me /home/me/Websites
sudo chmod -R a=+rw /home/me/Websites
```

My expectation was the -R flag would recursively change ownership of all files and directories. But I found for directories this was not so. Ownership of the directory /home/me/Websites changed as expected. But ownership of al its subfolders did not. The file manage warned that the directory structure was in an inconsistent state, and that I might not be able to all file operations. In frustration I executed once again the command:

```
sudo chown -R me:me /home/me/Websites
```

All subdirectories of  /home/me/Websites disappeared. All files in this directory path show a size of zero bytes. How did all the directories and files get destroyed? What is the right way to do this? Is recovery possible without having to copy from backups?

---

### Post by HermanAB on 2019-03-06
Howdy,  

The permissions of files and directories are not handled the same.  A directory needs to have the execute bit set and with your a=rw parameters, you forced the x bit off.

More details here:
[https://linux.die.net/man/1/chmod](https://linux.die.net/man/1/chmod)

A directory with its x bit set allows the user to cd (change directory) into this directory, and access the files in it. The ability to read the names of files stored in this directory. The ability to rename files in the directory, create new files, or delete existing files, if you also have Execute permissions.

You could run find with exec to make a script that will recursively look for directories and turn the x bit on again.

An easier way could be to turn all permission bits, including the execute bit, on, for everything:
sudo chmod -R 777 /home/me/Websites

---

### Post by artist-wavenet on 2019-03-06
The command:
```
sudo chmod -R 777 /home/me/Websites
```
Made all subdirectories appear again, all files show their sizes again. Thanks.

---

### Post by oldfred on 2019-03-06
Seems like a better way as you have more control over what is executable. Isee post #8 & 10 by morbius1.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)
sudo chmod -R a+rwX,o-w /home/$USER/Websites
 sudo chown -R $USER:$USER /home/$USER/Websites
#where $USER should be your login name
#or to see user
echo $USER

---

### Post by HermanAB on 2019-03-07
Now that you can see the files again, you can try the following to turn the exec bits off for the files only:
sudo find /home/me/Websites -type f -exec chmod 0644 {} +

That should recursively make all the files rw for the user and r for group and world, which is reasonably sane, while leaving the directories alone.

Anyhoo, do read up on the find command - it is very powerful.

---

