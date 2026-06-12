---
title: "Combining 2 commands in shell scripting"
date: 2008-06-18
forum: General Help
---

### Post by ravi.786 on 2008-06-18
Hi All,
I am a bit confused here, what i am planning to do here is
to trying to combine 2 commands in shell scripting.
here is what i need ...
i want to cd to a directory for ex cd /usr/local/ and then run a command from there for example tar -cvf /var/tmp/*.tar * in one single command.

so it should be like cd /usr/local then tar -cvf /var/tmp/*.tar * from directory cd /usr/local..

help is appreciated

---

### Post by bapoumba on 2008-06-18
Moved to General Help.

In bash, ";" will go from one command to the other, ignoring errors. && will go to the next command if the previous one has been executed without error.

---

### Post by ravi.786 on 2008-06-18
Thanks a lot...But is there any way if i can do the same thing without shell script like in shell :
[root@myunix2 scripts]# grep cd /usr/local/appstage && ls -ltr

I did not got any output. but i should get the timestamp for files under /usr/local/appstage ..

i dont know what to try..

---

### Post by bapoumba on 2008-06-18
> **ravi.786 said:**
> Thanks a lot...But is there any way if i can do the same thing without shell script like in shell :
[root@myunix2 scripts]# grep cd /usr/local/appstage && ls -ltr

I did not got any output. but i should get the timestamp for files under /usr/local/appstage ..

i dont know what to try..
I'm not quite sure what the "grep" is here for.. No output means there was nothing to grep.
```
 bapoumba@scorpio:~$ cd /tmp && ls -a
.                keyring-fE8uOd   ssh-cWmqq10006          .X11-unix
..               keyring-ocqsaw   tmp.RtBJUp6761          .xfsm-ICE-LTA4CU
gconfd-bapoumba  orbit-bapoumba   Tracker-bapoumba.11270
.ICE-unix        seahorse-iOWol0  .X0-lock
bapoumba@scorpio:/tmp$ 
```

---

### Post by MacAnthony on 2008-06-18
Why not just do:

ls -ltr /usr/local/appstage

---

### Post by ravi.786 on 2008-06-18
Let me be little more specific in what i am doing here...
I was trying to create a script which will take the backup fro remote machines for that i have enabled the ssh between the box where i am running my script to the box where the files are..


ssh -l root my server cd /usr/local/appstage && tar -cvf /usr/local/BUILD_RELEASE/BUILD_BACKUP/CA/DEV/$Build_Number.tar *

when i run the command without ssh( locally) it is working fine..but with ssh -l then it does not give me the expected output

---

### Post by MacAnthony on 2008-06-18
Enclose the command you want to run in quotes.


ssh -l root my server 'cd /usr/local/appstage && tar -cvf /usr/local/BUILD_RELEASE/BUILD_BACKUP/CA/DEV/$Build_Number.tar *'

---

### Post by ravi.786 on 2008-06-19
Thanks, when i tried the command in the given pattern 

ssh $USR@$URL 'cd /usr/local/appstage && tar -cvf /usr/local/BUILD_RELEASE/BUILD_BACKUP/CA/DEV/$Build_Number.tar *'

i saw the backup was taken like /usr/local/appstage/$Build_Number.tar......

Instead of just $Build_Number.tar as i am already into the directory appstage. then it should just take the backup from here, but script is taking backup from some where else ?

---

### Post by MacAnthony on 2008-06-19
Is this part of another script? Where are the $USR, $URL and $Build_Number variables coming form?

---

### Post by MacAnthony on 2008-06-19
Either way, I think it should work if you use double quotes instead.

ssh $USR@$URL "cd /usr/local/appstage && tar -cvf /usr/local/BUILD_RELEASE/BUILD_BACKUP/CA/DEV/$Build_Number.tar *"

Then the variable should be replaced with the value instead of the literal sting.

---

