---
title: "OS won't boot after dist-upgrade"
date: 2017-11-25
forum: General Help
---

### Post by Vitor_Hugo on 2017-11-25
Hello Community,


I have a problem with my OS, has the title suggests this situation occurred after a dist-upgrade.

The system hangs everytime it boots and some, and it is visible some scratches on the screen (like it does when you have some video card problem)

To bypass i have to enter recovery mode pressing ESC at boot time, and select advanced options / recovery mode, then select normal startup

from the list provided. (edited) (i don't have a video card problem/driver problem ;)  )

My question is, how do i solve this, i know for my experience that this occurred when the internet connection dropped in the middle of the update

trough the terminal.

I tried making the commands again apt-get update, apt-dist-upgrade but it doesn't solved it,  has i have new version already (17.10) but i think

something is wrong, and i can't seem to find the solution, have tried the dpkg command , and not successful either, i'm a linux newbie,

(edited) - I search before making the thread as a guest, did,'t find my problem in a topic marked as solved, recovered password by email to actually 

post this.

Thanks in advance !

---

### Post by yancek on 2017-11-25
Were you doing an upgrade from 17.04?

If your internet connection dropped during the upgrade, I would expect serious problems.  So what exactly happens when you try to update/upgrade again?  Any output in the terminal.

---

### Post by Vitor_Hugo on 2017-11-25
Hello Yancek, 

Thanks for your quick answer, yes i think i had 17.04 and i updated to 17.10 trough terminal.

As my OS is in  Portuguese, it says 0 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 0 não actualizados. when i try updating

it suggests there's nothing to upgrade, in my system profile/benchmark , in OS summary says i have 17.10 but it seems broken.

Any advice ? 

If it is too complicated, i think i will try a fresh install, but i'm curious about it, because it can happen again in the future

Thank you

---

### Post by Autodave on 2017-11-25
I run 13 machines and rarely have had any luck upgrading from one OS to the next. Last try, one machine worked with no problems, 3 had several problems, the rest were goners.

Every 2 years, a long term service release is made. These LTSs have a service life of 5 years: security and software updates are available for 5 years after the release.  The last LTS was 16.04. 16 stands for the year of the release, 04 stands for the month (April). The next LTS will be 18.04. Releases in the interim will be 6 month releases and only supported until the next release.

I stick with only the LTSs and even then I usually wait a month after their release before installing them. Further, I do not upgrade to them but completely install the new release after copying all files that I need to save to an external HD.

---

### Post by Vitor_Hugo on 2017-11-25
Ok, so it seems it's a common problem in ubuntu upgrade, i will do a fresh install and stick to the LTS releases as you suggest, thank you man !

---

### Post by slickymaster on 2017-11-25
> **Vitor_Hugo said:**
> <---snip--->

As my OS is in  Portuguese, it says 0 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 0 não actualizados. when i try updating

<---snip-->
Just translating the terminal output```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Vitor_Hugo on 2017-11-25
Thank You !

Obrigado ! :)  


;)

---

### Post by deadflowr on 2017-11-25
Are there any other kernels listed in the Advanced Option menu of GRUB?

Not sure if you ran dist-upgrade or do-release-upgrade.

dist-upgrade will never outright upgrade releases, to do that you need to edit your sources.list file for apt to point to the new releases archives.
(you would have needed to change the archives in the sources.list file manually from zesty to artful to get 17.10 from a 17.04 install)

do-release-upgrade on the other hand is the tool you would use to upgrade from one release to another.
(and it does not require you to manually edit any files)

In either case older kernels would remain.
at least one older kernel.

---

### Post by Vitor_Hugo on 2017-11-25
Hello Deadflowr

Yes there are other 2 kernel modules available in the list, 2 older ones i think ( i can't remember the details about the names only remember something 

about generic something :/  (can't restart now to see) , i had more but i think the command autoremove, removed some of them/ or other thing.

Thanks for your answer, will do in the future the do-release-upgrade instead the dist-upgrade one , it's easy than to edit files, in my case now i will

edit the sources.list! 

The best

(can't rep you guys) :p i like forums to have a reputation system, to people who actually loose some time of their own to answer questions...it seems 

there's isn't implemented here, not a big deal anyway, i do not see before has a i'm newbie to this forums.

Thanks to you three !

Vitor Hugo

---

