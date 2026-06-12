---
title: "keyring popping up every few minutes"
date: 2015-07-24
forum: General Help
---

### Post by ariel8 on 2015-07-24
Hello!

in the past couple of days my computer has been acting weird.
the "enter password to unlock your keyring" popup has been appearing every few minutes.
this has started happening a few days ago, i dont know what is the cause of this, i haven't installed any new software...

ps. i dont want to just disable the keyring, i want to know what causes it to pop up every few minutes.

---

### Post by Bucky Ball on 2015-07-25
It should tell you why the keyring is required. What application is requiring it?

---

### Post by ariel8 on 2015-07-25
> **Bucky Ball said:**
> It should tell you why the keyring is required. What application is requiring it?
it doesnt say what application, it just say "your keyring wasn't unlocked when you logged in to your computer"

---

### Post by Bucky Ball on 2015-07-25
BTW, off-topic, but are you using 14.10 and this has only just started happening? Might have something to do with the fact that 14.10 is now end-of-life and no longer supported. Did you do an update in the last couple of days? Run these commands and please report any errrors:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Once you have an identifiable error message you can research that message and add 'ubuntu' to the end. From 'keyring unlock ubuntu' I found [this]("http://ubuntuhandbook.org/index.php/2013/07/disable-unlock-login-keyring-ubuntu-13-04/"). It is for 13.04 but might work. 

You might find more clues [here]("https://duckduckgo.com/?q=keyring+not+unlocked+ubuntu"). Good luck and let us know what happens.

Are you using auto-login?

---

### Post by ariel8 on 2015-07-25
> **Bucky Ball said:**
> BTW, off-topic, but are you using 14.10 and this has only just started happening? Might have something to do with the fact that 14.10 is now end-of-life and no longer supported. Did you do an update in the last couple of days? Run these commands and please report any errrors:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Once you have an identifiable error message you can research that message and add 'ubuntu' to the end. From 'keyring unlock ubuntu' I found [this]("http://ubuntuhandbook.org/index.php/2013/07/disable-unlock-login-keyring-ubuntu-13-04/"). It is for 13.04 but might work. 

You might find more clues [here]("https://duckduckgo.com/?q=keyring+not+unlocked+ubuntu"). Good luck and let us know what happens.

Are you using auto-login?

it says there are no new updates avilable,
i tried the method for 13.04 and it seemed to work. thanks for the help!

---

### Post by Bashing-om on 2015-07-25
ariel8; Hey; 

Exercise care:
> 
i tried the method for 13.04 and it seemed to work. thanks for the help!

If you are indeed running a 'raring (13.04)' release, it also is End_Of_Life and has no support.
In that event of running 13.04, you know what to do.

[INDENT][INDENT]help is what we do
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-07-25
> **Bashing-om said:**
> ariel8; Hey; 

Exercise care:

If you are indeed running a 'raring (13.04)' release, it also is End_Of_Life and has no support.
In that event of running 13.04, you know what to do.

[INDENT][INDENT]help is what we do
[/INDENT][/INDENT]

Don't think 13.04 is the case. The fix I linked to was for 13.04 but no reason it wouldn't work on the newer releases either. And it did. :)

---

### Post by Bashing-om on 2015-07-25
> **Bucky Ball said:**
> Don't think 13.04 is the case. The fix I linked to was for 13.04 but no reason it wouldn't work on the newer releases either. And it did. :)

K ..:)
Better safe than sorry, ( take time to read the full story, young-un)

[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

