---
title: "memory usage keeps climbing"
date: 2015-10-24
forum: General Help
---

### Post by xeddog on 2015-10-24
I have two fresh installs of Ubuntu 15.10.  Both machines are older i-7 processors with either 6GB RAM or 4GB RAM.  I also installed nZEDb which seems to run fine for a while, like an hour or two, and then the machines become unresponsive, or at least VERY sluggish.  I was finally able to find out that the memory usage was over 95%, and swap was over 50% so the machines were beating themselves to death.  I was able to get all of the nZEDb stuff closed down, but the memory utilization was still high.  On the machine with 6GB RAM, System Monitor shows process "indicator-session-service" is using 4GB of that precious 6GB RAM.  On the machine with 4GB RAM it is at 2GB.  Is this normal???  It seems to me that with "indicator" in the process name, and with all of my applications closed, that the memory utilization should drop, but it isn't.  Also, the system is still a little sluggish to respond.  


Any help appreciated,

Wayne

---

### Post by sudodus on 2015-10-24
Maybe some processes are still left after closing nZEDb. Maybe there is some memory leak associated with the program.

What is the memory usage after rebooting the systems? And what happens when you run some other application programs?

Are you running Ubuntu desktop 64-bit, installed from the **ubuntu-15.10-desktop-amd64.iso** file?

-o-

My experience is that the kernel grows with every new version, and the RAM usage will grow along with that. But only a little. 4 GB RAM should still be enough for many application programs.

If you use some application, that needs a lot of RAM or fast graphics, you could try an Ubuntu flavour with a lighter desktop environment. Xubuntu and Ubuntu MATE are medium light, Lubuntu is ultra light.

---

### Post by grahammechanical on 2015-10-24
I am using a 2 week old install of 15.10 on a machine with only 1 GB of RAM and System Monitor shows indicator-session-service as using 2.9MiB of memory. I am guessing that this service is referring to the indicators in the top panel to the right.

System Monitor will give a break-down of memory usage for all the app indicators. Is there an indicator related to app that has been installed since Ubuntu was installed that is using a lot of memory? Is there a service running at start-up that is showing in Startup Applications that might need to be removed?

Regards.

---

### Post by xeddog on 2015-10-24
I am running the 64-bit Ubuntu 15.10 from the iso.  I was a little concerned because I downloaded the iso on the morning of the official release.  After installing it, I did a apt-get update and apt-get upgrade and there was a bunch of updates so I may have gotten the ISO a little too early even though it was on the official Ubuntu website.

After a fresh boot the memory used by "indicator-session-service" is about 30MB on one machine and about 13MB on the other.  Since the installations are almost identical I am not sure why such a difference.  The total amount of RAM used after the boot is around 1.2GB on the computer with 6GB RAM, and about 850 on the one with 4GB RAM, and it will stay at that level, or nearly so, until I start nZEDb so it does seem like something nefarious going on with nZEDb.  Once it starts, memory usage slowly keeps growing until I run out.  Once nZEDb is started though, memory usage never comes back down.  I have looked through all of the processes that are still active after shutting nZEDb down, and I don't recognise anything that looks like it is left over.

Just now I rebooted both machines.   I then used Firefox and browsed a few things on the web.  No change in the memory usage.  Then I started SABnzbd, Sickbeard, and CouchPotatoServer on one machine.  On the other I started SABnzbd (V0.8 beta 1), SickRage, and CouchPotatoServer.  The memory usage went up a tad but nothing serious.  On the machine with 6GB RAM the memory usage went from 1.2 up to 1.6GB and stayed there.  On the other machine it went up from 850MB to 1.3GB and stayed there.

Then, in preparation for running nZEDb again, I did a mysql optimise for all of the tables.  On the 6GB machine memory usage went to 2.1GB, and the indicator-session-service went to 64MB.  When the optimise completed the numbers were down slightly to 1.9GB and 62.5MB.  On the other machine the total memory went to 1.5GB and 24MB while the optimise was running.  When it completed the numbers stayed where they were at 1.5GB and 24MB.

Then I started nzedb.  On the 6GB machine memory went to 2.4GB and the indicator app to 208MB.   In only about a minute they were at 3GB and 800MB.  From there it was a slow steady increase until memory is at 95%+ and swapping starts increasing.  From there, of course, performance goes into the toilet.

If it weren't for the process hogging all of the memory being an Ubuntu module I would be heading over to the nzedb support site.   Well, I'll be doing that too, but since it looks like it could be an Ubuntu issue to me, here I am.

Anyway, that's my story and I'm stickin' with it.

Wayne

---

### Post by sudodus on 2015-10-24
It seems Ubuntu works normally with the other programs you tested. I don't know nZEDb, so I can't help you with it.

Maybe you can try with Lubuntu 14.04 LTS, which is well debugged and polished.

-o-

Let us hope someone here or at the nZEDb support site has experience of running nZEDb in Ubuntu :-)

---

### Post by xeddog on 2015-10-24
grahammechanical - no new indicator applets.  There are a couple of new startups that run like MariaDB and Apache, but nothing rears it's head until I start the actual nzedb applications.  There are a bunch of php scripts that run under tmux to do all of the processing.  I have been running all of the scripts one at a time, but everything seems to work fine when done this way.  So far, that is.

Wayne

---

### Post by xeddog on 2015-11-03
Just for an update - 

I took my 6GB machine and installed Ubuntu 14.04.3, and then re-installed nZEDb as close as I could to the way it was on 15.10.  The memory problem seems to have gone away.  When running tmux with everything I needed and then some works just fine.  The "indicator-session-service" process uses a fairly consistent 2.5(ish) MB of memory and I never saw it get over 3MB.  

However, that gives me back the problem I had that made me upgrade Ubuntu in the first place.  SickBeard absolutely REFUSES to do a backlog search.  Once a title hits the backlog queue the only way to get it to download is to go into the nZEDb web interface, search for the title, manually download the nzb, then switch to SABnzbd and change the download options so it will get post-processed correctly.  



Wayne

---

