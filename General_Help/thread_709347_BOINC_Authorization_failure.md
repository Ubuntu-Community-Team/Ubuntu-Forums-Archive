---
title: "BOINC Authorization failure"
date: 2008-02-27
forum: General Help
---

### Post by xyious on 2008-02-27
hi !

i have tried for weeks to solve this problem ....

```
xyious@Melanie:~$ sudo boinc_cmd --get_state
Authorization failure: -102
```

used apt-get install boinc-client to get boinc, have not installed boinc manager, on account of the computer in question being a server with no gui. i haven't been able to find anything on this forum nor the rest of the internet.... hoping someone here will have a clue.


  -alexander knopf

---

### Post by xyious on 2008-02-28
guess not ....

---

### Post by Paul_K on 2008-05-29
xy-

It might be ok.  Take a look at ps aux | grep boinc 

I was getting this:

$ ps aux | grep boinc
boinc     7855  0.1  0.3   8208  3296 ?        S    10:26   0:00 /usr/bin/boinc_client --check_all_logins --redirectio --dir /var/lib/boinc-client

and:

$ boinc_cmd --get_state
Authorization failure: -155

I noticed my working (Gutsy) boinc didn't have the --check_all_logins so I edited:  sudo gedit /etc/init.d/boinc-client

old: BOINC_OPTS="--check_all_logins --redirectio --dir $BOINC_DIR $BOINC_OPTS"
new: BOINC_OPTS="--redirectio --dir $BOINC_DIR $BOINC_OPTS"

now I see:

pkeser@pdkwj3:~$ ps aux | grep boinc
boinc     8120  0.5  0.3   8224  3328 ?        S    10:28   0:00 /usr/bin/boinc_client --redirectio --dir /var/lib/boinc-client
boinc     8131  1.0  7.0  74972 72424 ?        SN   10:28   0:00 setiathome-5.27.i686-pc-linux-gnu
boinc     8132  0.5  7.1  76340 73796 ?        SN   10:28   0:00 setiathome-5.27.i686-pc-linux-gnu
boinc     8143  0.0  7.1  76340 73796 ?        SN   10:28   0:00 setiathome-5.27.i686-pc-linux-gnu
boinc     8144 93.0  7.1  76340 73796 ?        RN   10:28   0:03 setiathome-5.27.i686-pc-linux-gnu
boinc     8145  0.0  7.1  76340 73796 ?        SN   10:28   0:00 setiathome-5.27.i686-pc-linux-gnu
boinc     8146  0.0  7.0  74972 72424 ?        SN   10:28   0:00 setiathome-5.27.i686-pc-linux-gnu
boinc     8147 94.0  7.0  74972 72424 ?        RN   10:28   0:03 setiathome-5.27.i686-pc-linux-gnu
boinc     8148  0.0  7.0  74972 72424 ?        SN   10:28   0:00 setiathome-5.27.i686-pc-linux-gnu
pkeser    8150  0.0  0.0   3004   760 pts/1    R+   10:28   0:00 grep boinc

I still get:

pkeser@pdkwj3:~$ boinc_cmd --get_state
Authorization failure: -155

But I can connect with boinc manager and it is working.  There may be a syntax issue using boinc_cmd with a password.

I hope this helps...but you've probably already fixed or moved on :-)

-PaulK

---

### Post by moky on 2008-06-25
I just had the same problem.

typing
boinc_cmd --get_results
in any directory works, but *ONE* ... the one where I wrote a script using it !

(astonishing however : when the script is launched by crontab, it works).

Anyway, I just changed my script of repertory, and it works.

Did you tried to launch
boinc_cmd --get_results
in a shell open in different directories ?

---

### Post by Hiperi0n on 2008-06-27
I have been having the same problem. boinc_cmd --get_state gives authorization failure -155 EXCEPT when typed in the boinc work directory. Could this be a bug? It is strange indeed

---

