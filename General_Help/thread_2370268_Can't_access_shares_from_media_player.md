---
title: "Can't access shares from media player"
date: 2017-09-01
forum: General Help
---

### Post by wurlyfan on 2017-09-01
Hi there. I have a network with two Ubuntu desktops acting as media servers in different rooms, both containing the same media and smb shares. I also have two hardware media players (AC Ryan and Mede8er), both able to access either desktop. Since upgrading one desktop from Ubuntu 16.04 to 17.04, neither media player can access the shares on the 17.04 desktop, showing a "Login fail" message. Both media players can still access the shares from the 16.04 desktop, the two desktops can each see the shares from the other and my Windows laptop can access them from either desktop. Can anyone suggest what has happened? I've checked and changed UNIX and Samba passwords, and smb.conf on the 17.04 machine, and can't see anything wrong. There have been no changes to the media player hardware, software or configuration.

I'll post additional information on request but, first, has anyone else had this problem after upgrading to 17.04? :mad:

Output of testparm -s from 17.04 box (some shares removed):

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[TV1]"
Processing section "[MEDIA1]"
Processing section "[MEDIA2]"
Processing section "[DATA]"
Processing section "[BACKUP]"
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
    server string = Samba Server %v
    domain master = Yes
    preferred master = Yes
    name resolve order = bcast host
    nt pipe support = No
    server min protocol = NT1
    map to guest = Bad User
    security = USER
    username map = /etc/samba/smbusers
    dns proxy = No
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    browseable = No
    printable = Yes
    create mask = 0700

[TV1]
    path = /media/TV1
    valid users = <myuname> media

[MEDIA1]
    path = /media/TMEDIA1
    valid users = <myuname> media

etc.

Output of testparm -s from 16.04 box (some shares removed):

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
...

Processing section "[MEDIA1]"
Processing section "[MEDIA2]"
Processing section "[MEDIA3]"
...

Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
    server string = Samba Server %v
    security = USER
    map to guest = Bad User
    server min protocol = NT1
    min protocol = NT1
    nt pipe support = No
    name resolve order = bcast host
    dns proxy = No
    usershare owner only = No
    idmap config * : backend = tdb

[MEDIA1]
    path = /media/NAS1
    valid users = media <myuname>

[MEDIA2]
    path = /media/NAS2
    valid users = media <myuname>

etc

---

### Post by TheFu on 2017-09-01
I'd read the upgrade notes pertaining to the new version of samba.  Sometimes things change that break old things.  

Plus HW devices trying to implement the CIFS/SMB protocol often do not actually follow the specs.  In the last few years, many security patches have happened thanks to issues caused by Windows viruses.  So, the devices might only implement smbv1 when new settings default to smbv2 for security reasons.  That is where I'd start.

I think there is a min_smb_version setting that can be enabled.  Or perhaps it is a max_smb .... 
[https://lists.samba.org/archive/samba/2015-March/190157.html](https://lists.samba.org/archive/samba/2015-March/190157.html) has some commands that shows how to check some things.

---

### Post by wurlyfan on 2017-09-02
Thanks TheFu, I think this is the right track. I tried adding "min protocol = xxx" to the samba.conf on the 16.04 machine and found that the media players would not connect with xxx = SMB2. NT1 works, but only on the 16.04 machine. SMB1 can't be used on either machine (the smbd service fails to start). I'm beginning to thing I'll have to downgrade back to 16.04, although I suspect the problem will reappear when I eventually have to upgrade for some other reason. I'm surprised that more 17.04 users aren't complaining about this!

---

### Post by TheFu on 2017-09-02
> **wurlyfan said:**
>  I'm surprised that more 17.04 users aren't complaining about this!

I don't use non-LTS releases. Every.  6 months for support just isn't worth my effort to install, especially for something like a media server.  I'm actually still using 14.04 on mine, waiting for 16.04 to be stable. ;)  Only 5% of my systems are on 16.04.  The rest are still happily running 14.04.

Other people running 17.04 are seeing the issue, but it is fixable between Windows and OSX clients.  With specific HW devices like you have, things can be much more challenging.  I used to have players like you. Switched to Kodi/OSMC running on raspberry-Pi devices for the better v-codec support. Much better experience, more flexible.

Newer isn't always better.

New is the enemy of stable.

---

### Post by Morbius1 on 2017-09-02
I don't know if I can help you since I am not familiar with your media devices but ...

You might want to post the output of testparm on the 17.04 server:
```
testparm -s
```
If you "upgraded" a 16.04 machine to 17.04 there may be a setting that no longer works ... maybe.

[COLOR=#0000cd]*Some inconsequential "fun facts":*[/COLOR]

*** smb.conf is not the samba configuration file despite how it sounds and despite the documentation for Samba calling it that. In fact there is no samba configuration file as most of the settings for Samba and CIFS are embedded in the Linux kernel itself. smb.conf is used to add to or override those settings.

*** You can however see the settings indirectly by using a carefully constructed testparm command sequence.

*** You can use that command sequence to find the default min and max smb dialects the Linux server will respond to this way:
```
testparm -sv /dev/null | grep protocol
```
You should get back something like this:
> server max protocol = SMB3
server min protocol = LANMAN1
A samba server will negotiate what dialect it uses with the client from LANMAN1 ( which predates NT1 ) to SMB3. In Windows this would correspond to something like Win98 ( if not earlier ) all the way up to Windows 10.

I don't think this is a samba version issue it's something else. What that is exactly I do not know.

---

### Post by wurlyfan on 2017-09-03
Hi Morbius1, thanks for answering. Yes, the protocol query returns exactly the result you predicted, and I've added the output of testparm -s to the original post. Your remarks about smb.conf are interesting, but it obviously has some effect because I set up all my shares by direct editing of it! At this stage I'm pretty convinced the problem is directly related to smb v1 being disabled in 17.04, and the fact that the firmware in the Realtek chips in both my media players was compiled with an old version of Linux that can only use smb v1 (this from the media player forums). I've complained about it in the mp forum but been told that there will be no future firmware upgrades! Nevertheless. I'm quite willing to listen to alternative explanations for the problem if you have one.

Thanks again TheFu, actually the box that acts as my primary media server is still running Ubuntu 16.04, and I use Plex (Rasplex running on a RaspberryPi) for most of my viewing. Plex is inconvenient for some types of content (documentaries, for example) and I suspect that all Kodi-based systems are the same. The media players' ability to go directly to a file in a hierarchical folder structure is useful in this context, and sometimes I want to view media that hasn't made it's way onto the 16.04 box yet.

I have found an acceptable workaround, however, which is to use NFS shares, which both media players handle well and which don't use the smb protocol.

---

### Post by TheFu on 2017-09-03
> **wurlyfan said:**
> Hi Morbius1, thanks for answering. Yes, the protocol query returns exactly the result you predicted, and I've added the output of testparm -s to the original post. Your remarks about smb.conf are interesting, but it obviously has some effect because I set up all my shares by direct editing of it! At this stage I'm pretty convinced the problem is directly related to smb v1 being disabled in 17.04, and the fact that the firmware in the Realtek chips in both my media players was compiled with an old version of Linux that can only use smb v1 (this from the media player forums). I've complained about it in the mp forum but been told that there will be no future firmware upgrades! Nevertheless. I'm quite willing to listen to alternative explanations for the problem if you have one.

Thanks again TheFu, actually the box that acts as my primary media server is still running Ubuntu 16.04, and I use Plex (Rasplex running on a RaspberryPi) for most of my viewing. Plex is inconvenient for some types of content (documentaries, for example) and I suspect that all Kodi-based systems are the same. The media players' ability to go directly to a file in a hierarchical folder structure is useful in this context, and sometimes I want to view media that hasn't made it's way onto the 16.04 box yet.

I have found an acceptable workaround, however, which is to use NFS shares, which both media players handle well and which don't use the smb protocol.

NFS is always best for non-Windows connections.  No doubt.

BTW, you can place documentaries in a "Video" group on Plex or Kodi and as long as the filename is what you want to see, it isn't an issue.  I use both Plex and Kodi.  Plex for media management and remote streaming.  Kodi for viewing.  I use the PlexBMC kodi addon to access the Plex libraries.  PlexBMC can suck as some other addons seem to interfere with it, which makes ZERO sense to me. Regardless, I like having Plex know what we've seen, what we haven't and in a multiple player house, that is important.  Stopping in 1 room and picking up later from a hotel 1,000 miles away is nice.
BTW, I dislike all the plex-based players and do not have a Plex login.

So actually, I think you've solved this and made it better.  NFS is not a workaround, it is the preferred solution.

---

### Post by Morbius1 on 2017-09-03
> **wurlyfan said:**
> Your remarks about smb.conf are interesting, but it obviously has some effect because I set up all my shares by direct editing of it!smb.conf is a diff file. It's contents is an add or override of the default settings.
> At this stage I'm pretty convinced the problem is directly related to smb v1 being disabled in 17.04, and the fact that the firmware in the Realtek chips in both my media players was compiled with an old version of Linux that can only use smb v1 (this from the media player forums). 
There is one big reason why I believe you are incorrect. By default another Linux system only can use SMB1 when connecting to any SMB / Samba server. If SMB1 was disabled on the server your other Linux machine would not be able to access it.

You can prove this to yourself when you have nothing else to do:

[1] Connect to the 17.04 server from your other Linux machine.
[2] Then on the server run this command:
```
sudo smbstatus
```
Here is my output from doing the same on my network:
> tester@vub1704:~$ sudo smbstatus

Samba version 4.5.8-Ubuntu
PID     Username     Group        Machine                                   Protocol Version  Encryption           Signing              
----------------------------------------------------------------------------------------------------------------------------------------
4578    nobody         nogroup  xub1404 (ipv4:192.168.1.143:40479)           NT1               - 
The client ( a xubuntu 14.04 machine ) is accessing the server ( an ubuntu 17.04 machine ) using the SMB1 ( NT1 = SMB1 ) dialect.

May I ask what this is all about:
> domain master = Yes
preferred master = Yes
nt pipe support = No
All of those deviate from the default settings. What issue were you trying to resolve with those setting?

[COLOR=#0000cd]**EDIT**[/COLOR]: I may have stumbled upon the answer for one your your overrides ["nt pipe support = No"]("https://www.tecmint.com/fix-sambacry-vulnerability-cve-2017-7494-in-linux/").
And an interesting comment on using it here: [https://linustechtips.com/main/topic/789043-what-functionality-does-nt-pipe-support-no-disable/](https://linustechtips.com/main/topic/789043-what-functionality-does-nt-pipe-support-no-disable/)
> It disables access to shared folders. Learned the hard way when our  shares stopped working for most users a week after adding the line to  our confs. I finally saw it mentioned here [https://www.tecmint.com/fix-sambacry-vulnerability-cve-2017-7494-in-linux/](https://www.tecmint.com/fix-sambacry-vulnerability-cve-2017-7494-in-linux/), though it says it disables access to shares *listing* from *Windows* clients, it also affects Ubuntu and Mac clients. Most users in our environment couldn't access shares at all. 

Here's a recommendation: 

Run this command:
```
dpkg -s samba | grep Version
```
If the version you get is **samba 2:4.5.8+dfsg-0ubuntu0.17.04.2 **or greater you do not need this nt pipe support workaround as your vulnerability is already fixed.

If you remove the line in smb.conf restart smbd and see if it fixes the original problem:
```
sudo service smbd restart
```

---

### Post by wurlyfan on 2017-09-03
> **Morbius1 said:**
> smb.conf is a diff file. It's contents is an add or override of the default settings.

There is one big reason why I believe you are incorrect. By default another Linux system only can use SMB1 when connecting to any SMB / Samba server. If SMB1 was disabled on the server your other Linux machine would not be able to access it.

You can prove this to yourself when you have nothing else to do:

[1] Connect to the 17.04 server from your other Linux machine.
[2] Then on the server run this command:
```
sudo smbstatus
```
Here is my output from doing the same on my network:

The client ( a xubuntu 14.04 machine ) is accessing the server ( an ubuntu 17.04 machine ) using the SMB1 ( NT1 = SMB1 ) dialect.

May I ask what this is all about:

All of those deviate from the default settings. What issue were you trying to resolve with those setting?

[COLOR=#0000cd]**EDIT**[/COLOR]: I may have stumbled upon the answer for one your your overrides ["nt pipe support = No"]("https://www.tecmint.com/fix-sambacry-vulnerability-cve-2017-7494-in-linux/").
And an interesting comment on using it here: [https://linustechtips.com/main/topic/789043-what-functionality-does-nt-pipe-support-no-disable/](https://linustechtips.com/main/topic/789043-what-functionality-does-nt-pipe-support-no-disable/)

Here's a recommendation: 

Run this command:
```
dpkg -s samba | grep Version
```
If the version you get is **samba 2:4.5.8+dfsg-0ubuntu0.17.04.2 **or greater you do not need this nt pipe support workaround as your vulnerability is already fixed.

If you remove the line in smb.conf restart smbd and see if it fixes the original problem:
```
sudo service smbd restart
```

Hey Morbius1, I really appreciate your help with this.Even though I've bypassed the problem with NFS I'd still like to know what's happening, so ...

(a)  Samba versions for both boxes:

2:4.5.8+dfsg-0ubuntu0.17.04.5
2:4.3.11+dfsg-0ubuntu0.16.04.10

(b)  nt pipe support: Removing this line makes no difference to the problem, and adding it to the smb.conf on the 16.04 box didn't stop the media players connecting to it. I've removed it from the 17.04 smb.conf, though, since you've proved it to be unnecessary. (In fact I only added this line after I started researching this problem).

(c) SMB1/NT1: I confirm your test results; the 16.04 box is still able to connect to the 17.04 shares using NT1 protocol. Output of "sudo smbstatus" is:

9357    media        media        192.168.1.101 (ipv4:192.168.1.101:43318)  NT1

I guess that wasn't the right track after all. Nevertheless, something is stopping the media players (two different devices) connecting to the 17.04 box using exactly the same credentials as I used for this test. Doing the same test on the 16.04 server when accessed from the media player gives the output:

 9722    media        media         192.168.1.104 (ipv4:192.168.1.104:57910) NT1

On another track, I see your Username/Group are set to nobody/nogroup. Could this be a factor affecting the 17.04 samba version? I've read about this but thought it only applied to root access.

(c)  "What this is all about"

From memory, I used to have the problem that if I took down one of my boxes for too long, after restoring it I couldn't access the other box. Some research suggested that the other box had become the "master" and some required information wasn't available on that box. I followed a post suggesting adding those two lines to smb,conf and it hasn't happened since. It was a rather uninformed "fix", however, and I was even more a newbie then than I am now! Removing these lines doesn't affect my problem.

Again, I appreciate you taking time to think about this and, if nothing else, I'm learning a lot from your responses. For completeness, I've also added the output of testparm -s from the 16.04 box to the original post, just in case it helps.

---

### Post by Morbius1 on 2017-09-04
Without knowing exactly how these media devices are implementing samba I don't know how to take this any further. I did a quick search on the Mede8er forum and this "Logon Failure" could literally be from anything: Misconfigured samba server, firewall, DNS, host name resolution ... etc.

Note: The following is a wild-ass guess and I publicly admit so:

I thought to myself ( it happens occasionally ) that the issue isn't the samba dialect as it is the password authentication method that's the issue. I looked at the difference in the default settings of both 16.04 and 17.04 and there is one parameter that did in fact change: **ntlm auth. **In 16.04 it's set to Yes but in 17.04 it's set to No.

If you want to try something edit smb.conf and add - under the workgroup = WORKGROUP line - an override:
```
ntlm auth = Yes
```
Then restart smbd:
```
sudo service smbd restart
```

Anyhoo, like I said it's a guess.

---

### Post by wurlyfan on 2017-09-07
You, sir, are a gentleman and a scholar! ntlm auth = Yes did the trick, my Mede8er now connects to my 17.04 box beautifully. I haven't tried the AC Ryan yet, but I'd lay money that will work as well. Thanks heaps for sticking with it and leading me to a successful conclusion.:p

---

### Post by ravenseldon on 2018-09-02
I know this is an old thread, but Morbius1, I owe you big time. I registered only to thank you guys:D
Not even using Ubuntu, but NAS4Free/XigmaNAS. I have the same ACRyan player as wurlyfan, and had a very similar issue (could access the shares from phone and pc, but the player was unable to log in). Apparently the N4F/FreeBSD guys just changed this NTLM setting now... Added this additional parameter and all is good again. So relieved (although I would have probably switched to NFS if this doesn't work:)

---

