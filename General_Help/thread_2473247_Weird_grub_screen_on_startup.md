---
title: "Weird grub screen on startup"
date: 2022-03-29
forum: General Help
---

### Post by robert71 on 2022-03-29
I get this weird scrren on startup that i have to type exit before the list of my Operating Systems load, its attached. 
Can anyone assist me in disabling or understanding this behaviour from GRUB. 


thanks

---

### Post by Bashing-om on 2022-03-29
Hey robert71 -

Grub not happy with config file ?

Before we get all hot and bothered:
what returns:
```

sudo apt update
sudo apt upgrade
sudo update-grub

```

-kernel heal thyself-

---

### Post by robert71 on 2022-03-30
So I ran the commands and it updated successfully. 
I didn't see the startup screen when it booted. 
Not sure what was fixed but i am glad it was.

Thanks for your help.

---

### Post by Bashing-om on 2022-03-30
Hey hey robert71 :D

Great. Glad the simple thing worked out.
Here most likely the commands redid grub's config file.

As this matter is now concluded -
 Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

-just keep on keep'n on-

---

