---
title: "Is there any method mcomix can access to an external hard drive?"
date: 2018-05-18
forum: General Help
---

### Post by cametan2 on 2018-05-18
Hello.

I have just upgraded to Xubuntu 18.04LTS and noticed there is no more COMIX I have used and loved.
Instead, Ubuntu software suggested MCOMIX as an alternative.
Here comes the problem.

If MCOMIX found zip or rar folders, containing jpg or png files such as mangas, for instance, on /home, it would be O.K. It works like COMIX; however, if it found such archived and compressed stuff on an external drive, it could not access to it and mention like "There is no pictures in the folder". Very strange.

Is there any way to let MCOMIX access to files/folders on an external hard disk drive?

---

### Post by Holger_Gehrke on 2018-05-18
That is strange. I switched from comix to mcomix several years ago and never had trouble accessing comics on my external hd. Since you're saying you installed it through Ubuntu Software it might be a snap and those are sandboxed according to policies set by the packager. There was a similar case involving vlc installed as a snap which could not access external media. You can check whether mcomics is a snap by entering 'snap list' in a terminal. If it's on the list, it's a snap ...

So if it is, the solution is simple: remove it and install with 'sudo apt install mcomix' in a terminal. This will get and install a deb-package and those are not constrained as snaps are.

Holger

---

### Post by cametan2 on 2018-05-18
To Mr. Holger

Oh, yes. I did not notice that Ubuntu Software prepares "Permission" for MCOMIX. After I turned three switches on, MCOMIX could access an external hard drive.

Thanks for your kind advice!

---

### Post by silvanos on 2018-05-19
Hello cametan2,

I have the same issue on Ubuntu 18.04, could you explain how did you do that?

Thanks in advance!

---

### Post by silvanos on 2018-05-19
solved, reinstalled and noticed the Permission button.Thanks anyway for the hint!

[ATTACH=CONFIG]279746[/ATTACH]

---

