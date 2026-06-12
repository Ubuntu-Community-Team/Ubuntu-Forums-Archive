---
title: "[SOLVED] Cant empty a file out of trash permission denied"
date: 2008-06-12
forum: General Help
---

### Post by tunznath on 2008-06-12
OK I have a folder with 2 files in it in the trash - the folder permissions say create and delete, the folder in the 1st folder has permission set as access files, the files in this folder have permission set as read and write - I cant change the permissions -get a thing saying operation not supported by backend - ???????

in the first folder I cannot apply the permissions to the enclosed files either??????
How do i delete these

---

### Post by drs305 on 2008-06-12
Added: My preferred solution is posted in #15 and doesn't require a sudo delete.

> **tunznath said:**
> OK I have a folder with 2 files in it in the trash - the folder permissions say create and delete, the folder in the 1st folder has permission set as access files, the files in this folder have permission set as read and write - I cant change the permissions -get a thing saying operation not supported by backend - ???????

in the first folder I cannot apply the permissions to the enclosed files either??????
How do i delete these

If these are in hardy's user trash. The first command will show you what is about to be deleted. The second will delete them.
```

sudo find ~/.local/share/Trash
# If you use the following command, MAKE SURE YOU COPY THE ENTIRE COMMAND 
sudo rm -rf ~/.local/share/Trash
```

---

### Post by Radioman991 on 2008-06-12
I had a similar issue.  Had to log in as root, and as root, browsed to the trash folder and deleted...cleaned them right out.

Took me a couple searches to find the right path, so search the forums, and you should find it.  I can't look at my install now, as I am working and sadly running XP on the company laptop :-(

Regards, PK

---

### Post by aysiu on 2008-06-12
If you use the *sudo rm -R* command, be sure to **paste** the command in [the terminal](http://www.psychocats.net/ubuntu/terminal). Do not retype it. It can be a very dangerous command if you mess it up.

Alternatively, you can use the command ```
sudo chown -R *username:username* /home/*username*
``` where *username* is your actual username so you have ownership of all the files in your home directory (as it should be), including the trash.

---

### Post by tunznath on 2008-06-12
I did this

nath@nath-laptop:~$ sudo chown -R nath:nath /home/nath
[sudo] password for nath: 
chown: cannot access `/home/nath/.gvfs': Permission denied
nath@nath-laptop:~$ 

Help
Please

---

### Post by tunznath on 2008-06-12
OK 
I did the sudo  that drs305 said to do now theres nothing in the trash,
THANKS drs305. 
one other problem - the trash still has a full icon?

---

### Post by aysiu on 2008-06-12
Great. Now can you empty the trash?

---

### Post by drs305 on 2008-06-12
> **aysiu said:**
> If you use the *sudo rm -R* command, be sure to **paste** the command in [the terminal](http://www.psychocats.net/ubuntu/terminal). Do not retype it. It can be a very dangerous command if you mess it up.

Alternatively, you can use the command ```
sudo chown -R *username:username* /home/*username*
``` where *username* is your actual username so you have ownership of all the files in your home directory (as it should be), including the trash.

Every time I mention the sudo rm command I get nervous. I think I'll incorporate your method in the future. I don't want to be responsible contributing to a disaster!  ;-)

---

### Post by tunznath on 2008-06-12
ok shut down and restarted  - icon back to normal - thanks once again everyone for the quick response - i thought the trash with stuff in it that couldnt be deleted was going to drive me nuts - always a little full icon, NOW that I know how to do it if it happens again WHY did it happen - is this common.

Thanks Nath

OK must learn the cli terminal thing - used to have an amiga 500 where i used to use the cli - but have got lazy due to windoze

---

### Post by aysiu on 2008-06-12
You probably used some root-run application to delete those files, so they were owned by root.

Did you, by chance, run a root graphical app with *sudo*?

That can do it sometimes. Read more here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by tunznath on 2008-06-12
Hi Dont know how or what I did only had ubuntu for about a week or 2 - still trying to get it all up and running, and still learning  - i will read up on running sudo graphically

---

### Post by markharding557 on 2008-06-13
> **drs305 said:**
> If these are in hardy's user trash. The first command will show you what is about to be deleted. The second will delete them.
```

sudo find ~/.local/share/Trash
# If you use the following command, MAKE SURE YOU COPY THE ENTIRE COMMAND 
sudo rm -rf ~/.local/share/Trash
```

this solved my issue too cheers

---

### Post by rotary12 on 2008-06-13
> **drs305 said:**
> If these are in hardy's user trash. The first command will show you what is about to be deleted. The second will delete them.
```

sudo find ~/.local/share/Trash
# If you use the following command, MAKE SURE YOU COPY THE ENTIRE COMMAND 
sudo rm -rf ~/.local/share/Trash
```

mys too thanks

---

### Post by yragrelluf on 2008-06-18
Used drs305 advice, under precautions, because that is a very dangerous command. Make sure you explore other options first.

---

### Post by drs305 on 2008-06-18
I am going to try not to post the sudo rm solution in the future as I always feel a bit uncomfortable recommending it to others, even with the warning. In the future, once you find the offending trash owned by root in the local trash folder, I am going to recommend:
```
sudo chown -R username:username ~/.local/share/Trash[/
rm -r ~/.local/share/Trash
```

This changes ownership of all root trash in the user's trash bin to the user. The user can then delete it without using administrative powers. I'm noting this method in my earlier post as well.

---

