---
title: "Cannot install desktop or many other get-apt items"
date: 2015-01-15
forum: General Help
---

### Post by ddemers on 2015-01-15
I installed server 12.04, but I am not able to install the desktop

I tried sudo apt-get install ubuntu-desktop  then I get a super long list of items I dont have and it fails.

What can I do to resolve this?

---

### Post by oldos2er on 2015-01-15
Please post all the output from *sudo apt-get install ubuntu-desktop* so we can see exactly what's failing.

---

### Post by ddemers on 2015-01-15
i can take a picture with my phone I guess... All I have is a command line and not sure how to get the text from there to my notebook to post.

Server is rebooting now, will do that when it comes back up.  Is it possible that I just need to mount the CD rom or something?   Its been years since I have dealt with Linux, if I remember correctly basic things liek floppy/CDroms needed to be enabled before being usable?

---

### Post by ddemers on 2015-01-15
[https://www.dropbox.com/sh/xu5dk8u2p3wkcsy/AAApa2o5WuTXYN4llMPc7czka?dl=0](https://www.dropbox.com/sh/xu5dk8u2p3wkcsy/AAApa2o5WuTXYN4llMPc7czka?dl=0)

I took 2 pictures, the start and finish

---

### Post by Holger_Gehrke on 2015-01-15
You have some packages set on 'hold'. Use 'apt-mark showhold' to find out which those are, then 'apt-mark unhold <packages>' (replace <packages> with the package names) to reset that state for them.

---

### Post by ddemers on 2015-01-15
when I run that command it doesn't output anything.

I re-installed the OS just in case I had done something wrong.  and I have the same issue.

I also did a apt-get upgrade.  this didnt seem to fix anything, but it did take sometime to upgrade.

---

### Post by ddemers on 2015-01-15
Actually I cannot install anything on this machine...  I tried sudo apt-get install openssh-server  and it tells me it needs dependencies

---

### Post by ddemers on 2015-01-15
[http://askubuntu.com/questions/265007/ubuntu-12-04-why-does-apt-get-update-fail](http://askubuntu.com/questions/265007/ubuntu-12-04-why-does-apt-get-update-fail)   Found this post which seems to have resolved my issue.

While researching the SSH installation issue I came across some steps which pointed me to another issue, which got me to that link!

thanks for your time.

---

