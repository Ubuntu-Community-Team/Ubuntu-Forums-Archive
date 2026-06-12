---
title: "will not save configuration"
date: 2005-05-22
forum: General Help
---

### Post by belred on 2005-05-22
i just installed kedit and when i run it, i get this message:

will not save configuration.
Configuration file "/home/bryan/.kde/share/config/keditrc" not writeable.

and i'm not able to change the font or anything.   when i sudo kedit, of course it works as expected but i don't think i should need to do this just to run it.  so my question is why don't i (a regular user) have permission to save the configuration when it's my preferences in my own home directory?  i can set the preference in other programs, such as kate without a problem.  so what is different about kedit?  do i need to do something since i installed it after installing the kubuntu?

sorry is this is such a basic question.  this is my first time playing around with linux.  after installing every distrobution i could get my hands on this past few weeks, i feel most comfortable with kubuntu, so thanks to whoever i should be thanking !!! 

thanks,

bryan

---

### Post by dave9191 on 2005-05-22
Its probably cause you dont have permission to edit the config file. Its been most likely created as root (when you installed with sudo), and as a normal user you cant write to it. You will have to edit the file permissions. If you open konqueror as root you can find the file and right click for the properites. 

Or you can just use chmod to give everyone write permission to the file

sudo chmod 777 /home/bryan/.kde/share/config/keditrc

Best thing to do would be to change the file owner to yourself (either using konqueror or chown), but the above will work :)

---

### Post by belred on 2005-05-22
thanks... i used konqueror as you suggested and it was really simple and intuitive to change the permissions (just like windows :)   so, when you install anything with kynaptic, aren't you always root since you have to type in your password which does a sudo for you?  is this the normal procedure that i will need to change the configuration files for all applications in each user's home dir that i install with kynaptic?  or did i do something wrong to cause the kedit configuration files to be ownd by root even though they were in the users home dir.

thanks,

bryan

---

### Post by dave9191 on 2005-05-23
Its not normal procedure to have to change file permissions, and its not something that you did wrong. Its most likely to be a tiny oversight in the kedit package by whoever put that together. Ive had something like that happen once or twice out of probably over a hundred installed packages :)

Dave

---

