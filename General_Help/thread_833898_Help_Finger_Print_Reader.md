---
title: "Help: Finger Print Reader"
date: 2008-06-19
forum: General Help
---

### Post by shooterjames on 2008-06-19
Hi 

Does anyone know how to get an IBM finger print reader configured? I have just installed 8.04 on my X41 laptop and havent got a clue where to start or if its even possible to get it working outside of windows.

Can anyone help?

---

### Post by cariboo on 2008-06-19
Have you tried IBM they have a lot of good linux resources.

Jim

---

### Post by shooterjames on 2008-06-19
Thanks i will take a peek

J

---

### Post by moore.bryan on 2008-06-19
you may want to check-out this:
[http://thinkwiki.org/wiki/Integrated_Fingerprint_Reader](http://thinkwiki.org/wiki/Integrated_Fingerprint_Reader)

---

### Post by cacycleworks on 2008-06-19
This thread talks about the concept of finger print reading: [http://ubuntuforums.org/showthread.php?t=503928](http://ubuntuforums.org/showthread.php?t=503928)

It will be much better for you if ibm had a ready working solution though. :)

:) Chris

---

### Post by shooterjames on 2008-06-19
Oooops somthing has gone wrong The install went ok and I ran the commands as per the wikki.

I ran tftools --aquire three times swipeing each time;

When i ran the tf-tools --verify it said that the communication with the fingureprint reader failed.

I rebooted and after entering my username i got the password or swipe finger prompt [unexpected given that it just told me communication failed], i swiped my fingure and it loops back to username i cant override with my password also i seem to be stuck in this loop between username and password. You can press ESC and it will allow a text entry but only gives you a nano second to enter anything before it loops back to the username entry.

I think i may have buggered it, unless anyone knows how to get round it so i can get back into terminal and disable it again?

cheers
James

---

### Post by cariboo on 2008-06-20
the only thing I can think of is to issue a Ctrl-Alt-F1 to get into a console and see if there is a service running for the fingerprint scanner and stop it. Try something like:

```
ps ax | grep tf*
```

If it is running use:

```
sudo kill <program id number>
```

Good luck

Jim

---

### Post by shooterjames on 2008-06-20
Its not looking to good, i can get into the consol but no further it imidetly asks for login and then swipe or password. I think i am going to have to do a fresh install.

Its all good fun, i have only just switched so luckely i have not got anyting i am worried about loosing anything on the HD.

---

