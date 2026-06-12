---
title: "ddrescue finishes straight away..?"
date: 2014-05-21
forum: General Help
---

### Post by hopelessone on 2014-05-21
Hi,

From the log:

# Rescue Logfile. Created by GNU ddrescue version 1.16
# Command line: ddrescue -v -r3 /dev/sdg1 /dev/sdh1 logfile --force
# current_pos  current_status
0x22010E7000     +
#      pos        size  status
0x00000000  0x1D1C1000000  +

both HDD's are unmounted, trying to move all contents on /mnt/sdg1 to blank larger drive on /mnt/sdh1, what do I seem to be doing wrong here?

Thanks,

---

### Post by coldcritter64 on 2014-05-21
Are you using that as root ? You need to be, if you aren't. It doesn't look as though you are going by the Command line given in your post. 

Try it with,
```
sudo ddrescue -v -r3 /dev/sdg1 /dev/sdh1 logfile --force
```
Edit: I am also assuming the command is correct, I have no idea if the options etc are right. I use plain old "dd" regularly and need to use as root to access or write to any /dev/ addresses as they are owned by root.

---

### Post by hopelessone on 2014-06-02
Yes, I'm using sudo

blade@pangolin:~$ sudo ddrescue -v -r3 /dev/sdg1 /dev/sdh1 logfile --force
[sudo] password for blade: 


GNU ddrescue 1.16
About to copy 2000 GBytes from /dev/sdg1 to /dev/sdh1
    Starting positions: infile = 0 B,  outfile = 0 B
    Copy block size: 128 sectors       Initial skip size: 128 sectors
Sector size: 512 Bytes

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:     2000 GB,  errsize:       0 B,  errors:       0
Current status
rescued:     2000 GB,  errsize:       0 B,  current rate:        0 B/s
   ipos:         0 B,   errors:       0,    average rate:        0 B/s
   opos:         0 B,     time since last successful read:       0 s
Finished
blade@pangolin:~$

there are about 766 bad sectors...

---

