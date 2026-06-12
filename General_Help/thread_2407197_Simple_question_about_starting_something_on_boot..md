---
title: "Simple question about starting something on boot."
date: 2018-11-30
forum: General Help
---

### Post by dissolution on 2018-11-30
I am running Ubuntu 18.04.1 LTS in a VM.    Currently it is running Grafana, Telegraf, and Influxdb

It is all working and the monitoring is awesome, but I am having an issue when it reboots (forgive me as I am a noob and have been searching the internet and forums for 2 days on this)

When it boots and tries to grab influxdb.service it does not work.  however, if I stop this and run sudo influxd in the terminal everything starts running perfectly.

I have been trying to figure out how to open a terminal and run this command (influxd) automatically.  I added @reboot influxd in the root crontab and that didn't work.   I have also tried adding rc.local giving it +X permissions but that doesn't seem to work either.

I'm sure this is super simple but if anyone can give me a hand that would be awesome. Thanks

---

### Post by TheFu on 2018-12-01
I know ZERO about those programs/daemons. ZERO.  Actually haven't heard of them before, but I've been around a long time, so perhaps this reply will be helpful.

Sounds like some environment variables aren't being setup in the "service" and cron setups that your interactive account does setup.  This is a common issue for everyone, not just noobs.

To prove my guess, try 2 exercises. Open 2 terminals, 1 and 2. Then
1) sudo -i ; influxd     
I bet this fails to work. There should be some output explaining the problem.
Stop the influxd daemon. This is very important.  Only 1 program at a time can grab a socket.

2) sudo -s ; influxd
I bet this does work.

So, what is the difference between -i and -s options to sudo?  The sudo manpage is useful:

```
     -i, --login
                 Run the shell specified by the target user's password database entry as a login
                 shell.  This means that login-specific resource files such as .profile or .login
                 will be read by the shell.  If a command is specified, it is passed to the shell for
                 execution via the shell's -c option.  If no command is specified, an interactive
                 shell is executed.  sudo attempts to change to that user's home directory before
                 running the shell.  The command is run with an environment similar to the one a user
                 would receive at log in.  The Command environment section in the sudoers(5) manual
                 documents how the -i option affects the environment in which a command is run when
                 the sudoers policy is in use.

     -s, --shell
                 Run the shell specified by the SHELL environment variable if it is set or the shell
                 specified by the invoking user's password database entry.  If a command is speci-
                 fied, it is passed to the shell for execution via the shell's -c option.  If no com-
                 mand is specified, an interactive shell is executed.
```

The short answer is
-s <--- uses the userid's environment running the sudo command - thefu
-i <--- uses the userid's environment that the sudo command runs under - root

Linux and all Unix-like OSes are multi-user from the ground up. Always remember that.  Every process has an environment which is based on the parent process setup and the userid running it.  cron has very little environment since it is all set pre-login.  sudo being run later, usually interactively, means more environment settings are inherited.  Things like the HOME directory are set, which aren't setup in either service startups or under many versions of cron.

So what is the fix?   Setup the necessary environment variables for the start/stop of the daemon. This is commonly done by having a script to setup the necessary variables which will be inherited by the daemon process.  In theory, the installation guides for each of those tools will spell out all the required environment variables.  In theory.

Complicated services must be configured before use on Linux.  Just doing the install is not enough.

Anyway, hope this is helpful.

---

### Post by HermanAB on 2018-12-01
My first question:
If you want to run a database, why do you reboot?  Leave the machine running.

---

### Post by TheFu on 2018-12-01
I don't know which set of instructions were followed. Found this:
[https://computingforgeeks.com/install-influxdb-on-ubuntu-18-04-and-debian-9/](https://computingforgeeks.com/install-influxdb-on-ubuntu-18-04-and-debian-9/) seems to have links for setting up the entire system you want.  I didn't see anything too funny in those instructions. I cannot say that site is reputable for providing solutions, though I didn't see anything bad in the skimming of the articles read.

Take a look at the system log files.  There should be something inside which helps. The logs are almost always good to find errors.

---

### Post by yancek on 2018-12-01
You could also try entering the full path to the influxd executable command in crontab rather than simply:  sudo influxd

---

### Post by dissolution on 2018-12-01
I am running this in a homelab, so due to the odd power outage in my house etc sometimes things reboot. Otherwise I'll leave it running.   

So I ran both commands and go the following output.. I couldn't get the service stopped after the first one and had to reboot.

user@grafana:!# sudo -i; influxd
user@grafana:!#




user@grafana:!# sudo -s; influxd
user@grafana:!#

The odd thing is, after the second I ran another reboot and I noticed it was running now.. I tried a few more reboots and success.. So I guess my issue is fixed.  Are these commands persistent after a reboot?  Or did my 2 days of screwing around actualy change something and now it's working?

Either way thank you guys for the knowledge and help. I'm a VMware/SAN/Windows guy but am thinking about going full linux to avoid reinstalls my homelab due to licences.

!!!EDIT

After looking again  i see"@reboot influxd" in crontab   I ran "sudo crontab -e" to put it in there so I am assuming it is being run as root..  I don't know why it wasn't working before though and now it is.

Thanks again

---

### Post by TheFu on 2018-12-01
crontab doesn't have much environment. The PATH is small and probably doesn't include things you need. As 
yancek suggests, fully specifying the path to the program is highly recommended.  In short, NEVER trust the PATH inside any crontab.  
**which influxd** will tell you the answer for that program.

The sudo commands are 1 time and forgotten.  The ones provided didn't do anything permanent.

---

### Post by freemedia2018 on 2018-12-01
> **dissolution said:**
> I am running this in a homelab, so due to the odd power outage in my house etc sometimes things reboot. Otherwise I'll leave it running. 

Don't take this the wrong way, I live on modest means so I understand what it sounds like when someone suggests throwing money at a problem. That said, I've never met anybody who said "I wish I hadn't purchased that UPS." 

The solution to this problem is software configuration. But as a side-suggestion, it could extend the life of your equipment and the integrity of your file system.

---

### Post by TheFu on 2018-12-01
> I've never met anybody who said "I wish I hadn't purchased that UPS." 

+1. After $400 in fried components, I saw the light and started with a single 500VA UPS.  That was a very long time ago. 

Now my home/office has (2) 1500VA UPSes. I can't imagine connecting a computer to power without a UPS.

---

### Post by dissolution on 2018-12-01
Thanks for the tip. I had a surge a few months back from a down powerline that took out a treadmill and blew a few things in the house.  I think a ups is on the short list for things to buy also.. plus in those little power blips it can save time rebooting or things crashing.        I have  a bunch of surge protectors on order too.

---

