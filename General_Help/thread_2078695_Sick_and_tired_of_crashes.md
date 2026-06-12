---
title: "Sick and tired of crashes"
date: 2012-10-31
forum: General Help
---

### Post by ibrahim52 on 2012-10-31
Same thing had happened during Fedora 16 to 17 upgrade. I did upgrade and It was successful but than all the application started crashing and the same going on after switching to Ubuntu and doing upgrade from 12.04 to 12.10.

Following application keeps DISAPPEARING without even popping up any SEND ERROR REPORT.

1. Thunderbird
2. Remmina
3. Firefox
4. Pidgin
5. VLC (Hangs but Video keeps playing and freeze the whole system until I logout)
6. Sometimes FREEZING is so disgusting that I have to keep holding the POWEROFF button and start again.


Following what I found in apport.log

ERROR: apport (pid 3367) Wed Oct 31 11:24:37 2012: called for pid 3318, signal 11, core limit 0
ERROR: apport (pid 3367) Wed Oct 31 11:24:37 2012: executable: /usr/lib/thunderbird/thunderbird (command line "/usr/lib/thunderbird/thunderbird$
ERROR: apport (pid 3367) Wed Oct 31 11:24:37 2012: executable version is blacklisted, ignoring
ERROR: apport (pid 3995) Wed Oct 31 11:51:02 2012: called for pid 3696, signal 11, core limit 0
ERROR: apport (pid 3995) Wed Oct 31 11:51:02 2012: executable: /usr/lib/thunderbird/thunderbird (command line "/usr/lib/thunderbird/thunderbird$
ERROR: apport (pid 3995) Wed Oct 31 11:51:02 2012: executable version is blacklisted, ignoring
ERROR: apport (pid 5073) Wed Oct 31 12:52:11 2012: called for pid 4097, signal 11, core limit 0
ERROR: apport (pid 5073) Wed Oct 31 12:52:11 2012: executable: /usr/lib/firefox/firefox (command line "/usr/lib/firefox/firefox")
ERROR: apport (pid 5073) Wed Oct 31 12:52:11 2012: executable version is blacklisted, ignoring
ERROR: apport (pid 5414) Wed Oct 31 13:18:22 2012: called for pid 5360, signal 11, core limit 0
ERROR: apport (pid 5414) Wed Oct 31 13:18:22 2012: executable: /usr/lib/firefox/firefox (command line "/usr/lib/firefox/firefox")
ERROR: apport (pid 5414) Wed Oct 31 13:18:22 2012: executable version is blacklisted, ignoring

---

### Post by COMECON on 2012-10-31
Upgrading isn't secure as a fresh install, you can loose your data. I recommend doing a fresh install, but if you want to do an upgrade anyway, you should backup your data before...

---

### Post by oldfred on 2012-10-31
Power button off is one of the worst things you can do. Only do that if remebering the elephants does not work.

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

Generally pressing and holding Ctrl+Alt and
then PrintScr, R, E, I, S, U, B (Raising Elephants Is So Utterly Boring)
should do a clean reboot.
R gives back control of the keyboard, S issues a sync, E sends all processes but init the term singal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system

---

### Post by Slim Odds on 2012-10-31
Generally speaking, linux is extremely stable. Once upon a time, when I had a system that was segfaulting a lot (that's what signal 11 is, a segmentation fault), it turned out to be a failing power supply (low voltage).

---

### Post by ibrahim52 on 2012-10-31
Honestly I am a FAN of linux and specially UBUNTU and perhaps that is the reason I had stopped using Ubuntu than Switched to FEDORA but because of broken RPM package issues switched to Ubuntu and had wonderful time using 12.04 until I upgraded to 12.10 and that's it, the nightmare starts. 

1. If i watch a movie in VLC and minimize or resize the screen, it freeze the whole system and I have to do CTRL+ALT+DEL and LOGOUT and LOGIN

2. Write a big email to bosses and Tadaa, thunderbird DISAPPEARS 

3. Going through some important articles in Firefox, aabraa ka daabraa firefox DISAPPEARS without popping up even "send error report" window.

4. Wake up my laptop from SUSPEND mode , It was evolution calendar which used to crash until I reinstalled it yesterday. Phewww, nothing yet so far.

5. Remmina, being in networking field I can't live without this app but again if I access Windows Server 2008 and it freeze sometimes until I access SYSTEM MONITOR and forcely kill the process.

6. Today I kept audacity running on 1 hour duration track and took a nap. When I woke up It was still playing but I couldn't even move cursor to even close audacity and finally I had to press POWEROFF button.


I had worst scenario during F16 to F17 upgrade but Ubuntu atleast have some LIFE left in it and let me use the OS. 


(Even the above comment I am posting, in the end I have copied to clipboard. In case of any surprise)

---

### Post by snowpine on 2012-10-31
Sorry to hear about your troubles with Ubuntu. Here are some random thoughts on the topic, I wouldn't even categorize it as advice, just thinking out loud:

1. Ubuntu is available as "Live CD" so that you can thoroughly evaluate it before installing/upgrading. If you had tried the Live CD before installing/upgrading, then you would have known about the bugs ahead of time.

2. Many users report problems with upgrades and will recommend a fresh reinstall for that reason. The forums are full of such stories.

3. Non-LTS Ubuntu releases (like 12.10) are not stable, they are "bleeding edge" and it should be expected they will have bugs. Especially if only a few days old like 12.10! Same goes for Fedora three-fold, it is a bleeding-edge development arm of Red Hat, not recommended if stability is your #1 concern. 

4. I personally have had rock-solid stable experiences with: Debian, CentOS, Slackware.

---

### Post by ibrahim52 on 2012-10-31
Thanks snowpine for so quick response. I really appreciate Ubuntu developers for their efforts and time they put to come up with so surprising improvements and makes Ubuntu more "easier" to use. 

I believe that if i could post some of logs over here which might be a help to track down the issue or if it doesn't work than I will go for a fresh install. The only thing is I need to have plenty of time to do backup and Install from scratch (which is FUN to do) but these days I am hardly having time for myself.

Please If somebody can advice me like what kind of logs I should post over here, ill do that.

---

### Post by COMECON on 2012-10-31
You could also try LMDE. It's Debian, but it may remind you to Ubuntu because of its simplicity :)

---

### Post by ibrahim52 on 2012-10-31
Yeah even others have suggest LINUX MINT :) but still I am more comfortable in UBUNTU and its awesomely awesome UNITY launcher.

---

### Post by snowpine on 2012-10-31
Hmmm, LMDE... isn't that based on Debian TESTING? :)

---

### Post by COMECON on 2012-10-31
> **snowpine said:**
> I would never use or recommend LMDE, especially not to someone looking for stability, since it is based on Debian TESTING. Please phrase your recommendations as your own rather than piggy-backing them onto someone else's post, thanks.

Sorry, I deleted the quotation. About the stability, first, Debian Testing isn't really unstable, maybe for servers, but for a desktop/workstation IMO it isn't. Second, LMDE doesn't provide exactly a mirror to Debian Testing's repos, they just provide packages tested by Mint's staff and developers and provide them with Update Packs... Which is a bit odd for me, I don't understand it, but it'd be more stable than an standard Debian Testing. So basically I recommend LMDE over Debian Testing because of this, but I recommend Debian Stable over LMDE if you need a rock-solid and ultra-stable distro (e.g., servers).
Apologies again!

---

### Post by snowpine on 2012-10-31
I didn't realize that's how they worked the repos. Maybe I'll give it another try someday. :) 

(edited my previous post to sound a little friendlier, sorry!)

---

### Post by COMECON on 2012-10-31
> **snowpine said:**
> I didn't realize that's how they worked the repos. Maybe I'll give it another try someday. :) 

(edited my previous post to sound a little friendlier, sorry!)

No problem! At least that's what I understood, some years ago LMDE's repos were a mirror of Debian Testing, more or less. Recently they added that odd Update Pack thing, and lots of LMDE users now use Debian Testing repos instead of LMDE's because of this. But doing that can broke your system due to some mint-specific dependencies, so I don't recommend to do that (also I think it has no sense, installing drivers and plugins on Debian just takes a few minutes).

---

### Post by Topsiho on 2012-10-31
Ubuntu is that good, that if you get (so many) crashes, you should think of hardware that is faulty. Someone mentioned a failing power supply, you might also check the memory (RAM), you can use the LiveCD for that.

You can also check whether your hard disk is still OK, using the Disk Utility, and see what S.M.A.R.T. has to say.

Even the new 12.10 already runs quite well on the computer on which I have it installed. STOTA (State of the art), but very stable.

You should think of hardware.

Topsiho

---

### Post by oldfred on 2012-10-31
Are you overclocking your system?

---

### Post by ibrahim52 on 2012-10-31
I did the hardware test. S.M.A.R.T over all assessment test shows DISK is OK and didn't had any issues at all in 12.04. It only started after upgrading to 12.10. Anyways, I have done some repairs and reinstallation of packages and for now it is running and if nothing happens till Friday than its good otherwise I am going to make a fresh install for 12.10. Thanks everyone and will post further on upcoming Friday :)

---

