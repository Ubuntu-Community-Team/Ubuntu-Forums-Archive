---
title: "boot log messages"
date: 2008-04-27
forum: General Help
---

### Post by KhaosMind on 2008-04-27
is there anyway to see boot log?

dont tell me to enable bootlog like this thread [http://ubuntuforums.org/showthread.php?t=49925]("http://ubuntuforums.org/showthread.php?t=49925")

because it does not work 

see bugs
[https://bugs.launchpad.net/upstart/+bug/98955]("https://bugs.launchpad.net/upstart/+bug/98955")
[https://bugs.edge.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/137254]("https://bugs.edge.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/137254")
is any workaround to be able to see the boot log?

thanks

---

### Post by ghost_ryder35 on 2008-04-27
/var/log/boot.log doesnt work?
I must have been on another planet, didnt know it didnt work.  SH

---

### Post by ryanhaigh on 2008-04-27
The output of dmesg should show you pretty verbose logs of the boot process as well as what happens after. You could redirect the output to a file in your home directory.

```

dmesg > ~/dmesg.log

```

---

### Post by sefs on 2008-04-29
The only file I see in /var/log is a file called boot. and its empty.  How do we enable it to see all the lines that are printed on the black screen during boot up?

thanks.

---

### Post by ryanhaigh on 2008-04-29
> **sefs said:**
> The only file I see in /var/log is a file called boot. and its empty.  How do we enable it to see all the lines that are printed on the black screen during boot up?

thanks.

Perhaps try this, from the post above?

> 
The output of dmesg should show you pretty verbose logs of the boot process as well as what happens after. You could redirect the output to a file in your home directory.
```

dmesg > ~/dmesg.log

```


---

### Post by sefs on 2008-04-30
That prints out something other than what I see scrolling past at boot up.


> **ryanhaigh said:**
> Perhaps try this, from the post above?

---

### Post by Virtual_Ron on 2008-04-30
/var/log/syslog usually has all boot messages as well.

---

### Post by ryanhaigh on 2008-04-30
> **sefs said:**
> That prints out something other than what I see scrolling past at boot up.

Perhaps if you used verbose instead of silent/quiet as the kernel option it is what you would see.

From dmesg man page:
> 
       dmesg is used to examine or control the kernel ring buffer.

       The  program  helps  users  to print out their bootup messages.  Instead of copying the messages by hand, the
       user need only:
              dmesg > boot.messages
       and mail the boot.messages file to whoever can debug their problem.


---

### Post by sefs on 2008-04-30
I can tell then that dmesg does not operate as dmesg man indicates.  Maybe they have changed the behaviour of it to print out something else other that the boot messages at start up.

---

### Post by King Louie on 2008-04-30
I also simply want to see a log of the exact messages that scroll by at startup (in verbose/non-quiet mode). I have looked at all the files in /var/log/. There is a file named 'boot' but it is empty- nothing logged there. None of the other files contain the boot messages. I'm specifically concerned about the "Fail" messages that come up, but they scroll by so fast that I can't see what they are. dmesg also does not print out the info i need. 

If there is no log of those boot messages, is there a way to slow down or pause the boot process so that i can read the messages before they scroll past?

thanks!

---

### Post by King Louie on 2008-05-06
There must be a way to do this. Anybody? 

bump

---

### Post by Cannaregio on 2008-05-07
What about 
```
sudo cat /var/log/messages
```
and eventually
```
sudo cat /var/log/messages | grep cannot 
```

---

### Post by King Louie on 2008-05-23
bump

---

