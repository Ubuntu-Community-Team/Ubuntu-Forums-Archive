---
title: "BASH  ssh problem -  changing SD card OS in Rpi causes this"
date: 2013-03-24
forum: General Help
---

### Post by Tim036 on 2013-03-24
Now i got to see the hidden files with ls -a

but I can't seem to get into root to find the files that need changing.

Feel very nervous about this, don't want to nuke the OS !

```
tim@tim-A880G:~$ ssh -l pi 192.168.1.105 
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@ 
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @ 
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@ 
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY! 
Someone could be eavesdropping on you right now (man-in-the-middle attack)! 
It is also possible that a host key has just been changed. 
The fingerprint for the ECDSA key sent by the remote host is 
b5:a2:ef:bf:83:61:ae:c0:b2:f4:59:0e:b3:12:8f:ff. 
Please contact your system administrator. 
Add correct host key in /home/tim/.ssh/known_hosts to get rid of this message. 
Offending ECDSA key in /home/tim/.ssh/known_hosts:6 
  remove with: ssh-keygen -f "/home/tim/.ssh/known_hosts" -R 192.168.1.105 
ECDSA host key for 192.168.1.105 has changed and you have requested strict checking. 
Host key verification failed. 
```

Any thoughts anyone ?

A puzzled,

Tim

---

### Post by efflandt on 2013-03-24
If by Rpi you mean a Raspberry Pi (or any computer with sshd) the files you want to replicate on your own computers are the "key" files is /etc/ssh.  Otherwise those files are uniquely generated the first time you run Raspbian.

You probably need to use **sudo** to **cp** those files into place, whether you do that directly to the SD card, or scp them over in your username and then use **sudo cp** to copy them into /etc/ssh.
```
efflandt@raspberrypi ~ $ ls /etc/ssh
moduli       ssh_host_dsa_key      ssh_host_ecdsa_key.pub
ssh_config   ssh_host_dsa_key.pub  ssh_host_rsa_key
sshd_config  ssh_host_ecdsa_key    ssh_host_rsa_key.pub
```On thing you may want to do is install avahi-browser on your Rpi's. Set a different hostname in /etc/hostname and /etc/hosts of each SD card and then you can access them from Ubunu (or Apple or Windows with Bonjour installed) with their hostname.local```
efflandt@XPS8100-1204:~$ tracepath -n raspberrypi.local
 1:  172.16.0.50                                           0.104ms pmtu 1500
 1:  172.16.0.102                                         46.849ms reached
 1:  172.16.0.102                                         23.246ms reached
     Resume: pmtu 1500 hops 1 back 64
```

---

### Post by Tim036 on 2013-03-24
I think I needed to explain the set up more...sorry I did not in the first post.

I use Ubuntu 12.04 as the sh to gain access to the RPi.

I don't think its the RPi's fault, just the way Ubuntu works.

I dont know how access the root directory of Ubuntu and then /etc etc

I'm stuck in the home directory.

Hope that makes sense.

Lack of Bash knowledge ins my proble. (one of them *LOL*)

Many thanks for responding


Tim

---

### Post by Lars Noodén on 2013-03-24
If you changed the OS on the SD card or the SD card itself,  the keys in /etc/ssh/ will have changed unless you copied the old ones over onto the new chip or system.  If you are confident that the key "b5:a2:ef:bf:83:61:ae:c0:b2:f4:59:0e:b3:12:8f:ff" is the right one, then you can follow the instructions given in the error message to remove the old fingerprint from your local file:

```

ssh-keygen -f "/home/tim/.ssh/known_hosts" -R 192.168.1.105 

```

Once you have logged into your server (Rpi) you can double check the key fingerprint with [ssh-keygen](http://manpages.ubuntu.com/manpages/precise/en/man1/ssh-keygen.1.html).

```

ssh-keygen -lf /etc/ssh/ssh_host_ecdsa_key

```

---

### Post by Tim036 on 2013-03-24
Many many thanks !  That is Brillian.

I gave it a poke and did this:-

At my normal Terminal prompt:-

su
and at the password prompt I entered my password

cd /

cd /root

entered the :-

ssh-keygen -f "/home/tim/.ssh/known_hosts" -R 192.168.1.105

(not knowing how to get back to my normal prompt, I closed the terminal and restarted it.

and lo !   It worked !

So in the root directory I wrote a little script with 'nano' editor:-

```
#!  /bin/sh

#  chmod a+x ssh_fix

#For whenh the Raspian SD card is changed and problem logging occurs

ssh-keygen -f "/home/tim/.ssh/known_hosts" -R 192.168.1.105
```

So if anyone, like me, doesn't know the difference between sudo and su, has the same problem.  That the fix that worked for me !

Silly details often bring me to my knees when trying to use Linux !

So many many thanks to the members of this Forum that stop me tearing more of my hair out ! ! !

:P:P:P

Tim

---

### Post by Lars Noodén on 2013-03-24
A way to avoid the problem in the first place is to backup the following files from your old system and transfer them to your new card or new system:

```

/etc/ssh/ssh_host_dsa_key
/etc/ssh/ssh_host_dsa_key.pub
/etc/ssh/ssh_host_ecdsa_key
/etc/ssh/ssh_host_ecdsa_key.pub
/etc/ssh/ssh_host_rsa_key
/etc/ssh/ssh_host_rsa_key.pub

```

The utility [tar](https://help.ubuntu.com/community/BackupYourSystem/TAR) should do the job nicely, but you can also use plain [sudo cp](http://manpages.ubuntu.com/manpages/precise/en/man1/cp.1.html).

---

### Post by Tim036 on 2013-03-24
PS

On the RPi

```
ssh-keygen -lf /etc/ssh/ssh_host_ecdsa_key
```


works well but to get to root on a RPi

you may need this

```
sudo passwd root
```

once you have set your password 

su gets you to root

---

