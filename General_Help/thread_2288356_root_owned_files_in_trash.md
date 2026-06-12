---
title: "root owned files in trash"
date: 2015-07-26
forum: General Help
---

### Post by zathras1974 on 2015-07-26
I've run into a slight problem, which I'm hoping someone might be able to assist me with.

I recently restored my system with a fresh install of the latest version of Ubuntu Gnome (15.04). After the restore I pulled my files from an external HDD. After I attempted to access them I found the backup program had made the owner root, so I couldn't read them. So, I figured, "No problem! I'll just sudo nautilus, change the ownership, and all will be cool!". That worked, but then I made a boo-boo. I deleted a directory that was a duplicate while I still had elevated access. So now I can't empty the trash of those files with my normal user.

"But wait", you say, "just sudo nautilus again and delete the files". Ahhh, I wish it was that easy. When I try that and click on the trash, it gives me an error of "This location could not be displayed. Sorry, could not display all the contents of 'trash:///': Operation not supported". 

Granted, the files aren't that large, and won't affect my day to day usability, but my OCD is having a conniption. Is there a command in the CLI I can use to squash these files, or will I just have to grow to live with them?

Thanks for reading! :)

---

### Post by bapoumba on 2015-07-26
Yes there is, but you need to be careful with the rm command, as it will remove the files without any option to get them back.

First open a terminal and cd to the file where they are, to the place you were trying to delete them from the gui. Then ls will list all the files present there. Remove them one by one if they are not that many, that will be safer.
```
cd ToTheTrashFile
ls FileToRemove
sudo rm FileToRemove

```
rm accepts wild cards such as ? and * but once again, be careful using them with sudo. To test proof your command, you can use ls, that will show the files you will be acting upon.
[http://linux.die.net/man/1/rm](http://linux.die.net/man/1/rm)

---

### Post by zathras1974 on 2015-07-27
That worked like a charm. Thank you very much. :)

Marking thread as solved. :)

---

### Post by bapoumba on 2015-07-27
Glad to see you worked it out :)

One thing though, running nautilus as root, *with sudo*, was calling for problems. At least, please use **sudo -H**
[http://ubuntuforums.org/showthread.php?t=2225832&p=13032745#post13032745](http://ubuntuforums.org/showthread.php?t=2225832&p=13032745#post13032745)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

(thanks Vladlenin5000)

---

