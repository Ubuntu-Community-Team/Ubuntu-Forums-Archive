---
title: "Apt-get errors..please help"
date: 2012-12-24
forum: General Help
---

### Post by isac630728 on 2012-12-24
Hello All, 

I'm trying to install snmp and snmpd services, But I get these errors.. Please help me fix this. 

Ubuntu Version 3.2.0-32-generic
temp_account@server_001:~$ sudo apt-get install snmp snmpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
linux-image-server : Depends: linux-image-3.2.0-34-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

What happens if I try apt-get -f ? Will install those packages without installing that linux-imgae-3.2.0.34-generic? OR Will it do something else? It's a Production server and I can't afford any downtime. Any workaround for this?

I do have one more server with a similar error message.. here is the output

I had already posted a similar thread in Installation & upgrades, but that had few different errors which is now resolved.

Here are the replies I received regarding that error. Please help me fix this...

> **oldos2er said:**
> *apt-get update* refreshes all source lists, /etc/apt/sources.list and any lists in /etc/apt/sources.list.d/

You're seeing the 404 errors because Maverick is no longer supported; it's repositories have been moved to old-releases.

*apt-get install -f* attempts to fix broken packages. From the man page: 

Fix; attempt to correct a system with broken dependencies in place. This option, when used with install/remove, can omit any packages to permit APT to deduce a likely solution. If packages are specified, these have to completely correct the problem. The option is sometimes necessary when running APT for the first            time; APT itself does not allow broken package dependencies to exist on a system. It is possible that a system's dependency structure can be so corrupt as to require manual intervention (which usually means using dselect(1) or dpkg --remove to eliminate some of the offending packages). Use of this option together with -m may produce an error in some situations. Configuration Item: APT::Get::Fix-Broken.

Have you run *apt-get update* on this system lately?



> **moneynut said:**
> Yes I did try apt-get update on those systems. It was successful in Server_001 and Server_002. Still I cannot install snmp and snmpd. So Shall I just try apt-get install -f snmp snmpd ?

It wont bring down the server or any services right?

---

### Post by lisati on 2012-12-24
Thread closed, dupplicate of [http://ubuntuforums.org/showthread.php?t=2097836](http://ubuntuforums.org/showthread.php?t=2097836)

---

