---
title: "Troubles with rm"
date: 2013-08-22
forum: General Help
---

### Post by exw on 2013-08-22
Heya, 

I had a little "accident" where i right clicked the terminal and pasted a script i had in my clipboard. None of the files were actually deleted as far as I could tell.
But none of the commands could be used either, they were all putting out an error for example /bin/ls - no such file or directory
This mean that the server was broken and init scripts couldn't be run on boot up due to the same error. I did try rsyncing the core files from a backup machine, such as /usr and other directorys, but nothing helped, here are the commands which broke it:

```
        rm -R "$2/folder1"
        rm -R "$2/folder2"
        rm -R "$2/folder3"
        rm -R "$2/folder4"
        rm -R "$2/folder5"
        rm -R "$2/folder6"
```

Does anyone have any idea of what exactly broke and how to potentially fix it in the future, note that I did test these commands on another server that I had and the same thing happened

---

### Post by jjaison-daniel on 2013-08-22
actually $2 is nothing if you typed directly in terminal unless via script. so your command is equal to the following
```

rm -R "/folder1"
rm -R "/folder2"
rm -R "/folder3"
rm -R "/folder4"
rm -R "/folder5"
rm -R "/folder6"
```

Check any other command used or any other "rm" command like "rm /usr" or "rm $xxx/usr" ($xxx might be valid only inside script so outside script its empty then again its equal to /usr (not only with usr, bin and other directory, may used directly or indirectly)). As you said none of the files deleted how you are confirming this ?. If really none of the files deleted then better you can try rebooting the machine.:-k

"rm -R" is very danger.:(:frown:

---

### Post by cortman on 2013-08-22
Sounds like something else occurred, or you ran those rm commands with an argument in the CLI (like jjaison-daniel said). If indeed after a reboot you can't run commands like "ls", etc., sounds like your system is messed up.

---

### Post by exw on 2013-08-22
Okay, like i said, I tested the commands on a brand new server, just to see if it would happen again, and it did, if you have an ubuntu machine that you don't use, you can try it yourself

---

### Post by Impavidus on 2013-08-23
These commands can have deleted /folder{1..6}. If these directories didn't exist, nothing should have happened, which is clearly not the case. If this wasn't a root terminal already, nothing should have happened either – which shows why it's best not to keep root terminals open. The only thing that could have happened is that you deleted some system files (folder{1..6} may have been something like {bin,etc,usr}). The solution would be to boot from a live medium and restore your backup, or reinstall.

Unless something really strange is going on...

---

