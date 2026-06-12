---
title: "procmail - foward"
date: 2006-08-14
forum: General Help
---

### Post by pat270881 on 2006-08-14
hello,

I have two questions:

1) How could I configure that, that all mails are not forwarded automatically to /var/spool/mail but to the directory mail in my home-directory?


2) I have defined some .procmail rules, maybe somebody could look if the are correct defined?
```

#Put mails with a subject like this in the spam-directory, instead of 
the i 1 or ! is also possible with any a's and g's but the r and a at the end only one time
0:
* ^(From|Cc|To).*V[i,1,!]a+g+ra
/home/patrick/spam


#Put mails with a word phrase "to remove XXX address" in the body in the 
spam directory, XXX can stand for string with 0 or more numbers or letters
1:B
* to remove [a-z A-Z 0-9]* address
/home/patrick/spam


#Put mails with sender badguyXXX@spammers.org in the spam directory, 
XXX can stand for any number between 1 and 4444
2:
* ^(From|Cc|To)badguy[123][0-9][0-9][0-9]@spammers.org
/home/patrick/spam

3:
* ^(From|Cc|To)badguy[4][0-4][0-4][0-4]@spammers.org
/home/patrick/spam


#Put mails bigger than 50000 Byte in the spam directory
4:
* > 50000
/home/patrick/spam

```

It would be gread if somebody find time to answer me the questions!

Regards

---

### Post by pat270881 on 2006-08-14
Nobody an idea?? :confused:

---

