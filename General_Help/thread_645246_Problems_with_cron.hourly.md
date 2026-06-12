---
title: "Problems with cron.hourly"
date: 2007-12-19
forum: General Help
---

### Post by haines.justin on 2007-12-19
I have written a script and placed it in cron.hourly, but it is not being executed.  When I perform the command:
 ```
sudo run-parts --report /etc/cron.hourly
```
my script runs just as it should.  As far as I know, the above command is pretty much what the crontab does and should do the same thing...  anyone have any idea where my problem is?
I have checked /var/log/syslog and there are no errors, but Im not completely sure what it should look like...  here are the last few lines:
```
Dec 19 19:17:01 jhaines-desktop /USR/SBIN/CRON[9579]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 19 19:34:20 jhaines-desktop -- MARK --
Dec 19 19:54:20 jhaines-desktop -- MARK --
Dec 19 20:14:21 jhaines-desktop -- MARK --
Dec 19 20:17:01 jhaines-desktop /USR/SBIN/CRON[9657]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 19 20:34:21 jhaines-desktop -- MARK --
Dec 19 20:54:21 jhaines-desktop -- MARK --

```
Thanks in advance for any help!

---

### Post by HermanAB on 2007-12-19
Two possibilities:
1. You forgot to make the script executable.
2. You forgot to use the *full* path to the utilities called from the script.

Cheers,

Herman

---

### Post by capink on 2007-12-20
See if whether is running in the background

```
ps aux | grep cron
```

---

### Post by haines.justin on 2007-12-21
The script is executable here is cron.hourly's ls -l

```
jhaines@jhaines-desktop:/etc/cron.hourly$ ls -l
total 8
-rwxr-xr-x 1 root root 210 2007-12-19 01:15 ip
-rw-r--r-- 1 root root 212 2007-12-19 00:56 ip~

```

and all of the paths in the script are full...

Here is the output for ps aux | grep cron:

```
jhaines@jhaines-desktop:/etc/cron.hourly$ ps aux | grep cron
root      6042  0.0  0.0  20900   940 ?        Ss   Dec20   0:00 /usr/sbin/cron
jhaines   9279  0.0  0.0   5120   828 pts/0    S+   00:08   0:00 grep cron

```

It looks like the cron daemon is running, any ideas what I should do next?

Thanks for the help!

---

### Post by capink on 2007-12-21
What is the name of the script you have places in /etc/cron.hourly. Does it contain spaces or dots or any unusual character. I have heard that cron don't run some scripts if the filename contain certain characters. Try renaming the script and see if it works.

---

### Post by haines.justin on 2007-12-21
The script has been called "ip" all along... last night I made a simple test script to create a folder on my desktop and it has been firing off without fail, so it appears to be a problem with the script itself... So this is what Im trying to do:  I have a DSL router that is receiving a dynamic IP from my ISP that is set up to forward port 22 to my desktop.  I want to be able to SSH into my desktop when I am not at home.  The problem I am trying to solve is that I can't know what the current IP of the router is without already being logged in (chicken and egg thing...)  My solution was to write a script that will pull my ip off of www. whatismyip.org and send it to the UNIX server at my school.  I will put this script in cron.hourly so my IP will be updated fairy often.  This way if I discover my IP has changed and I can't connect to my computer, I will simply log in to the UNIX server and grab the new IP.

Its a little bit of a strange workaround, but the best thing I could come up with.  If anyone has any better ideas, I am definitely open to them.

My solution has two scripts, one in perl that pulls the info off the website and one shell script that sends the txt file.  The perl script is /home/jhaines/ipupdate/getip.pl and the shell script is at /etc/cron.hourly/ip

This is the perl:
```

#!/usr/bin/perl
use LWP::Simple;

my $response = get("http://www.whatismyip.org");
if ($response eq "" )                                            
{
        print "\nFAILURE attempting get page\n\n";
}
else
{
        print "$response\n";
}


```

and this is the shell script:

```
#!/bin/sh
/home/jhaines/ipupdate/getip.pl > /home/jhaines/ipupdate/ip.txt
pscp -batch -pw <password omitted> /home/jhaines/ipupdate/ip.txt jhaines@unix.andrew.cmu.edu:/afs/andrew.cmu.edu/usr1/jhaines
```

Now before people bite my head off, I know storing my password in a script is a bad idea security-wise.  I tried to set up an RSA pair for the server, but unix.andrew.cmu.edu is not set up to do it, so this was the next best option.  My desktop is physically secure in my apartment and I trust my roommates...

Please let me know if you see any problems with what I am trying to do.
Thanks,
Justin

---

### Post by haines.justin on 2007-12-22
bump

---

### Post by haines.justin on 2007-12-22
I made a recent helpful discovery.  The script previously had a line to delete the text file, but I removed that line, and now it produces a file.  The script successfully pulls the text off the webpage and stores it in the text file, the only problem is that the file does not get sent...  When I run the script by hand, it does send the file, anyone have any idea why using the cron daemon to run it would change anything?

---

### Post by lgambett on 2007-12-22
You should also check the permission for the script... Did you use the user crontab or the system wide /etc/crontab ?

---

### Post by haines.justin on 2007-12-22
The permissions for the script are 755 and it is in /etc/cron.hourly and I did not edit any of the crontabs.  What confuses me is that since the website is being queried and the text file being created, both scripts are being run, its just that the pscp line is not working when it is called by the daemon...

---

