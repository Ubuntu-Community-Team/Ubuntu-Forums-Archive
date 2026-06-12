---
title: "Using debsums to troubleshoot potential security issue."
date: 2014-05-19
forum: General Help
---

### Post by vRanger on 2014-05-19
testuser@mailhost:~$ sudo debsums -l
binutils
libberkeleydb-perl
php5


These showed up today, last week they didn't.  Any thoughts on how to check if my server has been intruded?  I'm not sure if there is anything to worry about, and not sure how to find out.

---

### Post by tgalati4 on 2014-05-20
Look in your log files to see if those packages were updated since last week:

```
cat /var/log/apt/history.log
```

I'm not familiar with *debsums* so I don't know where or how the checksums are updated.  But I would spend some time reading on how *debsums* works.

After reading the documentation for *[debsums]("http://manpages.ubuntu.com/manpages/trusty/man1/debsums.1.html")*:

The -l switch simply lists packages without an md5 checksum.  So you can create them for those packages or investigate why the checksums are missing.  As to why they didn't show up last week, perhaps those packages were recently added with installation of another package.  Again, look at your package history.

If the checksum differs on a package between when it was installed and now, then that would warrant further investigation.  A missing checksum just means it needs to be generated.  Not all packages have checksums--it depends on the package maintainer and quality control of package repository.

---

### Post by matt_symes on 2014-05-20
Hi

Install tripwire and use that instead of debsum.

I keep the tripwire binaries, config files and databases on a USB pen drive that has a physical switch to write protect it.

Use the standard check with tripwire, update with apt, update with tripwire procedure.

Kind regards

---

### Post by vRanger on 2014-05-23
Thank you for the suggestion to use tripwire.  After digging, I'm not sure it is a replacement for debsums, but certainly a must have.  I liked what people were saying on this thread:

[http://www.linuxquestions.org/questions/linux-security-4/rkhunter-and-chkrootkit-vs-tripwire-547858/](http://www.linuxquestions.org/questions/linux-security-4/rkhunter-and-chkrootkit-vs-tripwire-547858/)
> [COLOR=#000000][FONT=Verdana]Hrmmmm...let's say your car has airbags and seatbelts. Wouldn't you feel better knowing both were in place and usable?[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Security should be run in layers...Should one layer fail, the others make it much more difficult to pull off an exploit. Prime example is iptables, PAX, and RSBAC. Your first line of defense is your firewall. Should the attacker bypass that, then PAX (assuming we're talking buffer overflow attacks, since they're quite common) should pick up the slack. Should PAX fail, RSBAC attempts to contain or minimize the damage.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]So why rkhunter or chkrootkit? Ask yourself this...if an attacker is successful, then he/she can update tripwire, yeah? How often do you honestly check tripwire's update dates? If you check daily, kudos to you. (and if you place the hashes on a read-only filesystem (i.e. CD), then kudos even more so). Point is, if it can be done, it can be undone, so layering your security should always be a goal...and no, I don't agree that running JUST rkhunter or chkrootkit is "secure".[/FONT][/COLOR]

---

### Post by tgalati4 on 2014-05-23
If you have a linux server running, then you can use *rsyslog* to remotely send log files from desktops and laptops to the server.  That way, the log files are kept, because many intruders erase the log files to cover their tracks.  Of course a sophisticated hacker who has root privilege on your machine can turn that off, but at least some log entries previous to the intrusion will be captured.

It's also a good idea to use rate-limiting, such as *fail2ban*.

---

