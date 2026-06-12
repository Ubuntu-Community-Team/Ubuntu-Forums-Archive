---
title: "[SOLVED] Terminal will not accept password"
date: 2008-07-04
forum: General Help
---

### Post by jmszr on 2008-07-04
When I open the terminal and enter a command and then enter a password at the prompt I get this:

jeff@jeff-desktop:~$ sudo dpkg --configure -a
[sudo] password for jeff: 
Sorry, try again.
[sudo] password for jeff: 
^[ORSorry, try again.
[sudo] password for jeff: 

I went into System>Preferences>About Me and changed the password to no avail. I can login to Ubuntu but the terminal is having none of it.
Any help anyone can give me would be much appreciated.
Thank you.
             jmszr

---

### Post by cptasker on 2008-07-04
This happened to me, I just typed it in really slowly! t seemed to take a few seconds for the cursor to move in between, its probably something completely different but worth a try!

---

### Post by jmszr on 2008-07-04
cptasker,
          Thank you,but that didn't work-I waited 10 sec between letters-no go. Thanks anyway,
                                  jmszr

---

### Post by Pacopag on 2008-07-04
does it accept your password for things like Synaptic.  I mean, is it JUST at the terminal?

---

### Post by hayden92 on 2008-07-04
That happened to me lately, I just closed the terminal and opened it again from the menu. It worked after that. Good luck!

---

### Post by spiderbatdad on 2008-07-04
you can run the command ```
sudo cat /etc/sudoers
```and look for this line: ```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

Then run the command ```
id
```and verify that your user is in the admin group.

---

### Post by jmszr on 2008-07-04
Pacopag- Synaptic,Update manager and App. get/remove all come up with an error message that tells me I have to run dpkg --configure -a which I can't do because the terminal won't accept my password.

Hayden92- I have opened and closed the terminal numerous times-unfortunately that didn't do it. 

Spiderbatdad- I can't run any of those commands as the terminal won't accept my password.

Thank all of you for your time and interest.

jmszr

---

### Post by aysiu on 2008-07-04
Maybe this will help:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by jmszr on 2008-07-04
aysiu,
      That worked-Thank you,Thank you. It's a little bit scary in there, but I have to learn sometime.
                               Thanks again,
                                            jmszr

---

### Post by VMC on 2008-07-04
That "psychocats" is a cool cat! Many people have been helped using it, Including myself!

---

### Post by l0fls on 2008-07-05
i have noticed that ubuntu doesent take passwords sometimes. i just keep typing it in and eventualy it works but has anyone else noticed you get problems with passwords

---

### Post by l0fls on 2008-07-05
psycocats rule i have no clue what they are but the sure do help out

---

