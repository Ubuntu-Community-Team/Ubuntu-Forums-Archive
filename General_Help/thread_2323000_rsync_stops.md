---
title: "rsync stops"
date: 2016-05-02
forum: General Help
---

### Post by pdcooper on 2016-05-02
im backing up a windows(10) share 
im mounting it 

 ```
mount -t cifs //192.168.1.106/Users/PC/Documents  /mnt/Jane-PC  -o username=xxxx,password=xxxx,ro,uid=mars,gid=mars
```

 and then using rsync 

```
rsync -avvvz  /mnt/Jane-PC /mnt/098fede1-b2f2-4db7-b142-1ccc1c7fc4e5/ 
```

after a few minutes of copying stuff it stops  and waits ( for ever ) 
 running strace gives me this 

```
write(1, "send_files(579, /mnt/Jane-PC/fam"..., 94) = 94
open("Jane-PC/familystuff/Family Photos/2005/Bluebell Wood May05/123_2361.JPG", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0755, st_size=2871820, ...}) = 0
write(1, "send_files mapped /mnt/Jane-PC/f"..., 111) = 111
write(1, "calling match_sums /mnt/Jane-PC/"..., 96) = 96
write(1, "Jane-PC/familystuff/Family Photo"..., 72) = 72
read(3, "\377\330\377\341)\376Exif\0\0II*\0\10\0\0\0\t\0\17\1\2\0\6\0\0\0z\0"..., 262144) = 262144
select(6, [5], [4], [5], {60, 0})       = 2 (in [5], out [4], left {59, 999993})
read(5, "(Jane-PC/familystuf", 19)      = 19
write(4, "H\310\0\7\177\373\24\235\365[\223\337\37\306\367\21\25\221\6\351\230\n\322!-9\25i\1\25\351\230"..., 51276) = 51276
select(5, [], [4], [], {60, 0})         = 1 (out [4], left {59, 999996})
write(4, "\311\300\0\7\177\377\305\261\231\207C\371\375o|\212R\326\220}\231\312\236\220}\237\251|\262/\241\354"..., 49357) = 49357
select(5, [], [4], [], {60, 0})         = 1 (out [4], left {59, 999995})
write(4, "i\301\0\7\177\377\vX\4$\300W>\235\200\347,\2336\267t\242FA\366\233+\306\303^\305\261"..., 49517) = 49517
select(5, [], [4], [], {60, 0})         = 0 (Timeout)
select(5, [], [4], [], {60, 0})         = 0 (Timeout)
select(5, [], [4], [], {60, 0})         = 0 (Timeout)
select(5, [], [4], [], {60, 0})         = 0 (Timeout)
select(5, [], [4], [], {60, 0})         = 0 (Timeout)
select(5, [], [4], [], {60, 0})         = 0 (Timeout)
select(5, [], [4], [], {60, 0})         = 0 (Timeout)
select(5, [], [4], [], {60, 0})         = 0 (Timeout)
```


The same things happens if I omit the -z flag 
Anyone any idea how i sort it out further ?

---

### Post by ubu_dynamite on 2016-05-02
Most likely a cifs/network problem not rsync.
If this is going over wifi then you probably got a disconnect.

---

### Post by pdcooper on 2016-05-02
but i can browse the directory ( and view the images)  by going to /mnt/Jane-PC /.....

---

### Post by pdcooper on 2016-05-02
an if i wait long enough this happens 
> select(5, [], [4], [], {60, 0})         = 0 (Timeout)
select(5, [], [4], [], {60, 0})         = 0 (Timeout)
select(5, [], [4], [], {60, 0})         = 0 (Timeout)
select(5, [], [4], [], {60, 0})         = 0 (Timeout)
select(5, [], [4], [], {60, 0})         = 0 (Timeout)
select(5, [], [4], [], {60, 0})         = 0 (Timeout)
select(5, [], [4], [], {60, 0})         = 0 (Timeout)
select(5, [], [4], [], {60, 0})         = 0 (Timeout)
select(5, [], [4], [], {60, 0})         = 0 (Timeout)
select(5, [], [4], [], {60, 0})         = 0 (Timeout)
select(5, [], [4], [], {60, 0})         = 0 (Timeout)
select(5, [], [4], [], {60, 0})         = ? ERESTARTNOHAND (To be restarted if no handler)
--- SIGWINCH {si_signo=SIGWINCH, si_code=SI_KERNEL} ---
select(5, [], [4], [], {52, 250442})    = ? ERESTARTNOHAND (To be restarted if no handler)
--- SIGWINCH {si_signo=SIGWINCH, si_code=SI_KERNEL} ---
select(5, [], [4], [], {52, 225736})    = ? ERESTARTNOHAND (To be restarted if no handler)
--- SIGWINCH {si_signo=SIGWINCH, si_code=SI_KERNEL} ---
select(5, [], [4], [], {52, 213643})    = ? ERESTARTNOHAND (To be restarted if no handler)
--- SIGWINCH {si_signo=SIGWINCH, si_code=SI_KERNEL} ---
select(5, [], [4], [], {52, 198905})    = ? ERESTARTNOHAND (To be restarted if no handler)
--- SIGWINCH {si_signo=SIGWINCH, si_code=SI_KERNEL} ---
select(5, [], [4], [], {52, 184385})    = ? ERESTARTNOHAND (To be restarted if no handler)
--- SIGWINCH {si_signo=SIGWINCH, si_code=SI_KERNEL} ---
select(5, [], [4], [], {52, 172206})    = ? ERESTARTNOHAND (To be restarted if no handler)
--- SIGWINCH {si_signo=SIGWINCH, si_code=SI_KERNEL} ---
select(5, [], [4], [], {52, 148986})    = ? ERESTARTNOHAND (To be restarted if no handler)
--- SIGWINCH {si_signo=SIGWINCH, si_code=SI_KERNEL} ---
select(5, [], [4], [], {52, 136233})    = ? ERESTARTNOHAND (To be restarted if no handler)
--- SIGWINCH {si_signo=SIGWINCH, si_code=SI_KERNEL} ---
select(5, [], [4], [], {52, 71163})     = ? ERESTARTNOHAND (To be restarted if no handler)
--- SIGWINCH {si_signo=SIGWINCH, si_code=SI_KERNEL} ---
select(5, [], [4], [], {52, 61285})     = ? ERESTARTNOHAND (To be restarted if no handler)
--- SIGWINCH {si_signo=SIGWINCH, si_code=SI_KERNEL} ---
select(5, [], [4], [], {52, 40026})     = ? ERESTARTNOHAND (To be restarted if no handler)
--- SIGWINCH {si_signo=SIGWINCH, si_code=SI_KERNEL} ---
select(5, [], [4], [], {52, 22271})     = ? ERESTARTNOHAND (To be restarted if no handler)
--- SIGWINCH {si_signo=SIGWINCH, si_code=SI_KERNEL} ---
select(5, [], [4], [], {52, 4085})      = ? ERESTARTNOHAND (To be restarted if no handler)
--- SIGWINCH {si_signo=SIGWINCH, si_code=SI_KERNEL} ---
select(5, [], [4], [], {51, 984550})    = ? ERESTARTNOHAND (To be restarted if no handler)
--- SIGWINCH {si_signo=SIGWINCH, si_code=SI_KERNEL} ---
select(5, [], [4], [], {51, 964872}

---

### Post by ubu_dynamite on 2016-05-02
[cifs client timeouts and hard/soft mounts]("https://lists.samba.org/archive/samba-technical/2010-December/075029.html")

[CIFS and SMB Timeouts in Windows]("https://blogs.msdn.microsoft.com/openspecification/2013/03/19/cifs-and-smb-timeouts-in-windows/")

---

### Post by pdcooper on 2016-05-02
They are English ( i think ) but not as i know it !
I assume the fix may be  a windows registry  edit. 
is there a workaround , other than putting  the rsync in a batch file, setting the timeout and testing if its rsyns is running  and if not , restart it

---

