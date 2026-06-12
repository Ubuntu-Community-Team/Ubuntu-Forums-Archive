---
title: "[SOLVED] Ran out of disk space during kernel upgrade - can't log in"
date: 2008-06-20
forum: General Help
---

### Post by KenBW2 on 2008-06-20
Last night I got the notification that there were updates available for Xubuntu. They were something about linux-headers, linux-kernel-ubuntu or something like that. Anyway, mid-installation my PC ran out of disk space (yes, I'm pretty pushed for space - 2GB HD) and that obviously caused problems.

After restarting I got a kernel panic error, dropped to a shell to delete a few things to free up space and, as the system recommended, did 'dpkg --configure -a'. I think that completed the installation successfully.

I now have 2 kernels at GRUB, and can boot either with the same results. It takes me all the way to the login screen with no problem, but when I try to log in it throws this at me:

> 
Your session lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix the problem.
[View details (~/.xsession-errors file)]
--------------
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: Permission denied
--------------

I'm then returned to the login screen.

I can log in on a shell (Ctrl+Alt+F1,2,3 etc) and I've deleted a few things from there. 'df' tells me I have 43MB free space on /, which has been enough in the past.

Any help greatly appreciated :(

---

### Post by drs305 on 2008-06-20
You may need to empty your trash folder. These instructions are for hardy and will also clean out any root-owned trash that may have ended up in your local trash bin.

```
sudo chown -R **username:username** ~/.local/share/Trash
rm -r ~/.local/share/Trash

```

Do you have a separate boot partition? The number of older kernels keeps growing. If you have a separate, small boot partition it may be full of older kernels that need to be deleted.

---

### Post by PmDematagoda on 2008-06-20
Try dropping to a tty by pressing Ctrl+Alt+F1, login and then run:-
```
startx
```
or 
```
sudo startx
```
if the above didn't work.

---

### Post by dracayr on 2008-06-20
before hardy, the trash should be in ~/.Trash.

---

### Post by KenBW2 on 2008-06-20
@PmDematagoda
I did the startx, and it told me X is already running - X can successfully start, it's logging in that's the hurdle

@ drs305 & dracayr.
I did
```

sudo chown -R username:username ~/.Trash
rm -r ~/.Trash

```
and it's made a difference - I now get this error at login:
> 
GDM could not write to your authorization file. This could mean you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator


A quick look at df says I still have 43MB free space on /. Could it do any harm to chown my home directory? Maybe that's the problem
I'm not totally sure about the syntax, but here's a guess:
```

sudo chown -R kenneth:kenneth /home/kenneth/

```
and a chmod as well?

Incidentally, I'm doing all this on the old kernel (2.6.22-14-generic). Is that right?

---

### Post by drs305 on 2008-06-20
> **KenBW2 said:**
> 
I'm not totally sure about the syntax, but here's a guess:
```

sudo chown -R kenneth:kenneth /home/kenneth/

```



Yes, that would be the correct command to ensure you are the owner of your home folder.

---

### Post by KenBW2 on 2008-06-20
I'm back to the original error message
> 
Your session lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix the problem.
[View details (~/.xsession-errors file)]
--------------
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: Permission denied
--------------


I'm not sure whether that's a good or bad thing :confused:

What about chmod?

---

### Post by drs305 on 2008-06-20
To remove any trash you might have in / run the following to see what is there:
```
sudo ls /root/.local/share/Trash/files
```

If there are a lot of files, or large files:
```

sudo chown -R kenneth:kenneth /root/.local/share/Trash/files
rm -r /root/.local/share/Trash/files

```

I know that chmod is sometimes necessary if the .dmrc file is messed up but don't know in this particular case. Someone else will have to chime in on that.

---

### Post by KenBW2 on 2008-06-20
Why are you focussing on the Trash? I have sufficient free space. I'll try it anyway

---

### Post by KenBW2 on 2008-06-20
Sorry, I should've said - I'm running Xubuntu Gutsy (the one in my signature), so as dracayr said the location is different. Anyway, there's only one small file in root's trash, but I deleted it anyway.

Still no banana.

---

### Post by KenBW2 on 2008-06-20
I did an ls-l on my home folder and it's showing:
> 
**Folders:**
drwxr-xr-x 2 kenneth kenneth <size> <date> <time> <name>
**Files:**
-rwxr-xr-x 1 kenneth kenneth <size> <date> <time> <name>


so it looks like they're all owned by me.

---

### Post by drs305 on 2008-06-20
> **KenBW2 said:**
> Why are you focussing on the Trash? I have sufficient free space. I'll try it anyway

It seemed to me that this would have been a simple solution if the problem was the second part of the error message you were receiving:
```

If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.
```

Trash takes up space and is not always accounted for when a system reports how much free space is available. This apparently is not the cause of the problem so other avenues will have to be explored.

Hope you get this resolved.

---

### Post by KenBW2 on 2008-06-20
Not quite sure why, but this fixed the problem
```

sudo chmod a+w /tmp

```

Hope it helps anyone else with this problem

---

