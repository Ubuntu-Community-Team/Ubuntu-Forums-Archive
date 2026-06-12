---
title: "Ubuntu 12.10 Software Center and Update Manager not working"
date: 2012-11-09
forum: General Help
---

### Post by VideoRoy on 2012-11-09
I have had lots of issues with one of my installs of Ubuntu 12.10 and have resolved most.

On one particular workstation I cannot run Software Center from the menu as it just never loads.  I see it try to start in the menu bar then just exits.

Update Manager is a similar problem as it never starts but puts a red alert in the indicator area saying there was a problem.

So here is what I have tried and done:
1. I can run Software Center from a terminal "sudo software-center" and it runs no problem.
2. I can run "sudo apt-get update" and "sudo apt-get upgrade" from terminal no problem.
3. I can run Synaptic Package manager and it works no problem.
4. I have uninstalled and reinstalled Software Center and Update Manager from Synaptic but they still do not work.

Very strange behavior altogether and my work around is just to use Synaptic or run commands from Terminal for now.  Also I finally just uninstalled Update Manager completely since it just kept throwing up the error message in the indicator constantly.

This was a fresh install from DVD even formatting over my partitions to try and eliminate any variables.

I have a laptop running the same version from the same DVD that works properly.

Any ideas?

---

### Post by dino99 on 2012-11-09
these tools are very buggy, use synaptic instead

---

### Post by VideoRoy on 2012-11-09
> **dino99 said:**
> these tools are very buggy, use synaptic instead

No problem using Synaptic, that is my fallback.  Personally this is the first time I have had issues with these tools on any computer through quite a number of installs and generations.

12.10 is a mess in a lot of areas and may have to go back to 12.04 LTS at least on this one workstation.

Thanks.

---

### Post by cwsnyder on 2012-11-09
Have you updated lately?  I used to have that problem (from Beta 1) and reported the bug, but it is working for me now on Lubuntu 12.10.  The problem seemed to be that the menu was not asking properly to be run as root.

---

### Post by VideoRoy on 2012-11-10
> **cwsnyder said:**
> Have you updated lately?  I used to have that problem (from Beta 1) and reported the bug, but it is working for me now on Lubuntu 12.10.  The problem seemed to be that the menu was not asking properly to be run as root.

Thanks for the reply.  

Yes system us up to date.  I actually reinstalled from scratch a number of times to see if I had something out of date or corrupted.  On my final install I reformatted all the partitions and then did all the updates manually.

Originally I had just upgraded the system from 12.04 and that actually was working better in some areas but not all.  I even installed Xubuntu Desktop on top of the clean install so I could move back and forth in case it was Unity related.

Everything seems to work fine except for just these 2 packages.  My netbook had altogether difference install issues but Software Center and Update Manager work fine there.

First time I have had this many issue install / package issues in years of installs that was not related to a hardware component incompatibility.

---

### Post by HiImTye on 2012-11-10
try
```
sudo chown -R $USER:$USER $HOME
```
and see if it fixes your problem

---

### Post by VideoRoy on 2012-11-12
> **HiImTye said:**
> try
```
sudo chown -R $USER:$USER $HOME
```and see if it fixes your problem

Thanks for the reply.

That did not solve my problem but it gave me an idea of what the problem was.  I was also thinking a rights problem but could not figure it out until I ran "software-center" at the terminal prompt without "sudo".  I had been running it with "sudo" without thinking and as soon as I ran as my regular user it showed and error message that it could not access my apt.conf file.

When I did this install I copied my old apt.conf and somehow I ended up as just "rw" rights for root without "r" for everyone else.  I just did a "chmod +r" and solved my problem.

For those that do not know apt.conf contains proxy settings to get through a firewall that both Software Center and Update Manager use.  Synaptic uses it as well but Synaptic requires root access right when you launch and after looking at the other apps they require root access only when you are going to perform an actions.

Thanks for the ideas here that got me past my mental block.

---

### Post by jzvbrt on 2013-02-23
> **VideoRoy said:**
> Thanks for the reply.

That did not solve my problem but it gave me an idea of what the problem was.  I was also thinking a rights problem but could not figure it out until I ran "software-center" at the terminal prompt without "sudo".  I had been running it with "sudo" without thinking and as soon as I ran as my regular user it showed and error message that it could not access my apt.conf file.

When I did this install I copied my old apt.conf and somehow I ended up as just "rw" rights for root without "r" for everyone else.  I just did a "chmod +r" and solved my problem.

For those that do not know apt.conf contains proxy settings to get through a firewall that both Software Center and Update Manager use.  Synaptic uses it as well but Synaptic requires root access right when you launch and after looking at the other apps they require root access only when you are going to perform an actions.

Thanks for the ideas here that got me past my mental block.


Hi VideoRoy, I have the same issue. Software center works from terminal  when sudo but freezes when run by click on the icon.  I didnt' quite  understand how you fixed the problem. Would you please write some  details? I'm new to Ubuntu and obviously not very familiar with the  procedures

---

