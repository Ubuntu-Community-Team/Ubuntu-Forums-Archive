---
title: "xterm: can't connect to /tmp/.X11-unix/X0"
date: 2007-03-29
forum: General Help
---

### Post by gradstudent on 2007-03-29
Hello,

I was previsouly working with Fedora Core and I just installed Ubuntu Dapper a few days ago to further test a program I have written as a grad student and I'm having some problems. I have not been able to track the problem to my program (which was working with FC) and was hoping that if it was an Ubuntu problem someone here could help me.
Sometimes I get the following error when I try to run xterm from my program:
/usr/bin/xterm Xt error: Can't open display: :0.0

Note that I can run xterm from bash, but when my program does an execve of /usr/bin/xterm it doesn't work.

I searched a lot about this error and found things on the DISPLAY variable not being set properly (but mine is set to :0.0), allowing other hosts to connect using xhost + (I tried that but it instead made things worse)

So, I ran strace and found that my problem was because of the following:
connect(3, {sa_family=AF_FILE, path="/tmp/.X11-unix/X0"}, 19) = -1 ECONNREFUSED (Connection refused)

What are the reasons that this connection will be refused?:confused: 
I have not been able to find anything about this. 
Please any help would be appreciated as I am new to Ubuntu

Thanks.

---

### Post by gradstudent on 2007-03-29
Can anyone please give me any hints as to why the connection fails?
What are various reasons for this connection to be refused?

---

### Post by schilcha on 2007-03-29
One way I can reproduce this error message is when I try to start an X-application (e.g. xterm) from a login-shell that opened a different session than the session owning the screen. 
I know, that noone could ever understand that sentence, so I'll try to make that clear with an example:
```

su - schilcha -c 'export DISPLAY=:0.0; xterm'

```
So, "su -" will open a login-shell for user "schilcha" and then executes the commands following the -c switch (don't forget the single quotes to trap the semicolon.

That'll give the error you described.

xhost can't solve this problem. 

If your situation is comparable, then you need to tell your X-server to accept tcp-connection (which is disallowed by default). I've never done that (I use ssh in such situations). I think it has to be configured within gdm's config-files (or kdm's or xdm's, whatever login-manager you use.

Hope that helped.

---

### Post by gradstudent on 2007-03-30
Thanks for your help.
Actually in my situation I was trying xterm inside a chroot. 
I then tried a simple echo ```
"hello">/dev/stdout
``` and found that nothing was echoed back even though no error was displayed. 

I found that in order for these to work I have to mount (with bind option) /tmp, /proc, and /dev. Unfortunately I haven't found an explanation for this. Is it true this has something to do with the fact that communication inside the chroot was only happening one way? For example, although the connect done by xterm could find the socket it failed with the error that no one was listening on the socket because it could not get a reply. Similary, echo to stdout could send the text but it wasn't coming back to the chroot and being displayed.

I don't know if what I said makes any sense, but its the only reason I can think of so far.

---

