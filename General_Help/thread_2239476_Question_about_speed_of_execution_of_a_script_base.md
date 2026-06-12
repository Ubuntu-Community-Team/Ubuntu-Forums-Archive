---
title: "Question about speed of execution of a script based on load average of the server."
date: 2014-08-14
forum: General Help
---

### Post by cherva on 2014-08-14
I have a script that forks to do its job and now the load average is 10 on a 4CPU machine....
Will it run faster if I make it to fork 4 times and lower the cpu load average to be between 3.5 and 4 ?
I mean if I have 4 lanes and all 4 of them are full of moving cars the traffic will move faster than if the cars that try to squeeze trough are 10 lanes....

---

### Post by JetStorm on 2014-08-14
Not sure whether you know it or not, so in order to clarify things for the people that will actually help you later, I'll say that load average is not showing just the CPU load but it also considers the disk load and a few other factors, so first you might want to make sure that the disk I/O for example is not the problem in your case.
While running the script open top and see the "wa" column in the Cpu(s) row - if that number is high, the CPU is most likely not utilized at the moment.
Again, sorry if you already know all of this.

---

### Post by cherva on 2014-08-14
I think it is a CPU problem because the 
CPU user time is 83.23%
CPU system time is 16.73%
CPU idle time is 0.00% :)
And correct me if I'm wrong in my calculations, but the disk usage from zabbix shows an average of 5.92 ksps writes, that is (5.92*1024)*512 = 3103784.96 bps ~ 3.10378496 Mbps
And the reads are 200kbps

---

### Post by JetStorm on 2014-08-14
Had to be sure, because when many people say system load or average load in Linux, they actually think this is only the CPU load which makes finding the problem harder.  Guess it's different in your case...
I'm always interested in better performance but unfortunately I can't give an answer to your original question, so you can wait for someone else or if it's not too much work or too hard you can modify the script and post whether there's an improvement.

---

