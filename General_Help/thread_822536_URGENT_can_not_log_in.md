---
title: "URGENT can not log in"
date: 2008-06-08
forum: General Help
---

### Post by aks2008 on 2008-06-08
Hi
I got automatically logged out when I clicked on firefox icon. Only other program running was virtualbox but no virtual machine was started. Now I get your session lasted less than 10 seconds error when I try to log in.
This is the error I get when I try to log in with FAIL-SAFE gnome
"SESSION_MANAGER=local/user_laptop:/tmp/.ICE-unix/5966"
Any help will be appreciated

---

### Post by x1a4 on 2008-06-08
Hi,

Deleting /tmp/.ICE-unix/5966 should do the trick.

EDIT: stop GDM first.
Ctrl+Alt+F1
login as yourself
run ```
sudo /etc/init.d/gdm stop
```

now delete the file
```
sudo rm /tmp/.ICE-unix/5966
```

start GDM
sudo /etc/init.d/gdm start

---

### Post by aks2008 on 2008-06-13
Hi x1a4
 thanks for reply. but unfortunately i have reinstalled windows. Just curious though how does one stop GDM? Any command I used to type in terminal fail-safe mode I used to get some sorta segmentation error.
 and by the way last number in my original error(5966) used to change every time I tried to log in, so I am not sure deleting that specific file would have worked. May be whole /tmp/.ICE-unix needed to be deleted. But I couldn't do so as terminal would not accept any command. May be because GDM was running? I needed to have my laptop working urgently and I was not in mood for dual-boot(I have heard windows second dual boot doesn't work well anyway) so I did clean windows install. Thanks again for reply I will try to search forums for stopping GDM incase I need to come back to ubuntu.

---

### Post by FAJALOU on 2008-06-13
I would really really recommend trying Ubuntu again, Windows is so shoddy, especially with crashing, freezing, and all the 'wonderful' errors. Try dual-booting, that way if ubuntu fails you, you always have a Windows version to go back to.  Also for your error; a fresh install might do the trick.

---

### Post by wripley on 2008-06-13
> **aks2008 said:**
> Hi x1a4
 thanks for reply. but unfortunately i have reinstalled windows. Just curious though how does one stop GDM? Any command I used to type in terminal fail-safe mode I used to get some sorta segmentation error.
 and by the way last number in my original error(5966) used to change every time I tried to log in, so I am not sure deleting that specific file would have worked. May be whole /tmp/.ICE-unix needed to be deleted. But I couldn't do so as terminal would not accept any command. May be because GDM was running? I needed to have my laptop working urgently and I was not in mood for dual-boot(I have heard windows second dual boot doesn't work well anyway) so I did clean windows install. Thanks again for reply I will try to search forums for stopping GDM incase I need to come back to ubuntu.

all you have to do is open up a terminal window and type in 

```
sudo /etc/init.d/gdm stop
```

and then to start it back up i believe you type in 

```
sudo /etc/init.d/gdm start
```

also, you really shouldn't give up on ubuntu like that, i've jumped around between all sorts of os's in my day.  linux is hard to get used to, but ubuntu has the best interface and support forums (read: here) of all the other distros.  i used to be a diehard fedora guy, but couldn't keep up with the releases, which is another reason to choose ubuntu.  anyways, come back to the light side when you feel ready.

---

### Post by dldeskins on 2008-09-30
I have an identical problem.  When i delete the file, a new file i created and i still get the same error (different file).

Any more suggestions?

---

### Post by FAJALOU on 2008-10-01
dldeskins;

Try changing the permissions on the file.  I was getting issues with the .dmrc file, so it is a little different.   try this also:```
sudo chown <<username>>:<<username>> -R /home/<<username>>
```
To do this, log into failsafe terminal, and type in the code.  You could also click Ctrl+alt+F1 and that will hopefully get you a tty screen to put this into.  If this fails, try changing the permissions of $HOME itself with the commands; 
```
chmod -R 755 /home/chris
chown -R chris:chris /home/chris
shutdown -r now
```
Assuming your name is Chris (ie change chris to what your name is.)

Finally, you could try changing the permissions of the file to be what they are supposed to be...  which you can do with:
```
sudo chown -R chris:chris /tmp/.ICE-unix/5966
sudo chmod 777 /tmp/.ICE-unix/5966
```

I actually do not have this file... mine is a different number, so if the above works, great, if it doesn't, remove the file with ```
sudo rm /tmp/.ICE-unix/5966
```

Hopefully this works.  You could try changing the number also, mine is 6139.

As always return results so we can help further.  thanks.

---

### Post by dldeskins on 2008-10-01
Hey FAJALOU,

Thanks for the reply.

I have played with it quite a bit on command line and it looks like everything is good... I even have a connection to my home network and can ssh to my server.  All the files seem to be intact, that I can tell.

I will try what you suggest when I get home this evening. 

Thanks again

---

### Post by dldeskins on 2008-10-01
FAJALOU,

I did what you suggested but to no avail... I got the same results.  

Unless you guys can tell me why gnome is not starting, I am going to reinstall the system (right now, I am copying my Documents folder to my server to prepare for that.  As I said, it looks like everything is working, EXCEPT gnome.

I look forward to a reply.

---

