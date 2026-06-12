---
title: "How to Keep lsyncd on reboot"
date: 2022-09-05
forum: General Help
---

### Post by limotux2 on 2022-09-05
Hi all,
This is my first post here as I am new to Ubuntu (and a bit new to Linux as well.)

I have some local folders on my drive (e.g.: source1, source2, source3) I want to lsync them 2 way with (target1, target2, target3) respectivly.

I successfully did:
[HTML]lsyncd -insist -rsync /home/limo/source1 /home/limo/target1[/HTML]
and
[HTML]lsyncd -insist -rsync /home/limo/target1/ /home/limo/source1[/HTML]

[FONT=monospace]Which I believe went fine and synced both folders 2 way![/FONT]

[FONT=monospace][B]I am trying to find a way to make these commands permanent and automatically run by itself after reboot. (this is the main goal now)
[/B]
[/FONT]Another extra thing I need to do is to sync between folders on external USB driive(s) and be sure I can unplug one USB drive, go to visit a friend, copy and delete files... then I go back home and just plug it and it syncs automatically.

I will appreciate any guidance (in simple language, specific commands to run... as I am absolute noob)

Thank you very much in advance.

---

### Post by #&amp;thj^% on 2022-09-05
Please show us this, as many things come in to play here:
```
tail -f /var/log/lsyncd/lsyncd.status
```
Also might be worth checking your:
```
ls /mnt/
```
That may helps us here to help you better.

---

### Post by limotux2 on 2022-09-05
[HTML]limo@fujitsu:~$ tail -f /var/log/lsyncd/lsyncd.status
tail: cannot open '/var/log/lsyncd/lsyncd.status' for reading: No such file or directory
tail: no files remaining

[/HTML]

and
[HTML]limo@fujitsu:~$ ls /mnt/
limo@fujitsu:~$ 

[/HTML]

Thank you very much. I really appreciate your help.

---

### Post by #&amp;thj^% on 2022-09-05
Ok now this:
```
systemctl status lsyncd
```
Thanks for being prompt with you reply.;)

---

### Post by limotux2 on 2022-09-05
You are welcome. It is me who should thank you.
[HTML]limo@fujitsu:~$ systemctl status lsyncd
&#9679; lsyncd.service - LSB: lsyncd daemon init script
     Loaded: loaded (/etc/init.d/lsyncd; generated)
     Active: active (exited) since Mon 2022-09-05 18:28:34 EET; 54min ago
       Docs: man:systemd-sysv-generator(8)
    Process: 767 ExecStart=/etc/init.d/lsyncd start (code=exited, status=0/SUCCESS)
        CPU: 1ms

Sep 05 18:28:34 fujitsu systemd[1]: Starting LSB: lsyncd daemon init script...
Sep 05 18:28:34 fujitsu systemd[1]: Started LSB: lsyncd daemon init script.
limo@fujitsu:~$ 

[/HTML]

---

### Post by #&amp;thj^% on 2022-09-05
Can we have a peek at this as well;
```
cat etc/lsyncd/lsyncd.conf.lua
```
As you can now see many things come in to play here.

---

### Post by limotux2 on 2022-09-05
I see... I tried to find a way just to keep those 2 commands after booting.
Would it be easier to make a script .sh to run them and put it in auto start?

[FONT=monospace][COLOR=#54FF54]**limo@fujitsu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ cat etc/lsyncd/lsyncd.conf.lua[/COLOR]
cat: etc/lsyncd/lsyncd.conf.lua: No such file or directory
[COLOR=#54FF54]**limo@fujitsu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ [/COLOR]

[/FONT]

---

### Post by #&amp;thj^% on 2022-09-05
This may be the easiest approach for you: [https://www.howtoforge.com/how-to-synchronize-directories-using-lsyncd-on-ubuntu/](https://www.howtoforge.com/how-to-synchronize-directories-using-lsyncd-on-ubuntu/)
Keep us posted and take your time reading the link.
Good Luck :)

---

### Post by limotux2 on 2022-09-05
Thank you.

---

