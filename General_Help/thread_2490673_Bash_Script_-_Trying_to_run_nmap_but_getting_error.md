---
title: "Bash Script - Trying to run nmap but getting errors"
date: 2023-09-12
forum: General Help
---

### Post by Alan5127 on 2023-09-12
Hi All,

I am trying to create a bash script (partly for my own learning to be fair), that runs nmap against a remote machine, but I am getting an error I can't understand.

This is my nascent bash script:

```
#!/usr/bin/bash


CheckIfResponding() {

    echo $2
    echo $3

    bRunningHTTPS1=$(`/usr/bin/nmap $2 -PN -p $3`)

    echo $bRunningHTTPS1

    }



CheckIfResponding TestMachine 10.2.1.5 443



```

It errors with the following:

ZZ_Test.sh: line 9: Starting: command not found

Line 9 being:

```
bRunningHTTPS1=$(`/usr/bin/nmap $2 -PN -p $3`)
``` 

The echos are me trying to debug so I know I am passing the correct parameters.  They correctly return:

10.2.1.5
80

If I try running this on the command line it works fine:

```
$ /usr/bin/nmap 10.2.1.5 -PN -p 443

Starting Nmap 7.80 ( https://nmap.org ) at 2023-09-12 21:30 NZST
Nmap scan report for 10.2.1.5
Host is up

PORT      STATE SERVICE
443/tcp filtered  https

Nmap done: 1 IP address (1 host up) scanned in 0.07 seconds


```


I am thrown by the result 'Command not found' which appears to be saying that 'nmap' is not found, but clearly it is 'found' and installed, else the interactive command would fail?


Thanks in advance for any pointers you can provide.

Alan.

---

### Post by Holger_Gehrke on 2023-09-12
```
bRunningHTTPS1=$(_`_/usr/bin/nmap $2 -PN -p $3_`_)
```

Are those backticks ? Are they intentional ? Backticks and $(...) are two separate ways of doing command line substitution.. You are telling the shell to execute nmap and then to execute the output of nmap and put the standard output of that into the variable bRunningHTTPS1. Whatever output nmap produces is probably not a valid command, so that's where the 'command not found' comes from. Remove the backticks or the '$( ... )' so you only have one level of command substitution.

Holger

---

### Post by Alan5127 on 2023-09-13
Hi Holger,

> **Holger_Gehrke said:**
> ```
bRunningHTTPS1=$(_`_/usr/bin/nmap $2 -PN -p $3_`_)
```

Are those backticks ? Are they intentional ? Backticks and $(...) are two separate ways of doing command line substitution.. You are telling the shell to execute nmap and then to execute the output of nmap and put the standard output of that into the variable bRunningHTTPS1. Whatever output nmap produces is probably not a valid command, so that's where the 'command not found' comes from. Remove the backticks or the '$( ... )' so you only have one level of command substitution.

Holger

Yes - they are back-ticks, and I guess they were intentional in that I filched a reply to another piece of script on the net that seemed to be doing something similar to what I wanted, but did not understand it enough to realise what I was actually doing :-(

Removing them makes it work as intended - thank you for that, and also for furthering my understanding of bash scripting!


Alan.

---

