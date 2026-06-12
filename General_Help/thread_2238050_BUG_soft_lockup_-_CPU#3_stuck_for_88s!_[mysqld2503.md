---
title: "BUG: soft lockup - CPU#3 stuck for 88s! [mysqld:25038]"
date: 2014-08-05
forum: General Help
---

### Post by Joe_Linnell on 2014-08-05
Hello!

I'm an IT Admin recently hired to support a small shop of approx. 20+ employees and I'm trying to troubleshoot performance issues on our production system.  It consists primarily of two VMs (on VMware ESXi 4.1 hosts), both running Ubuntu 10.04 currently (planning to upgrade to 12 soon).  The app server runs tomcat6 and connects to the database server with MySQL for the in-house application they use.  The application logs and interacts with business data to generate reports and provide other services.  

The most common issue is users getting booted out of the system or reports hang and fail to run.  When this happens the Band-Aid to keep production going (uuuuber-important as day trading is going on and cannot stop for a second) is to stop tomcat6, restart mysql, and start tomcat6 again.  Works every time, but happens too often.  I'm new in this role, so I started a spreadsheet to track the frequency and types of issues we are seeing.  In the past week and a half, two of the three crashes were due to soft lockups on the database server (the other one may have been a zombie process--didn't get good data on that).

Here are the errors:

Last week:
BUG:  soft lockup - CPU#0 stuck for 86s! [sftp-server:11626] 
BUG:  soft lockup - CPU#2 stuck for 85s! [mysqld:11135] 
BUG:  soft lockup - CPU#1 stuck for 85s! [mysqld:20244]

Today:
BUG:  soft lockup - CPU#3 stuck for 88s! [mysqld:25038] 
BUG:  soft lockup - CPU#1 stuck for 83s! [vmtoolsd:1450]

I found another thread from a while back on [here]("http://ubuntuforums.org/showthread.php?t=1757773") with a somewhat similar setup/issue that suggested possible kernel issues at fault.  We have the upgrade to Ubuntu 12.04 on the horizon, but I'm not sure that will solve the problem.  Does anyone have any experience with these errors in a similar setting?

Thanks so much in advance for taking the time to read (and hopefully reply) to my post.  Best wishes.

---

