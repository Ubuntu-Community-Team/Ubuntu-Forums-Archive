---
title: "bash: input/output error when using any command"
date: 2007-11-20
forum: General Help
---

### Post by jpwoodbridge on 2007-11-20
hi all,

 having a wee problem. when ever i try any command, ls, df, netstat, shutdown -r...... i get

root@..# <command>
-bash: /bin/<command>: Input/Output error
root@...#

can no longer open another ssh session, or log into vmware console, or access any machines running on vm server.

i was making a few vpn files on one of the virtual machines when all dropped out. 

biggest problem server is in a data centre, went in today and worked fine (worked perfect at office for almost a month) all afternoon, now all of a sudden its stopped responding. please help!

thanks

---

### Post by cmnorton on 2007-11-20
This looks like either root's .bashrc or .profile has something in it that could be causing this problem, or /etc/bash.bashrc might be the problem.

I once installed a product that did not have a workaround for Red Hat 9's "errno" warning, which is issued  anytime a program using CRTL was executed. This product did not filter the results of its shelling out to a command line, and basically broke bash. 

If you cannot sudo vi /root/.bashrc or /root/.profile, then you'll need to boot with a live disk and look at the files.

---

