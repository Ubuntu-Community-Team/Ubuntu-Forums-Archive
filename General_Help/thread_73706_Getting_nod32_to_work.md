---
title: "Getting nod32 to work?"
date: 2005-10-09
forum: General Help
---

### Post by dgermann on 2005-10-09
Hi--

I have been trying off and on for over a month to get nod32 (an anti-virus product from eset) to work on two Ubuntu 5.04 boxes.

I have some progress, but am stumped on some others.

1. Had eicar.com test virus in the root directory. It kept reporting it could not clean this virus. I added the -u delete option and that deleted it.

2. I can run the on-demand nod32 from command line, but it will not run from crontab. Here is my crontab file (I even added a couple blank lines at the bottom, because I remember one file saying it needed them):
```
 # cat /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
#

0 * * * * root /usr/sbin/nod32_update
# 0 3 * * * root 0 3 * * * root /usr/sbin/nod32 -l -z -c clean /* -/dev -/proc
0 3 * * * root 0 3 * * * root /usr/sbin/nod32 -lz -c clean -u delete --mail --boots --adware --unsafe /* -/dev -/proc







root@/etc/nod32 #

```

3. Shouldn't nod32 refer to the nod32.cfg file for its options, instead of having to put in all the options I have in the crontab file?

4. The nod32_update is not running.

5. It allowed me to download the eicar.com viruses from their website, so apparently the on access scanner is not working, either.

Any help you can offer on any or all of these. The tech guy is helpful but is probably getting a little tired of my linux questions and I am getting more and more "all versions of linux are different, and I am not familiar with Ubuntu" answers. So hopefull you gurus may have some things to try....

Thanks!

---

### Post by dgermann on 2005-10-10
Hi--

Well, I have solved part of it--

```

0 * * * * root /usr/sbin/nod32_update
# 0 3 * * * root 0 3 * * * root /usr/sbin/nod32 -l -z -c clean /* -/dev -/proc
0 3 * * * root 0 3 * * * root /usr/sbin/nod32 -lz -c clean -u delete --mail --boots --adware --unsafe /* -/dev -/proc

```

Previously I had not had "root" in the nod32_update line; adding it seems to have solved that update issue--one of the machines I have updated.

Then I saw that the 03 line had an extra "0 3 * * * root" in front of it, and removing that seemed to solve that issue--it at least ran at 3 am.

So, anybody any ideas on the remaining ones (3 and 5)?

---

### Post by Efwis on 2005-10-10
I'm presuming this is commented out for a reason.

```

# 0 3 * * * root 0 3 * * * root /usr/sbin/nod32 -l -z -c clean /* -/dev -/proc
```

looks to me that might go hand in hand with the on access cleaning. Just remove the # see what happens.

other than that I dunno. 
I'm curious as to why you want a antivirus program running, for the most part as long as you have a firewall running, software or hardware, there really is no need for it until Linux gerts more widespread. I know there are viruses out there for linux, but they are so far and few between its pretty much non-existant. so clam-av should do the trick nicely.
I also know you can download and install F-prot from the repos. just some thoughts there.

---

### Post by dgermann on 2005-10-11
Efwis--

Thanks for your help!

The line you quote is an extra--it amounted to a test to see if I could get it to run while I was sitting in front of the console. It did not, because of the extra "0 3 * * * root" So I commented it out to remind myself what I had done. A way of leaving breadcrumbs on the trail, I suppose....

As to using an anti virus, a couple of reasons: 1. One linux box I have this on solely runs backups from a Samba server. The server serves up files to Win95 boxes and one WinXP. So it has Windows files and if there is a virus there, it will affect five machines on my small business network, potentially.

2. Another Linux box I have this on will become a desktop machine for me, and a model for a desktop machine for another person. Those machines will run Win4Lin so we can run 2 or 3 essential legacy Win95 apps we rely on in our business--at least until we can transition to something in Linux that will work for us.

3. Adware is covered by this A-V, and that I suspect can affect browsers no matter what the platform. 

It sounds like you know some things about viruses and Linux. Am I on the right track here?

Thanks for your help, Efwis.

---

### Post by Efwis on 2005-10-11
[QUOTE=dgermann]
3. Adware is covered by this A-V, and that I suspect can affect browsers no matter what the platform. 

It sounds like you know some things about viruses and Linux. Am I on the right track here?

Thanks for your help, Efwis.[/QUOTE]
you are but there a couple of things to take into consideration with Ubuntu. 

[color=red]Please note not all Linux distros are the same, the information here is based on Ubuntu only.[/color]

First a little about myself, I spend countless hours in malware removal forums helping people on Windows environments get rid of all malware, whether its spyware, trojans, keyloggers, worms, spyware thats what I enjoy doing, too bad it doesn't pay :)

anyway onto the considerations I was going to talk about.[list]
A. With Ubuntu, unless you have made the system insecure by making Root the only user on the system, which is *not* default, spyware, adware, etc from a windows application will not take hold in the linux machine. 

B. Almost all of them are designed with ActiveX now as well as they are designed to enter unsuspecting machines through *KNOWN* Microsoft holes that they won't fix.

C. As with the information mentioned in B above, unlike Windows, Linux dev teams care about their work, when a Open source product has a security flaw found, it is fixed immediately.

D. The adware that Nod32 detects consists of tracking Cookies. this can be resolved by clicking on Tools>options>Cookies in Firefox. Next step to do is to set the "keep cookies" tab to "unitl I close Firefox". by doing that everytime you shut down FF it deletes the cookies and there will be no spyware on the system.
[/list]

You are not mistaken on wanting to make sure your machine is safe, there are Linux specific viruses and worms out there. But until Linux becomes more mainstream, like Windows, it won't be targetted as often as Windows. I'm not familiar with lin4win's setup, I dont' know if that opens root up to vunerabilities or not. I do know that as long as you don't run Ubuntu as a root user, you have nothing to fear.
for what it's worth, I have every possible security setting on my Windows drive set to protect my machine, I use Spybot: Search & Destroy and Adaware the only  tracking cookies they ever find are located in the IE directory, You never see one listed in the FF directory. Thats because FF doesn't have the known security flaws that IE has. As stated before, with the open source community, which Mozilla.org is part of, they take care of their products and close the holes asap.

HTH.

---

### Post by dgermann on 2005-10-11
Efwis--

Thank you.

In addition to that, I am not just trying to protect my Linux boxes from attack, but I have guessed that if there were a virus in a file on my Linux server and one of the Windows boxes got into it, it could be a problem. 

Thanks for your help here. I will have to bump the tech services guy at eset and see what he can do to help with the two remaining questions--he has not answered my e-mail of a few days ago yet.

---

### Post by jasmuz on 2005-10-11
What is your standpoint in the NOD32 vs ClamAV both for Linux and Windows?

---

### Post by Efwis on 2005-10-12
[QUOTE=jasmuz]What is your standpoint in the NOD32 vs ClamAV both for Linux and Windows?[/QUOTE]
My standpoint is simple, Nod32 is better then ClamAV. reasons being that the Nod32 definitions are much frequently updated then ClamAV from what I have seen. 
Also in a recent side by side comparisons of quite a few Anti virus software programs, Nod32 was #1 for all aspects of detection, removal, and prevention in an independant study. ClamAV was not in the list of the top 10 AV programs to use. As the list stands now here is how it broke down.

1. Nod32
2. Kaspersky
3. AVG 
4. F-prot
5. F-Secure
6. Norton
7. Mcafee
8. Etrust EZ antivirus
9. bitdefender pro
10. Panda

Hope this helps. Personally just because I purposely go out and try to find malware for my research in the forums, I use F-prot on my box.

---

### Post by dgermann on 2005-10-12
Efwis--

Interesting, and heartening, study results.

Could you tell us where we might see more of this study, please?

Thanks Efwis!

---

### Post by Efwis on 2005-10-13
[QUOTE=dgermann]Efwis--

Interesting, and heartening, study results.

Could you tell us where we might see more of this study, please?

Thanks Efwis![/QUOTE]
sure, I need to contact an acqauintance of mine in the chat rooms I frequent, hopefully  he remembers where it is. it was on his site, I pulled my info from my IRC log of that chat session. I'll post back after I get the link.

I forgot to mention, I use AVG on my Windows install, and I am going to contact Grisoft about making a Linux compatible version of it.

---

### Post by dgermann on 2005-10-13
Efwis--

Great! I will look forward to hearing from you.

---

