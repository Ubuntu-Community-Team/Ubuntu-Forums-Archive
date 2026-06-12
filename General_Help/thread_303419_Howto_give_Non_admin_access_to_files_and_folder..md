---
title: "Howto give Non admin access to files and folder."
date: 2006-11-20
forum: General Help
---

### Post by AdonisV on 2006-11-20
I have this stepmania game where it does'nt require install. it has a folder where all files are already ordered. now I unzipped the folder into "/home/myaccountname/stepmania-3.9" where I can run the game perfectly. now I gave my brother an account so he can't bug me using my "admin" account where only thing he can't do is admin the system. now the weird thing is he can't run the stepmania game and it says permision dennied. so I tought that maybe if I put it in /usr/share instead it might work. now runing it using his account still does'nt make it work. I'm stuck

---

### Post by wongdai on 2006-11-20
> **AdonisV said:**
> I have this stepmania game where it does'nt require install. it has a folder where all files are already ordered. now I unzipped the folder into "/home/myaccountname/stepmania-3.9" where I can run the game perfectly. now I gave my brother an account so he can't bug me using my "admin" account where only thing he can't do is admin the system. now the weird thing is he can't run the stepmania game and it says permision dennied. so I tought that maybe if I put it in /usr/share instead it might work. now runing it using his account still does'nt make it work. I'm stuck

Try going to the directory where you the game lives, and type:
chmod 777 *

and see how you go.

---

### Post by bettlebrox on 2006-11-20
777! That's generally a bad thing to do. 

777 will mean anyone on the system will able to do almost anything to in that directory. That could be bad, especially if you got hacked or something.

Try 755 instead, or if your brother needs write access to the directory set the permissions to 775, use chgrp to set the files to below to the games groups, and make sure your brother is in the games groups;

chgrp games /usr/share/stepmania-3.9

And another thing, it can be a bad idea to mix your stuff with systems files. I'd move the stepmania directory to /usr/local/games

---

### Post by AdonisV on 2006-11-29
ok thanks. :KS

---

