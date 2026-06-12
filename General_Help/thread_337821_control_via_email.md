---
title: "control via email"
date: 2007-01-13
forum: General Help
---

### Post by insane_alien on 2007-01-13
would it be possible to set it up so i could send bash shell commands to my PC via email? and to limit the accepted ones to commands sent from a particular address and with a certain subject (say, COMMAND). 

I just realised it would be useful sometimes if i want to have some music playing when i get in, have stuff i need printed out while i'm enroute and i'm sure if i had lego mindstorms, have a cup of tea waiting for me too. all the stuff you hate wasting time on when your in a hurry.
or even to record a sow you've forgat to set a timer for.

so 
1. Is it possible?
2. if yes, how? and if no, damn.

---

### Post by schilcha on 2007-01-13
you can use nail (a command-line mail-program). Install it, if not available -- it's in the repos.

I've tried the following:
```

# send mail to myself locally
nail -s qaqa schilcha@localhost < /tmp/some.mail.text
# lookup messages with subject-line "qaqa" 
echo -e '(subject "qaqa")\nd' | nail -R

```
nail -R makes all of this read-only, but in principle, the second command prints all mails with subject-line  "qaqa".

nail's man-page does contain loads of information, which should get you close to what you need:
read the mails' contents into a file and source the bash commands then.

You might think about using gpg to sign your mails to make sure nobody else submits arbitrary commands.

HTH, good luck, 
   schilcha

---

### Post by insane_alien on 2007-01-14
> You might think about using gpg to sign your mails to make sure nobody else submits arbitrary commands.

ahh theres an idea. thats why i was suggesting only accepting emails from a certain address and a certain subject (the one i have in mind is a little more complex than COMMAND, its 48 characters long and has a lot of numbers and change of case in it. looks like gibberish.) but PGP sounds better. i'll have a look in to this.

---

### Post by insane_alien on 2007-01-15
okay, i want the commands to execute while i'm away from the PC. i send an email from my phone and the command get executed when it gets recieved. i can't get commands to execute without running a seperate command at the PC. i suppose this is a security feature of linux and is a good thing to have, but i wanna show off :P

---

### Post by phansiizwe on 2007-01-15
Can't you set up a cron job for that?
Let cron look for subject the way schilcha showed and then when a certain subject pops up, run another command from the cron job.

---

### Post by insane_alien on 2007-01-16
that would work, ta.

---

