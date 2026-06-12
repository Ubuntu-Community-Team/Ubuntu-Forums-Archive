---
title: "Having Problems opening programs"
date: 2013-02-06
forum: General Help
---

### Post by hedg70 on 2013-02-06
Hello all i will just let you know im a noob to ubuntu from windows 7 and have used windows since 2000 i have reciently switched to ubuntu 12.4, so far i am impressed and have installed it on 4 other pcs that my friends and family use because its not full of rubbish and tends to run faster.

i have installed it on my main gaming pc, hoping to join the valve beta but have come across a problem, if i open up the update manager or software manager i get this box, i have no clue as to what to do or where to start, i see something about my GPU drivers am i right?

any help on how to fix this would be great, thanks

Carl

[http://image.torrent-invites.com/view.php?filename=395Screenshot_from_2013_0.png](http://image.torrent-invites.com/view.php?filename=395Screenshot_from_2013_0.png)

[IMG]http://image.torrent-invites.com/view.php?filename=395Screenshot_from_2013_0.png[/IMG]

---

### Post by wildmanne39 on 2013-02-06
Hi, please open the terminal ctrl+alt+t and copy and paste the following commands one at a time.
```
sudo rm /var/lib/apt/lists/* -vf

```
The first command will remove the damaged list and when you run the second command it will replace it with a new list.

```
sudo apt-get update
```
then try to install the application again.
Thanks

---

### Post by hedg70 on 2013-02-06
Thank you for your help ill get back to you once i have done this to let you know the result.


Edit -

I have typed this in the console but it asks for a password for my user i.e. 

carl@ubuntu:~$ sudo rm /var/lib/apt/lists/* -vf
[sudo] password for carl: (i typed my password here)
Sorry, try again. (every time it says this)
[sudo] password for carl: 


any help on if there is a defult password?

---

### Post by Impavidus on 2013-02-06
Just type carls' password. The one carl uses for login. The characters won't show up in the terminal, so you have to pay attention whilst typing if you are used to feedback from the screen. After typing the password hit enter. Watch the capslock key.

---

