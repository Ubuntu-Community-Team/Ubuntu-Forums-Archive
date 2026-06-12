---
title: "Problems Getting Qpopper Running!"
date: 2008-05-06
forum: General Help
---

### Post by kj6eo on 2008-05-06
Hello and thanks for reading my post!  I'm having problems getting qpopper running on Gusty.  I installed it through the package manager (says it's installed correctly > no errors).  I wrote a little script so that I could start it with xinetd:

> service pop3
{
     port          = 110
     socket_type   = stream
     protocol      = tcp
     wait          = no
     user          = root
     server        = /usr/sbin/in.qpopper
}

However if I try to start it i.e:

service pop3 start

I get the following back:

> /etc/init.d/pop3: 9: port: not found
/etc/init.d/pop3: 9: socket_type: not found
/etc/init.d/pop3: 9: protocol: not found
/etc/init.d/pop3: 9: user: not found
/etc/init.d/pop3: 9: server: not found
wait: 9: Illegal number: =

This just keeps scrolling over and over in the terminal window until I do a CTRL C.  If I just let it go it will lock up the machine and I have to hit the "reset button".

I'm obviously missing something here :confused:  Would someone help me out please?

Your expert advice and guidance are always appreciated!

Regards,

Bill KJ6EO

---

### Post by kj6eo on 2008-05-06
Hello All -

I'd like to add something to my first post.  The errors that I listed on my first post were caused by not doing "sudo" in front of the command of course.  Most of the time I log on as "root" so I don't have to type "sudo" all of the time.  Anyway when I execute "service pop3 start" as root the machine just hangs up (complete lock up).  The only way out is to hit the RESET button.

Is there some configuation step that I'm missing?  Or maybe qpopper will only start by stopping and restarting all the xinetd services.

Any suggesions would be appreciated!

Regards,

KJ6EO

---

### Post by iclebyte on 2008-11-27
You are correct, it would be xinetd which actually starts the /usr/sbin/in.popper program.

That script you wrote should go in /etc/xinet.d/pop3 - however you need to put the 'disable' line on it (I think). The contents of my /etc/xinet.d/pop3 file is as follows

```

# Begin /etc/xinetd.d/pop3
# This is for the qpopper application

service pop3
{
    disable         = no
    port            = 110
    socket_type     = stream
    protocol        = tcp
    wait            = no
    user            = root
    server          = /usr/sbin/in.popper -f /etc/qpopper.conf
}

# End /etc/xinetd.d/pop3

```

You then start xinet.d i.e. ```
/etc/init.d/xinetd start
```
If its already running you might need to run: ```
/etc/init.d/xinetd reload
```

You can then check that the pop3 service is listening by using ```
nmap localhost
``` You should see port 110 listening.

Good luck.

---

