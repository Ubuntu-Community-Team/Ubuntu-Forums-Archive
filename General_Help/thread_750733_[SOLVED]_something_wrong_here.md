---
title: "[SOLVED] something wrong here"
date: 2008-04-09
forum: General Help
---

### Post by mandrill on 2008-04-09
Anybody know why my terminal looks looks this? 


jim@
monkey:~$


or why my numlock suddenly stopped working?

 Or why I suddenly have this every time I log in?      "An error occurred while loading or saving configuration information for gnome-settings-daemon. Some of your configuration settings may not work properly". Details: Bad key or directory name: "/desktop/gnome/peripherals/keyboard/host-
monkey/0/numlock_on": `
' is an invalid character in key/directory names
I had this thing doing everything but backflips, and now this......ideas? Please?

---

### Post by gsmanners on 2008-04-09
Weird. Try this:

cat /etc/hostname
cat /etc/hosts

See if there's something strange there.

---

### Post by mandrill on 2008-04-09
> **gsmanners said:**
> Weird. Try this:

cat /etc/hostname
cat /etc/hosts

See if there's something strange there.

I was just in both files....blocked out the ipv6 lines in /etc/hosts, saved the file....127.0.0.1 localhost
127.0.1.1 monkey.mshome

# The following lines are desirable for IPv6 capable hosts
#::1 ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts


did not touch sudo gedit /etc/hostname, but this is what I found there,


monkey - on the 2nd line

---

### Post by gsmanners on 2008-04-09
That could be it. I don't think you should have a \n in the /etc/hostname file.

---

### Post by mandrill on 2008-04-09
> **gsmanners said:**
> Weird. Try this:

cat /etc/hostname
cat /etc/hosts

See if there's something strange there.

cat /etc/hostname = 

monkey
jim@
monkey:~$

cat /etc/hosts = 


127.0.0.1 localhost
127.0.1.1 monkey.mshome

# The following lines are desirable for IPv6 capable hosts
#::1 ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts

---

### Post by mandrill on 2008-04-09
> **gsmanners said:**
> That could be it. I don't think you should have a \n in the /etc/hostname file.

I don't have a \n anywhere....

---

### Post by gsmanners on 2008-04-10
> **mandrill said:**
> I don't have a \n anywhere....

I mean, an end of line character (aka "
").

---

### Post by mandrill on 2008-04-10
solved -  did clean install

---

