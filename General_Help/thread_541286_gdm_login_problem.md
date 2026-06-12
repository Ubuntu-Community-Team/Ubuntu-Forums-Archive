---
title: "gdm login problem"
date: 2007-09-02
forum: General Help
---

### Post by multi on 2007-09-02
I'm new to linux and I installed Xubuntu on an old pc. I wanted to be able to login remotely, so i tried this howto: [http://ubuntuforums.org/showthread.php?t=488207&highlight=remote+login+x11vnc](http://ubuntuforums.org/showthread.php?t=488207&highlight=remote+login+x11vnc)

Thing is, when I try to boot from the harddrive i get a blue and grey error screen with the following text:

"The GDM user 'gdm' does not exist. Please correct GDM configuration and restart GDM."

Obviously gdm doesn't start and I get presented with a non gui login screen. Logging in with my normal user account doesn't seem to work anymore, I just get  "login incorrect" when i try. 

Tried booting through recovery mode, it gave me the following error: 
chown: `root:utmp': invalid user
chown `root:tty': invalid user
sulogin: cannot open password database!
Segmentation fault
init: rcS-sulogin main process (3923) terminated with status 139
After this loading stops.

Any help will be appreciated.

---

### Post by multi on 2007-09-02
Problem is solved:

Turned out I accidently wrote my x11vnc password file over my /etc/passwd. I restored a backup file and after that it took me another while to figure out that the rights for passwd had to be changed. Now it's all up and running and it is possible to remotely login to the pc with x11vnc and xinetd.

---

### Post by ardhy on 2008-01-31
I have the same problem with you though I'm not trying to remote my desktop. I'm really an apprentice in Linux world, so can you explain how can I restore my previous configuration.
Thanks.

---

