---
title: "sh process wont die"
date: 2008-05-14
forum: General Help
---

### Post by Silpheed2K on 2008-05-14
I tried installing some compilers and I had to use a install.sh file... I tried logging out and logging back in... I dont know much about the terminal since I'm new [if you all could recommend me some basic commands i'll need that'll be fine]

But my real question is.. how do i kill this install.sh process so I can run it again and insert the correct serial number for my install.
I really need to know.

---

### Post by pedro_orange on 2008-05-14
```
pedro@pedro-laptop:~$ ps -A
```

Will give you all the processes listed.

Example output:

```

 PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0

```

Find the process you want. Write down it's PID (Process ID)

Then go:

```
kill -9 PID
```

With PID being the Process Id. Eg. init would be 1. 
(Don't kill init! :))

---

### Post by Silpheed2K on 2008-05-14
okay that's not working for me it seems... i need to kill a .sh file so i can run it again
```
rex@rex-desktop:~$ kill -8596 PID
bash: kill: 8596: invalid signal specification
rex@rex-desktop:~$ kill -9047 PID
bash: kill: 9047: invalid signal specification

```
have any better alternatives?

edit: I got it I killed the sh instances and i think the  commands might have been mixed a little it was telling me to put PID before the number... thanks for the help

---

### Post by pedro_orange on 2008-05-14
```
kill -9 8595
```

To kill process ID 8595

---

### Post by Silpheed2K on 2008-05-14
oh okay thanks.. i got it.. it killed it somehow but i didnt enter that... strange... I really appreciate the help and thanks that advice help solve my problem

---

