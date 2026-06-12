---
title: "Manually start MySQL and Apache in Desktop Development LAMP"
date: 2008-06-04
forum: General Help
---

### Post by Chosen320 on 2008-06-04
Hi,

Firstly thanks to everyones knowledge that I've gleamed over the last few weeks as I've been getting into Linux.

I am a web developer and in the past have always developed in a WAMP environment. I want to move my development over to my ubuntu setup on my laptop (acutally I have no choice cos I jumped in deep and deleted my windows partition).

So far I've done the following in Hardy.

```
sudo apt-get install apache2 php5 mysql-server-5.0 phpmyadmin
sudo gedit /etc/apache2/apache2.conf
```

And added in the following in the apache2.conf file:
```
# Enable PHPMyAdmin
  Include /etc/phpmyadmin/apache.conf
```

I have 4 really easy and simple questions (I think)

1. How do I make it so that MySQL and Apache do not start up by default whenever I boot my laptop?

2. What would I have to type in the terminal to start these up manually?

3. How do I make a script that I can add to one of my panels that with a simple click will startup MySQL and Apache? 

4. How do I create a panel short-cut to this script? I'm assuming I just create a standard launcher, give the path to the script and then drag it onto my Panel an lock it where I want it.

Looking forward to the replies.

Gareth

---

### Post by mattress on 2008-06-04
> 
1. How do I make it so that MySQL and Apache do not start up by default whenever I boot my laptop?

Fire up your service manager (I use rcconf from the cli) and disable them. 

```

2. What would I have to type in the terminal to start these up manually?

```
sudo /etc/init.d/mysql start 
sudo /etc/init.d/apache start (it may be apache2 or httpd, i don't remember)

```

3. How do I make a script that I can add to one of my panels that with a simple click will startup MySQL and Apache?

```
It may be easiest to disable the sudo password for these two commands and create a little bash script to run the restart commands to get this done. Open up a terminal and run **sudo visudo** and make changes accordingly. I'll be home later this evening so if you need further help...

```

4. How do I create a panel short-cut to this script? I'm assuming I just create a standard launcher, give the path to the script and then drag it onto my Panel an lock it where I want it.

```
You're 100% correct on this one..

HTH

m

---

### Post by Chosen320 on 2008-06-04
Thanks Mattress,

Answers to the first 2 worked out well.

In rcconf I also saw another 2 mysql services namely "mysql-ndb" and "mysql-ndb-mgm". What are these? and will I also be able to start them up in the same way?



With Question 3 I should have clarified, I assumed I would need some kind of bash script I just don't know how to create one. (Although I should probably check my ubuntu help, I'm sure this is something they would cover).

I tried typing using "sudo visudo" as I agree that removing the need for root access to start these up would definitely be more convenient.

But... I didn't know what to do with what I was represented with :) Where in this file should I make changes, and how do I make them because it wouldn't let me type :)


Regards,

Gareth

---

### Post by mattress on 2008-06-04
Heading home shortly. I don't have access to an Ubuntu box at work.
I'll have answers for you shortly :)

m

---

### Post by Chosen320 on 2008-06-09
Hey,

I haven't gotten any help on this yet. Anyone able to answer the last little bit?

:)

---

