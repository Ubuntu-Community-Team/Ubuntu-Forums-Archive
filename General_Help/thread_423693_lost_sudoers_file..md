---
title: "lost sudoers file."
date: 2007-04-26
forum: General Help
---

### Post by STREETURCHINE on 2007-04-26
ok i was editing my sudoers file,so i did not have to use my password all the time ,
i tried to use vim but it kept telling me i did not own the file so i could not change it,

so i used gksudo nautilus and dragged the file there made the changes then could not put the file back in,for some reason i do not own it,

so i was having a think and the power went out so now no sudoers file and i cant use sudo

so how do i get it back,there is a file in there called "sudoers.tmp.save"

---

### Post by chrisccoulson on 2007-04-26
You are meant to use the command 'visudo' to edit your sudoers file I think.

I'm not sure what is the best way to get it back. I suppose you're just going to have to recreate it. I've attached mine to use as a reference, from my Feisty install.

---

### Post by STREETURCHINE on 2007-04-26
yes you use sudo visudo but when i trid to save it it came up with permission errors,

so that is still a major problem because i cant even get in to rereate it even when i am running as root it will not let me ,so i definatly have permission problems.

---

### Post by chrisccoulson on 2007-04-26
Can you boot in to recovery mode and fix it?

---

### Post by STREETURCHINE on 2007-04-26
yes i went to recovery mode and did 

         ```
mv /etc/sudoers.tmp.save /etc/sudoers
```

and that has given me back my sudoers file now i get 

       ```
rex@rex-rex:~$ sudo aptitude update
sudo: /etc/sudoers is mode 0600, should be 0440

```

so i guess i need to chmod it now but have no idea how to structure the command

---

### Post by STREETURCHINE on 2007-04-26
well i got that one sorted out with 

       ```
chmod 0440 /etc/sudoers
```

all is back to normal .
thanks for your time  chrisccoulson just having someone replying can help jog your memory and lead you in the right direction

---

### Post by TheWizzard on 2007-04-26
> **STREETURCHINE said:**
> ok i was editing my sudoers file,so i did not have to use my password all the time ,
i tried to use vim but it kept telling me i did not own the file so i could not change it,

so i used gksudo nautilus and dragged the file there made the changes then could not put the file back in,for some reason i do not own it,

so i was having a think and the power went out so now no sudoers file and i cant use sudo

so how do i get it back,there is a file in there called "sudoers.tmp.save"

i see you solved your problem. i would like to give a bit of advice:
- don't move config files around! 
- backup config files before editing. 
- try to get used to a console editor. you may need one if you break X. i like nano a lot. 
```
sudo nano -B /etc/sudoers
``` the '-B' option is to create a backup!

cheers

---

