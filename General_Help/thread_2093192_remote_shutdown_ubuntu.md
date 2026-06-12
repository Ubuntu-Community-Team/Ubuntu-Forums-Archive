---
title: "remote shutdown ubuntu"
date: 2012-12-10
forum: General Help
---

### Post by mag87 on 2012-12-10
Hello, i have 12 pc with ubuntu os....
i want to remote shutdown it...
is there any software that can be used to remotely shutdown pc on ubuntu?????
:p

---

### Post by ernest1 on 2012-12-10
I think ssh can help u. ;-)
Look at [http://help.ubuntu.com/community/SSH/OpenSSH/ConnectingTo](http://help.ubuntu.com/community/SSH/OpenSSH/ConnectingTo) and [http://z-computer-z.blogspot.hk/2010/01/remote-shutdown-and-remote-reboot-on.html](http://z-computer-z.blogspot.hk/2010/01/remote-shutdown-and-remote-reboot-on.html).[]("http://help.ubuntu.com/community/SSH/OpenSSH/ConnectingTo")

---

### Post by slickymaster on 2012-12-10
On the computers you want to shut down, install openssh-server:
```
sudo apt-get install openssh-server
```

Type this command on a terminal window:
```
ssh user@remote_computer sudo poweroff
```
Replace _user_ and _remote_computer_ with the username and ip addresses of the computers you want to shut down.

You should notice that those two command will prompt you a password twice. To make it not ask you for a password you should copy you ssh key to your remote computers.

---

### Post by rnerwein on 2012-12-10
> **slickymaster said:**
> On the computers you want to shut down, install openssh-server:
```
sudo apt-get install openssh-server
```Type this command on a terminal window:
```
ssh user@remote_computer sudo poweroff
```Replace _user_ and _remote_computer_ with the username and ip addresses of the computers you want to shut down.

You should notice that those two command will prompt you a password twice. To make it not ask you for a password you should copy you ssh key to your remote computers.
hello
the harder they come.
12 pc's - are there anybody working on some of these boxes.
i prefer: shutdown with the option of time and a message (altough you can stop the shutdown in the amout of the given time if you want)
cheers

---

### Post by dstnvns on 2012-12-10
You could install Webmin on the systems and use the WebUI to shutdown systems. More system resources would be required on the systems most likely than with SSH, but if you perform other administrative tasks it could be worth it. Cluster administration would simplify tasks done to all 12 by eliminating the need to perform them more than once.

SSH would be my first choice, but it's always good to have options.

---

### Post by alfa16vjtd on 2012-12-10
You can also use a cronjob if you only use them during daytime.

---

### Post by newbie-user on 2012-12-10
ClusterSSH allows you to ssh into multiple computers and pass commands to all of them at once.

---

### Post by tgalati4 on 2012-12-10
man shutdown

sudo shutdown -h 30

The shutdown command will give notices to users of impending shutdown.  You can change the time to anything you want.

You can also add a script to user's .bash_logout to shut the machine down after 30 minutes after 9 pm for instance--if this is a computer lab.

You need to describe the use case more thoroughly before we can be more specific.  There are lots of ways to shut machines down remotely.  You can also add shutdown times with each computer's BIOS.  For instance if a computer lab shuts down at 9 pm, you can set the machines to shutdown automatically at 10 pm.

You might put less stress on the machines if you put them to sleep rather than shut them down completely.

---

### Post by Rebelli0us on 2012-12-11
Why not just set an auto-suspend interval in Power management? That way if somebody is working on one of the machines they won't be rudely interrupted.

---

