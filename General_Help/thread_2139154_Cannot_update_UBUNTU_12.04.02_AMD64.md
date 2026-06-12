---
title: "Cannot update UBUNTU 12.04.02 AMD64"
date: 2013-04-26
forum: General Help
---

### Post by Gakhar on 2013-04-26
HELP. HELP. I have installed Ubuntu 12.04.02 AMD64 but cannot upgrade or install any package. The Software center is aslo not working and seems to hang on "Waiting jockey-backend to complete". I have been using various linux distros for quite some time but this is first time that i encontered this message. One thing has changed. I am connecting to internet through proxy server.

HELP. HELP. URGENT.

---

### Post by Gakhar on 2013-04-26
I tried "sudo apt-get update" but got message "
raja@raja-Veriton-X2610G:~$ sudo apt-get update
[sudo] password for raja: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
help needed.

---

### Post by Gakhar on 2013-04-26
I tried "sudo apt-get update" but got message "
raja@raja-Veriton-X2610G:~$ sudo apt-get update
[sudo] password for raja: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
help needed.

---

### Post by plucky on 2013-04-26
> **Gakhar said:**
> I tried "sudo apt-get update" but got message "
raja@raja-Veriton-X2610G:~$ sudo apt-get update
[sudo] password for raja: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
help needed.

That usually means you have more than one package manager open.

Close all package managers,Software Updater,etc or reboot and then run ```
sudo apt-get update
``` and see if you get the same problem.

If you do , then you can run from a terminal ```
sudo rm /var/lib/apt/lists/lock
``` to delete the lock file and then run ```
sudo apt-get update
``` and see if it now works.

Good Luck

---

### Post by Bucky Ball on 2013-04-26
@ Gakhar: To improve your chances of help I have moved your post to its own thread. Please post new threads with a descriptive title and outline your problem rather than hijack another, existing thread (with a title and topic that have nothing to do with your problem).

---

### Post by ibjsb4 on 2013-04-26
This usually means that you have more than one package manager open.  Like maybe the software center when you tried apt-get.  Only one can be open at a time.

If this is not the case you can manually remove the lock.

```
sudo rm /var/lib/apt/lists/lock
```

And welcome to the forums :)

---

### Post by Gakhar on 2013-04-29
I have installed Ubuntu 12.04.02 64-bit. I am connected to internet through a proxy server. I am so far unable to update the operating system, either through command line or through the software center.

when i issue command:

> sudo apt-get update
I get many messages like shown below.

W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages)  407  Proxy Authentication Required

E: Some index files failed to download. They have been ignored, or old ones used instead.

Help me in resolving this problem.

Thanks.

---

### Post by lisati on 2013-04-29
@ Gakhar: Please do not start multiple threads, it dilutes the community's ability to help. I have merged your threee threads.

---

### Post by varunendra on 2013-04-29
Hello Gakhar,

I believe you have already solved your 'lock' problem with the previous two advices. For the current one -
> **Gakhar said:**
> W: Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages](http://pk.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages)  **[COLOR="#FF0000"]407  Proxy Authentication Required[/COLOR]**
.. as the error message suggests, please try a direct connection to avoid proxy authentication, or try changing the server (in Ubuntu Software Center > Edit > Software Sources) from "Pakistan" to "Main Server".

---

### Post by Gakhar on 2013-04-29
Thanks. I am new to forums and that's why i may have bungled.

---

### Post by Gakhar on 2013-04-29
Yes the lock problem is solved but i still can't download updates. 
I am getting the same message "407  Proxy Authentication Required".

---

### Post by varunendra on 2013-04-30
> **Gakhar said:**
> I am getting the same message "407  Proxy Authentication Required".

Did you try what I suggested in my previous post ? -
> .. as the error message suggests, please try a direct connection to avoid proxy authentication, or try changing the server (in Ubuntu Software Center > Edit > Software Sources) from "Pakistan" to "Main Server".

---

### Post by Gakhar on 2013-05-01
Already did but the problem remains. Why can't ubuntu update/install with internet via proxy. The firefox browser is working perfectly and i don't have any problem in surfing and downloading content.
I think it is related to some configuration file.

HELP. HELP. HELP or should i revert back to stupid windows.

---

### Post by varunendra on 2013-05-01
> **Gakhar said:**
> Why can't ubuntu update/install with internet via proxy.

Explained here : [http://www.checkupdown.com/status/E407.html](http://www.checkupdown.com/status/E407.html)

Please check this out : [http://askubuntu.com/questions/88976/407-proxy-authentication-required](http://askubuntu.com/questions/88976/407-proxy-authentication-required)

If you prefer to use the Synaptic way (I prefer it over Software Center anyway), but have problem in downloading it too (in *apt-get install synaptic*), you can use the following command to get the URI of the package(s) to be downloaded for synaptic:
```
apt-get install --print-uris synaptic
```
Then you can download them directly using your browser and install with **dpkg -i *** command.

---

