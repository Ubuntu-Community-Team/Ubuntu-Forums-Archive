---
title: "AMSN Display Picture messed up &amp; cannot remove it"
date: 2007-09-12
forum: General Help
---

### Post by kingrattus on 2007-09-12
I set a photo for my disply pic & I changed a setting because I wanted to see what the settings did. Well, I no longer can change my disply photo. When I go to Change display image  the picture is MASSIVE & I can only see about 1/8th (if that) of the image & NO setting options. 

Its slowing amsn right down & its not only affecting me. My buddy who also uses amsn said the image is so huge he has to remove it just so he can talk to me :(

I tried looking for the image in the amsn folder & had no luck.. So I thought maybe its code & its linking to the image in a folder or something.. so I moved the origional image.. nope didn't work.

I'm not a pro at this stuff.. still learning. Please make the steps very clear as I don't understand all this linux stuff yet... I'm getting a lot better, but by far not a pro.


Thanks in advanced

Jess

---

### Post by kingrattus on 2007-09-13
I tried to uninstall amsn & just start over... well when I reinstalled it, it auto loged me in!!   Wow that was sooooo helpful... the uninstall did nothing!  Man this really sucks. :(   I just want to be able to use amsn without bogging down the program  *bangs head on desk*

---

### Post by kingrattus on 2007-11-08
Is anyone able to help?  I hate the program I'm currently using.. I just need to know where the display files are stored for AMSN, so I can delete it... Please Anyone :(

---

### Post by JCrowly on 2008-01-06
I had the exact same problem and managed to fix it, so here's how in case you're still dealing with that.

Browse to: /home/<your username>/.amsn/<your email address>
note that your email address will have any "." or "@" symbols replaced with "_"'s

Now you can either open the folder named "displaypic" and delete the picture you're currently using as well as the associated .dat file,

--or--

Open config.xml with gedit or whatever text editor you like.

Scroll down to, or search for "displaypic". Just below that you will see a line with the path to an image file. Replace that line with "amsn.png". Save the config.xml file and open up amsn.

Both of those methods worked for me. I hope they help you out if you haven't already fixed it.

---

### Post by kingrattus on 2008-01-06
Thank you for answering my plea for help. 

My friend was farting around(neither of use great at this) & he learned there was hidden files in home/"username"  Then he told me to find the pic & delete it... I use Mercury now as AMSN had me upset for far too many months.

Hopefully this thread will help others with this issue,

---

### Post by 4591jenny on 2008-04-21
i cant do both of the things :( 
please help me

---

### Post by ryanhaigh on 2008-04-21
Given that you are having trouble Im just going to offer a simpler solution, open your home directory by going to Places>Home Folder, go to the View menu and press the Show Hidden Files option, now find the folder called .amsn and delete it. This will remove ALL your amsn settings so you will have to create them again but that isn't generally a big deal as all your contact info is on the msn servers. 

You may also want to checkout a program called emesene, available at getdeb.net which is a nicer msn client than amsn, unless you need webcam support which it doesn't yet have.

---

### Post by 4591jenny on 2008-04-21
haha i have found my solution i went to my documents and went into C:/ documents and settings that was just after i unistalled amsn, i av now reinstalled nd this is amsns last chance LMAO!!!

---

### Post by ProfKaramba on 2008-05-14
this worked for me :)

thkx

---

### Post by kingrattus on 2008-05-14
> **ryanhaigh said:**
> Given that you are having trouble Im just going to offer a simpler solution, open your home directory by going to Places>Home Folder, go to the View menu and press the Show Hidden Files option, now find the folder called .amsn and delete it. This will remove ALL your amsn settings so you will have to create them again but that isn't generally a big deal as all your contact info is on the msn servers. 

You may also want to checkout a program called emesene, available at getdeb.net which is a nicer msn client than amsn, unless you need webcam support which it doesn't yet have.

Mercury has Webcam support. The only thing I believe Mercury doesn't have is group chat.. or whatever its called (its been years since I have used MSN messenger).

I am glad everyone has been able to resolve this annoying issue we all had. :KS :KS :KS :KS :KS

---

