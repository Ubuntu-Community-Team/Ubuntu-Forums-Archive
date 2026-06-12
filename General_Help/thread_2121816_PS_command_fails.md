---
title: "PS command fails"
date: 2013-03-03
forum: General Help
---

### Post by patzer on 2013-03-03
I'm relatively new to Ubuntu - I'm run ning 12.04 LTS. When I try to run the ps command its failing with the message:

ps -ef
ps: error while loading shared libraries: libprocps.so.0: cannot open shared object file: No such file or directory

I'm trying to run a script that uses the ps command so I need to figure out whats wrong on my laptop.

Any suggestions on where to start.

---

### Post by prodigy_ on 2013-03-03
[http://askubuntu.com/questions/144954/recover-ps-command](http://askubuntu.com/questions/144954/recover-ps-command)

---

### Post by patzer on 2013-03-03
Tried re-installing procps as per link but still getting the same message. Is procps dependant on some other package that I'm missing.

---

### Post by Bufeu on 2013-03-03
[http://www.raspberrypi.org/phpBB3/viewtopic.php?t=32282&p=277701](http://www.raspberrypi.org/phpBB3/viewtopic.php?t=32282&p=277701)
[http://stackoverflow.com/questions/14682783/error-while-loading-shared-libraries-libstdc-so-confused](http://stackoverflow.com/questions/14682783/error-while-loading-shared-libraries-libstdc-so-confused)

---

### Post by prodigy_ on 2013-03-03
Hm. I did some research and in fact 12.04 shouldn't even have the libprocps.so.0 library. It's provided by libprocps0, a package that first appeared in 12.10.

Did you add any repositories on your machine? Or install anything manually (from deb packages or sources)?

---

### Post by patzer on 2013-03-03
Prodigy, I was trying to follow the instructions ([http://wiki.openelec.tv/index.php?title=Building_and_Installing_OpenELEC_for_Raspberry_Pi](http://wiki.openelec.tv/index.php?title=Building_and_Installing_OpenELEC_for_Raspberry_Pi)) to cross-compile OpenELEC on my laptop when that make script failed on the "checking ps " line, so yes - there has been a fair bit of updating going on.

---

### Post by prodigy_ on 2013-03-03
I'm not familiar with OpenELEC but compiling something shouldn't break your system no matter what you compile.

Anyway, a little sanity check: ```
which ps
dpkg -l | grep procps
```

---

### Post by patzer on 2013-03-03
Prodigy, Sorry sleep was necessary. Here is output:

trevor@trevLaptop:~$ which ps
/home/trevor/bin/ps
trevor@trevLaptop:~$ dpkg -l | grep procps
ii  procps                                 1:3.2.8-11ubuntu6                       /proc file system utilities

running /bin/ps works fine, but my PATH is: . /home/trevor/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

Is this just a make script problem?

---

### Post by patzer on 2013-03-03
Prodigy, Sorry sleep was necessary. Here is output:

trevor@trevLaptop:~$ which ps
/home/trevor/bin/ps
trevor@trevLaptop:~$ dpkg -l | grep procps
ii  procps                                 1:3.2.8-11ubuntu6                       /proc file system utilities

running /bin/ps works fine, but my PATH is: . /home/trevor/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

Is this just a make script problem?

---

### Post by tgalati4 on 2013-03-03
Try reworking your PATH:

Mine is less mangled:

tgalati4@Mint14-Extensa ~ $ $PATH
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games: No such file or dir

---

### Post by prodigy_ on 2013-03-03
> **patzer said:**
> $ which ps
/home/trevor/bin/ps
Should be **/bin/ps**. Like **tgalati4** suggests, you should remove **/home/trevor/bin** from your $PATH variable. 

If you want to keep that **bin** folder in your home folder, you should also comment out the following line in your **.profile**: ```
PATH="$HOME/bin:$PATH
``` Otherwise simply: ```
rm -r ~/bin # be careful with this command
```

---

### Post by patzer on 2013-03-03
Thanks to Prodigy_  and tgalati4 for their help.
Modified the PATH as suggested and the make script  runs ok now. Don't know what inserted that /home/treevor/bin entry.

Regards, Trevor
PS: To mark this thread as Solved, do you have to manually add [SOLVED] to the title - can't find the Thread Tools menu referred to in the Help positing.

---

### Post by patzer on 2013-03-03
The issue with marking SOLVED is known. For fix see here:
[http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

---

### Post by Impavidus on 2013-03-04
> **patzer said:**
> Thanks to Prodigy_  and tgalati4 for their help.
Modified the PATH as suggested and the make script  runs ok now. Don't know what inserted that /home/treevor/bin entry.

Regards, Trevor
PS: To mark this thread as Solved, do you have to manually add [SOLVED] to the title - can't find the Thread Tools menu referred to in the Help positing.

If the directory exists /home/$USER/bin is in your PATH by default. Alternative solution is to rename the file /home/treevor/bin/ps and any other files there that cause unintentional naming conflicts with commands.

---

