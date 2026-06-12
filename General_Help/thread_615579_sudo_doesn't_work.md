---
title: "sudo doesn't work"
date: 2007-11-17
forum: General Help
---

### Post by marvel.bakke on 2007-11-17
at the terminal prompt is type:
- name@home2:~$ sudo -s
and I received this error:
sudo: unable to resolve host home2

my version: uname -r - 2.6.22-14-386

---

### Post by mindwarp on 2007-11-17
Please paste the contents of your /etc/hosts file.  Most likely, you will need to add your hostname there, which will have to be done using sudo, or booting from a live cd.

---

### Post by taurus on 2007-11-17
> **mindwarp said:**
> Please paste the contents of your /etc/hosts file.  Most likely, you will need to add your hostname there, which will have to be done using sudo, or booting from a live cd.

Or from a recovery mode (from GRUB menu).

---

### Post by IanVaughan on 2008-04-08
I had the exact same problem, but I know what I did to effect this, sudo was working fine until I change the following :

I had added my PC to my Domain by adding the domain name in Network Settings->General tab.
This then added/changed (not sure on this) a host in the Hosts list.

My /etc/hosts file looked like this after my change which stoped sudo working :-
127.0.0.1 localhost
127.0.1.1 bart.Simpsons

So I changed the General tab by removing the Domain name, this did not cause the Hosts to be updated.
So I then changed the Hosts list in the Network Settings to remove the ".Simpsons" from the "bart" host name.

This did the trick.

---

### Post by Sauli on 2008-04-16
Thx Ian, you solved my problem too. :KS

I got the message "sudo: unable to resolve host myhostname" with Ubuntu 8.04 beta.
Like in the previous message also in my case sudo ceased to work after I had added the domain name in System -> Administration -> Network -> General tab. Also the remedy was the same I had to remove the domain name from the item in the hosts list.

---

### Post by polmir on 2008-04-16
What is sudo?
```
man sudo
```

[QUOTE=''man sudo'']DESCRIPTION
       sudo allows a permitted user to execute a command as the superuser or another user, as specified in the sudoers file.  The real and
       effective uid and gid are set to match those of the target user as specified in the passwd file and the group vector is initialized
       based on the group file (unless the -P option was specified).  If the invoking user is root or if the target user is the same as the
       invoking user, no password is required.  Otherwise, sudo requires that users authenticate themselves with a password by default
       (NOTE: in the default configuration this is the user’s password, not the root password).  Once a user has been authenticated, a
       timestamp is updated and the user may then use sudo without a password for a short period of time (15 minutes unless overridden in
       sudoers).[/QUOTE]



```
sudo -h
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
```

 ```
sudo -s

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.
```

And read this:
[http://qref.sourceforge.net/Debian/reference/ch-tune.en.html#s-sudo]("http://qref.sourceforge.net/Debian/reference/ch-tune.en.html#s-sudo")

---

### Post by agent8131 on 2008-04-24
See **[Ubuntu Bug #32906]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906")**

---

### Post by gganitis on 2008-04-28
I have the same problem since I upgraded to 8.04, but I didn't understand what I should do...

the /etc/hosts includes:
   127.0.0.1 localhost
   127.0.1.1 ubuntu HM

   # The following lines are desirable for IPv6 capable hosts
   ::1 ip6-localhost ip6-loopback
   fe00::0 ip6-localnet
   ff00::0 ip6-mcastprefix
   ff02::1 ip6-allnodes
   ff02::2 ip6-allrouters
   ff02::3 ip6-allhosts


In the Network Settings, in the General tab I have:
   Host name: ubuntu HM
   Domain name: -

Can anyone help me please???

---

### Post by Chemist on 2008-04-28
I had this issue if you boot into recovery mode you can edit the hosts file. 

> nano /etc/hosts

You should see something like this
> 
127.0.0.1 localhost
127.0.1.1 Bert.THE INN

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

All I did was remove .THE INN and rebooted. After that I could use the sudo command again

---

### Post by anvar on 2008-04-28
> **Chemist said:**
> I had this issue if you boot into recovery mode you can edit the hosts file. 


I was about to try the recovery mode, but ended up using gksudo instead :) Worked a treat and is much less mucking about :)

a.

---

### Post by Vin¢ on 2008-05-05
Okay, I don't have any host names to edit in my /etc/hosts file, gksudo doesn't work, and I don't have an Administration entry in my K > System menu. How bad does it suck to be me?

---

### Post by roderick on 2008-05-05
Spaces in hostnames is not gonna work. THe name has to follow some simple DNS (Domain Name System) rules, one of which is no spaces. Simple words, starting with letters, and no special characters, other than a '-' if you like.

---

### Post by tammersalem on 2008-05-15
I had the same issue using Ubuntu on my company network. As soon as I added the domain name to DNS, it added it to the host file, and presto sudo couldn't resolve the machine name (as my company DNS didn't allow external machine names to get registered).

There is a quick workaround for this, and that is to used gksudo to start an editor (like gedit)

```
gksudo gedit
```

Then use your normal root password to run gedit as root, then navigate to /etc and open the hosts file and comment out your existing entry:

```
#127.0.01   my-machine-name.some-domain-name.com
```

and add a new entry:

```
127.0.01   my-machine-name
```

This should work, and having used gedit as root you can save the file.
Now sudo should work fine

---

### Post by pata on 2008-06-04
System -> Administration -> Network

click to unlock button

go to "General" and delete "Domain name"

then is all ok ..

---

### Post by Spudinski on 2008-07-14
I had a similar problem, with usign the "sudo" command.
After changing the hostname, it stopped, but to get it back up and running you should chagne it back.

```
admin@server:~$ su root
Password:
admin@server:/home/admin# hostname server
```

---

