---
title: "Admin multiple Desktop environments from Central Admin Desktop"
date: 2019-09-11
forum: General Help
---

### Post by Adam_GUI on 2019-09-11
I've got a pet project I want to work on, and am a little unsure how to go about it.

I want to be able to administrate a group of machines from a central machine.

Master____________________________
|___________|_____________|_______|
Box 1_______|Box 2________|Box3__|Box 4

Can I use Apt to install, say, cairo-dock on the Master machine and have the master push the command "apt install cairo-dock" to Boxes 1-4?

I know I could use RDP on the same network and do that one-at-a-time.  I searched for a way to try and do it all at once and didn't find any info newer than 2003.
Could be a mix of me not knowing what to look for and using DuckDuckGo over Google Search.

Can I use a mix of 32 and 64 bit machines as long as I'm on the same domain?

I'm wanting to use Desktop installs for a Teacher -> Student setting.

---

### Post by TheFu on 2019-09-11
Uh .... ssh script?
Or any of the 15 DevOps tools?

ssh is THE WAY Unix systems are administrated.  There are probably 500 tools based on ssh to do remote things on other systems.  ssh, scp, sftp, rsync, ansible, sshfs, clusterssh, off the top of my head.

A Windows background doesn't help, but pretty much any Unix background would have taught ssh tool use.

If you want to go crazy, O'Reilly has a book just on ssh.  [http://shop.oreilly.com/product/9780596000110.do](http://shop.oreilly.com/product/9780596000110.do) You don't need that book, btw.

ssh is why managing Unix system counts of 2, 5, 500, 5000 isn't much different or much more effort with a little thought.
[https://help.ubuntu.com/lts/serverguide/openssh-server.html](https://help.ubuntu.com/lts/serverguide/openssh-server.html) 
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
[https://www.cyberciti.biz/faq/ubuntu-linux-install-openssh-server/](https://www.cyberciti.biz/faq/ubuntu-linux-install-openssh-server/)

If you have the server running on the default port, 22/tcp, then by installing **fail2ban**, brute force attacks are automatically blocked.  **sudo apt get install ssh fail2ban** - run that on every system.  After that, you can ssh into any of the systems from any other of the systems.   **ssh thefu@box1** ... for example. This assumes "thefu" userid exists on the "box1" Linux machine (it can be any Unix-like OS) and that the current machine can find box1 on the network using normal DNS or IP name lookups.  Windows name lookups will not work.

If you are in Georgia, come out to an ALE meeting or an ALE-NW meeting. We'll help with hands on examples.

---

### Post by Adam_GUI on 2019-09-11
I've had classes in Windows Server 2003.  But, that was a long time ago and I've forgotten a lot.
The closest thing I could remember was Windows Active Directory, and I honestly don't remember enough to think if that would have done what I wanted or not.

I took intro to Unix at Dalton State and they actually taught Fedora Core ~7.  Way out of date for the time; and only enough for an intro to KDE, installing from RPM and setting up printing.
I handed out a ton of printed Ubuntu CDs that Semester.

I know that's not exactly helpful, or an excuse.  I've had health issues and my memory really does get fuzzy after time.

I'll definitely lookup the book and start reading up.

I looked for a LOCO in NW Georgia and didn't see anything alive.  Didn't think to check closer to Atlanta.
Is there a LOCO link or schedule I can check out?  
It's like an hour and forty five minute drive for me, but, if I can sketch out a date I might can arrange a meetup.

---

### Post by TheFu on 2019-09-11
[https://wiki.ubuntu.com/GeorgiaUSTeam/GeorgiaOrganizations](https://wiki.ubuntu.com/GeorgiaUSTeam/GeorgiaOrganizations) Some of the locations are out of date. ALE has over 1300 members, but only about 5-20 will attend any specific meeting because traffic can be terrible around town.

Maybe Chattanooga is closer?  

Colleges often have a LUG.  Nobody uses "LOCO" that I've seen. Search for a town/university + linux + lug.
If you want to start a LUG in your area, perhaps others are interested too?  Join the ALE email lists and ask if anyone else is interested.  Find a place to meet, schedule 3-4 meetings, see who shows up.  ALE-NW has had people from Tennessee come to meetings a few times.

Cartersville has a monthly computer security meetup (DC770) and almost everyone there will know ssh. I don't know the exact schedule, think it is on a Tuesday evening. Their location is about 45 min for me to get there on a weeknight.  
ALE-NW meets on Sunday afternoons, 3p-6p.

ssh isn't hard. There are lots of webpages for beginners and youtube videos that show exactly how it works. 
[http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html](http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html) shows some things you can use ssh to accomplish. Don't worry if you don't understand all of them.

Right now, I have 10 terminals open connected to 8 different systems ... all through ssh.  Authentication is key-based, not passwords. Any system on the internet shouldn't use passwords for authentication.

---

### Post by SeijiSensei on 2019-09-11
I'd look into the [Linux Terminal Server Project]("http://www.ltsp.org/").

---

### Post by Adam_GUI on 2019-09-11
Cartersville isn't a terrible drive.  I'll look at that.
I'm interested in ALE-NE.  But, I have prior engagements on Sunday and can't attend.

Thanks a lot for the resources so far, TheFu.  You've given me a lot to read over.

---

### Post by scorp123 on 2019-09-12
> **Adam_GUI said:**
>  Can I use Apt to install, say, cairo-dock on the Master machine and have the master push the command "apt install cairo-dock" to Boxes 1-4? 

I have multiple machines at home (Linux + Mac) and for such things I use **Ansible**.

Ansible basically just does what you suggest: It logs in remotely (via SSH) to those other machines and then, based on the playbook (the set of commands you want to execute) does exactly that, e.g. install or remove packages, and then let you know in a short summary if it was able to do what you wanted or if the command failed on any of the machines.

Resources to get you started with Ansible, if you are interested:

[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-ansible-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-ansible-on-ubuntu-18-04)
[https://www.cyberciti.biz/faq/how-to-install-ansible-on-ubuntu-18-04-for-it-automation/](https://www.cyberciti.biz/faq/how-to-install-ansible-on-ubuntu-18-04-for-it-automation/)

Ansible discussion + mailing list:
[https://groups.google.com/forum/#!forum/ansible-project](https://groups.google.com/forum/#!forum/ansible-project)

Also, there are many good step-by-step video tutorials and beginner's guides on YouTube.


A very simple Ansible playbook to roll out the package "cairo-dock" to all your hosts could e.g. look like this:

```

---
- hosts: yourdesktops

  tasks:
          - name: Install 'cairo-dock' package if needed
            package:
              name: cairo-dock
              state: present

```

For this to work you'd need to have a working installation of Ansible and your Ansible hosts definition file would need to have a group entry for "yourdesktops" (please change and adjust as needed) so it knows what machines it is supposed to talk to and perform the defined actions on. Let's assume you saved that little playbook above as "install-cairo.yml", and let's assume Ansible is installed and functional, you'd then execute it like this:

```
ansible install-cairo.yml
```

Screen output would then look something like this:

```

PLAY [yourdesktops] *****************************************************************************************************************

TASK [Gathering Facts] ***************************************************************************************************************
ok: [host1]
ok: [host2]
ok: [host3]

TASK [Install 'cairo-dock' package if needed] ****************************************************************************************
ok: [host1]
changed: [host2]
ok: [host3]


PLAY RECAP ***************************************************************************************************************************
host1              : ok=4    changed=0    unreachable=0    failed=0
host2              : ok=3    changed=1    unreachable=0    failed=0
host3              : ok=4    changed=0    unreachable=0    failed=0

```

The output above tells us e.g. that "host1" and "host3" had the package already installed but "host2" needed to be changed. If I execute the playbook again I'd now get an "ok" from all of them.


I hope this was somewhat useful to you + sorry for the long post.

---

### Post by TheFu on 2019-09-12
Ansible is very powerful and for more than about 8 systems, the extra complexity needed to use it might be worth it.  If you are wiping and rebuilding systems all the time and want them to be nearly identical then ansible really shines.  Definitely use it.

For fewer systems, ssh with a loop in bash is probably sufficient.

```
#!/bin/sh
SRVS="host1 host2 host3 host4"
for D in $SRVS ; do
  echo "
======
INFO: Patching $D"
   ssh deploy951@$D  "sudo apt-get update && sudo apt-get dist-upgrade"
done
```

deploy951 account needs to be configured to run apt-get without password prompts. That's 1 line in the /etc/sudoers file on each of the "SRVS".    
Any command can be put into this script.  Have 2 or 2000 hosts? Not an issue.  Want to do things in parallel?  That's possible too.  Unix provides simple solutions that can be used together for solving more complex  needs.

If the hostnames for ssh login are sequential, then 
```
#!/bin/bash
# For loop 4 times
for i in {1..4} ; do
   echo "host$i "
done
```

---

### Post by scorp123 on 2019-09-12
> **TheFu said:**
>  For fewer systems, ssh with a loop in bash is probably sufficient. 

If you only have few systems and you don't care too much about the features of Ansible... maybe "**ClusterSSH**" will do?
Article with tutorial:
[https://www.linux.com/tutorials/managing-multiple-linux-servers-clusterssh/](https://www.linux.com/tutorials/managing-multiple-linux-servers-clusterssh/)

It will basically take your input from the main window and replicate that input to the other open connections.

---

### Post by TheFu on 2019-09-12
I've used clusterssh.  As long as everything you type is what you want, exactly, to be entered on every other system, it is useful.  It is possible to only type commands into 1 session as well.
Is uses a ~/.csshrc file for specifying "clusters" - which are really just groups of similar computers.
For example:
```
vmware_clients = root@pki42 ror48 root@fss59 videos54  android55 spamgw qbe
```
Add a line for each sort of "cluster" you'd like to connect and command.
Connect using: **clusterssh vmware_clients** for the example above.

---

