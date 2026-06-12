---
title: "Power off many remote machines."
date: 2012-12-23
forum: General Help
---

### Post by ibrahim.k on 2012-12-23
Good day!

I am in a network that has more than 20 computers running under ubuntu.

How can I turn all of these computers off remotely?

---

### Post by fdrake on 2012-12-23
you need to be logged in the machine with ssh and run the commands "poweroff" "shutdown". check the man.

check how to configure ssh. [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

also the user loggin into the machine need to have sudo/admin priv to turnoff the machines.

just googling around you'll find many resources like this [http://z-computer-z.blogspot.com/2010/01/remote-shutdown-and-remote-reboot-on.html](http://z-computer-z.blogspot.com/2010/01/remote-shutdown-and-remote-reboot-on.html)

---

### Post by rnerwein on 2012-12-23
> **ibrahim.k said:**
> Good day!

I am in a network that has more than 20 computers running under ubuntu.

How can I turn all of these computers off remotely?
hi
but don't forget to inform the oter usres before.
use the shudown ( informs the users being loged in, give a time slice and if you got an emergeny call you can stop the shutdown on that system). to have root access on those systems you can add - at the last line - in the /etc/sudoers
your_username    ALL=NOPASSWD: /sbin/shutdown
this to avoid a direct root loging and your ssh can run the shutdown command via sudo.
cheers

---

### Post by Old_Grey_Wolf on 2012-12-23
You may want to install cssh. ClusterSSH is a tool for making the same change on multiple servers at the same time. The 'cssh' command opens an administration console and an xterm to all specified hosts. Enter the command once in the terminal and all servers get the command.

---

### Post by ibrahim.k on 2012-12-24
> **Old_Grey_Wolf said:**
> You may want to install cssh. ClusterSSH is a tool for making the same change on multiple servers at the same time. The 'cssh' command opens an administration console and an xterm to all specified hosts. Enter the command once in the terminal and all servers get the command.


Could you please help me with the configuration of it?
How can I add machines that I want to control?
for example 
user1@machine1
user2@machine2
etc...
There is a file for configuration called "Config"
and this is it's location.
/home/myuser/.clusterssh/
But I don't know what should I do with it!
and after the configuration what commands do I have to execute in order to get connected to the machines that I have configured above and where should I execute them, In a normal terminal window?

This is the output of the config file.[http://paste.ubuntu.com/1461320/](http://paste.ubuntu.com/1461320/)

Thank you in advance.

---

### Post by Old_Grey_Wolf on 2012-12-24
This is a tutorial for configuring it and using it. [http://www.linux.com/learn/tutorials/413853:managing-multiple-linux-servers-with-clusterssh](http://www.linux.com/learn/tutorials/413853:managing-multiple-linux-servers-with-clusterssh)

---

### Post by ibrahim.k on 2012-12-26
> **Old_Grey_Wolf said:**
> This is a tutorial for configuring it and using it. [http://www.linux.com/learn/tutorials/413853:managing-multiple-linux-servers-with-clusterssh](http://www.linux.com/learn/tutorials/413853:managing-multiple-linux-servers-with-clusterssh)

Good day,

The tutorial says that I have to configure it via its global configuration file — /etc/clusters, or via a file in the user's home directory called .csshrc

But I can't find any of these files!
All I have is 
/home/myuser/.clusterssh/
and it contains a file called cofing,
It has a lot of information and scripts that I don't understand! 
[http://paste.ubuntu.com/1466438/](http://paste.ubuntu.com/1466438/)

Thnx

---

### Post by Old_Grey_Wolf on 2012-12-26
Try what this person did [http://ubuntuforums.org/showthread.php?t=1683139](http://ubuntuforums.org/showthread.php?t=1683139)

---

### Post by N00b-un-2 on 2012-12-26
hack into the local electric company's computer system and shut off the power to the area where these computers are plugged in.  Fool proof! :p

---

### Post by ibrahim.k on 2013-01-03
> **Old_Grey_Wolf said:**
> Try what this person did [http://ubuntuforums.org/showthread.php?t=1683139](http://ubuntuforums.org/showthread.php?t=1683139)

I using kubuntu 12.10 and installed the application by typing
 "sudo apt-get install clusterssh" 
in the terminal.
I have created a new file
 /etc/clusters
Then configured the new location of the file 
"extra_cluster_file=/etc/clusters"
the /etc/clusters file contains this addresses 
cluster user@172.16.0.11 user@172.16.0.12 user@172.16.0.13
and when I type in a terminal "cssh cluster"
I get 
Unknown configuration parameters: auto_closeibrahim@ibrahim-HP-Pavilion-dv6-Notebook:~
! please help.

---

### Post by Old_Grey_Wolf on 2013-01-03
Let us look at this a step at a time. If you enter cssh user@172.16.0.11 do you get to the server 172.16.0.11?

Can you connect using ssh user@172.16.0.11?

When you normally ssh to 172.16.0.11, do you use ssh user@172.16.0.11". Or do you use ssh and something else; such as, hostname with no userid?

---

### Post by Old_Grey_Wolf on 2013-01-03
I just thought about this. We appear to be in very different time zones. 

While you wait for me to be back on-line to answer your questions you may want to explore the cssh manual page by entering ```
man cssh
``` in a terminal. You can also look at the cssh manual page at [http://linux.die.net/man/1/cssh](http://linux.die.net/man/1/cssh). The cssh manual page may answer your questions.

---

