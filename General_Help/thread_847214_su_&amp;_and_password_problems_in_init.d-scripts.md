---
title: "su &amp; and password problems in init.d-scripts"
date: 2008-07-02
forum: General Help
---

### Post by Ballena on 2008-07-02
Hi.

I have written (or at least I'm trying) a script that will close a session of screen when the system is going down (rc0) or rebooting (rc6).

I have placed this script in /etc/init.d/ and chmoded it u+x.
```

#!/bin/bash
# Script name = irctor

case $1 in
start)
  /home/xxxxx/bin/screen/start.sh
  ;;
stop)
  su --login -c 'screen -S irctor -X quit' xxxxx
   ;;
esac

# test if the scripts runs
echo 'It do works' > /home/xxxxx/works.txt

```

I have also made symbolic links to rc0 and rc06 which I added with the tool *sysv-rc-conf*

```

xxxxx@compton:~$ cd /etc/rc0.d/
xxxxx@compton:/etc/**rc0**.d$ ls -l *irctor*
lrwxrwxrwx 1 root root 16 2008-07-02 14:26 S74**irctor -> ../init.d/irctor**
xxxxx@compton:/etc/rc0.d$ cd /etc/rc6.d/
xxxxx@compton:/etc/**rc6**.d$ ls -l *irctor*
lrwxrwxrwx 1 root root 16 2008-07-02 14:35 S74**irctor -> ../init.d/irctor**

```

It looks OK I think. If I have understood everything right links in runlevel 0 or 6 will be called with the parameter 'stop' which will in this case stop the session of screen named *irctor*.

But the thing is that screen-sessions are user-bound so root can't (at least I think) access or stop screen sessions that I (erikw) have started. To solve this you should probably use the command *su* like I did in the */etc/init.d/irctor* script but the problem with that is that *su* seems to required a password input to continue executing to command.

My question is: how do i get around the enter-password-thing?

Any help is appreciated! ( I have red this [**manual**]("http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit") or what is it)

---

### Post by Gunman1982 on 2008-07-02
Root can stop them, root can stop every process running (apart from zombie processes).

for the stop I would either do
su - xxxxx -c 'screen -S irctor -X quit'
or to make it work for other user too:
killall irctor

---

### Post by Ballena on 2008-07-02
@Gunman1982: I don't think root can quit screen sessions. Look here:

```

xxxxx@compton:~$ screen -ls
There is a screen on:
	5270.irctor	(Detached)
1 Socket in /var/run/screen/S-erikw.

xxxxx@compton:~$ sudo su
root@compton:/home/erikw# screen -ls
No Sockets found in /var/run/screen/S-root.

```

and the "su - xxxxx -c 'screen -S irctor -X quit'" seems to required a password so how can I automate that?

---

### Post by Frozsyn on 2008-07-03
> **Ballena said:**
> My question is: how do i get around the enter-password-thing?

I heard about a language called Expect that allow to interact with a program directly instead of using the stdin/stdout pipeline stuff. You can install it from the repository. I have tried this litle program:

```
#!/usr/bin/expect -f 
spawn su username
expect "Password" 
send "userpassword\n"
interact
```

And it works fine. Maybe that can help you.

Homepage: [http://expect.nist.gov/](http://expect.nist.gov/)
Tutorial: [http://dslab.lzu.edu.cn/docs/summer_school_2005/kernel_debuging/doc/timelog/tutorial.html](http://dslab.lzu.edu.cn/docs/summer_school_2005/kernel_debuging/doc/timelog/tutorial.html)

By the way, get around the password that way should work, but I don't think it's the better solution. Anyway, I'm not a "screen" user so I have nothing else to propose.

I hope this helps

---

### Post by Ballena on 2008-07-03
@Frozsyn: That sure sounds interesting! But you are probably right that it's maybe not the best solution. Are there no other ways of closing screen sessions the belongs to another user than actually  *su* that user?

---

### Post by justleen on 2008-07-03
"su - xxxxx -c 'screen -S irctor -X quit'"

that should not require a passwd, if you do that as root..

Root may su to anyuser w/o passwd prompt

---

### Post by Ballena on 2008-07-03
@justleen: You seems to be right because I could execute that command as root whitouy a prompt for password. But the script is still not run (which I know since no *works.txt* file can be found in my home directory) when changing run level to poweroff or reboot.

What more is required for a script to run in a run level then what I already have done? The script takes the argument *start* and *stop* and symbolic links to the script in /etc/init.d/ exists n both /etc/rc0.d/ and /etc/rc6.d/.

---

### Post by Frozsyn on 2008-07-03
@Ballena: I have try to simply terminate the SCREEN processes by using the kill commance, and it works pretty good, and screen terminate correctly. Is there any reason why you do not want to use the kill command (or killall proposed by Gunman1982) ? A more screen way to do is maybe to use the multiuser mode. Have you try to use the multiuser mode and add the user root to the acl ?

---

### Post by Frozsyn on 2008-07-03
Have you try to put your "echo 'It do works' > /home/xxxxx/works.txt" at the beginning of your init script file too? Maybe the script is called and never finish for some reason...

---

### Post by Gunman1982 on 2008-07-03
I assume your script will be executed but you can't see it using such a file becaus of the /etc/rc0.d/S60umountroot after that script you can't access your home anymore, therefor not write in it. make a different link K10irctor.

And what I meant with using killall is that you actually shut down the process (irctor?) you run in the screen instead of shutting down the screens. You can shutdown the screens with as root too. Do a 'killall screen' as root or rather if you want to test it with sudo and see what happens to your started screen sessions.

---

### Post by unutbu on 2008-07-03
Rename your symlinks  as K74irctor instead of S74irctor.
Scripts that start with 'K' are sent the stop command,
Scripts that start with 'S' are sent the start command.

---

### Post by Gunman1982 on 2008-07-03
> **unutbu said:**
> Rename your symlinks  as K74irctor instead of S74irctor.
Scritps that start with 'K' are sent the stop command,
Scripts that start with 'S' are sent the start command.

Thought so at frst too but I doubt it, it would make the commands like /etc/rc0.d/S60umountroot useless because they do nothing in their (start) branch of the switch/case tree.

---

### Post by unutbu on 2008-07-03
[http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit](http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit)

> When init changes runlevel first the targets of the links whose names start with a K are executed, each with the single argument stop, followed by the scripts prefixed with an S, each with the single argument start. (The links are those in the /etc/rcn.d directory corresponding to the new runlevel.) The K links are responsible for killing services and the S link for starting services upon entering the runlevel.

For example, if we are changing from runlevel 2 to runlevel 3, init will first execute all of the K prefixed scripts it finds in /etc/rc3.d, and then all of the S prefixed scripts in that directory. **The links starting with K will cause the referred-to file to be executed with an argument of stop, and the S links with an argument of start. **

---

### Post by Ballena on 2008-07-03
Ahhh that was the problem. Of course the soft links should begin with a **k** (kill) and not a **s**. I just tested it and it works!

As some mentioned another variant is ti kill the whole screen process and maybe that is also OK. I imagined that sending a quit-message to the screen session, called irctor, would not be so  harmful compared to just killing the whole screen process. I'm a right or wrong?

Anyway thanks for all the help!

---

### Post by Ballena on 2008-07-03
One last question tho: Am I free to use what ever unused number for my softlink that I want? Maybe some numbers are not allowed to use or such.

---

### Post by The Cog on 2008-07-03
I believe the numbers are executed in order. K00...K99. I guess they are just sorted alphabetically to be honest. There may be dependencies which influence your choice of which order things are started and stopped in.

---

### Post by unutbu on 2008-07-03
Ballena and Gunman1982, what I said in post #11 is wrong (and Gunman1982 is correct in post #12), and it was only by dumb luck that my suggestion worked. According to
[http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit:](http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit:) 

> The two runlevels 0 (halt) and 6 (reboot) are slightly different. In these runlevels, the links with an S prefix are still called after those with a K prefix, but they too are called with the single argument stop.

So Ballena, if your script works with K74, but does not work with S74, it must mean that S74 comes too late in the sequence. Something important (like S40umountfs) would prevent S74 from running because you can't run /bin/su if you there is no /bin. 

So moving the script to K74 did not succeed because of the K, it worked because it was simply earlier in the shutdown sequence. Perhaps S19irctor would have worked too, for example.

This sheds some light on your last question, Ballena.

> 
Am I free to use what ever unused number for my softlink that I want?

I am not sure for what the range of numbers your script will work. Perhaps experimentation is the easiest way to tell. 

I don't think you have to worry about numbers being "unused" however. If two scripts have the same number, I believe they are simply executed in alphabetical order.

---

### Post by Ballena on 2008-07-03
@unutbu: :D OK so I just had no luck at first. I will try to pick some lower numbers for my own /etc/init.d/ scripts. Thanks for the answer!

---

