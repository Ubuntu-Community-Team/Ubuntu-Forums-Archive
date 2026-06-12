---
title: "su not working for any user"
date: 2014-06-13
forum: General Help
---

### Post by wolfgentleman on 2014-06-13
I enabled root a while back, and I can login directly to root. Everything was working fine until, for whatever reason, crontab and sudo lost setuid/setgid which I fixed both using the solution on [ServerFault]("http://serverfault.com/questions/78159/what-could-cause-permission-denied-for-command-crontab-e"). However I realized that su wasn't working either. I thought, OK, let's try creating a new user via root login and go back to my regular user and use su to login to it. I still got "su: Authentication failure". So I tried the solution for crontab and sudo, but it didn't work. I did some googling but it didn't turn anything up that was useful in my case. Any ideas?

---

### Post by wolfgentleman on 2014-06-18
Bump
Anyone?

---

### Post by steeldriver on 2014-06-18
I'm not clear what you're saying - are you trying to su to the (unlocked by you) root account, or to a regular user account ('su - someuser')? what was the "reason" that "sudo lost setuid/setgid" (these things don't just spontaneously happen)

---

### Post by grahammechanical on 2014-06-18
Just a question. Was su ever working for you in Ubuntu? I ask because in researching this problem I have found a few threads on this forum and on AskUbuntu where the poster is saying: > "[COLOR=#333333][FONT=UbuntuRegular]I am unable to switch to super user (using "su" command). Its showing "Authentication failure" plz help me.."[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]

[SIZE=2][FONT=arial]Are you trying to fix something that does not work in Ubuntu anyway? It seems to me that a person with a root account would not be using su. But what do I know?

Regards.[/FONT][/SIZE][/FONT][/COLOR]

---

### Post by wolfgentleman on 2014-06-18
> **grahammechanical said:**
> Was su ever working for you in Ubuntu?Yes


> **grahammechanical said:**
> Are you trying to fix something that does not work in Ubuntu anyway? It seems to me that a person with a root account would not be using su. But what do I know?

I don't understand the question. When using su, I'm on my regular account trying to do mass actions in my home folder and I hit folders and/or files uploaded or created by the webserver thus the ownership is www-data:www-data. For the sake of lazyness I use su to drop to a root shell and do what I need to, then chown/chmod it to have the ownership of user:www-data and 660 for permissions. Then exit back to my normal account.

> **steeldriver said:**
> I'm not clear what you're saying - are you trying to su to the (unlocked by you) root account, or to a regular user account ('su - someuser')?
The root account. Basically this is a cloud hosted server, so I have no physical access. So rather than logging in as a regular user and putting sudo in front of everything I unlocked root and allowed root connections through ssh (I know, I know. Bad practice). I can login as root through SSH, but for whatever reason su no longer allows me to drop to a root shell.
 
> **steeldriver said:**
> what was the "reason" that "sudo lost setuid/setgid" (these things don't just spontaneously happen)
A while back I screwed up a permission fixing script that (was supposed to anyway) grab each user that had a home folder in /home and recursively set the permissions for the files in the home folder to rw for the user and group but nothing for others, then set the ownership to the user and the group to www-data. It epically failed and chmod'ed all files, including the bin folders. The ownership ended up as root:www-data. I had to repartition to make a recovery install and reverted the changes from there, or so I thought. However the problem with su is not with that because I used su since then.

I had forgotten about my very emarassing mistake on the script until I logged into linode and saw my recovery partition.

---

### Post by steeldriver on 2014-06-18
OK so this may be a silly question but if you don't have physical access to the box and su isn't working, how do you know the root password is correct?

Aside from that, given your 'mishap', did you check the setuid bit on su?

```

$ ls -l $(which su)
-rwsr-xr-x 1 root root 31116 Sep 12  2012 /bin/su

```

BTW why couldn't you have just used sudo -i when you needed a "root shell"?

---

### Post by wolfgentleman on 2014-06-18
> **steeldriver said:**
> OK so this may be a silly question but if you don't have physical access to the box and su isn't working, how do you know the root password is correct?
SSH access.
> **wolfgentlman]and allowed root connections through ssh (I know, I know. Bad practice). I can login as root through SSH[/QUOTE]

[QUOTE=steeldriver said:**
> Aside from that, given your 'mishap', did you check the setuid bit on su?
Yes, I even did chmod "adding" setuid just because I could.
```
chmod u+s /bin/su
```

> **steeldriver said:**
> BTW why couldn't you have just used sudo -i when you needed a "root shell"?
The account I used to test sudo was different from the one that I normally use. My normal one doesn't have sudo-powers.

---

