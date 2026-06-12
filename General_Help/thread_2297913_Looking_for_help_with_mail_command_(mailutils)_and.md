---
title: "Looking for help with mail command (mailutils) and why two configs have dif results"
date: 2015-10-07
forum: General Help
---

### Post by Boktai1000 on 2015-10-07
Hello,

I'm looking for assistance as to why two hosts that have the same exact Postfix configuration are sending mail with the "mail" command, and the email address they are sending from is different on each. The username, /etc/hostname, /etc/hosts, /etc/resolv.conf, /etc/mailname, and /etc/postfix/main.cf files are all exactly the same - and I have done a postfix reload / service restart and rebooted the servers several times.

I made a post on serverfault here [http://serverfault.com/questions/726886/two-identical-postfix-main-cf-files-but-sending-mail-from-cli-appears-different](http://serverfault.com/questions/726886/two-identical-postfix-main-cf-files-but-sending-mail-from-cli-appears-different) that has a lot of the info that I've dug into so far, but right now I'm stuck investigating the mail.log and I can see that the sending as email addresses are different for whatever reason and I can't for the life of me figure out what's causing it.

For the Mail.log comparison please see below:

Mail01 (I like the way this one sends out) [http://pastebin.com/AAYPi1Q4](http://pastebin.com/AAYPi1Q4) Mail02 (this is the one sending as mail.example.com - cant figure out why) [http://pastebin.com/2D853s9u](http://pastebin.com/2D853s9u)
Mail01: uid=1000 from= Mail02: uid=1000 from=operations@mail.sansio.com Mail on mail01 is submitted with a bare username (operations), so postfix appends myorigin making [email]operations@sansio.com[/email]. Mail on mail02 looks to be submitted with the full email address as the from, so Postfix doesn't append myorigin.

These are both running on Ubuntu 14.04.3 VMs that were created fresh for this, and fully updated.

Thanks!

---

### Post by QIII on 2015-10-07
Duplicated at [http://ubuntuforums.org/showthread.php?t=2297914](http://ubuntuforums.org/showthread.php?t=2297914)

Closed

---

