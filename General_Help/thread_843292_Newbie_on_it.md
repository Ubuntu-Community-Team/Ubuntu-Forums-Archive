---
title: "Newbie on it"
date: 2008-06-28
forum: General Help
---

### Post by nemiux on 2008-06-28
I just installed ubuntu, could people help me find soft, or give URL to it?
I would need a msn live messenger.

Ty for time

---

### Post by lisati on 2008-06-28
Gaim internet messenger (I think it's now called "Pidgin") can connect with MSN messenger.

---

### Post by robertchahine on 2008-06-28
if you want, try amsn it looks like WLM. And you can use webcam and voice recoreder with it

go to the terminal and tyep
```
sudo apt-get install amsn
```

---

### Post by nemiux on 2008-06-28
> **robertchahine said:**
> if you want, try amsn it looks like WLM. And you can use webcam and voice recoreder with it

go to the terminal and tyep
```
sudo apt-get install amsn
```

Pls, explain to me what is that code ant where i should put it? I just installed ubuntu, before that i used XP

---

### Post by robertchahine on 2008-06-28
> **nemiux said:**
> Pls, explain to me what is that code ant where i should put it? I just installed ubuntu, before that i used XP
ok nemiux, don't worry about that.
Look on the top of your screen, you should see a bar or pannel.Click on "Applications" then "Accessories" then "Terminal".It will open a window, that you can put commands in it.
write this code
```
sudo apt-get install amsn
```.
it will ask you for your password, type it and press enter.Then i think it will ask you if you agree for downloading some packages, so put the letter "y" and press enter.
Once the installation finished, go to the "apllications" pannel >"internet">"amsn.

---

### Post by nemiux on 2008-06-28
Thanks, now I know more about it... If I'll need help, i will whrite in here.. Thanks again

---

### Post by nemiux on 2008-06-29
Could someone tell a good soft for listening to multimedia (in windows it was winamp)

---

### Post by dexter.deepak on 2008-06-29
amarok is my favourite.
but for all types of media, you need vlc
```

sudo apt-get install amarok vlc

```

---

### Post by nemiux on 2009-01-07
Ok, look. Few more things. One is PHP. I downloaded it:
[http://lt2.php.net/get/php-5.2.8.tar.bz2/from/a/mirror](http://lt2.php.net/get/php-5.2.8.tar.bz2/from/a/mirror)
but when i extracted it, what should i do? TY

---

### Post by cariboo on 2009-01-07
The preffered way to install software is to use Applications-->Add/Remove Programs and System-->Administration-->Synaptic package Manager. If you try to install programs downloaded for some web site you will run into nothing but problems. There are over 30,000 packages listed in the repositories.

If you want to install php you will need to install a web server and a database program too. To install php go to System-->Administration-->Synaptic Package Manager-->Edit--Mark Packages by Task. When the menu comes select LAMP and click OK. Just follow the prompts to install the packages.

Jim

---

### Post by nemiux on 2009-02-03
Ok.
Now 1 more thing.
I want to know the basic terminal commands with normal explanations, if there is a web, link it, if no, please take your time and write everything detailed.

Thanks

---

### Post by howefield on 2009-02-03
Try this one...

[http://linuxcommand.org](http://linuxcommand.org)

---

### Post by nemiux on 2009-02-03
Ok ty, that helped me. Now look, im at xampp instaliation and these are instructions:
Go to a Linux shell and login as the system administrator root:

su

Extract the downloaded archive file to /opt:

tar xvfz xampp-linux-1.7.tar.gz -C /opt

So i did, i wrote su, entered password, but when i entered that line it wrote to me: 
tar: xampp-linux-1.7.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

File is on desktop, names match (i didn't change the name when downloading). Gimme the correct syntax, thanks

---

### Post by nemiux on 2009-02-03
I just got a problem, i created a user account for me, and i didn't add root privilegies. I know root psw but it tells me i can't login via user screen. How should i login to that account? Thanks

P.S. Sorry for so much questions, im just newbie

---

### Post by xc1024 on 2009-02-03
use "sudo" (without quotes) before the command. it lets you run this particular command as root. after hitting enter you need to enter your own password, not the root one.if it doesn't work (which i doubt) add yourself to wheel group.

---

### Post by howefield on 2009-02-03
> **nemiux said:**
> Sorry for so much questions, im just newbie

Sorry for even saying it, but it helps if you have a seperate thread with a descriptive title for unrelated questions in order that posters can best help you. Also it lets others benefit when the same question comes up.

---

### Post by nemiux on 2009-02-03
That didnt help, same error:

nemiux@ubuntu:~$ tar xvfz xampp-linux-1.7.tar.gz -C /opt
tar: xampp-linux-1.7.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
nemiux@ubuntu:~$.

---

### Post by nemiux on 2009-02-03
Ok, ill keep that in mind, after this question, im ending this topic

---

