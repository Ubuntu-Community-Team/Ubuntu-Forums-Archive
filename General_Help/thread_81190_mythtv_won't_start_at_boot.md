---
title: "mythtv won't start at boot"
date: 2005-10-23
forum: General Help
---

### Post by frkstein on 2005-10-23
I am new with working on mythtv. My problem is that if the machine I have it on reboots, it will not start up mythtv on its own. from the logs, it will try but fail. The only way I can get mythbackend started is using a terminal, log in as root and start it that way. No other user can start up mythbackend. Any ideas of what is happening.

---

### Post by frkstein on 2005-10-25
I found the problem. There is a script named mythtv-backend located inside /etc/init.d.  Inside this script there is a line which lets you specifiy which user id to use to initiate the script. Needless to say, I modified the line to be:

USER = root

That solved the problem.

---

### Post by nwlinkvxd on 2005-12-02
frkstein, thank you very much.

---

### Post by mteppo on 2008-04-26
> **nwlinkvxd said:**
> frkstein, thank you very much.


Was it that you were missing mythtv- user? (Just a wild guess - my backend runs as mythtv and you should not run something as root if you can avoid it due to security concerns related)

I also migrated my backend to another machine and came across few issues.
I installed Gutsy 7.10 and mythbuntu-control-center on top of that.


Mythtv will not start at boot but will fail at db-queries. 
I had to poke around with the order of things to be started in rc*.d - links.
for example there was rc2.d/S24mythtv-backend - link that starts the mythtv. But mysql had not yet came available and backend failed to contact db. I "moved" all the links for backend startup to be "later" S98mythtv-backend and now it works. You can use update-rc.d to accomplish this.

I have amd x64 dual-core - should the thing be timing or x64 issue or something alike.

---

