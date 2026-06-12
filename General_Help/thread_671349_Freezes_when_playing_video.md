---
title: "Freezes when playing video"
date: 2008-01-18
forum: General Help
---

### Post by Repabil on 2008-01-18
Hello,

Yesterday my computer froze three times when I watched a divx video in vlc. Everytime it was utterly frozen, I couldn't change to another tty with Ctrl-Alt-F# neither could I ssh into the machine or kill the X server with Ctrl-Alt-Backspace. So I had to resort to powering off the computer and turning it on again. I gone through /var/log/syslog without finding anything, the last page before the crash is just lines about networking showing, what I believe, my firewall doing its job (removed addresses from it before posting):```
Jan 18 18:58:26 elsa kernel: [ some number] Inbound IN=eth1 OUT= MAC=some number SRC=some number DST=some number LEN=131 TOS=0x00 PREC=0x00 TTL=99 ID=27029 PROTO=UDP SPT=26429 DPT=59050 LEN=111
```

Today I had a freeze like yesterdays only that I was viewing the video in Totem. Couldn't find anything in the logs today either. The reason for me using Totem is actually also a problem: vlc isn't working since yesterday. It won't start simply. Got a tip when starting it in console though:```
VLC media player 0.8.6c Janus
The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 476 error_code 11 request_code 148 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

Dunno if the following has with this to do but things seems to fall apart so it may.  Since I was afraid it being a hardware error I thought about how my boinc client was doing so I started its manager but found it to behave about the same way as vlc is. When I start it in a console it says:```
Skin Manager: Failed to parse static line color. Using default.
Skin Manager: Application name was not defined. Using default.
Skin Manager: Failed to load application logo. Using default.
Skin Manager: Company name was not defined. Using default.
Skin Manager: Company web site was not defined. Using default.
Skin Manager: Project name was not defined. Using default.
Skin Manager: Default tab was not defined. Using default.
Skin Manager: Exit message was not defined. Using default.
Skin Manager: Failed to load attach to project wizard bitmap logo. Using default.
Skin Manager: Attach to project wizard title was not defined. Using default.
Skin Manager: Failed to load attach to project wizard bitmap logo. Using default.
Skin Manager: Attach to project wizard title was not defined. Using default.
Skin Manager: Failed to load 'a' icon. Using default.
The program 'boincmgr' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 505 error_code 11 request_code 148 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

Would appreciate any help. I've checked the tempratures in my case and they were OK and also recently cleaned the insides of it making sure air is getting through. Is there a conspiracy against me? Are my executables corrupted? Hardware falling apart? World coming to an end?

---

### Post by jeffus_il on 2008-01-18
There is a problem with the latest xorg-xserver package,  they are working on it.
Apparently this fixes the problem:
```
sudo apt-get install xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8  
```
will solve the problem

---

### Post by Repabil on 2008-01-18
> **jeffus_il said:**
> There is a problem with the latest xorg-xserver package,  they are working on it.
Apparently this fixes the problem:
```
sudo apt-get install xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8  
```
will solve the problem
Thanks for a quick reply. Does this install an alternative to the standard package or  what is it?

---

### Post by jeffus_il on 2008-01-18
This should install an older version than the one you have, I suggest that you search the forum for news on the subject, there are many threads about it, what I did read earlier is that they are working on it, and an update should appear soon in the repository and should be automatically updated by your system. Search for terms like xorg vlc xserver etc. OK?

---

### Post by fakeollie on 2008-01-27
I've been having the same nasty lockups when playing assorted video, and it all started a few days ago after the xorg update. Thanks for the tip to downgrade xserver-xorg-core.

It would be great if someone could tip us off when a fixed xserver-xorg-core update is available, so we can unfreeze this package version and let it upgrade.

---

