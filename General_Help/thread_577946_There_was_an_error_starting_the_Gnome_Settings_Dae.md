---
title: "There was an error starting the Gnome Settings Daemon"
date: 2007-10-16
forum: General Help
---

### Post by tuckie on 2007-10-16
This has happened three times in the last two weeks, it stops responding (sometimes using it, sometimes not), but the hard drive activity will spike so that the led is practically lit solid, and it will stay this way for probably 10 minutes or so.  When it finally finishes whatever it was doing (I have no idea what that might be), it pops up with said error message, and says  > Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bu security policy blocked the reply, the reply timeout expired, or the network connection was broken.

This is on 7.04, I wasn't accessing the computer at the time, but was running the dd_rescue command on the box through putty at the time.  Any ideas as to what's going on?

---

### Post by tuckie on 2007-10-17
I'm not sure if this is related as the computer isn't locked up at this point, but my cpu usage is around 80 percent and there are a roughly 15 instances of mythbackend that spawned itself and around 27 or so instances of mysqld

---

### Post by tuckie on 2007-10-17
Another update:  htop shows that one of my cores is constantly at 100 percent while the other is hovering around 5.  Yet, when I look at the list sorted by cpu usage, the highest cpu usage is coming from python (torrentflux) at 2 percent.  What is using up all these cycles?

---

### Post by rlongfield on 2007-10-22
I am having the same error message after upgrading to 7.04. 
This problem seems to only plague one user (thus far).
Also it seems that files on my desktop occasionally show up and trying to browse my computer using the File Browser is a painful experience.
Why I check top, nothing seems to be using a lot of CPU cycles.

I would really like to get this fixed.

---

### Post by dwmcc on 2007-10-24
Hi Guys,
I'm having the exact same problem.

The Message reads:

[B][U]There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in[/U][/B]



If you find a solution, please let me know.

Thanks,
Dwmcc

---

### Post by anuradha.d on 2007-10-25
hi all,

I got this issue and I did some thing like this. (guessed and did), but it helped. It seems to be a crashing with the settings in your .gnome or .gnome2 or .gnome2_private or gcont, gcongd (I'm not sure which of it, so I removed all of them). 

$ cd /home/xxx
$ ls -al
$ rm -rf .gnome .gnome2 .gnome2_private .gconf .gconfd
$ sudo reboot

Remove all the gnome related directories in /home/xxx and restart the computer. And in the login prompt set the session to Run X-Client script, or Gnome. That's it. Hope this will be helpful to you, but not sure whether it'll work on your end. :-)

cheers!

---

### Post by thai84 on 2007-10-26
I did exactly something you told, but the error have repeated.:confused:
who has different idea to solve this error ? :(

---

### Post by commonplace on 2007-10-26
I have a whole labful of computers that just started throwing up this error this afternoon. They've been fine for months and were working fine even this morning. Now, it's hard to login, and once logged in, we get the error mentioned in this post. I have no idea what's wrong or what happened... but I have 25 computers to fix. Grr! Anyone have any ideas?

/Kevin

---

### Post by funkythumb on 2007-10-29
Just wanted to add my 2 cents...experiencing same problem. In my case, it's the latest Gutsy install of Ubuntu Studio. Downloaded fresh ISO, checked integrity, installed from scratch on Dell Latitude D600. Install went perfectly (except for desktop not matching my external screen, but apparently an older ATI driver problem!), until after a couple rounds of updates were applied got the dreaded message.

==========================

[FONT="Courier New"][I]There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.[/I][/FONT]

==========================

Unfortunately, didn't keep track of exactly which update preceded the issue.

Hope someone has a clue - my wife's laptop is the exact same model, and need to restore it after some software corruption. She's been doing great in Feisty (until the crash) and she's a new convert to Linux. Don't want to hear incessant nagging if this error pops up on her machine...

---

### Post by peterx14 on 2007-11-28
I'm seeing the same error message. It has been doing this intermittantly starting weeks... perhaps even a month or two (I don't think I had this issue prior to upgrade to 7.10).

I don't notice any other ill effects though; it seems to login about the same speed. My desktop background is still working, but the theme is wrong. Compiz is working. Interestingly (maybe) all my hard drive and network connection short-cuts on my desktop are *not* showing. Also, in the Places menu, these connections are not showing.

I know from previous experience rebooting will clear this problem. To give an idea of how intermittant it is, I boot into Ubuntu at least once every day and the last time I had this problem must have been more than 2 weeks ago... perhaps as much as 4 weeks ago.

---

### Post by shellhrs on 2007-11-30
@ funkythumb:

I also use Ubuntu Studio. The first time it boots (after installation), everything is OK. After I reboot, the same error appeared. I used the method described by anuradha.d in the post above to fix it. No more error now.

---

### Post by GOwin on 2008-01-10
This works. However, please take note that this will also delete your customization settings and bookmarks. So make a backup first.

> **anuradha.d said:**
> hi all,

I got this issue and I did some thing like this. (guessed and did), but it helped. It seems to be a crashing with the settings in your .gnome or .gnome2 or .gnome2_private or gcont, gcongd (I'm not sure which of it, so I removed all of them). 

$ cd /home/xxx
$ ls -al
$ rm -rf .gnome .gnome2 .gnome2_private .gconf .gconfd
$ sudo reboot

Remove all the gnome related directories in /home/xxx and restart the computer. And in the login prompt set the session to Run X-Client script, or Gnome. That's it. Hope this will be helpful to you, but not sure whether it'll work on your end. :-)

cheers!

---

### Post by intrader on 2008-03-12
The error is pretty solid for me. Happens every time I boot and prevents me from fully getting the desktop. 
I am thinking that I need to reinstall but I am afraid to loose a lot of thunderbird addresses and firefox bookmarks as well as some eclipse projects.
The error says the following:
"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background
settings may nor work correctly.

The last error message was;

Process /usr/lib/knome-control-center/gnome-settings-
daemon exitd with status 127

GNOME will still try to restart the Settings Daemon next time you log in."

CTL/ALT/Backspce restarts the X session. but I then get the same error.


:(

---

### Post by pizpot on 2008-03-12
If you get this message, don't try to fix it. Just log out and back in. The message comes and goes. I get it on a fresh install and an old install, makes no difference. Both my laptop and desktop do it... amd vs intel. I get it one boot but not another. I have no idea what the problem is, almost like the filesystem isn't ready and gnome is trying to use it and times out rather than waiting.

---

### Post by smithhn on 2008-03-17
I started getting this TODAY, and I have made no updates to software. The specific error in my case was "Failed to connect to socket \tmp\dbus= ..... 

Notice how the Suspend and Hibernate options are no longer available.

If I create a new user, all is well again, but user the original user the problem occurs. 

This is what I did to get rid of this problem:

I re-started the machine. 
That did not work.
So, I re-started the machine again, with a couple of switch users in between.
That did not work.
So I did it again.
It worked.

Now THAT is odd. Any clues on what is going on?

---

### Post by boas on 2008-04-07
Got the same problem after running Ubuntu 7.10 for two days. It came after an installation of Xgl and Wicd, but I don't know if the error message is connected to the installs. An easy sollution is:

Alt+F2
and then write: gnome-settings-deamon

but it's only an intermittent sollution because the problem pops up again after restarting the PC.

---

### Post by mathematician314 on 2008-04-24
I had the same problem. On this forum I found out that deleting folders
.gnome
.gnome2
.gnome2_private
doesn't help, so I restarted the system in recovery mode and deleted them as root. Suddenly it all worked. 
It is possible that when you delete these folders from your account and log out, gnome saves all those settings that caused this error in the first place.

---

### Post by ulugeyik on 2008-04-30
I do not think deleting those folders is a good suggestion. If nothing else, my whole f-spot database is saved under .gnome2 and there could be other programs that save their information under those folders.

This being said, I have the same problem on my upgrade with Hardy Heron on my laptop.

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

---

### Post by rushtoshankar on 2008-05-16
try this solution, i found this after spending some time for googling....

add two line in file /etc/network/interfaces:
auto lo
iface lo inet loopback

and commenting out all entries with IPv6
then type sudo ifup lo on terminal, then reboot the system or gnome !

---

### Post by shoppy123 on 2008-05-22
I'm having this same problem. I would say 50% of the times I start my laptop I get this message.

---

### Post by jaypd on 2008-05-23
I attempted to run Ubuntu 8.04 LTS Desktop Edition from CD (created the CD from the ISO) and am getting this error.  I get to the install screen and attempt to run run without changes from the CD, and about 2 minutes in this window pops up.  It wouldn't be so bad, but the computer hangs up at this point (won't let me close the error message).  I tried the test memory function (success) as well as checked the CD for defects (also success).  Tried Safe Graphics mode as well to no avail.  Any suffestions?

The current config is HP Pavilion N5170 XP SP2, 128 KB Ram, and 40 GB HD.

---

### Post by billstei on 2008-05-28
I have had this error (intermitently) for at least a year.  It is some kind of race condition, and what I have discovered is that when I get to the login screen I type in name, then password (don't hit return yet), then wait about 10 seconds and watch for the HD light to come on solid for about 2 seconds then off, then wait about 2 seconds more, then hit return.  Kludgey?  You betcha.  But at least I win the race (most of the time).

Bill

---

### Post by arunpc on 2008-05-31
Hi folks,
I got this error and i the way i got out of this was to have the settings for my loopback interface configured correctly, The error to me was because there are services who can get loopback replies. For the description and the solution of my problem, please refer to my blog,
[http://arunpc.com/2008/06/01/ubuntu-there-was-an-error-starting-the-gnome-settings-daemon/](http://arunpc.com/2008/06/01/ubuntu-there-was-an-error-starting-the-gnome-settings-daemon/)
Do let me know what you think.

Thanks,
Arun.PC

---

### Post by arunpc on 2008-05-31
Hi folks,
I got this error and i the way i got out of this was to have the settings for my loopback interface configured correctly, The error to me was because there are services who can get loopback replies. For the description and the solution of my problem, please refer to my blog,
[http://arunpc.com/2008/06/01/ubuntu-there-was-an-error-starting-the-gnome-settings-daemon/](http://arunpc.com/2008/06/01/ubuntu-there-was-an-error-starting-the-gnome-settings-daemon/)
Do let me know what you think.

Thanks,
Arun.PC:guitar::guitar:

---

### Post by billstei on 2008-05-31
arunpic:  Thanks for the info...I read your blog entry and indeed I do not have lo in the /etc/hosts file, nor is it pingable (unknown host) but I also have a Hardy system running as a virtual machine which does not seem to have this problem and it also does not have lo in /etc/hosts and lo is not pingable.  There must be something more to this issue (for me).

Bill

P.S.  Being a race condition, my Hardy system proves nothing.  Oh well.

---

### Post by kodemaan on 2008-06-03
> **rushtoshankar said:**
> try this solution, i found this after spending some time for googling....

add two line in file /etc/network/interfaces:
auto lo
iface lo inet loopback

and commenting out all entries with IPv6
then type sudo ifup lo on terminal, then reboot the system or gnome !

I accidentally deleted those 2 lines and adding them back fixed the problem completely, thanks.

---

### Post by bevis on 2008-06-05
I've tried all the solutions in this and other threads, but none of them worked for me.  The daemon dies within a couple of minutes every time I log on.  I'm using ubuntu 8, upgraded from 7.

This does seem to be a pretty fundamental bug, and a search for the problem on google suggests that a great number of people are encountering it.  I'm surprised that the ubuntu team don't appear to have looked into it yet!

This week I may try a re-install if I can face it.



bevis

---

### Post by dunno on 2008-06-24
hey y'all!

my laptop was having this problem as well.  After googling around a bit, I found this thread and arunpc's post.  his post mentions something about the problem is the loopback device not being configured correctly.  I read his blog and excitedly tried his suggestions only to find that my lo/loopback device was indeed configured correctly.

however, since upgrading from gutsy to hardy, my wireless card hasn't worked correctly and I haven't gotten around to fixing it.  regardless, the old wireless config isn't correct for the newly release hardy.  long story short: my /etc/network/interfaces was FUBAR (and my wireless didn't work) and I was getting this gnome-settings-daemon error.

today i got around to messing with my wireless and made it work and in the process fixed all the errors in my /etc/network/interfaces file.  the gnome-settings-daemon error has since gone away.

my interfaces file now looks like:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto ath0
iface ath0 inet dhcp
```

so, if you're having troubles with this gnome-settings-daemon demon, i'd start by:

```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```

then strip that interfaces file down to the bare essentials, and build it back up until it breaks again and then [-o<.

if things get worse, ```
sudo cp /etc/network/interfaces.bak /etc/network/interfaces
```
and try again.

i hope this helps someone else.
word!
\\:D/=D>

---

### Post by JamesieAB on 2008-06-26
I got this same message on startup (along with a long pause with a blank screen and a white rectangle where the error message was) after changing localhost to testhost in my hosts file while I was following a websites guide to getting started with php.

The solution was to navigate through the menu to System->Administration->Network and change it back to localhost, then I rebooted and no longer have that long pause on startup or the message.

Hope this is of some help to somebody.

---

