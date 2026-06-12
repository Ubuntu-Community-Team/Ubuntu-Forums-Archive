---
title: "stop having to put passwords"
date: 2008-05-30
forum: General Help
---

### Post by chriskin on 2008-05-30
i know that having to write my password keep me secure but i am kind of bored to do it all the time
i mean, i want to change sth, i have to write it
i want to install a new application, i have to write it
etc etc

also, i have asked for an automatic login at the system/administration/login windows but is seems that i just have to write the password once it has loading the profile

is there any way that i can bypass passwords everywhere?

---

### Post by LaRoza on 2008-05-30
> **chriskin said:**
> i know that having to write my password keep me secure but i am kind of bored to do it all the time
i mean, i want to change sth, i have to write it
i want to install a new application, i have to write it
etc etc

also, i have asked for an automatic login at the system/administration/login windows but is seems that i just have to write the password once it has loading the profile

is there any way that i can bypass passwords everywhere?
If you need to do a lot as root, you can use a root shell:

```

sudo -i

```

As for changing the security policy of Ubuntu: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by wpshooter on 2008-05-30
> **LaRoza said:**
> If you need to do a lot as root, you can use a root shell:

```

sudo -i

```

As for changing the security policy of Ubuntu: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

If you have to do everything at a terminal and type SUDO, then you might as well type in the password.

---

### Post by zvacet on 2008-05-30
That is not recommended but if you want to do it read** Remove Password Prompt For SUDO** [here.]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Zorael on 2008-05-30
Now I'm being something of an (donkey), but the point is to get all applications installed, all system-wide settings fixed, and then be a normal, unprivileged user. :>

As linux grows easier to use, it'll attract more non-"power users" who are, arguably, more easily suckered into installing malware. *"Your computer may be at risk! Install this to speed up your system! This codec will play everything!"*

It's supposed to be tedious-ish. :>

---

### Post by chriskin on 2008-05-30
it might be my lack of knowledge
but i think that you are all saying about having to put no password on the terminal
i am talking about "everyday" use, can i stop pushing passwords if i become the "superuser" said in the link zvacet gave?

---

### Post by BLTicklemonster on 2008-05-30
Every time you enter a password is one less time that you would have normally run an antivirus program.

think about it.


better yet:

Every time you enter a password, God boils a script kiddie in oil.

so yeah, it's worth the effort of being inconvenienced, if you can call it that.

hey, I know, as long as you're going to do away with your password, leave the doors and windows to your house wide open every night, and leave the keys to your car in the ignition, and invite homeless people to your house then show them the refrigerator and your little sister, then leave for a few days.

(okay, okay, that's pushing it. Just because they're homeless doesn't mean they haven't eaten)

---

### Post by chriskin on 2008-05-30
> **BLTicklemonster said:**
> Every time you enter a password is one less time that you would have normally run an antivirus program.

think about it.


better yet:

Every time you enter a password, God boils a script kiddie in oil.

so yeah, it's worth the effort of being inconvenienced, if you can call it that.

hey, I know, as long as you're going to do away with your password, leave the doors and windows to your house wide open every night, and leave the keys to your car in the ignition, and invite homeless people to your house then show them the refrigerator and your little sister, then leave for a few days.

(okay, okay, that's pushing it. Just because they're homeless doesn't mean they haven't eaten)


i started my post saying that i know that it might be dangerous
yet it is my decision is it not? :S

---

### Post by BLTicklemonster on 2008-05-30
Choose thinking, then carry on. If it's worth the risk, go for it!

---

