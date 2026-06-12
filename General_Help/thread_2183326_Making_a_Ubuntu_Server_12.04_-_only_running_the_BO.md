---
title: "Making a Ubuntu Server 12.04 - only running the BOINC-client, LM-sensor, sendmail/pos"
date: 2013-10-24
forum: General Help
---

### Post by danhansendenmark on 2013-10-24
**Making a secure Ubuntu Server 12.04 - only running the BOINC-client, LM-sensor, sendmail/postfix!?**                          [HR][/HR]                                                                   Hello Ubuntu friends ;)

I'm making a Ubuntu Server 12.04 - only running the BOINC-client,  LM-sensor, running a shell script which uses sendmail/postfix to warn  about high CPUtemp. and shutdowns the computer if it gets to hot!

**What I wan't to do:**
I'm running my own primary nameserver. webserver, mailserver, sqlserver  etc. (ISPconfig3) and use fixed IP, router is using NAT and my  ISPconfig3 server is using DMZ at this time.

I'm trying to build a secure Ubuntu Server 12.04 only using the  BOINC-client and LM-sensor as mentioned above.. Nothing else, no  graphical stuff or anything... 
I need to make the servers safe, because my plan is to make the servers  reachable from outside the LAN. This because I want to be able to  contact the servers via SSH from outside at all times and because I've  been testing a program called AndroBOINC, which works directly on the  boinc-client.

I gathered some inputs from other guides - from when I setup webservers  and from the ubuntu forum network, but, I'm still not that good a  building servers using the Linux OS. This is the reason for these  questions.

Here's what I found. First I'll show my idea, and then I'll show the  complete guide's (without the text defining the commands/setups)

**In short:**
Want to build secure ubuntu 12.04 server, only running:
Ubuntu Server 12.04
Boinc-client
Lm-sensor
sendmail/postfix ??? 
shell-script (CPUtemp.sh monitor/shutdown - warning via sendmail/postfix???)

 	Code:
 	My idea:

Building a secure Linux/Ubuntu 12.04 Server --> BOINC-client, LM-sensor ONLY! Running a "monitor CPUtemp" shell script & using AndroBOINC from outside and in

1a. Running a shell script which monitors CPUtemp. Need a mailprogram to send/smtp alert mails from the CPUtemp shell script. Sendmail? Postfix? Included in Ubuntu Server!?!
1b. Need some kind of protection program due to the use of a SMTP program???
2. Need some kind of program to view log-files or make an intranet site to view server status!?! Any ideas?

#1 Install and configure Firewall - ufw
#2 Secure shared memory - fstab
#3 SSH - Disable root login and change port
#4 Protect su by limiting access only to admin group
#5 Harden network with sysctl settings
#6 Scan logs and ban suspicious hosts - DenyHosts and Fail2Ban
#7 Intrusion Detection - PSAD
#8 Check for RootKits - RKHunter and CHKRootKit
#9 Scan open Ports - Nmap
#10 Analyse system LOG files - LogWatch
#11 SELinux - Apparmor
#12 Audit your system security - Tiger

#13 Amavisd-new,
#14 SpamAssassin,
#15 Clamav

#16 Change The Default Shell --> /bin/bash ???



**Sources:**

 	Code:
 	SOURCES:

FROM "How to secure an Ubuntu 12.04 LTS server. Part 1 The Basics" - WHICH IS A GOOD IDEA TO USE? [http://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics](http://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics)

Install and configure Firewall - ufw
Secure shared memory - fstab
SSH - Disable root login and change port
Protect su by limiting access only to admin group
Harden network with sysctl settings
Disable Open DNS Recursion and Remove Version Info - Bind9 DNS
Prevent IP Spoofing
Harden PHP for security
Restrict Apache Information Leakage
Install and configure Apache application firewall - ModSecurity
Protect from DDOS (Denial of Service) attacks with ModEvasive
Scan logs and ban suspicious hosts - DenyHosts and Fail2Ban
Intrusion Detection - PSAD
Check for RootKits - RKHunter and CHKRootKit
Scan open Ports - Nmap
Analyse system LOG files - LogWatch
SELinux - Apparmor
Audit your system security - Tiger

FROM "The Perfect Server - Ubuntu 12.04 LTS" - WHICH IS A GOOD IDEA TO USE? [http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3-p3](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3-p3)

Change The Default Shell --> /bin/bash
Disable AppArmor??? Due to complications !?!?
Install rkhunter, binutils
Install Amavisd-new, SpamAssassin, And Clamav


FROM "Monitor critical temperatures in Ubuntu Server - Lucid/Karmic" - I MADE A SHELL SCRIPT BASED ON THIS
[http://www.havetheknowhow.com/Configure-the-server/Monitor-server-temperatures.html](http://www.havetheknowhow.com/Configure-the-server/Monitor-server-temperatures.html) 
         
                                                                      
I hope there's someone of you guru's in here who will help me or point me in the right direction ;)

                __________________
                Kind Regards
Dan

[COLOR=DimGray]__________________________________________________  _______
Fixed IP/WAN
DMZ -> "ispserverip"
Primary NameServer -> ns1.myprimarynameserver.tld
Secondary NameServer -> ns2.somedomainservice.tld

Ubuntu Server 12.04.2
ISPconfig 3 v.3.0.5.2 (Single Server Setup)
NameServer: BIND v.9.8.1-P1
SquirrelMail: v.1.4.22
MailServer: PostFix v.2.9.6 - IMAP/POP3 Dovecot v.2.0.19
Database: MySQL Server v.5.5.29-0ubuntu0.12.04.2
Tutorial: "ThePerfectServer-ISPconfig3-Ubuntu12.04"[/COLOR]

---

