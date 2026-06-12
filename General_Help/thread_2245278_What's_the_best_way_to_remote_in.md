---
title: "What's the best way to remote in?"
date: 2014-09-22
forum: General Help
---

### Post by vbmark on 2014-09-22
I've been running a Windows Server Virtual PC in Windows Azure since the beginning of the year and it's been as smooth and fast as working locally.  I now have a need for a Virtual Linux box in Azure and picked Ubuntu.  

I tried xrdp and it is so slow it's unusable.  

I tried different VNC servers and have different issues like it logs me in as root, or I can't get the windows to display full screen, or I loose the interface and just get a command box.

I read about Vino but it doesn't seem to be installed.  Probably because some instructions I read had me install xfce4.

Can someone please tell me what the recommended way is to remote into Ubuntu from Window?

It needs to be as smooth and fast as Windows Server, not log me in as root, and allow full screen.

Thank you.

---

### Post by TheFu on 2014-09-22
x2go. It will not make video stream, but for productivity apps, it works 3x or more better than other free options.
Oh - and don't use Unity (default desktop). Use a pure WM or lxde/xfce4 - something lite that doesn't demand hw accel GPU.

Plus, the other solutions (VNC/RDP) don't have any real security and shouldn't be used over the internet without a full VPN.

---

### Post by vbmark on 2014-09-22
Looks good.  I'll check it out.  Thanks!

---

### Post by TheFu on 2014-09-22
Clearly, ssh is the best way to remote around the world, but if you must have a desktop, x2go is the best of the free options or options that cost under $1,000.  Opinion, of course.  The Xen commercial VDI solution is extremely impressive - don't think that works on Azure.

Be certain to use key-based ssh authentication, NEVER PASSWORDS.  Also, setup **fail2ban** to protect all ssh connections from unlimited hacking attempts.  For internet-based authentication, using passwords means you've already failed to properly secure it.

I use x2go from all over the world to get a remote desktop back home, on a trusted network. Some places I've traveled have less-than-honest governments who I'd rather not give access to any personal data. I don't worry about the session data being tapped with ssh-keys used for authentication.

---

### Post by vbmark on 2014-09-22
x2go works great!  It doesn't support xfce4 so I ended up installing minimum KDE desktop.  I'd really given up hope for a reasonable remote access solution but this is really the best.

I'm struggling through figuring out how to do key-based ssh authentication.  I now have the public and private keys made.  I logged on to my Linux box with regular password authentication for now until I get this working.

I'm having some problems as I can't do some basic things like set the time or install software.  Either I don't have permission or from the command line it keeps complaining:

No protocol specified
 xhost: unable to open display ":50"

I've tried different things but I'm stuck here.  So any pointers on this is appreciated.

Thanks for the tips!  Once I get the permissions/display issue resolved I'll try to get the public key installed.  Then on to fail2ban.

---

### Post by TheFu on 2014-09-23
Please do **fail2ban** immediately. It is more important than keys.  If the ssh connection is on port 22 on the server, then the defaults are great.

You can and should use router-based port translation - 53022 ext ----> 22 internal  - this will minimize the attacks.  Listening on 22 is just asking for constant attacks.

There are 10,000 how-tos for ssh keys. No need to repeat that. google is your friend.

Be certain to learn about the ~/.ssh/config file - it will make your remote connection life wonderful.

Oh - and x2go definitely DOES support xfce4.  Just use the custom startup - or launch an xterm and manually start it yourself. If you are coming from a mainly Windows background, this can be daunting. Not all options are available thru the GUI. That is common.

---

### Post by vbmark on 2014-09-23
OK, key-pair passwordless authentication is the most awesome thing ever.  

fail2ban is up and running and will send me emails.  How cool is that?

> **TheFu said:**
> You can and should use router-based port translation - 53022 ext ----> 22 internal

I have no idea what that means.

And I still cannot change the time or settings in KDE.

---

### Post by TheFu on 2014-09-23
KDE doesn't have anything to do with the time. It is just a GUI and correct time is an OS thing.  Use ntp, point to an NTP server (probably preconfigured correctly for you), then you just manage the TZ environment. This will get you millisecond accurate time.  NTP solved this like 30 yrs ago.```

sudo aptitude install ntp
```

[https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime) might be helpful too.

Inside your LAN, use port 22 for ssh.
Outside your LAN, use some other port - anything is better than 22 - and have the router translate it to the internal machine on port 22.  There are many reasons to do this and only 1 reason NOT to do it - which doesn't apply in your situation.  That is what was meant above by port translation.  The only routers that I've seen which didn't support this translation were netgear.

Glad that you've gotten so much working.  Key-based authentication does completely rock - people not using it don't know what they are missing AND they aren't as secure.  In trying to help someone else earlier today, I found a few other great links for ssh - [You Don't Know SSH about ssh]("http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh"). Enjoy.

---

