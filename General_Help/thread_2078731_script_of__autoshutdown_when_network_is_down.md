---
title: "script of  autoshutdown when network is down"
date: 2012-10-31
forum: General Help
---

### Post by rushikesh988 on 2012-10-31
I am using ubuntu 12.10  and I use my laptop for downloading some contents from internet . I keep my _laptop in on state for downloading at night_ .but sometimes it happens that my network gets disconnected and my laptop remains ON for a whole night . I am using DataCard for internet acess.

so  ** I want to create a command/script which will make my computer shutdown when network gets disconnected.**

---

### Post by rushikesh988 on 2012-10-31
anybody??

---

### Post by Lars Noodén on 2012-11-01
You could do it like this.  The pause gives you five minutes to cancel the shutdown if you happen to be logged in.  

```

#!/bin/sh

target=8.8.4.4

if ! ping -qnc 1 -w 1 $target > /dev/null ; then
  sleep 60;
  if ! ping -qnc 1 -w 1 $target > /dev/null ; then
    sleep 60;
    if ! ping -qnc 1 -w 1 $target > /dev/null ; then
      /sbin/shutdown +5 minutes "Lost network connection" &
    fi
  fi
fi

```

There might be smarter ways of detecting network outage.

---

### Post by rushikesh988 on 2012-11-01
I have saved it  as  shell script file  and tried to run(as a superuser) but Its not working ..  
I also kept that file in sbin and then tried to executed

---

### Post by Lars Noodén on 2012-11-01
Did you make the file you saved into an executable?

```

chmod +x autoshutdown
./autoshutdown

```

That has to be done before it will run as a program.

---

### Post by rushikesh988 on 2012-11-01
Yes I made that ...but its still not working ..
output is simply

> rushikesh988@rushikesh988-AOD257:~/Desktop$ sudo rushi
rushikesh988@rushikesh988-AOD257:~/Desktop$ 

---

### Post by Lars Noodén on 2012-11-02
The script will produce no output if the target host can be pinged.  If you want feedback that the net is up (or at least that host) then put in some "else" statements.

---

### Post by rushikesh988 on 2012-11-02
No I did't mean that .... about showing some output ... I tried disconnecting the network after running script but its not showing the message ... i.e 
> Broadcast message from rushikesh988@rushikesh988-AOD257
	(/dev/pts/1) at 19:36 ...

The system is going down for maintenance in 5 minutes!
minutes Lost network connection ..

I think it should show something like that .. ( Please Correct me if I am wrong)

---

### Post by Lars Noodén on 2012-11-02
The script only detects whether the target host is available at the time the script is run.  If you want to check a second time, you have to run the script a second time.  If you want to have the script monitor the connection continuously you have to put in a loop.

```

#!/bin/sh

target=8.8.4.4

echo "Polling $target";

while true; do
  if ! ping -qnc 1 -w 1 $target > /dev/null ; then
    sleep 60;
    if ! ping -qnc 1 -w 1 $target > /dev/null ; then
      sleep 60;
      if ! ping -qnc 1 -w 1 $target > /dev/null ; then
        /sbin/shutdown +5 "Lost network connection" &
        exit;
      fi
    fi
  fi
  sleep 60;
done

```

That or a variation of it should do the job.

---

### Post by rushikesh988 on 2012-11-02
thanks... its working now but still there is a little problem (I think its because of it)
the computer start shutting down but at last it just hangs on ubuntu boot screen (on last dot) .

---

### Post by Lars Noodén on 2012-11-02
Try this instead:

```

/sbin/shutdown -h +5 "Lost network connection" &

```

It tells shutdown to halt or power off after shutdown

---

### Post by rushikesh988 on 2012-11-02
thanks :)  You Rock !!

---

