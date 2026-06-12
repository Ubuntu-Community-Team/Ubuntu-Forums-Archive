---
title: "tsp (task spooler) output from each job not to /tmp"
date: 2015-04-23
forum: General Help
---

### Post by Termo on 2015-04-23
Hi all

I run some heavy scientific calculations on my Ubuntu server, and found that tsp is pretty close to the easy job manager I wanted. My only problem is that the output from the job is stored in /tmp, and a couple of days ago the system locked up after running several calculations. So I needed a forced hard reboot, which meant that all the output files in /tmp where flushed away :(

I can not see how I can choose where to put the output from each job in tsp. I can choose to set the TMPDIR variable, but I would rather that I can choose from tsp directly where the output should be stored for each job I upload to the queue.

I'm now back to the screen/byobu solution.

/regards

---

### Post by dino99 on 2015-04-23
your wish seems not listed sadly  [http://www.ubuntugeek.com/task-spooler-personal-job-scheduler.html](http://www.ubuntugeek.com/task-spooler-personal-job-scheduler.html)
but gzip can be used  [http://manpages.ubuntu.com/manpages/saucy/man1/tsp.1.html](http://manpages.ubuntu.com/manpages/saucy/man1/tsp.1.html)

That feature is to be implemented in the future [http://vicerveza.homeunix.net/~viric/soft/ts/Changelog](http://vicerveza.homeunix.net/~viric/soft/ts/Changelog)

---

### Post by HermanAB on 2015-04-23
Make a soft link for each output file from /tmp to somewhere else? Read the ln man page.

---

