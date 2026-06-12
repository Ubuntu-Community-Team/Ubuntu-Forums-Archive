---
title: "Software Updater - Package Operation Failed"
date: 2016-05-21
forum: General Help
---

### Post by wagb278 on 2016-05-21
The last few times running Software Updater have ended with the message: “**Package Operation Failed - The installation or removal of a software package failed.**”  I get the same error message when I install software via the Ubuntu Software Center.  

I am running Ubuntu-MATE 16.04 LTS (64-bit).

Today I tried sudo apt-get update and then upgrade to see what could be causing my problem.  Terminal session is in the attached file.  It looks like there are errors near the end of the upgrade operation, but I have no clue what those errors mean and how to fix them.  Can someone provide help on how to resolve those errors? - Which I hope will also fix the Software Updater error. 

Errors reported by apt-get upgrade I noticed are: 
```
Setting up postfix (3.1.0-3) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: misplaced delimiter: Green..actdsltmp
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: Green..actdsltmp
dpkg: error processing package postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
Setting up udev (229-4ubuntu5) ...
addgroup: The group `input' already exists as a system group. Exiting.

```

Thanks in advance for any suggestions

---

### Post by RobGoss on 2016-05-21
Hello and welcome, Try changing the server from which you receive the system down you can do this by accessing **Software & updates**, you'll see a link from the drop-down menu **choose other,** then choose **select best server.** It will search for the best server in your area save and that should work

---

### Post by vasa1 on 2016-05-21
Run```
dpkg -l | grep ^..r
```to confirm which package is broken. You could also try ```
sudo dpkg -C
``` 

Then run
[s]```
sudo apt-get -f update
```and[/s]```
sudo apt-get install --reinstall postfix
```if *postfix* was the broken package.

Before running the *reinstall* command, you may want to run```
sudo apt-get clean
```to eliminate the unlikely chance that the corresponding .deb, if still present in */var/cache/apt/archives*, is damaged.

---

### Post by wagb278 on 2016-05-21
Thanks both for the replies.  I tried both suggestions. 

RobGoss - I did as you suggested and it selected a different server.  Maybe that will help with future Software Updates.

vasa1 - the dpkg -C command reported that package "postfix" is only partially configured. But I was not able to resolve that - see attached record of my actions. Should I try to remove that package or do something else. 

Thanks again.

---

### Post by RobGoss on 2016-05-21
> **wagb278 said:**
> Thanks both for the replies.  I tried both suggestions. 

RobGoss - I did as you suggested and it selected a different server.  Maybe that will help with future Software Updates.

vasa1 - the dpkg -C command reported that package "postfix" is only partially configured. But I was not able to resolve that - see attached record of my actions. Should I try to remove that package or do something else. 

Thanks again.


Did you run the software updater to see if you get any errors?

---

### Post by wagb278 on 2016-05-21
RobGoss - Yes, After changing servers the Software Updater application now reports the Software is up to date on this computer.  I'm holding off declaring total success until I get notice of an update from Ubuntu and it performs the update successfully.  There seems to be a corrupt or miss-configured 'postfix' package still hanging around my system.

---

### Post by RobGoss on 2016-05-21
> **wagb278 said:**
> RobGoss - Yes, After changing servers the Software Updater application now reports the Software is up to date on this computer.  I'm holding off declaring total success until I get notice of an update from Ubuntu and it performs the update successfully.  There seems to be a corrupt or miss-configured 'postfix' package still hanging around my system.


Yes it should be ok after changing servers I have trouble sometimes with the servers but for the most part it always seems to work once I change to another. best of luck and I hope it works for ya :)

---

### Post by vasa1 on 2016-05-22
Sorry about the *sudo apt-get -f update* bit. It is nonsense. I don't remember where I got it from :(

---

