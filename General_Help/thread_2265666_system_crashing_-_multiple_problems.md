---
title: "system crashing - multiple problems"
date: 2015-02-16
forum: General Help
---

### Post by heroquestelf on 2015-02-16
I am currently running Ubuntu 14.04.1 LTS on a Toshiba Satellite P-305.

I am having multiple problems, and I don't know where to start. I have already uninstalled and reinstalled Ubuntu from the ground up, and I'm still getting the problems.

First off, it started with my system not reading an external hard drive. The system then crashed, and when I went to reboot it, it would not pull up the GUI, so I wound up having to reinstall.

Now, the first problem I've been having is the software center has been flaky, often times shutting down in the middle of a download and not installing the requested software. 

The next problem I've been having is with Firefox. I will be on Firefox and it will suddenly crash for no apparent reason and it will not pull back up again without a reboot, and once Firefox crashes, it takes the Software Center with it. Once Firefox crashes, if you click on the icons on the sidebar for Firefox, the little spinning "I'm thinking" cursor comes up, but then nothing happens. Likewise if you try and access the Software center once Firefox crashes you get the same result.

And lastly, the desktop search function seems to be disabled. If you click on the Ubuntu logo icon at the top of the sidebar, the search function comes up, but it won't find anything. And it's not like I'm searching for anything exotic. For example, my last search was for "terminal". It told me that no files could be found that matched that description. I'm just about to my wits end because I don't know which dog to chase first. I would just reinstall Ubuntu all over again, but considering that I've already done it once I don't want to go through all of that work all over again if it is not going to solve the problem. 

Any ideas?

---

### Post by grier-devon on 2015-02-16
There are two things I would check, first off I would open the driver utility and see if you are missing any special drivers for your machine. Secondly I would open the "system log" and look for error's. The log's can be a little hard to read but with your software center failing you should see some error's in the "dpkg.log". If you are seeing any failures in the system log  post it so I can look through them.

---

### Post by heroquestelf on 2015-02-17
Actually, I gave up and tried another reinstall... it appears at least to have solved the problem.

---

