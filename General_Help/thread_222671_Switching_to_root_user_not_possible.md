---
title: "Switching to root user not possible??"
date: 2006-07-25
forum: General Help
---

### Post by pat270881 on 2006-07-25
hello,

I created a new user (testuser) only for exercises so I have created the corresponding entries in the passwd, shadow and group.

After that when I try to switch to the root user with sudo -s and my password nothing happens. No Error msg or anything else, I only see the same prompt with my username@host$ and no root@host#.

Does anybody know how I can fix that?

---

### Post by JonnyRo on 2006-07-25
I usually just do 

sudo bash

To get a bash prompt as root.  Does that work for you?

---

### Post by pat270881 on 2006-07-25
No unfortunately the same:

[16:18:01]patrick@Achatschitz:~$ sudo bash
Password:
[16:51:34]patrick@Achatschitz:~$


I enter the password and then I see the same prompt...

Has nobody an idea for this strange behaviour..?? :(

---

### Post by taurus on 2006-07-25
You want to log in (or su) as root?  Then do

```

sudo passwd root
(enter you own password here...)
(enter root password)
(re-enter root password)
su -
(enter new root password)

```
Now, you are root so better be careful.  Don't forget to "exit" when you're done doing whatever you plan to do...

---

### Post by cantormath on 2006-07-25
> **taurus said:**
> You want to log in (or su) as root?  Then do

```

sudo passwd root
(enter you own password here...)
(enter root password)
(re-enter root password)
su -
(enter new root password)

```
Now, you are root so better be careful.  Don't forget to "exit" when you're done doing whatever you plan to do...

or just open a terminal and type sudo -i
laptop:~$ sudo -i
Password:
root@cantormath-laptop:~#

---

### Post by cantormath on 2006-07-25
loging in as root in x is dumb.......you should really use sudo.

---

### Post by pat270881 on 2006-07-25
Okay when I try this commands:

[17:35:23]patrick@Achatschitz:~$ sudo passwd root
[17:35:32]patrick@Achatschitz:~$ sudo -i
[17:35:43]patrick@Achatschitz:~$

As you see nothing happens...I cannot understand that, why this does not work anymore...? :((

---

### Post by taurus on 2006-07-25
What groups do you belong to?  Type this at the prompt...

```

id

```

---

### Post by oldgit on 2006-07-25
sudo su

and when you are finished, ctl + d

---

### Post by mlind on 2006-07-25
Your user has to belong to **admin** group in order to get sudoing privileges. Or add your user to /etc/sudoers using visudo.

---

### Post by PingunZ on 2006-07-25
sudo -s  
If that doesnt work .. reinstall bash or change to Dash ...

---

### Post by cantormath on 2006-07-25
> **pat270881 said:**
> Okay when I try this commands:

[17:35:23]patrick@Achatschitz:~$ sudo passwd root
[17:35:32]patrick@Achatschitz:~$ sudo -i
[17:35:43]patrick@Achatschitz:~$

As you see nothing happens...I cannot understand that, why this does not work anymore...? :((

cantormath is in the admin group.....
if you insist on changing the password of root, 

cantormath@cantormath-laptop:~$ sudo passwd root
Changing password for root
(current) UNIX password:you user password
Enter new UNIX password: the new root password
Retype new UNIX password:.......etc

if you want to just be root in terminal....you dont need to set the root password. just type 
cantormath@cantormath-laptop:~$ sudo -i
Password:
root@cantormath-laptop:~#
thats all.

if you want to login into X and use the desktop of root.....well, thats just not very smart.

---

### Post by pat270881 on 2006-07-25
I tried your advices:

[17:59:01]patrick@Achatschitz:~$ id
uid=1000(patrick) gid=1000(patrick) Gruppen=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admon),1000(patrick)
[17:59:07]patrick@Achatschitz:~$ sudo su
[17:59:08]patrick@Achatschitz:~$ visudo
visudo: /etc/sudoers: Permission denied
[17:59:44]patrick@Achatschitz:~$

First id that you can see the information of my user account. When I try sudo su nothing happens..

And when I try visudo I get a Permission denied.

Maybe any other ideas?? ](*,)

---

### Post by taurus on 2006-07-25
> **pat270881 said:**
> I tried your advices:

[17:59:01]patrick@Achatschitz:~$ id
uid=1000(patrick) gid=1000(patrick) Gruppen=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admon),1000(patrick)

Is that a typo or do you actually have a group admon instead of admin???

---

### Post by pat270881 on 2006-07-25
I think admon is a group, because when I use the group command from my user account the following groups are displayed:
```

[18:16:50]patrick@Achatschitz:~$ groups
patrick adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admon

```

Does that help you?

PS: I cannot look into the group file as I am not logged in as root.
```

[18:18:28]patrick@Achatschitz:~$ vipw
vipw: Datei konnte nicht gesperrt werden: Permission denied
vipw: /etc/passwd wurde nicht geändert
[18:18:55]patrick@Achatschitz:~$ vigr
vigr: Datei konnte nicht gesperrt werden: Permission denied
vigr: /etc/group wurde nicht geändert
[18:18:58]patrick@Achatschitz:~$

```

---

### Post by taurus on 2006-07-25
I think that could be your problem there.  Now, look at /etc/group to make sure it says admon?  

```

more /etc/group

```
If it is, then you need to boot into recovery mode (from GRUB menu) and change admon to admin in /etc/group...

```

nano /etc/group

```

---

### Post by mlind on 2006-07-25
How did you get a group called admon? Have you manually edited /etc/groups? :-k Like taurus said, changing name to admin *should* solve your problems.

---

### Post by pat270881 on 2006-07-25
That was the error :):) Now it works again, I changed the admon group-name to admin group name in the recovery mode. The only strange thing is that I cannot remember that I have changed the group name, in the /etc/group.

Thank you very much for your help and patience!!

But why was it not possible to switch to the root user when a group-name where the user patrick was participated in was not correct defined?

---

### Post by taurus on 2006-07-25
You need to belong to groups adm & admin and since you were on groups adm & admon, you couldn't su or sudo anything!  I bet you somehow modified /etc/group before and forgot all about it so it's the end of story...  [-(

---

