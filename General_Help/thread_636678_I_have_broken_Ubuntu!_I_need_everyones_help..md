---
title: "I have broken Ubuntu! I need everyones help."
date: 2007-12-10
forum: General Help
---

### Post by idiot1000 on 2007-12-10
I have only had Ubuntu for 3 days and already I have broken it.

Also I am extremly new to the world of Linux so please don't be to harsh.

Heres what happend.

I installed some thing on Ubuntu called Xampp it's like WAMP but for Linux ok.
It's directory was /opt and only root had access to it right.

So I thought to myself: "Hay if I chown the / directory to my usersname I will be able to write to the directory and every other"

#$#%ing stupid I know.

Heres the next stupid thing: I actually ran sudo chown -hR root / instead of sudo chown -hR anonymous /

So I log out and then I can't login again, I am forced to log into recovery mode and issue the command:

chown -hR anonymous /home/anonymous

I also know at some point I chowned the entire root dir to my user account and at which point daemons wern't functioning properly and I had to go back to recovery consol chown everything back to root then chown my home dir back.

IS THERE A WAY TO RESET ACCESS RIGHTS TO FOLDERS TO DEFAULT!?!

Will I have to re-install it?

Please help everyone I am a noob.

Also I can get into my account now but I have no internet connection it DNS times out.

What is the best way to fix this problem Ubuntu forums. :KS

---

### Post by sloggerkhan on 2007-12-10
I'd copy your home folder's documents somewhere and then just do a clean install.

---

### Post by PmDematagoda on 2007-12-10
+1 on what sloggerkhan said, there was a person with your same situation, but in the end the situation just became worse since the permissions and ownerships are not uniform to the different folders and files in the base folders in the Root directory. This means that you can either check and reset the ownerships one by one in every folder in the Root directory except the Home directory, or you can reinstall.

In this case, you would be better off just reinstalling the system.

---

### Post by amugofcoffee on 2007-12-10
Heh, I remember doing something like that, except it was chmod -R 777 /, and it was for XAMPP too.

---

### Post by staticvoid on 2007-12-10
well.

I'd say reinstall. get the stuff you need, as you can login, and then just reinstall.

it will start you fresh and you will be happy :)

you only used ubuntu for 3 days, how much tweaking could you have done?

reinstall man. I think thats the best way. But wait for a second opinion, cause i'm not certain about setting folder privledges to default.. but I doubt it..


static void

---

### Post by staticvoid on 2007-12-10
wow. once again I typed too slow :) there you have it, back up and reinstall.

---

### Post by idiot1000 on 2007-12-10
Guys thank you so much for the quck reply it does mean a lot to me.

When I set up Ubuntu I made sure I setup the /home on a seperate partion. I don't know but I think that means I can reinstall Ubuntu without losing anything?

I will use Google if you guys can't come up with a better solution thanks for the support.

---

### Post by idiot1000 on 2007-12-10
K I am really impantent I am going to re-install it now. I found a little guide to do it on your forums. Thanks again for all the help.

---

### Post by PmDematagoda on 2007-12-10
> **idiot1000 said:**
> 
When I set up Ubuntu I made sure I setup the /home on a seperate partion. I don't know but I think that means I can reinstall Ubuntu without losing anything?


Yes, and the good part is that you can use it with your new Ubuntu install with no problems, **provided** that the permissions and ownerships are correct.

---

### Post by idiot1000 on 2007-12-10
Hay it;s me again.

I am in the install and it is saying there is no users or operating systems suitable for importing from.

Is this going to be a problem?

It can;t find my user account.

What should I do can I install it anyway will it erase my data on my anonymous account?

---

### Post by sloggerkhan on 2007-12-10
just make sure you name your new user the same thing as your old user and that you don't format the /home partition and that you also mount /home as /home again.
I think the import user thing might be for importing users from windows? In any case, worse case, you might want to delete all the .dotfiles or re-own them if you need to.

---

### Post by idiot1000 on 2007-12-10
> **sloggerkhan said:**
> just make sure you name your new user the same thing as your old user and that you don't format the /home partition and that you also mount /home as /home again.
I think the import user thing might be for importing users from windows? In any case, worse case, you might want to delete all the .dotfiles or re-own them if you need to.

Well I am back online.

Have a fresh install of Ubuntu with no data loss at all which is more than what I could have hoped for.

I have created a new user and just copyed all the files from my old users account's desktop to my new ones.

Also why did you say to make the new user the same as the old one?

---

### Post by amugofcoffee on 2007-12-10
I believe that this allows you to take ownership of the home folder of the old user.

---

