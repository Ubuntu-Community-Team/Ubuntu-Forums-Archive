---
title: "display manager hell"
date: 2007-03-14
forum: General Help
---

### Post by guitarmaniac on 2007-03-14
I've been having hell lately with my display manager(s).
I have installed kubuntu-desktop so I have both GNOME *and* but the display manager for both will not work.
I dont know why they are palying up, as I have exactly the same setup on another (newer) computer.
I used to have to restart X at the display screen or else it would hang indefinitly, and now I boot it up and I get the terminal, have to use startx, which logs me into GNOME even though the default session is set to KDE.
How can I fix this?

---

### Post by guitarmaniac on 2007-03-23
the command```
sudo dpkg-reconigure gdm
```has given me back a display manager, however its still buggy. I have to ctrl+alt+backspace EVERY time I log in.
I have too many downloaded programs and whatnot to do a fresh install so I really need a fix for this.
I read that```
gksudo gdmsetup
```and unchecking the box marked "Enable accessible login" will fix this but when I try to start gdmsetup I get this> luke@swan-desktop:~$ gksudo gdmsetup
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.
luke@swan-desktop:~$ 

any suggestions?

---

### Post by Arby on 2007-03-23
I agree it's worth trying to fix this but if you do have to reinstall you might find the following useful if you haven't seen it before. ```
dpkg --get-selections >package_list.txt
``` That command makes a list of all the packages you have installed on your system and stores it in a file. As long as you save this file somewhere that isn't going to get hosed during the reinstall you can  then run the following commands in order ```
sudo apt-get update
sudo apt-get dist-upgrade
dpkg --set-selections <package_list.txt		
sudo dselect
``` That lot will reinstall all the packages you had before. If you have a lot of stuff installed it can take ages to download all the packages but it's saved me a lot of pain more than once.

Caveats:
1) This only works for packages that you installed with Synaptic/Adept/apt-get. If you installed anything from elsewhere it won't be covered.
2) If you use any repositories other than the standard Ubuntu ones you'll need to edit your sources.list file accordingly following the reinstall.

You may already know about this or it may not be any help. Feel free to ignore, just my 2 cents

Arby

---

### Post by guitarmaniac on 2007-03-23
Well thats a good last resort (I knew there was a way to do that but I didnt know the command) but I really dont have the bandwidth to download all those packages again (plus I DO have a few programs that arent in the repositories.

Anyone know if theres a non GUI way of doing what I mentioned above?
I really need help on this.

---

### Post by guitarmaniac on 2007-03-23
bump

---

### Post by guitarmaniac on 2007-03-25
double bump

---

### Post by guitarmaniac on 2007-03-25
Super Bump!!!

---

### Post by Ramses de Norre on 2007-03-25
If I understand your issue correctly, you have a problem with gdm and kdm? (The so called display managers)

Have you enabled both? You can check that with sysv-rc-conf (in the repos).
Are there permission problems? You might want to check the permissions on /etc/gdm/ and check whether the files can be written to by root.
Have you tried reinstalling gdm/kdm?
Have you tried reconfiguring them? (dpkg-reconfigure)
Do you have a manually altered .xinitrc ?

---

### Post by guitarmaniac on 2007-03-26
what boxes should be crossed in sysv-rc-conf?
I'm fairly sure I haven't manually edited .xinitrc.

---

### Post by Ramses de Norre on 2007-03-26
Well, enabling both seems like asking for trouble to me. So check one of them and disable the other one.

---

### Post by guitarmaniac on 2007-04-10
Its been about two weeks and I still cant get this damn thing to work, and to make matters worse, I've somehow stuffed up the display manager on my own machine as well as my girlfriends!!!

I played around with sysv-rc-conf but I dont want to play too much for fear of making it worse.

---

### Post by TheMono on 2007-04-10
OK, it sounds like it isn't going to get any WORSE here, so what I would suggest is killing GDM completely and switching to KDM

sudo apt-get remove gdm && sudo apt-get install kdm

See what happens when you do that... Worst case you can reinstall gdm from the command line.

---

### Post by guitarmaniac on 2007-04-13
> **TheMono said:**
> OK, it sounds like it isn't going to get any WORSE here, so what I would suggest is killing GDM completely and switching to KDM

sudo apt-get remove gdm && sudo apt-get install kdm

See what happens when you do that... Worst case you can reinstall gdm from the command line.

I've tried that, didnt work. I cant understand why it would crash at startup! Is there a file that I cant post to help diagnose this problem?

I really need a fix to this as my mother inlaw is completely computer illiterate and seeing a terminal come up makes her freak out. PLEASE DON'T MAKE ME LET HER GO BACK TO XP!!!

---

### Post by guitarmaniac on 2007-04-13
bump

---

