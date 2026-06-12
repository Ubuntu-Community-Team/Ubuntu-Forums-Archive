---
title: "run commands in delay or afther another command"
date: 2013-01-06
forum: General Help
---

### Post by then_dude on 2013-01-06
hello people,

 i got a problem for which i have a hard time finding a solution. 

situation:  i always open up a terminal and enter a command.
 for example: sudo badblocks -v /dev/sda1 > badblockssda1 

but then i want to start a second command,  for example: 
sudo badblocks -v /dev/sda2 > badblockssda2  
the  problem is that sda slows down when 2 processes like this are given.    

QUESTIONS;  

[LIST=1]
[*]can i command a process not to start before another is finished ? even if i'm not typing in the same terminal ? (something like halt)
[*]can i let the command wait like with the command 
sleep 1000 && sudo badblocks -v /dev/sda2 > badblockssda2 ; but then i have to type the password at the moment of runtime, hours later then the command, i might not even be around...
[*]the command at , same question as above.
[*]CRON command, it runs at a give minute, hours, day, month ...; when i run it, i run straight commands, is that possible ? i don't run a "batch file". i get an error log: the minutes are not recognised as command...
[/LIST]
what would be the best option ? 

i think waiting to finish another command and be able to type in the sudo password at once would be super


thanks guys

---

### Post by iponeverything on 2013-01-06
```
commmand1 && command2 

```
and do a man sudoers to see how to eliminate the need to type in the password when executing certain sudo commands (badblocks for exeample)

---

### Post by dcstar on 2013-01-06
```
man badblocks
```

       ```
Important  note:  If  the output of badblocks is going to be fed to the
       e2fsck or mke2fs programs, it is important that the block size is prop&#8208;
       erly  specified,  since  the block numbers which are generated are very
       dependent on the block size in use by the filesystem.  For this reason,
       **it  is  strongly recommended that users not run badblocks directly**, but
       rather use the -c option of the e2fsck and mke2fs programs.
```

---

