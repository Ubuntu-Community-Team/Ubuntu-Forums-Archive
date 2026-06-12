---
title: "Resuming a backgrounded process..."
date: 2013-01-07
forum: General Help
---

### Post by Tralce on 2013-01-07
I frequently open a terminal, and start a process. I then realize I'd meant to start it in screen. 

What I'm asking is this: Can you background, stop, or otherwise suspend a process outside of screen, then pick it back up from within screen?

---

### Post by Impavidus on 2013-01-08
Do you mean this:```

egroot@Iphigeneia:~$ kill -l
 1) SIGHUP     2) SIGINT     3) SIGQUIT     4) SIGILL     5) SIGTRAP
 6) SIGABRT     7) SIGBUS     8) SIGFPE     9) SIGKILL    10) SIGUSR1
11) SIGSEGV    12) SIGUSR2    13) SIGPIPE    14) SIGALRM    15) SIGTERM
16) SIGSTKFLT    17) SIGCHLD    18) SIGCONT    19) SIGSTOP    20) SIGTSTP
21) SIGTTIN    22) SIGTTOU    23) SIGURG    24) SIGXCPU    25) SIGXFSZ
26) SIGVTALRM    27) SIGPROF    28) SIGWINCH    29) SIGIO    30) SIGPWR
31) SIGSYS    34) SIGRTMIN    35) SIGRTMIN+1    36) SIGRTMIN+2    37) SIGRTMIN+3
38) SIGRTMIN+4    39) SIGRTMIN+5    40) SIGRTMIN+6    41) SIGRTMIN+7    42) SIGRTMIN+8
43) SIGRTMIN+9    44) SIGRTMIN+10    45) SIGRTMIN+11    46) SIGRTMIN+12    47) SIGRTMIN+13
48) SIGRTMIN+14    49) SIGRTMIN+15    50) SIGRTMAX-14    51) SIGRTMAX-13    52) SIGRTMAX-12
53) SIGRTMAX-11    54) SIGRTMAX-10    55) SIGRTMAX-9    56) SIGRTMAX-8    57) SIGRTMAX-7
58) SIGRTMAX-6    59) SIGRTMAX-5    60) SIGRTMAX-4    61) SIGRTMAX-3    62) SIGRTMAX-2
63) SIGRTMAX-1    64) SIGRTMAX    
#SIGSTOP is signal #19
egroot@Iphigeneia:~$ gedit &
[1] 5155
#gedit is process 5155
#Oops, I wanted this process to start in the foreground!
egroot@Iphigeneia:~$ kill -19 5155

[1]+  Gepauzeerd              gedit
#Program stopped
egroot@Iphigeneia:~$ fg
gedit
#Now it runs in the foreground
```The reverse works too:```

egroot@Iphigeneia:~$ gedit
#Oops, I wanted to start this program in the background
#Press cntr+z in the terminal
^Z
[1]+  Gepauzeerd              gedit
#Program has stopped, you get a new prompt
egroot@Iphigeneia:~$ bg
[1]+ gedit &
#Now the program runs in the background
```

---

### Post by Tralce on 2013-01-13
Almost, but I need it to go a little more like this:

tralce@tralce:~$ dd if=/dev/zero of=/dev/sdb1 #or some other time consuming process
#whoops, meant to run that in screen, don't want to start it over
^Z
tralce@tralce:~$ bg
tralce@tralce:~$ screen
tralce@tralce:~$ fg
#wohoo now it's running in a screen session that I can access over ssh from another host by screen -X

---

### Post by Tralce on 2013-04-24
Still no ideas?

---

