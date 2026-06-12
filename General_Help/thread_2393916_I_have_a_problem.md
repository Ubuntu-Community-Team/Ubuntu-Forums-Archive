---
title: "I have a problem"
date: 2018-06-10
forum: General Help
---

### Post by gsdunn1972 on 2018-06-10
So I'm trying to use a program called Chirp to program a radio, follow all the prompts and keep getting this error message-

[Errno 13] could not open port /dev/ttyUSB0: [Errno 13] Permission denied: '/dev/ttyUSB0' with the port number going down the complete list of options available to me, I've tried to add a username to dialout permissions in terminal by using-
sudo addgroup "$USERNAME" dialout and it tells me only 2 usernames can be added.

How do I find out what port my USB are on? Using a Toshiba Satellite laptop running 64 bit 18.04.

---

### Post by mörgæs on 2018-06-10
If you change the thread title to (for example) *'[Errno 13] could not open port /dev/ttyUSB0'* there is a better chance for getting help.

---

### Post by coffeecat on 2018-06-10
And posting in a support area rather than in a chat area will also give you a better chance of getting help.

*Thread moved to **General Help**.*

---

### Post by Holger_Gehrke on 2018-06-10
'addgroup' adds new groups to the system -- probably not what you want to do. To add group membership(s) to an user account you use 'usermod' with the options '--append' and '--groups' like so:```
sudo usermod --append --groups dialout USER_ACCOUNT_NAME
```

Holger

---

### Post by C.Snyder on 2018-06-30
Greetings,
I am also using the Chirp software to configure a Baofeng UV-5R XCVR and am having the same problem.
Holger_Gehrke's post:
```
sudo usermod --append --groups dialout USER_ACCOUNT_NAME
```
is similar to the advise I received from another HAM on the Chirp Email Forum.
gsgunn1972, have you made progress with the access to your radio?
73's

---

### Post by NM5TF on 2018-06-30
maybe you will find some help here......

[http://chirpsoftware.com/baofeng-uv-5r/#more-12]("http://chirpsoftware.com/baofeng-uv-5r/#more-12")

or here.....

[http://chirpsoftware.com/tutorials/]("http://chirpsoftware.com/tutorials/")

tommy

---

