---
title: "root passwd in Ubuntu live cd"
date: 2005-05-24
forum: General Help
---

### Post by xdark on 2005-05-24
I haved using other distro for some time like fedora, suse, centos, freebsd,
i recived the cd's, and is an excelent distro, but on the live cd i don't know how access to the root account to mount some partitions of my other harddrives, i have a machine with multiples os, Windows Xp profesional, FreeBSD, and Fedora Core 3 all configured with grub to boot.

somebody  knows how to access to root account on the live cd?

---

### Post by dekoi on 2005-05-24
This topic has been covered several times in different places, but (K)Ubuntu doesn't have a root-level/admin password. For the sake of being helpful:

(in terminal)

sudo mount <whatever you're going to mount> 
*then enter your USER password

As the primary (first installed) user, sudo allows you to perform actions as root.

---

### Post by Shakie on 2005-05-27
[http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)


This should help clear things up also.

---

### Post by Mez on 2005-05-28
I think you guys have misread here, so I'll post to make sure other people understand when trying to answer this guys CD

This guy is asking how to use root commands when he is using the LIVE cd, not an install of ubnuntu, but the LIVECD

---

### Post by roland on 2005-05-28
Mez, I don't think so. I have used the Live cd for a while now, and dekoi is right about sudo. "sudo" applies to both the installed Ubuntu and the Live cd. The difference is, that the Live cd uses the default account "ubuntu", for which no password is needed in order to use sudo. Obviously, the installed ubuntu does not.

---

### Post by sgmorr on 2005-06-29
I am also using the live CD. When I attempt to do something like change the date and time, I am asked for my password. There is not a prompt to enter user (ubuntu) for which there is not supposed to be a password. I am only asked for my password which I do not have. Do I need to create one? Thanks.

---

### Post by WakkiTabakki on 2005-07-07
[QUOTE=roland]Mez, I don't think so. I have used the Live cd for a while now, and dekoi is right about sudo. "sudo" applies to both the installed Ubuntu and the Live cd. The difference is, that the Live cd uses the default account "ubuntu", for which no password is needed in order to use sudo. Obviously, the installed ubuntu does not.[/QUOTE]

Well, try this:
1. Boot up with the live cd
2. Create a new user account
3. Start a new login (Applications/System Tools/New Login)
4. Login as the new user
5. Switch back to the original tty (Ctrl-Alt-F7), i.e to go back to user 'ubuntu'

Now, I sure do need to provide the password for user ubuntu... If I press enter it says "Login Cancelled"

/N

---

### Post by 5 bellies on 2005-07-07
[QUOTE=sgmorr]I am also using the live CD. When I attempt to do something like change the date and time, I am asked for my password. There is not a prompt to enter user (ubuntu) for which there is not supposed to be a password. I am only asked for my password which I do not have. Do I need to create one? Thanks.[/QUOTE]

I have the same issue with the Live CD. I'm trying to mount an existing ext2 partition where I have some .iso's that I need to burn.

Everytime I try to mount using sudo I get asked for the password. The password I entered during the expert mode does not work. I've rebooted 3 times with the same result.

I read somewhere the user ubuntu doesn't need to supply the passwd for the first 15 minutes and can use sudo unchallenged... this isnt the case from me and I get asked right from the get go.

 :???:

---

### Post by z_pod on 2005-07-11
[QUOTE=WakkiTabakki]Well, try this:
1. Boot up with the live cd
2. Create a new user account
3. Start a new login (Applications/System Tools/New Login)
4. Login as the new user
5. Switch back to the original tty (Ctrl-Alt-F7), i.e to go back to user 'ubuntu'

Now, I sure do need to provide the password for user ubuntu... If I press enter it says "Login Cancelled"

/N[/QUOTE]
 Ehmm.. what if "sudo passwd ubuntu" (type a new password) ? I'm asking since I used to have a similar problem which I solved by changing ubuntu user password (of course you may use sudo visudo to manually change sudoers properties)

Regards

---

### Post by biskup on 2005-09-22
I haven't tried this on the Hoary Hedgehog 5.04 live CD but, on the Breezy Badger 5.10 pre-release  live CD all you have to do is type:
  sudo su

That works for me.

---

### Post by jrizzy on 2006-04-19
do this:

Applications --> System Tools --> Run as different user

and type in the name of the program u wish to run.

worked for me first try and didn't have to create any new accounts or login

---

### Post by zwaardmeester on 2007-02-17
```
sudo xterm
```

will work

---

### Post by yobo on 2008-05-02
hello this is my first post here,

i had the same problem and this is what i did to use the sudo/root password in the Live CD (7.04):

Go to: System--> Administration--> Users and groups
You will find only one user, click on him and then click "Properties".
I do not know what the password is but you can change it!
And the you can do whatever you want...

i hope i 've been helpful...

---

### Post by sgmorr on 2008-05-02
Interesting to get a new post on this thread. I haven't looked at this one in about three years! Haven't done much with Ubuntu Live CD lately, but may give this one a try. yobo, do you have to do your password selection thing each time you begin a new Live CD session? Thanks.

---

### Post by trinikrono on 2008-05-06
so i was searching for answer for the same question raised here. Which i still found wasnt answered but then i remebered something and decided too post.
Run the following command too change the root user's password
sudo passwd root

and it will ask you for the new password you can put it as 1 or something:
just something for you guys who love su instead of sudo

---

