---
title: "How do you automate the installation of packages that usually prompt for usse input?"
date: 2012-11-25
forum: General Help
---

### Post by Cheesemill on 2012-11-25
Basically I'm writing a couple of scripts, one of them needs to install postfix and the other needs to install mysql-server.

How do you automate the dpkg-reconfigure part of the installation process so that the scripts can run without any user interaction?

---

### Post by Habitual on 2012-11-25
[Here's how I did it]("http://www.bournetoraiseshell.com/article.php/20101207105453509") for mysql-server.

pre-seeding postfix should also be possible in the same manner.


HTH.

JJ

Subscribed w\interest...

NOTE0:
I am unclear where dpkg-reconfigure comes in to the mix of things here.
I have never issued nor used dpkg-reconfigure in any pre-seed routine I
have managed to automate to suit my own needs. Sorry.
I fear my cheat notes may only be suitable for *new* installs...?
But my hope is that debconf-utils has some secrets I do not possess.

Have a Great Day.
may

---

### Post by Cheesemill on 2012-11-25
OK, so I think I know what I'm doing now...

The following works for installing postfix:
```
debconf-set-selections <<\EOF
postfix postfix/mailname string server.example.com
postfix postfix/main_mailer_type select Satellite system
postfix postfix/relayhost string mail.example.com
EOF
aptitude -y install postfix
```One last detail, how would I go about replacing the string server.example.com with the hosts FQDN, for example the output of:
```
hostname --fqdn
```I'd usually just put the command in backticks to expand it but that doesn't work in this situation.


For anyone that's interested the following is how to script installation of MySQL by pre-configuring the MySQL root password:
```
debconf-set-selections <<\EOF
mysql-server mysql-server/root_password password mysqlpassword
mysql-server mysql-server/root_password_again password mysqlpassword
EOF
aptitude -y install mysql-server
```

---

### Post by Habitual on 2012-11-25
> **Cheesemill said:**
> ...I'd usually just put the command in backticks to expand it but that doesn't work in this situation....

Tried the modern variant of backtick? ...
```
postfix postfix/mailname string $(hostname --fqdn)
```else your script would have to provide a variable for  "hostname --fqdn"
```
(SEEDHOST=$(hostname --fqdn)
...
postfix postfix/mailname string $SEEDHOST
...
```is my cursory guess.

HTH.

---

### Post by Cheesemill on 2012-11-25
That doesn't work either, I'm guessing it's because I'm trying to do expansion inside an EOF block.

I've settled on the following, it seems a bit hacky to me and I'm sure it's probably not best practice but hey, it works.
```
echo "postfix postfix/mailname string $(hostname --fqdn)" >/tmp/seedhost
debconf-set-selections /tmp/seedhost
debconf-set-selections <<\EOF
postfix postfix/main_mailer_type select Satellite system
postfix postfix/relayhost string mail.example.com
EOF
aptitude -y install postfix
```

---

### Post by Habitual on 2012-11-25
> **Cheesemill said:**
> That doesn't work either, I'm guessing it's because I'm trying to do expansion inside an EOF block.

I've settled on the following, it seems a bit hacky to me and I'm sure it's probably not best practice but hey, it works....

I'd agree with EOF block assessment, I have never used them in bash.

Until you find a more "correct" solution, yes, keyboard kung.fu is acceptable. :)

---

### Post by steeldriver on 2012-11-25
There seems to be a difference in how parameter expansion behaves within a here-document depending on whether you escape the label or not:

```
steeldriver@lap-t61p:~$ cat [COLOR=Red]<<EOF[/COLOR]
> Hostname is: $(hostname)
> EOF
[COLOR=Red]Hostname is: lap-t61p[/COLOR]
steeldriver@lap-t61p:~$ 
steeldriver@lap-t61p:~$ cat [COLOR=Red]<<\EOF[/COLOR]
> Hostname is: $(hostname)
> EOF
[COLOR=Red]Hostname is: $(hostname)[/COLOR]

```Same thing with quoting the label apparently:

[http://stackoverflow.com/questions/4937792/using-variables-inside-a-bash-heredoc](http://stackoverflow.com/questions/4937792/using-variables-inside-a-bash-heredoc)

---

### Post by Cheesemill on 2012-11-26
Thanks steeldriver, that's exactly the answer I was looking for.

Time to close the thread.

---

