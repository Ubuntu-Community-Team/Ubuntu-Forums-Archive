---
title: "2 times possible intrusion/infection after latest kernel updates? - Ubuntu 24.04"
date: 2024-07-17
forum: General Help
---

### Post by jeantasse on 2024-07-17
--
Edit July 18 13h50  Thanks to everyone for their help and suggestions.  The problem is "not solved" per say, but through the suggestions I received, I have enough stuff to read and to try.  Thanks to the community!
--

Hello to all, hope everyone is having a good week up to now.  Starting with the latest kernel updates, 2 weird things happen to me. The first one was last week, I was just watching a video on Instagram when suddenly a window appears and ask my password to perform an operation(see the attached file).  I stopped everything and used Clonezilla to return to a backup  of the week before .  I did not go on my PC before yesterday, so when I connect I do all the security updates(including kernel updates), everything seems fine but later in the evening I was listening to music, my screen closes to save energy, when I come back I move the mouse for the screen to re-appear and there is a window telling me "tls certificate error", I did not have time to take a screenshot and I did not know what to look for in the process list.

Like I said, last week I used Clonezilla to restore my Ubuntu disk and did the same with Windows disk and just to be sure I re-flashed my bios because after the first incident, each time I was booting and it came to grub, my cpu fan was running abnormally fast like if there was an intense cpu workload.

I do not want to be paranoid but 2 weird things happening like that after kernel updates is starting to remind me of the "YZ" backdoor problem we had in April. I am not saying that it's that(XZ), but I am wondering if someone did something similar to the kernels. 

Did something like that happen to anyone else in the last 2-3 weeks?

Should I be posting this in the security section?

Cheers

---

### Post by #&amp;thj^% on 2024-07-17
Nothing like that has happened here.

Just to help with your fear on the XZ, ....only if you used during the 24.04 noble *proposed* xz package at that time.

But now all is patched.
My Old eyes can't make out what your screenshot shows...:(

---

### Post by &amp;KyT$0P# on 2024-07-17
> **1fallen said:**
> My Old eyes can't make out what your screenshot shows...:(

1fallen, it shows what looks like a GNOME PolicyKit type password authentication prompt, which says "Authentication is required to perform file operations".

I was able to produce this (or at least very very similar looking) by navigating to [FONT=monospace]admin:///[/FONT] in Thunar and then authorizing starting gvfs-admin.

Never seen this before, certainly hasn't happened spontaneously here.

---

### Post by jeantasse on 2024-07-17
Hello 1fallen thank you for taking time to look into this, I think I messed up with the attached file, but for the "XZ" I did not use any old Ubuntu 24.04 beta or proposed package for the XZ. I was simply saying that I am worried that something similar to this could have infiltrated the kernel, but I am not a security expert.
[ATTACH=CONFIG]293978[/ATTACH]

---

### Post by #&amp;thj^% on 2024-07-17
> **halogen2 said:**
> 

Never seen this before, certainly hasn't happened spontaneously here.

Yep I would expect that:
```
thunar  admin:/// 
```
Thanks halogen2

I do wonder though if "last" shows anything useful
```
last
me       tty7         :0               Wed Jul 17 12:10    gone - no logout
reboot   system boot  6.8.0-31-generic Wed Jul 17 12:09   still running
me       tty7         :0               Wed Jul 17 10:04 - 12:08  (02:04)
reboot   system boot  6.8.0-31-generic Wed Jul 17 10:03 - 12:09  (02:05)
me       tty7         :0               Tue Jul 16 18:33 - 18:46  (00:12)
reboot   system boot  6.8.0-31-generic Tue Jul 16 18:33 - 18:46  (00:12)
me       tty7         :0               Tue Jul 16 18:22 - 18:32  (00:10)
reboot   system boot  6.8.0-31-generic Tue Jul 16 18:03 - 18:32  (00:29)

wtmp begins Tue Jul 16 18:03:38 2024

```

However anything from a browser wanting those permissions is just a plain "NO" here. :)
Unless logging in to a trusted site period.

---

### Post by oldfred on 2024-07-17
Do you have automatic updates on?
Some updates are considered as new files & require password.

I only manually update with script that runs updates & housecleaning, so can see exactly what file is asking for password & that is is part of an update. If file is not part of update then it may be an issue. 

Did you click on some phishing email? Most only run Windows .exe files that do not work in Linux both as Windows exe and as missing password to run.

---

### Post by jeantasse on 2024-07-17
Hello halogen2, thank you for taking time to look at my case.  I never experience something similar in the past with Ubuntu distros or more precisely Ubuntu 22.04, that is why I find it strange and I am a bit worried. 
Here is the screenshot, hopefully I did not messed up this time:
[ATTACH=CONFIG]293979[/ATTACH]

---

### Post by #&amp;thj^% on 2024-07-17
> **jeantasse said:**
> Hello 1fallen thank you for taking time to look into this, I think I messed up with the attached file, but for the "XZ" I did not use any old Ubuntu 24.04 beta or proposed package for the XZ. I was simply saying that I am worried that something similar to this could infiltrated the kernel, but I am not a security expert.
[ATTACH=CONFIG]293978[/ATTACH]

Not here....at times I have to go to the dark web to have a peek, and I've never or would never allow any permissions or unknown logins.

I suggest you run some system audits, search and you find many ways to scan your system.

What about the "last" command, anything strange there?

---

### Post by jeantasse on 2024-07-17
It was a legitimate website, I went there before on Linux with the same browser and it never happened, it just happened that "I was doing that" while it happened and of course I said no.  But something on my system wanted permission to act on a "super user" level, that is the thing I do not understand. For last week prompt it's too late, but I will try to check that today for yesterday "tls security error", thanks again :)

---

### Post by jeantasse on 2024-07-17
Hello oldfred, thank you for your time.  Ubuntu Pro is enable but I chose when to install the updates, which is everyday right after I login, same with snap.  
The only thing a bit out of the ordinary that I do is that I update packages like for example "file roller" that is fileroller-versionXXX to fileroller-versionXXX-ubuntu-1 that are mention/proposed via "apt" that comes from Ubuntu official repo, that I install in synaptic package manager.  

I do not have the "developer" proposed updates enable since it's my working environment and I want it to stay stable.  I do not have flatpak enable, I install only via snap or apt/synaptic.

As for clicking on a "unknow" email link, I never do that.  One thing different that I do is that I have a folder with Firefox inside that cannot be opened unless I unlock a specific container, separate from the official Firefox via snap, that I use only for my emails, Instagram or Facebook, never anything else, and _no clicking external links_ or surfing outside of these specific websites.

---

### Post by jeantasse on 2024-07-17
The funniest thing is that I was about to install Chkrootkit because of last week incident lol I will do that now but if I was infected by something, I will delete my old Clonezilla backups and start fresh. For the "last" command I only learned about it like a week ago and I did not think about it. I was away from Linux for a couple of years and before that I never had to review command lines, do an inspection of process or anything alike.  I had ClamAV and Chkrootkit installed and everything was always ok

---

### Post by ajgreeny on 2024-07-17
Why do you believe that you need ClamAV and Chkrootkit installed, and presumably run occasionally?
I suspect you will find few if any users of a normal desktop version of any of the 'buntu family of OSs would recommend either of them as being necessary though this may be different if you run a mail server supporting users of Windows machines when ClamAv might be considered.

I have never in my 19 years of using Ubuntu or any of the other 'buntu OSs used ClamAv or Chkrootkit but I admit to never running a WAN server of any kind though I do run a LAN media server to my own smartTV but never over the open network.

---

### Post by #&amp;thj^% on 2024-07-17
> **ajgreeny said:**
> Why do you believe that you need ClamAV and Chkrootkit installed, and presumably run occasionally?
I suspect you will find few if any users of a normal desktop version of any of the 'buntu family of OSs would recommend either of them as being necessary though this may be different if you run a mail server supporting users of Windows machines.

I have never in my 19 years of using Ubuntu or any of the other 'buntu OSs used ClamAv or Chkrootkit but I admit to never running a WAN server of any kind though I do run a LAN media server to my own smartTV but never over the open network.

+100, That's not really an audit I would need to run, Nicely put ajgreeny.

Here are a few of the many many tools:
```
Suggested packages:
  apt-listbugs  debsums   samhain  fail2ban   gksu             | ktsuss
  debsecan      tripwire  aide     menu-l10n  | kde-cli-tools lynis

```
```
apt policy lynis
lynis:
  Installed: 3.1.1-1
  Candidate: 3.1.1-1
  Version table:
 *** 3.1.1-1 500
        500 http://us.archive.ubuntu.com/ubuntu oracular/universe amd64 Packages
        100 /var/lib/dpkg/status

```
```
apt show lynis
Package: lynis
Version: 3.1.1-1
Priority: optional
Section: universe/utils
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Marc Dequènes (Duck) <Duck@DuckCorp.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 1,675 kB
Depends: e2fsprogs
Recommends: menu
Suggests: dnsutils, apt-listbugs, debsecan, debsums, tripwire, samhain, aide, fail2ban
Homepage: https://cisofy.com/lynis/
Download-Size: 227 kB
APT-Manual-Installed: yes
APT-Sources: http://us.archive.ubuntu.com/ubuntu oracular/universe amd64 Packages
Description: security auditing tool for Unix based systems
[B] Lynis is an auditing tool for hardening GNU/Linux and Unix based systems.
 It scans the system configuration and creates an overview of system information
 and security issues usable by professional auditors.
 It can assist in automated audits.
 .
 Lynis can be used in addition to other software, like security
 scanners, system benchmarking and fine-tuning tools.[/B]


```

---

### Post by currentshaft on 2024-07-17
> **jeantasse said:**
> Hello to all, hope everyone is having a good week up to now.  Starting with the latest kernel updates, 2 weird things happen to me. The first one was last week, I was just watching a video on Instagram when suddenly a window appears and ask my password to perform an operation(see the attached file).  I stopped everything and used Clonezilla to return to a backup  of the week before .  I did not go on my PC before yesterday, so when I connect I do all the security updates(including kernel updates), everything seems fine but later in the evening I was listening to music, my screen closes to save energy, when I come back I move the mouse for the screen to re-appear and there is a window telling me "tls certificate error", I did not have time to take a screenshot and I did not know what to look for in the process list.

Like I said, last week I used Clonezilla to restore my Ubuntu disk and did the same with Windows disk and just to be sure I re-flashed my bios because after the first incident, each time I was booting and it came to grub, my cpu fan was running abnormally fast like if there was an intense cpu workload.

I do not want to be paranoid but 2 weird things happening like that after kernel updates is starting to remind me of the "YZ" backdoor problem we had in April. I am not saying that it's that(XZ), but I am wondering if someone did something similar to the kernels. 

Did something like that happen to anyone else in the last 2-3 weeks?

Should I be posting this in the security section?

Cheers

You are being overly cautious. None of the behaviors you described indicate any compromise. Run "sudo lsof -Pni" to check for network listeners, "ps -ef" to see running processes and check /var/log/ for privileged user actions if you want some basic peace of mind though.

---

### Post by jeantasse on 2024-07-18
Sorry for the wait, for the last command, my output is similar to you, it's either me, reboot or shutdown all the way from the month of may.  Thanks for the suggestion ;)

---

### Post by jeantasse on 2024-07-18
Hello currentshaft, thank you for taking time to look at this. I will take note of your suggested command lines and take a look at the results.  Yesterday I installed and ran Chkrootkit, the results are in the 2 images that I have attached.  But one thing I do not understand is why suddenly my password is asked to perform a task while I am simply watching a video and why I have a tls error window popping out of nowhere.  I have use Linux for many years(as a user not a professional) and I have never experience things like that in the 3 different distros I have used.

Again thanks, I will take a look at that.

---

### Post by jeantasse on 2024-07-18
Hello ajgreeny, thank you for taking time to answer.  I did this years ago because I was coming from Windows like a lot of us.  I was doing this as prevention to avoid transferring Windows virus infected files that I was receiving and transferring to friends/family or work related.  For chkrootkit again I did not understand everything Linux wise years ago.  Since with Windows you have an antivirus and some kind of protection for rootkits, I wanted to keep an eye on that.  I was not going to use Chkrootkit anymore but because of those weird things happening, I installed it ran some tests and this came out.  I know that some of those files are false positive, it happened to me in the past, but still, I wanted to check.

---

### Post by jeantasse on 2024-07-18
Thank you for all of those suggestions, I will look into it. And for Chkrootkit and ClamAV, I did this years ago because I was coming from Windows like a lot of us. I was doing this as prevention to avoid transferring Windows virus infected files that I was receiving and transferring to friends/family or work related. For chkrootkit again I did not understand everything Linux wise years ago. Since with Windows you have an antivirus and some kind of protection for rootkits, I wanted to keep an eye on that. I was not going to use Chkrootkit anymore but because of those weird things happening, I installed it ran some tests and this came out. I know that some of those files are false positive, it happened to me in the past, but still, I wanted to check.

---

### Post by jeantasse on 2024-07-18
Thanks to everyone for the help.  Yesterday I install and ran Chkrootkit, the results are in the 2 images that I have attached. I do not want to be paranoid, but one thing I do not understand is why suddenly my password is asked to perform a task while I was just watching a video and why I have a tls error window popping out of nowhere. I have use Linux for many years(as a user not a professional) and I have never experience things like that in the 3 different distros I have used.  I am aware that in those results there is a possibility of false positive, but still here they are.

So again, thanks to everyone, I have a lot of things to to read and a lot of things to try. If things does not seem to be clear enough for me, I will just re-install from scratch to just be able to go on with my work.

Thanks to the community!

---

### Post by currentshaft on 2024-07-18
> **jeantasse said:**
> Thanks to everyone for the help.  Yesterday I install and ran Chkrootkit, the results are in the 2 images that I have attached.

There's no indication of compromise in them.

> **jeantasse said:**
> I do not want to be paranoid, but one thing I do not understand is why suddenly my password is asked to perform a task while I was just watching a video

Could be for a variety of reasons, for example apport trying to submit a diagnostic report about a background service that crashed. Check journalctl output next time you see it. Again, I would not worry about it.

> **jeantasse said:**
> and why I have a tls error window popping out of nowhere.

Probably due to system time being incorrect. No one knows unless you provide more specific details.

> **jeantasse said:**
> 
I have use Linux for many years(as a user not a professional) and I have never experience things like that in the 3 different distros I have used.  I am aware that in those results there is a possibility of false positive, but still here they are.

If you're worried about system security, there are better uses of your time and resources.

---

### Post by TheFu on 2024-07-18
If you are compromised, running tools on the same system using the same installed OS is never a way to know.  Boot from an ISO, install any rootkit detector, if you feel strongly about this and have it scan the connected storage.  I doubt anything will be found.  Most of the rootkit search tools have many false positives, so plan to look up each report and see what the false positives for it look like.

My #1 security tool is versioned backups.  If I thought a system were compromised recently, I'd compare all the files on the current system with all the files from prior "known clean" backup.  Any files that are different, are suspect.  Most of the time, I'll recognize any files that have changed recently, especially programs.  I don't allow patching daily, so any updates that happened since the most recent patch day, including snaps, would be highly suspect.  I only allow snap updates to happen on early Saturday mornings.  The logs show snap updates happening a few minutes after midnight on Saturday mornings.  Anyway, with versioned backups, comparisons are possible.  

Of course, before doing the comparisons, boot from a new ISO. Wouldn't want to connect to the backup storage for the comparisons on a system with active malware/cryptoware or just a nasty virus.  

So, ensure you have a flash drive to boot from available and ready, always.

The last time I had a virus was over 20 yrs ago and my versioned backups made determining what they'd tried to accomplish and where they'd dropped their temporary files pretty easy.  My laptop was hacked at a security conference a few years ago.  I'd wiped the system completely and did a fresh install, applied all patches the day before leaving.  However, I didn't disable bluetooth and during the king of the hill contest, one of the other teams was hacking all their competition.   They got into my laptop.  I don't use BT and hadn't in a fewyears prior to then, but the default Ubuntu desktop install enabled it.  I forgot to disable it. Sigh.

---

### Post by jeantasse on 2024-07-18
Thank you very much TheFu for taking the time to give me good advice.  I wanted to boot with my Ubuntu 24.04 USB key but since my USB key is not "read only", I did not know (in case my system was really infected) if there was a chance that it could get infected and decided to just try what the community recommended to me.  Before, I was only on Linux but as a simple user and never experience anything similar to that.  Also, Ubuntu 24.04 is new and could still have some bugs like any new distro.  I am back to Linux because of Windows 11 and since the present "threats" to Linux are different from past ones, I purchased some books about Linux security, system hardening (got them from Humble Bundle).  I know what to do an what not to do on a Windows PC, but not on a Linux one. This way I will have a better understanding of a modern Linux system and be ready for when I'll need to check on some stuff.

Again, thank you very much TheFu &#128077;

---

### Post by TheFu on 2024-07-18
If you boot off the USB, then it is extremely unlikely that any infection will move into that OS or storage.  That isn't how viruses work.  If the code used for booting isn't infected, then you won't have any security issues.  Of course, if you create the flash drive using the suspect computer, that isn't good, but I've never heard of any attack going after the ISO "burn" process for any Linux ISO being placed onto a flash drive.  Perhaps someone else has and can enlighten us.  Plus, ISO files are read-only, so when they are placed onto the flash storage, they remain read-only unless you do something extra.  I usually use the **cp** command to put the ISO file onto a flash drive.  Much easier for me than trying to use some complex tool just for 1 purpose. To each their own.  

Foundational books for Unix/Linux are great. They teach ideas, but not specifics that are current.  Keep that in mind.  By the time most computer books are printed, they are nearly out of date. If the edition of the book was printed 2 yrs ago, use the ideas, but don't expect specific commands to work, unless they are 20+ yr old Unix commands.  Of course, sometimes we get lucky.

---

### Post by jeantasse on 2024-07-22
Hello currentshaft, sorry for the time it took to try those commands.  All looks good from what I can see.  I will not go any further in this post, I already flagged it as "Solved" but I still wanted to thank you for your help.  I will most likely see this as a "new distro" bug since that is the case for Ubuntu 24.04 and just downgrade to Ubuntu 22.04 for a couple of months. Have a good week.

---

