---
title: "I made a mistake.... Help?"
date: 2008-03-30
forum: General Help
---

### Post by jhyland87 on 2008-03-30
ok, so here is the story, I was trying to install apache2 and php5 on my ubuntu 7.10 desktop, and I did the install just right, however I tried to make an index.php file in the www folder, it said I didnt have permissions. So I went to the users and groups administration, and I added my account (administrator) to the root group, and made the administration home folder the same as the root home folder..

I restarted my computer, now when I go to login as administrator with the right password, I get these errors..
> 
User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writeable by any other users.

I click ok..

> Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean  that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

I can go into safe mode and login as root, but what are the commands to reset the users and groups back to default

---

### Post by pseudo-random on 2008-03-30
```
sudo chown -R (yourname) /home/(yourname)
```
and
```
sudo chmod -R 644 /home/(yourname) 
```
also
```
sudo chown -R (yourname) /var/www
``` for the webroot

---

### Post by scragar on 2008-03-30
it would have been much better to just chown the /var/www folder than edit your permitions...

run this:
```
 sudo nano /etc/passwd
```
and change your home directory back. After that you should be able to log in using the cui and fix your problems.

---

### Post by jhyland87 on 2008-03-30
pseudo-random: I tried that and I get the exact same error :(

Scragar: I typed that into the terminal when I was in safe mode, and I can view the last line..

> **administrator:x:1000:0:Justin,,,:/root:/bin/bash**

Im guessing that ,,, should have a path between it... any idea?

---

### Post by scragar on 2008-03-30
no, just change:
```
/root
```
back to what it should be:
```
/home/Justin
```
ofcourse I'm guessing at your origional path, you'll know better than me.

---

### Post by jhyland87 on 2008-03-30
****, I dont remember it. let me do some guess work.

---

### Post by scragar on 2008-03-30
just check using:
```
ls /home
```

---

### Post by jhyland87 on 2008-03-30
ok, Thank you, it no longer says this:

> User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writeable by any other users.

But im still getting this:

> Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

Ill quote the entire log file for it

> 
(process:5839): Gtk-WARNING **: This proces is currently running setuid or setgid.
This is not a supported use of +GTK. You must create a helper program instead. For further details, see :

       [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initalize GTK+.

(process:5843): Gtk-WARNING **: This proces is currently running setuid or setgid.
This is not a supported use of +GTK. You must create a helper program instead. For further details, see :

       [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initalize GTK+. 
/etc/gdm/Xsession: Beginning session setup...
Can't create dir /home/administrator/Desktop
Can't create dir /home/administrator/Desktop
Can't create dir /home/administrator/Templates
Can't create dir /home/administrator/Public
Can't create dir /home/administrator/Documents
Can't create dir /home/administrator/Music
Can't create dir /home/administrator/Pictures
Can't create dir /home/administrator/Videos

(x-session-manager:5836): Libognomevfs-WARNING **:Unable to create ~/.gnome2 directory: Permission Denied
Could not create per-user gnome configuration directory `/home/administrator/.gnome2/`: Permisson Denied


---

### Post by scragar on 2008-03-30
are you sure /home/administrator was or origional home directory? sounds to me like it wasn't.

---

### Post by jhyland87 on 2008-03-30
I listed the folders in the /home... only one was administrator. and it got rid of the first error..

---

### Post by scragar on 2008-03-30
```
sudo chown -R $USER $HOME
```
try that, see if it fixes the problem.
```
startx
```
to launch x again without needing to restart.

---

### Post by jhyland87 on 2008-03-30
So I ran:
cd /home/administrator
then ls

got all of those files... public, bin, music, pictures, etc etc

---

### Post by jhyland87 on 2008-03-30
> **scragar said:**
> ```
sudo chown -R $USER $HOME
```
try that, see if it fixes the problem.
```
startx
```
to launch x again without needing to restart.

I ran those and after startx it and it seemed like it tried to get into the root account in the gui interface? threw a couple errors and then it looked like I was logged in as root, so I clicked on system to see if I could launch users and groups and it didnt let me, said it failed to launch.

I restarted and tried to log into administrator and nothing changed, same error log.

I am in recovery mode logged in as root btw.

---

### Post by scragar on 2008-03-30
launch it from a terminal, see what the message is:
```
gksu users-admin
```

---

### Post by jhyland87 on 2008-03-30
I am in the terminal, thats all recovery mode is, I cant login to administrator so I set a root password and logged in as root, however I cant login to root via the graphic gui interface, so its in recovery mode.

I ran that line.

> Root@Ubuntu-Justin:~# gksu users-admin
(gksu:5032): Gtk-WARNING **: cannot open display:


Root@Ubuntu-Justin:~# gksu users-administrator
(gksu:5032): Gtk-WARNING **: cannot open display:


---

### Post by jhyland87 on 2008-03-30
Thank you for the help so far by the way.... That account has a ton of things loaded on it, I use it to design websites, it would be a shame if I had to wipe it and reload it, I have so many needed files and installed programs that took days to install :(

---

### Post by scragar on 2008-03-30
can you log in normaly?

I'm above my expertise here, so no idea what your error is though, sure someone else will have a clue(a new thread would proberly get most attention).

---

### Post by jhyland87 on 2008-03-30
> **scragar said:**
> can you log in normaly?

I'm above my expertise here, so no idea what your error is though, sure someone else will have a clue(a new thread would proberly get most attention).

nope, thats just it, I cant login.. I just get errors and it logs me out.

You think I should make another new thread?

---

### Post by scragar on 2008-03-30
It would increase the number of people responding and the people who respond would be likly to have more knowledge on the subject.

---

### Post by jhyland87 on 2008-03-30
Alright, I hate making multiple threads about the same issue, but alrighty!

---

### Post by jhyland87 on 2008-03-30
anyone else have any ideas about this situation?

---

### Post by LeCzar on 2008-03-31
> **scragar said:**
> it would have been much better to just chown the /var/www folder than edit your permitions...

run this:
```
 sudo nano /etc/passwd
```
and change your home directory back. After that you should be able to log in using the cui and fix your problems.

How did you make this work? When I enter the ```
 sudo nano /etc/passwd
``` command, I am getting nothing but this console-like screen with no text that I could edit as you suggested. The ```
chown -R username /var/www
``` command did not work at all, there is no directory or file (or so) existing like that.

Thanks for all possible help!!

PS: I have got exactly the same problem: I changed my /home/username path to /root and got the same error messages.

---

