---
title: "Help me fix my wife's ubuntu from remote"
date: 2007-04-02
forum: General Help
---

### Post by kpkeerthi on 2007-04-02
OK... long story short. I installed edgy in my wife's PC and it's been working fine until last upgrade. The X is now broken (i think she did a kernel upgrade) and she only has the terminal now. I'm remote and I tried to walk her through the steps over phone and it did not help. She has no clue what I'm talking about. How do I take control of her PC and repair it from remote?

---

### Post by stylishpants on 2007-04-02
FIrst you need her to install the package openssh-server.

    sudo  apt-get install openssh-server


Then you need to know the machine's IP address, and  username and password of a user with "sudo" privileges on the machine.

The "ifconfig" command will tell her the IP address.  You should try it yourself first so you can tell her which part of the command's output you need.


Once you have all that information, you can try logging in to her computer with ssh like this:

   ssh user@192.168.0.1

Of course you must replace "user" with the username she provides, and "192.168.0.1" with the IP address of her machine.


Then you can start trying to figure out what's wrong with X.  

X usually leaves behind a file that contains error output when it fails to start.  Looking at that might be a good starting point.  Sorry but I don't remember the filename, I think that it is printed on the screen when X fails.

Good luck!

---

### Post by Sencer on 2007-04-02
Have her install ssh and log in remotely via shell. Once you get X running, you can use x11vnc to connect to that locally running X-Server with a vnc-client of your choice (via ssh and portforwarding). x11vnc has plenty of variables and parameters, and is very verbose - but the documentation is plenty as well.

---

### Post by kpkeerthi on 2007-04-02
Thanks. We managed to fix this.

---

