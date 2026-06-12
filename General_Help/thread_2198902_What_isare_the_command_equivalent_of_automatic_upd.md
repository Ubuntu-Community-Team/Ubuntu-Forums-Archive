---
title: "What is/are the command equivalent of automatic update manager?"
date: 2014-01-11
forum: General Help
---

### Post by arroy_0209 on 2014-01-11
In ubuntu 12.04 I receive automatic update notice from ubuntu every two weeks as configured. I receive a list of "security" and "other recommended" updates list in an window and I am supposed to do a click to start updating. I am not sure what is the commandline equivalent of this procedure: is it just "sudo apt-get update" or a combination of "sudo apt-get update" and "sudo apt-get upgrade" or is a combination of "sudo apt-get update" and "sudo apt-get dist-upgrade" or none of these. It appears to me that the last combination is the most apprpriate one for me. However before I switch over to command line updatation, I would like to know what is the command line equivalent of the update manager I had used so far. Thanks.

---

### Post by coldcritter64 on 2014-01-11
To do a basic update from the command line instead of using update manager, I use the command,
```
sudo apt-get update && sudo apt-get upgrade
```

**If** any packages are held back, that is packages are displayed as "not upgraded" in the terminal, I then run the code,
```
sudo apt-get dist-upgrade
``` This then finishes off the upgrading, if required (usually just the first code example is needed.)

When fully up to date, this is typical terminal output,

```
yeti@*********:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for yeti:

<snipped repository addresses for brevity>
                      
Fetched 128 kB in 7s (16.6 kB/s)                                               
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
yeti@*********~$
``` ********* is my hostname censored here. This is from a debian install but I do the same with my ubuntu installs :-).

---

### Post by cmcanulty on 2014-01-11
I made an alias in my .bashrc file for the above commands so I just type ud in terminal and get updated very fast

---

### Post by ibjsb4 on 2014-01-11
The command line equivalent of upgrade that is used in update-manager:

apt-get dist-upgrade

This command will install new kernel along with other upgrades, its sometimes called "safe upgrade".

Apt-get upgrade will not install upgraded kernels.

A handy apt-get list:

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by philinux on 2014-01-11
Why not just launch update manager and optionally pin it to the launcher. I do this as I like to read some of the change logs.

---

### Post by Dave_L on 2014-01-11
Note that you can use the -s (or --simulate) option with "upgrade" or "dist-upgrade" if you want to see what will be done, without any changes being made:

```
sudo apt-get -s upgrade
```
```
sudo apt-get -s dist-upgrade
```

---

### Post by coldcritter64 on 2014-01-11
> **cmcanulty said:**
> I made an alias in my .bashrc file for the above commands so I just type ud in terminal and get updated very fast
I did the same only using a separate .bash_aliases file, it is referenced from code in .bashrc.

Mine: 
agu : sudo apt-get update
agg : sudo apt-get -y upgrade
agdu : sudo apt-get -y dist-upgrade

@ OP, note what ibjsb4 points out re kernels and upgrade vs dist-upgrade. And the -s switch suggestion noted by Dave_L is a very good idea, will be using that myself more often ;).

---

### Post by deadflowr on 2014-01-11
> **philinux said:**
> Why not just launch update manager and optionally pin it to the launcher. I do this as I like to read some of the change logs.
On precise, if you pin it, the update icon will list the number of updates.
Nice little added bonus.
They dropped that after precise sometime.

Also, for the -s option, that'll work and be helpful on any apt-get action, from installs to purges and removals.
Nice little thing to use when you want to remove a package, but need to see what "other things" might get removed as well.

---

