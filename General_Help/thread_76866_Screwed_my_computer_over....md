---
title: "Screwed my computer over..."
date: 2005-10-15
forum: General Help
---

### Post by billy314159 on 2005-10-15
Well, I accidently deleted my home folder.  I didnt create any other logins, so the only way I can log in is through the failsafe terminal.  If anyone could tell me how to make another home folder and set it up, i would be thankfull.

Please be very specific and dont omit any steps, becuase im new to linux and wont assume anything.


Thanks!

---

### Post by GTvulse on 2005-10-15
First recreate your home directory using the failsafe session:
```
mkdir /home/<your_login_name>
```
Then copy the files in /etc/skel:
```
cp /etc/skel/.bash* /home/<your_login_name>
```
Finally, make sure that everything belongs to your account, that is set up ownerships:
```
chown -R <your_login_name>:<your_login_name> /home/<your_login_name>
```
Now, do not reboot, type exit and the system will boot up into the graphical login screen. Log on as your user and all other configuration files will be created automagically for you.

EDIT: I left a an buggy typo in there... Hmm...

---

### Post by matthew on 2005-10-15
EDIT: dradul and I must have been typing at the same time. His method looks good as well. Try it first. Fall back with mine, although it probably won't be necessary. My method is more detailed and probably unnecessary and I just realized you only deleted the home directory, not your entire user account...my method is more for the "oh, no! I deleted all my users" scenario.

When you log in using the failsafe terminal you have root privileges so the good news is that you have the authority to create new users. Once you have logged in, at the command prompt you can add a user. Here's the command and an approximation of what will be asked of you by the adduser command with some sample answers.

```
#adduser
Enter a username to add: george
...
Enter new UNIX password: [you won't see anything as you type here]
Retype new UNIX password: [type it exactly as in the previous line]
...
Full Name []: George Washington
Room number []: [you can pick whatever you want for most of these or just hit <enter>]
Work Phone []:
Home Phone []:
Other []:
Is the information correct? [y/N] [type a "y"]
``` Then you will go back to the command line.

Now you need to make sure your new user has admin privileges so he can use sudo and so on. This can be done a few ways. There is a command "usermod" that does this, but it is probably easiest to add the user to the most important groups by editing the file by hand.
```
nano /etc/group
``` Will bring up the nano editor with a file similar to this in it. There may be fewer or more lines than this (I took this from my computer and changed the username and some minor details), but these are the most important for starters. Make sure your new user is a part of these groups by putting the username (I'll use george) at the end of the lines. If your old username is still in the file, just put the new one in its place.
```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:george
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:george,cupsys
fax:x:21:
voice:x:22:
cdrom:x:24:george,hal
floppy:x:25:george,hal
tape:x:26:
sudo:x:27:
audio:x:29:george
dip:x:30:george
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:george
sasl:x:45:
plugdev:x:46:george,hal
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
matt:x:1000:
lpadmin:x:104:george
scanner:x:105:george
admin:x:106:george
crontab:x:107:
ssh:x:108:
slocate:x:109:
messagebus:x:110:
``` Hope that helps and good luck!!

---

### Post by billy314159 on 2005-10-15
Thanks so much for the good info!!!

---

