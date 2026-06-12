---
title: "SSHFS with expect script"
date: 2007-10-16
forum: General Help
---

### Post by Tobbera on 2007-10-16
I'm trying to mount a SSHFS throu a script with pre-defined username and passwd. I'm using the expect-function to have a dialog with the sshfs-program.

The problem is that it is never mounted. I have no problems mounting the verry same source and mountpoint manually with sshfs.

I think that is has something to do with how the expect-process ends the script. As shown in the script output, there is a dialog between expect and sshfs.

Here is my script (/etc/security/mount.global):
```
#!/usr/bin/expect -d
set timeout -1
set username [lindex $argv 0]
set password [lindex $argv 1]

spawn /usr/bin/sshfs -p 6922 -f $username@192.168.1.2:/home/teacherfiles /home/$username/Desktop/teacherfiles
expect "*assword*"
send "$password\r""
expect "\n"

```

Here is the output from the script:

```
tobias.radenholt@klient16:~$ /etc/security/mount.global tobias.radenholt mysecretpassword

expect version 5.43.0
argv[0] = /usr/bin/expect  argv[1] = -d  argv[2] = /etc/security/mount.global  argv[3] = tobias.radenholt  argv[4] = mysecretpassword
set argc 2
set argv0 "/etc/security/mount.global"
set argv "tobias.radenholt mysecretpassword"
executing commands from command file /etc/security/mount.global
spawn /usr/bin/sshfs -p 6922 -f tobias.radenholt@192.168.1.2:/home/teacherfiles /home/tobias.radenholt/Desktop/teacherfiles
parent: waiting for sync byte
parent: telling child to go ahead
parent: now unsynchronized from child
spawn: returns {12676}

expect: does "" (spawn_id exp6) match glob pattern "*assword*"? no
Password: 
expect: does "Password: " (spawn_id exp6) match glob pattern "*assword*"? yes
expect: set expect_out(0,string) "Password: "
expect: set expect_out(spawn_id) "exp6"
expect: set expect_out(buffer) "Password: "
send: sending "mysecretpassword\r" to { exp6 }

expect: does "" (spawn_id exp6) match glob pattern "\n"? no


expect: does "\r\n" (spawn_id exp6) match glob pattern "\n"? yes
expect: set expect_out(0,string) "\n"
expect: set expect_out(spawn_id) "exp6"
expect: set expect_out(buffer) "\r\n"
write() failed to write anything - will sleep(1) and retry...
```


Appreciate input.

---

### Post by catweazle1973 on 2007-11-12
Exchange your original spawn line with this one:

```
spawn -ignore HUP /usr/bin/sshfs -p 6922 -f $username@192.168.1.2:/home/teacherfiles /home/$username/Desktop/teacherfiles
```

This should prevent sshfs from terminating once the expect process ends.

It works for me at least.

---

