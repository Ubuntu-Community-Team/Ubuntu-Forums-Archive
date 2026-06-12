---
title: "studoers NOPASSWD not working"
date: 2007-01-31
forum: General Help
---

### Post by gaillard on 2007-01-31
Well I know I at least didn't do one thing.  The right thing. Sheesh.  Anyways, I have added the line

gaillard      ALL=(ALL) NOPASSWD: ALL

to studoers with visudo but it still prompts me for my password!
what am i doing wrong?

I need to use this because I am using sudo in a script and it will hang waiting for the password, so does anyone know?

Thanks so much

---

### Post by gaillard on 2007-01-31
just realised it should be

gaillard    ALL = NOPASSWD: ALL

but my post remains.. =( meaning its still not working...

---

### Post by konst88 on 2007-01-31
Change the line of %admin:
```
%admin ALL=(ALL) ALL , NOPASSWD: script1,script2 
```
This will make script1, script2 not ask for password.

---

### Post by gaillard on 2007-01-31
This is not working, the only time it doesn't ask me for a password is after I have already entered it and it just has not timed out.

I added that line with the script /home/user/script
still didn't work.

I have two commands in my script that use sudo and if I can add those somehow or just all users don't have to put in password it would be great.  Any way?

Oh alsa the script will be run by another program, and even if my password hasn't timed out, it still asks for password because the program that will run the script stops and has it in its log file.

---

### Post by konst88 on 2007-01-31
You have to add the commands to the sudoers file, not the script.
Just write them there, sepereted with comma, like the example I gave.

---

### Post by gaillard on 2007-01-31
Ok I just did ALL for now for testing and it is working without password except for one thing.  Before I could have the program that called the script to issue a stop signal to the command I have with "exec" in the script, but now the stop signal isn't working.  However when I go to system monitor and do stop it works fine.

the error I get is,

[OSError] [Errno 1] Operation not permitted (in method blah)

but it did before I sudoed the commands and still does in the system monitor.

Any ideas? 

Thanks for the help by the way =)

---

### Post by gaillard on 2007-01-31
nevermind the command needed the -u option for sudo user to be run as me... don't know why though if someone wants to inform me i am very curious.

---

### Post by gaillard on 2007-01-31
ok actually now with the sudo -u option the stop signal doesn't work when sent by the program.  But without it I get the error I posted before.  Catch 22 ! anyway around it?

Thanks everyone

---

