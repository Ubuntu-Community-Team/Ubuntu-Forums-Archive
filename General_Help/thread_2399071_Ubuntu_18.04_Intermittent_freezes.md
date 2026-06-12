---
title: "Ubuntu 18.04 Intermittent freezes"
date: 2018-08-21
forum: General Help
---

### Post by midugre on 2018-08-21
I"m experiencing intermittent freezes.
Sometimes it last a minute, but sometimes way more than that.

Please have a look at the attachment to see tasks runing while PC at freeze

Any help will be much appreciated.

Thanks

---

### Post by karthikeyan.d on 2018-08-24
I too have seen 18.04.1 hang once in a while. All hangs happened while a browser was running : Firefox or Chrome. When the hangs with Firefox happened, I was trying to open a link in a new tab by clicking the right mouse button. With Chrome, the hangs happened when I was watching some Youtube video. I googled and found the following bug

gnome-shell uses lots of memory, and grows over time
[https://bugs.launchpad.net/gnome-shell/+bug/1672297](https://bugs.launchpad.net/gnome-shell/+bug/1672297)

I decided to monitor free memory. I started a shell script every time I logged in. It ran "free" once every 10 seconds and logged it in a file. Nothing happened for a couple of days. Then today, the system froze while I was watching a Youtube video on Chrome. I restarted the system and checked the log. The last entry was

                     total         used           free      shared   buff/cache    available
Mem:        3905900     2117768      592588      501012     1195544     1054020 
Swap:       8119292           0     8119292 

There seemed to have been sufficient memory when the system froze. I started Firefox and was trying open the bug link (mentioned above) and the system froze again. The script log showed

                    total          used           free       shared  buff/cache    available
Mem:        3905900     1375800     1515952      186780     1014148     2112240 
Swap:       8119292           0     8119292 

So, the problem does not seem to be because of depletion of memory due to memory leak somewhere.

Is there anything else I can do to figure out the problem here? Some other tool to use or some other parameter to monitor? How to find out if this is a s/w or h/w issue?

So far the hangs have happened only while browsers were running. I have watched movies (using vlc) and saw no hangs. Every time the system hung I had to power it off and on. I tried the ALT + PrtScr + R E I S U B method I saw in a Ask Ubuntu page but it did not work for me.

System details :
Dell Inspiron 15 3567 (Came with 16.04. I upgraded to 18.04.1)
Intel(R) Core(TM) i3-6006U CPU @ 2.00GHz

Thanks

---

### Post by karthikeyan.d on 2018-08-24
The hangs that I saw did not seem to be intermittent. The system remained froze even after a few minutes. I had to power off every time.

Nothing interesting in the syslog file.

Thanks

---

