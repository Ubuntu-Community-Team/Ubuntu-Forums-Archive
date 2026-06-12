---
title: "Set up a hourly cronjob to update my system"
date: 2008-05-08
forum: General Help
---

### Post by euthymos on 2008-05-08
Hi,

I wanted to make my system update itself every hour.
So I wrote a bash script with those simple lines:
apt-get update
apt-get upgrade
and put it under /etc/cron.hourly and fixed permissions so that it can be run

Well, I discovered that this is not enough, since my system is not actually updating every hour :D

What have I made wrong?

Thank you in advance

---

### Post by Monicker on 2008-05-08
Once an hour seems execessive to me. apt-get by default prompts you with yes or no before it actually installs anything.  You would need to add the -y option to have it proceed without user interaction.

Also, is this cron job running under the root account?  If not, you would have to deal with sudo and entering the password for that.


Personally, I like to at least see what the packages are before installing any updates.

---

### Post by bodhi.zazen on 2008-05-08
New users often update often. In my opinion you should update less often and security only unless there is some feature you need. Keep in mind, an opportunity to update is an opportunity to break Ubuntu.

I always look at the forums first and make sure there are no thread re: ubuntu breaks after recent update ....

I advise security updates only (disable the non-security repos) daily + system updates weekly.

Last, do not forget that kernel update require a reboot. You do not want you computer to boot without your permission, in the middle of doing some project do you ?

---

### Post by euthymos on 2008-05-09
> **bodhi.zazen said:**
> New users often update often. In my opinion you should update less often and security only unless there is some feature you need. Keep in mind, an opportunity to update is an opportunity to break Ubuntu.
Why?

[QUOTE=bodhi.zazen]I always look at the forums first and make sure there are no thread re: ubuntu breaks after recent update ....[/quote]
How can you do this? There are package updates almost every day...

[QUOTE=bodhi.zazen]Last, do not forget that kernel update require a reboot. You do not want you computer to boot without your permission, in the middle of doing some project do you ?[/QUOTE]
Yes, I do. This computer works like a download/upload daemon.

---

