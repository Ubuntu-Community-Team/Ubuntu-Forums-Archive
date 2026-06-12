---
title: "Error Message - A problem occured when checking for the updates"
date: 2017-07-09
forum: General Help
---

### Post by Alan5127 on 2017-07-09
Hi All,

I am getting an error message (via a 'stop sign' at the top of my screen to the left of the networking, sound, date, and settings icons) that, when I click on it, says:

'A problem occured when checking for the updates'

If I run the 'Software Updater' it successfully checks and says I have no updates required (reporting that 'The software on this computer is up to date').

I have also run the following from the command prompt:

```
sudo apt-get clean && cd /var/lib/apt && sudo mv lists lists.old_`date '+%Y%m%d_%H%M'` && sudo mkdir -p lists/partial && sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade
```

which also runs without any errors and reports that nothing needs to be updated.

I have rebooted a few times, but the error icon always re-appears.


*Question*

How can I track down the cause of the error message?



Thanks,

Alan.

---

### Post by Bucky Ball on 2017-07-10
Try these commands and please post back any errors it outputs, if any.
```

sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

Run them one at a time, not concurrently, so we can see which commands throw which errors, if they do. 

Always include the release and flavour of Ubuntu you are using when posting for support. It will help things along and save a bit of time. ;)

What are you using?

---

### Post by Alan5127 on 2017-07-11
Hi Bucky Ball,

> **Bucky Ball said:**
> Try these commands and please post back any errors it outputs, if any.

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

Run them one at a time, not concurrently, so we can see which commands throw which errors, if they do. 


```


username@machinename:/var/lib/apt$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```


```


username@machinename:/var/lib/apt$ sudo apt update
Hit:1 http://nz.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://nz.archive.ubuntu.com/ubuntu xenial-updates InRelease                                                                                                                                           
Hit:3 http://archive.canonical.com/ubuntu xenial InRelease                                                                                                                                                   
Get:4 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]                                                                                   
Hit:5 http://ppa.launchpad.net/obsproject/obs-studio/ubuntu xenial InRelease     
Hit:6 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial InRelease  
Ign:7 https://mega.nz/linux/MEGAsync/xUbuntu_16.04 ./ InRelease
Get:8 https://mega.nz/linux/MEGAsync/xUbuntu_16.04 ./ Release [988 B]
Fetched 103 kB in 3s (27.1 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.


```


Query:  If I run <sudo apt full-upgrade> will that move the machine from 16.04LTS to some later version?  If so, I would rather not do that, as I would prefer to stay on LTS only.


> **Bucky Ball said:**
> 
Always include the release and flavour of Ubuntu you are using when posting for support. It will help things along and save a bit of time.

What are you using? 

Apologies.  I am running Ubuntu 16.04LTS - which appears to also be called 'Xenial' and / or 'Xenial Xerus' in various places just to add to my confusion :-)



Thanks for your assistance.  If it is 'safe' to run <sudo apt full-upgrade>, let me know, and I'll do that too.

Alan.

---

### Post by Bucky Ball on 2017-07-12
No, 'sudo apt full-upgrade' will NOT upgrade the release, just the software in it. I would never give you a command that would change the whole release without warning you that this would happen. :) (I only use LTS releases so I totally understand where you're coming from and good that you confirmed. Better to ask when unsure.)

I will mention that the full-upgrade command WILL upgrade the machine from 16.04.1 to 16.04.2 if you're not there already. If you don't want that, you have been warned. ;)

The good news is that the update produced no errors. Try the next one, considering previously mentioned, and see what that throws.

(PS: Yep, 'Xenial' or 'Xenial Xerus' = 16.04 LTS. A release name and number is always used. Some commands only give one or the other which, as you mention, does make things a bit confusing. You can use 'uname -a' and 'lsb_release -a' to check for info.)

---

### Post by Alan5127 on 2017-07-12
Hi Bucky Ball,

> **Bucky Ball said:**
> No, 'sudo apt full-upgrade' will NOT upgrade the release, just the software in it. I would never give you a command that would change the whole release without warning you that this would happen. :)

I'm sure you wouldn't - it was just an abundance of caution on my part.  No offence intended.



> **Bucky Ball said:**
> The good news is that the update produced no errors. Try the next one and see what that throws.

I ran that command too, and nothing untoward seems to have happened:

```


username@machinename:/var/lib/apt$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```


I have rebooted a nunmber of times, and still getting the 'stop sign' with the same error message as per my OP.


What do you think would be the next step to diagnose?

Thanks again,

Alan.

---

### Post by Bucky Ball on 2017-07-12
Good question as it appears there is nothing amiss from your update/upgrade commands. There are no errors, so it is an anomaly, which is, in a way, a good thing. The machine is not misbehaving in any other way?

PS: I added a few bits to my previous post prior to seeing yours. Might be of interest.

---

### Post by Alan5127 on 2017-07-12
Hi Bucky Ball,

> **Bucky Ball said:**
> Good question as it appears there is nothing amiss from your update/upgrade commands. There are no errors, so it is an anomaly, which is, in a way, a good thing. The machine is not misbehaving in any other way?

No - there are no other symptoms (as far as I know).

Is there any kind of command akin to:

sudo check_everything_on_this_machine_for_errors

that I can run?  I guess not, but you never know.  Perhaps a list of checks that I should run (in addition to the ones you suggested up front)?

Not sure if makes any difference, but if I click on the 'stop sign', it shows the error message.  If I then select 'Show updates' from the sub-menu that also appears, I get the normal (Software Updater) dialogue box that states 'The software on this computer is up to date'.


> PS: I added a few bits to my previous post prior to seeing yours. Might be of interest.

Brilliant.  I am wondering if I should replace 'sudo apt-get upgrade' with 'sudo apt full-upgrade' in my string of commands that I run periodically to check all is up to date (see my OP)?  I would never be concerned about going from, say, 16.04.1 to 16.04.2 - in fact, I would pretty much always make that change as soon as it comes out, and it seems that 'full-upgrade' does a more thorough check that just 'upgrade', but perhaps there is some downside that I am not seeing?

Thanks,

Alan.

---

### Post by Alan5127 on 2017-07-12
Hi Bucky Ball,

I just tried out 'uname -a' and 'lsb_release -a'.  The first one gave this:

```


Linux machinename 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:25 UTC 2017 i686 i686 i686 GNU/Linux


```


However, I got an error from the second one:

```


username@machinename:/var/lib/apt$ lsb_release -a
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/lsb_release.py", line 32, in get_distro_info
    csvfile = open('/usr/share/distro-info/%s.csv' % origin.lower())
FileNotFoundError: [Errno 2] No such file or directory: '/usr/share/distro-info/debian.csv'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/bin/lsb_release", line 25, in <module>
    import lsb_release
  File "/usr/lib/python3/dist-packages/lsb_release.py", line 51, in <module>
    get_distro_info()
  File "/usr/lib/python3/dist-packages/lsb_release.py", line 35, in get_distro_info
    csvfile = open('/usr/share/distro-info/debian.csv')
FileNotFoundError: [Errno 2] No such file or directory: '/usr/share/distro-info/debian.csv'


```


Could that be related to the update error, or should I start another thread to ask for help on that?


Thanks,

Alan.

---

### Post by Bucky Ball on 2017-07-12
Well, not sure if it's related. It may well be. One way or the other, it's a problem. You should be getting something like this:

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial
```

Yea, might be an idea to start a new thread (with an appropriate title) about the error that's thrown from the 'lsb_release -a' command. Add a link back to this thread from that new thread so things can tie together and a brighter spark than me may see some connection between the two.

We could be getting somewhere, though, although I didn't expect that command to throw an error! Was just passing on a handy command for you to use to get info in the future, but unexpectedly it may have provided a, or the, clue. ;)

---

### Post by Alan5127 on 2017-07-12
Hi Bucky Ball,

> **Bucky Ball said:**
> Yea, might be an idea to start a new thread (with an appropriate title) about the error that's thrown from the 'lsb_release -a' command. Add a link back to this thread from that new thread so things can tie together and a brighter spark than me may see some connection between the two.

We could be getting somewhere, though, although I didn't expect that command to throw an error! Was just passing on a handy command for you to use to get info in the future, but unexpectedly it may have provided a, or the, clue. ;)


I have started a new thread with the title:  'Error from lsb_release -a'

This is a link to that thread:

[https://ubuntuforums.org/showthread.php?t=2365934](https://ubuntuforums.org/showthread.php?t=2365934)

Let me know if you think of anything else I can try on the update issue in parallel to the 'lsb_release -a' thread.

Thanks,

Alan.

---

### Post by Alan5127 on 2017-07-13
Hi Bucky Ball,

The reinstall of 'lsb_release' as suggested in the other thread seems to have fixed that issue, and also resolved this one too, so I have marked that one as solved, and will mark this one as solved too.

Thanks for your help, and the suggestion which led to the solution.

Alan.

---

### Post by Bucky Ball on 2017-07-14
All good. Great news, great you marked threads solved and enjoy! ;)

---

