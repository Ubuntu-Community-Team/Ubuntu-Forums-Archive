---
title: "[SOLVED] Can't Login... but I have a Suspicion,,,please help :("
date: 2008-07-09
forum: General Help
---

### Post by ephman on 2008-07-09
hi,

i was fooling around with setting up a subdomain on the localhost when all of a sudden i couldn't open a terminal, and then i couldn't open gedit, and things just stopped working.  so i figured whatever, i'll restart.  so i did, and after i typed in my username and password, it accpeted it but went to a blank brown default ubuntu colour screen.  any ideas what i can do?

thanks,

ephman

---

### Post by iaculallad on 2008-07-09
Try to login using the restore mode, and using the virtual terminal, input the command below and post whatever it displays:

```
ls -l /home
```

---

### Post by ephman on 2008-07-09
thank you,

it says
> total 4
drwxr-xr-x 82 ephman ephman 4096 jul 9 21:58 ephman

any clues?

thank you,

ephman

---

### Post by iaculallad on 2008-07-09
While on the recovery mode, Try this:

```
sudo chown -R user_name /home/ephman
sudo chmod 755 /home/ephman
sudo rm -rf /home/ephman/.dmrc

```

Or if that does not work, try the commands below:

```
sudo chmod 644 .dmrc
sudo chown ephman .dmrc
sudo chmod 755 /home/ephman
sudo chown -R ephman /home/ephman
```

Assuming that ephman is your valid username.

---

### Post by ephman on 2008-07-09
unfortunatly neither option worked :(  any other suggestions?

thanks,
ephman

---

### Post by iaculallad on 2008-07-09
In the process of fooling around with your Ubuntu installation, had you in any way changed the permission of / and other root directories? If so, the final solution would just be a clean re-installation.

---

### Post by ephman on 2008-07-09
the chances of me changing the my root permissions are so rare.  i just can't imagine what it is...  i'm so glad i'm a pretty good backerupper.  

thanks for you help.

ephman

---

### Post by cariboo on 2008-07-09
Can you post the output of:

```
cat /etc/hosts
```

It seems you may have changed something in /etc/hosts that won't allow you to log in.

Jim

---

### Post by ephman on 2008-07-09
aaaahhhh that's it.  when i ran the command i got

> 127.0.0.1  domain.localhost

i'll let you know tommorow (it's late) if it works after i fix it.  but i have a gut feeling that's it.  thank you for your help.  

be well,

ephman

---

### Post by ephman on 2008-07-10
thank you so much!  that worked.  good karma right back at you.

be well,

ephman

---

### Post by gunashekar on 2008-07-10
If it is solved it might be usefult to mark the thread as SOLVED

---

### Post by ephman on 2008-07-10
ok where do you do that?

---

### Post by avtolle on 2008-07-10
Use the thread tools at the top of the thread.

---

