---
title: "Unable to login - sends me back to login screen"
date: 2014-02-24
forum: General Help
---

### Post by nihao123456ftw on 2014-02-24
[SOLVED]
Hello all,

Relatively new user here. After hours of trying to install amd proprietary drivers, which included a reinstall of the os, i have finally managed to get the drivers to work. The problem now though, is that for some reason i'm unable to login to my account. Sorry if anything I write down here is a bit bland in details, im just tired of debugging this stupid problem especially since it's late at night now.

When I type my password, the screen goes black as if it is about to load up my desktop, but then sends me right back to the login screen. No user accounts with passwords work, but the guest session works fine. 


Things i've tried:
-Creating a new user account and logging in through that (has the same problem)
-Adding a couple of permissions to 2 folders that I can't remember anymore (i'm seriously considering doing  something like chmod 777 / right now...) i think i tried /etc/lightdm, and something else
-Someone on google said that my /home folder for my account might not be being detected but it is
-Trying to look for various config files that for some reason everyone in the forums has but i dont (e.g /etc/lightdm/lightdm.conf, ~/.Xauthority)

Other notes:
-For some reason, control+alt+f# on login works only 50% of the time
-When it does work, I can login to any account through the terminal
-I'm tired so I won't answer this thread until tomorrow morning

Good night and thank you

EDIT:: Some more info that I think could be important:
-Using Ubuntu 13.10
-The last thing I did before this problem occured is install amd propietary drivers (fglrx) using the terminal, not the gui since that caused an error where I couldn't even get past grub

---

### Post by jeanjd63 on 2014-02-24
Hello
When you are logged in console (CTRL+ALT+F1) can you try to delete files :
**sudo  rm  .Xauthority  .ICEauthority**
and give the return for :
[B]df  -h
df  -i[/B]

---

### Post by nihao123456ftw on 2014-02-24
Hi,

I'm not sure where these .Xauthority and .ICEauthority files are, could you tell me where they're located? doesn't seem to be in my user's home folder.

If these df commands are for finding if i have enough space on my hard drive, i'm pretty sure I do. I haven't been using linux for long after all.

df -h:
filesystem:/dev/sda1 size:176G Used:15G Available:152G Use%:9% Mounted on:/
filesystem:none size:4.0K Used:0 Available:4.0K Use%:0% Mounted on:/sys/fscgroup
filesystem:udev size:3.9G Used:4.0K Available:3.9G Use%:1% Mounted on:/dev
filesystem:tmpfs size:787M Used:1.2M Available:786M Use%:1% Mounted on:/run
filesystem:none size:5.0M Used:0 Available:5.0M Use%:0% Mounted on:/run/lock
filesystem:none size:3.9G Used:0 Available:3.9G Use%:0% Mounted on:/run/shm
filesystem:none size:100M Used:0 Available:100M Use%:0% Mounted on:/run/user


df -h:
filesystem:/dev/sda1 size:184023124 Used:15668344 Available:158983852 Use%:9% Mounted on:/
filesystem:none size:4 Used:0 Available:4 Use%:0% Mounted on:/sys/fscgroup
filesystem:udev size:4018836 Used:4 Available:4018832 Use%:1% Mounted on:/dev
filesystem:tmpfs size:805792 Used:1212 Available:804580 Use%:1% Mounted on:/run
filesystem:none size:5120 Used:0 Available:5120 Use%:0% Mounted on:/run/lock
filesystem:none size:4028940 Used:0 Available:4028940 Use%:0% Mounted on:/run/shm
filesystem:none size:102400 Used:0 Available:102400 Use%:0% Mounted on:/run/user




I realised 1 other thing I did when I was trying to fix these problems:
I logged in as root from recovery mode and added +777 permissions for my user's home folder (and also /etc/lightdm/) because I was thinking that this was some sort of permissions error

---

### Post by nihao123456ftw on 2014-02-24
SOLVED: I didn't know that adding 777 permissions to root gives ownership to root and revokes the ownership of my main user account, and also the reason why I didn't see .Xauthority was because I only used ls and not ls -a. All I did was do "chown -hR [user's home directory] [username]" and then delete Xauthority using "rm ~/.Xauthority" (I swear I've done that before and said that there was no file there...)

---

### Post by bapoumba on 2014-02-24
Glad to see you fixed it. Please mark your thread as solved (under Thread Tools), thanks :)

---

### Post by Iowan on 2014-02-24
I marked it for you.
[Here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") is the technique I use. :)

---

