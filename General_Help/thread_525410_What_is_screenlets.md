---
title: "What is screenlets?"
date: 2007-08-14
forum: General Help
---

### Post by kdarkentity on 2007-08-14
What is screenlets exactly and how can i install it?

---

### Post by tors on 2007-08-14
Here you can read about Screenlets

[http://forum.compiz-fusion.org/forumdisplay.php?f=102](http://forum.compiz-fusion.org/forumdisplay.php?f=102)

---

### Post by kdarkentity on 2007-08-15
do you know if i would have to switch to compiz fusion to use screenlets?

---

### Post by misfitpierce on 2007-08-15
I do believe so since the screenlet options are under compiz fusion manager. Compiz fusion is not a bad upgrade tho for effects if your into that. :)

---

### Post by kdarkentity on 2007-08-15
alright ill have to try it out than... im currently using beryl with emerald theme manager ... will i still be able to use my emerald themes with compiz fusion?

---

### Post by kdarkentity on 2007-09-18
Ive been trying to install screenlets so that they will work with beryl but ive made no progress, could someone refer me to a good tutorial on how to do this?

---

### Post by kdarkentity on 2007-11-23
Im Still trying to get screenlets only now i am using compiz fusion.

---

### Post by FuturePilot on 2007-11-23
See here
[http://ubuntuforums.org/showpost.php?p=3783937&postcount=4]("http://ubuntuforums.org/showpost.php?p=3783937&postcount=4")
:)

---

### Post by santiagoward2000 on 2007-11-23
> **FuturePilot said:**
> See here
[http://ubuntuforums.org/showpost.php?p=3783937&postcount=4]("http://ubuntuforums.org/showpost.php?p=3783937&postcount=4")
:)

Hey FuturePilot!
There's one little problem with that guide. The repositories have changed. You should add:
```
deb http://download.tuxfamily.org/screenlets gutsy screenlets
``` in Third Party Software.
Then, type this on a terminal:
```
wget http://download.tuxfamily.org/screenlets/hendrikkaju.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by kantor on 2007-11-23
if you want to use them under the compiz fusion widgets layer the more flexible way it's to check the "treat as a widget" option on the properties menu.

---

### Post by kdarkentity on 2007-11-23
Wow this is wicked sweet i finally have it working!, but now how do i get them to display on each workspace and where is a good place to get additional screenlets?

---

### Post by FuturePilot on 2007-11-23
In the Preferences for each Screenlet there should be an option to have it displayed on every desktop

---

### Post by kdarkentity on 2007-11-23
> **FuturePilot said:**
> In the Preferences for each Screenlet there should be an option to have it displayed on every desktop

Ok i found it, its under window>sticky. Now where can i ge more screenlets?

---

### Post by santiagoward2000 on 2007-11-23
> **kdarkentity said:**
> Ok i found it, its under window>sticky. Now where can i ge more screenlets?

Just go to [http://www.screenlets.org]("http://www.screenlets.org") and check the **third-party screenlets**.

---

### Post by kdarkentity on 2007-11-23
> **santiagoward2000 said:**
> Just go to [http://www.screenlets.org]("http://www.screenlets.org") and check the **third-party screenlets**.

Whats funny is whenever i try going to [http://www.screenlets.org](http://www.screenlets.org) it just times out, and if i try to ping it the result is unknown host

---

### Post by santiagoward2000 on 2007-11-23
> **kdarkentity said:**
> Whats funny is whenever i try going to [http://www.screenlets.org](http://www.screenlets.org) it just times out, and if i try to ping it the result is unknown host

Hmm, you're right, I just tried it. Well, some of those screenlets can be found in [http://www.gnome-look.org]("http://www.gnome-look.org"), under the **Desklets** section...
I hope this one works! :lolflag:

---

### Post by kdarkentity on 2007-11-23
> **santiagoward2000 said:**
> Hmm, you're right, I just tried it. Well, some of those screenlets can be found in [http://www.gnome-look.org]("http://www.gnome-look.org"), under the **Desklets** section...
I hope this one works! :lolflag:

Well this time i can get to gnome look and download the desklets, however i get the error whenever i try to install one  "Invalid archive. Archive must contain a directory with the screenlet's name"

---

### Post by santiagoward2000 on 2007-11-23
> **kdarkentity said:**
> Well this time i can get to gnome look and download the desklets, however i get the error whenever i try to install one  "Invalid archive. Archive must contain a directory with the screenlet's name"

Just uncompress the file to:
/home/yourname/.Screenlets
If the folder doesn't exists you can create it.

---

### Post by kdarkentity on 2007-11-23
Ok good i can use them now , thanks.

I get this error whenever i logon tho "Unable to connect or launch daemon. Some values may be displayed incorrectly.

How can i fix that?

---

### Post by Flare183 on 2007-11-23
You can try using my version of the screenlets. See link below.



[http://www.mediafire.com/?3outgtojz1j](http://www.mediafire.com/?3outgtojz1j)

---

### Post by santiagoward2000 on 2007-11-23
> **kdarkentity said:**
> Ok good i can use them now , thanks.

I get this error whenever i logon tho "Unable to connect or launch daemon. Some values may be displayed incorrectly.

How can i fix that?

Pay no attention to that message. It's just the screenlets-daemon, which is started after you open screenlets-manager. Close the manager and open it back again, the message doesn't show up because it's already open.

---

### Post by kdarkentity on 2007-11-23
ahh alright, its just kind of annoying.

---

### Post by santiagoward2000 on 2007-11-23
Perhaps you could set the file:
```
python /usr/local/share/screenlets-manager/screenlets-daemon.py
```
to start with your system, but I haven't tried it, so I don't know if this would help.

---

### Post by kdarkentity on 2007-11-23
> **santiagoward2000 said:**
> Perhaps you could set the file:
```
/usr/local/share/screenlets-manager/screenlets-daemon.py
```
to start with your system, but I haven't tried it, so I don't know if this would help.

alright thanks ill let you know if it helps

---

### Post by santiagoward2000 on 2007-11-23
> **kdarkentity said:**
> alright thanks ill let you know if it helps

I just tried this and it worked! Just one thing: I had to add **python** before the code I posted before.
I just edited it up there.
Cheers!

---

### Post by kdarkentity on 2007-11-24
hmm i didn't even have to put in python before it but ill edit it in now.

---

### Post by santiagoward2000 on 2007-11-24
> **kdarkentity said:**
> hmm i didn't even have to put in python before it but ill edit it in now.

Well, if it's working I don't see why you should add it... It's good to hear it works!

---

### Post by kdarkentity on 2007-11-25
definitely, i added python in before it anyways and its still working great. Thanks for all of your help by the way.

---

### Post by santiagoward2000 on 2007-11-25
> **kdarkentity said:**
> definitely, i added python in before it anyways and its still working great. Thanks for all of your help by the way.

You're welcome!

---

### Post by kdarkentity on 2007-11-28
One more question, i have a screenlet that is based on windows vista's cpu meter but it doesn't sync up and update itself all of the time, is there a way i could fix that?

---

### Post by kdarkentity on 2008-02-12
has the source file for screenlets been changed again?

because i recently switched to 8.04 64 bit, tried to install screenlets, and acording to my terminal it cannot find the packages for download.

---

