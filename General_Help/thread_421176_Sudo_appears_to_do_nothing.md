---
title: "Sudo appears to do nothing"
date: 2007-04-24
forum: General Help
---

### Post by ngabrish on 2007-04-24
I recently installed 7.04 server edition on an old PC of mine to use as test box for web development. In addition to choosing the LAMP option during install I have installed SSH, Make, Hamachi, Subversion and Samba in that order. Everything seemed to be working fine but then when I was trying to do a sudo chmod on my apache root folder I found that nothing changed. I tried several times on that folder and a few others and found nothing worked. no error messages, it just returned the command prompt. I was able to use chmod successfully using my regular account. Since that time it seems that any commands that I try to execute using sudo do nothing. I am prompted for my password the first time as usual but no matter what I do it just returns the command prompt. Any help would be appreciated

---

### Post by lassegs on 2007-04-24
Try

```
sudo su
chown me /folder/thisonerighthere/thatsthespot/

```
(replace fake names with real username and real folder :P)
Does it do anything?

---

### Post by ngabrish on 2007-04-24
When I enter sudo su I am prompted for my password and sfter I enter it I an returned to the command prompt with no messages. the prompt is user@host:~$
It appears as though I am still entering commands as myself since trying to change permissions on a folder owned by root gives me the following error message:
chown: changing ownership of `/var/www/apache2-default/': Operation not permitted

---

### Post by taurus on 2007-04-24
What's the output on the screen when you run this command?

```
sudo aptitude update
```

---

### Post by ngabrish on 2007-04-24
I am prompted for my password, I enter and then I an returned to the command line. It's almost as though preceding anything with sudo drops it into a black hole.
if I run aptitude without sudo it works fine

---

### Post by ngabrish on 2007-04-24
I forgot to mention that I am doing this all from an SSH session using putty.

---

### Post by taurus on 2007-04-24
What's the output of this command?

```
id
```

---

### Post by ngabrish on 2007-04-24
It does not appear that my id changes when I use sudo or sudo su

```

nate@tophamhat:~$ id
uid=1000(nate) gid=1000(nate) groups=1000(nate),1003(www)
nate@tophamhat:~$ sudo aptitude
Password:
nate@tophamhat:~$ id
uid=1000(nate) gid=1000(nate) groups=1000(nate),1003(www)
nate@tophamhat:~$ sudo su
nate@tophamhat:~$ id
uid=1000(nate) gid=1000(nate) groups=1000(nate),1003(www)
nate@tophamhat:~$

```

---

### Post by taurus on 2007-04-24
To use sudo, you need to belong to groups adm and admin.  And since both of those two groups do not appear from your "id", you can't use sudo.

---

### Post by ngabrish on 2007-04-24
I must have belonged to them at one time since this is the id I created when installing Ubuntu and I was able to run sudo in the past. I must have blown it away when trying to add myself to other groups. How can I modify this  if I don't have access to root? Am I basically screwed?

---

### Post by taurus on 2007-04-24
You need to boot into recovery mode from GRUB menu and add your username to groups adm & admin in /etc/group.

```
nano -w /etc/group
```
<Ctrl>o to save and <Ctrl>x to exit.

---

### Post by ngabrish on 2007-04-24
I'll have to try this when I get home today. I am assuming I can't do this remotely. Thank you very much for your help you saved me from starting over from scratch. :)

---

### Post by taurus on 2007-04-24
You cannot do that over ssh unless you have a password for root.  Since you can't use sudo, you can't edit /etc/group to add your login name back.  Therefore, have to do it from the recovery mode.

---

### Post by ulli.winter on 2007-04-26
had the same problem....
solved!
thanks taurus! :)

---

### Post by ngabrish on 2007-04-26
I just wanted to let you know that I was easily able to fix the problem with your Help Taurus.

This does bring up a question for me however. Does this mean that with physical access to any Ubuntu machine someone can easily grant themselves whatever permissions they would like? 

I can move this question if it does not belong here.

---

### Post by chrisccoulson on 2007-04-26
^^^ Yes, with physical access to a machine, anyone who is determined enough and has some know-how can do what they like with your machine, regardless of what operating system you're running. You can take measures to make life more difficult for people who have physical access to the machine, such as locking the recovery mode entries in GRUB so that you need to enter a password to select them. However, you're not going to be able to stop someone who is determined enough from just booting from a live CD and mounting your partitions, unless you encrypt the system I suppose. This is true for any operating system, not just Ubuntu.

---

