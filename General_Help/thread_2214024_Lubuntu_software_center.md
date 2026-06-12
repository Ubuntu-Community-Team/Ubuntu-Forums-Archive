---
title: "Lubuntu software center"
date: 2014-03-30
forum: General Help
---

### Post by odce1206 on 2014-03-30
Hey, I installed lubuntu this afternoon on an old laptop. It was working  correctly and super fast. When I try to download something on the  lubuntu software center I have to authenticate myself *obviously*. The  problem here is that when I enter my password, it does not tell me  anything, it just pop up the authenticate box again. Also when I try to  download the package I wanted to install (Spyder) on the terminal and  when I enter my password again, it tells me that the password is  incorrect. Any of you guys know how to solve this problem?

---

### Post by vasa1 on 2014-03-30
Did you set a password during installation? Does this password work for anything at all? For example, what happens when you provide your password when you enter
```
sudo parted -l
```in a terminal?

---

### Post by odce1206 on 2014-03-30
Yes, the password I set during the instalation is the sameone that I'm using when logging in, I can login correctly but I cant have use sudo, cant authenticate in software center and cannot login to any tty

this is what i got when running sudo parted -l

```
 

orlando@orcuevas:~$ sudo parted -l
[sudo] password for orlando: 
Sorry, try again.
[sudo] password for orlando: 


```

---

### Post by vasa1 on 2014-03-30
> **odce1206 said:**
> Yes, the password I set during the instalation is the sameone that I'm using when logging in, I can login correctly but I cant have use sudo, cant authenticate in software center and cannot login to any tty

this is what i got when running sudo parted -l

```
 

orlando@orcuevas:~$ sudo parted -l
[sudo] password for orlando: 
Sorry, try again.
[sudo] password for orlando: 


```

Sorry, let's hope someone knows how to help. I don't have any experience in this problem :(

Maybe you should edit the title of your thread to show that your issue is with the password generally and not limited to the Lubuntu Software Center.

---

### Post by carl4926 on 2014-03-30
Just a guess
'You are using the wrong password'

---

### Post by vasa1 on 2014-03-30
> **carl4926 said:**
> Just a guess
'You are using the wrong password'
But OP **can** login. That is what is confusing me.

---

### Post by carl4926 on 2014-03-30
Ah OK
What version of lubuntu?

Do we have the complete story of instances that might have been a lead in to this situation?

---

### Post by Rex Bouwense on 2014-03-30
We have all broken things on our computer and someone tells you that he (or she) has not then he (or she) is telling you a story or hasn't tried hard enough.  That was my annual attempt at humor.  To fix the sudo read this:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

