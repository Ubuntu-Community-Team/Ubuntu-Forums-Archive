---
title: "How do I encrypt files in Ubuntu (HIPAA)"
date: 2007-04-24
forum: General Help
---

### Post by Tesgin on 2007-04-24
There has to be a way to do file encryption in Edgy (I've given up on Feisty:  too many problems).  I'm thiniking of converting my office to Ubuntu, but I need to be HIPAA compliant (federal regulations governing file security in health service settings).

Currently, on Windows XP, there are a number of programs I use to encrypt files individually (e.g., AxCrypt) or in mounted volumes.  I'm not finding anything like this in Ubuntu.

I've tried running AxCrypt in Wine, but for the life of me I can't get it to work (I get an error that says "wine: could not load L"c:j\\windows\\system32\\axcrypt.exe": Module not found").

If anyone could help me get Axcrypt running under Wine I'd be a happy camper (I've heard it's been done).  OR, are there other encryption programs that can encrypt my data for me so I can, for e.g., store it securely on a flash drive or something?

Thanks,
Tesgin

---

### Post by dcstar on 2007-04-24
> **Tesgin said:**
> There has to be a way to do file encryption in Edgy (I've given up on Feisty:  too many problems).  I'm thiniking of converting my office to Ubuntu, but I need to be HIPAA compliant (federal regulations governing file security in health service settings).

Currently, on Windows XP, there are a number of programs I use to encrypt files individually (e.g., AxCrypt) or in mounted volumes.  I'm not finding anything like this in Ubuntu.

I've tried running AxCrypt in Wine, but for the life of me I can't get it to work (I get an error that says "wine: could not load L"c:j\\windows\\system32\\axcrypt.exe": Module not found").

If anyone could help me get Axcrypt running under Wine I'd be a happy camper (I've heard it's been done).  OR, are there other encryption programs that can encrypt my data for me so I can, for e.g., store it securely on a flash drive or something?

Thanks,
Tesgin

I remember a few years ago someone posted a Nautilus script that encrypted files, do a forum search and you should find the HOWTO somewhere.

---

### Post by orb9220 on 2007-04-24
[http://www.truecrypt.org/](http://www.truecrypt.org/)

Truecrypt works in windows and linux. Their site has the .deb package for edgy 6,10
or it is in synaptic package manger. Be sure to enable the addtional reposortries.

The truecrypt gui for ubuntu is called forcefield.

---

### Post by SteveF on 2007-04-24
I've used ccrypt under both Linux and Windows.  I've also used a Windows program called Blowfish running under Windows and Wine.  No problems using either program.

Ccrypt is a command line app.  Blowfish has a GUI.

Steve

---

### Post by Tesgin on 2007-04-24
This is excellent.  Several possibilities to follow up with.  Thanks.  I will check these out and post my results.

Thanks everyone!
TB

---

### Post by Gotit on 2007-12-17
I too am trying to get AxCrypt to run under Wine.  My first issue was I needed to install IE v4 or better.  I was able to install IE 6 SP1 in Wine at W2K with no problems.

Then AxCrypt installed in Wine nicely.  However the only problem I seem to be having is opening an AxCrypt encrypted file.  I can use AxCrypt Decrypt OK, but opening and running encrypted filles is a problem.  I have run across a script that may "fix" this issue (haven't tired it yet) and you may want to give it a shot. 

You can check out the script at: [http://archives.free.net.ph/message/20071121.145337.b99d34e6.en.html]("http://archives.free.net.ph/message/20071121.145337.b99d34e6.en.html")

---

### Post by Gotit on 2008-01-08
Update:
I did use the scripts provided at [http://article.gmane.org/gmane.comp.emulators.wine.user/20010/match=script](http://article.gmane.org/gmane.comp.emulators.wine.user/20010/match=script) with success.
I also made a copy of the "axencrypt" and "AxEncrypt" scripts, chaged the option to "-o" to temp decrypt an encrypted file and open it with the associated program.  I found I needed to have the associated program installed in Wine and couldn't use a symlink to my linux install of the program.

---

### Post by nocturn on 2008-01-08
> **Tesgin said:**
> There has to be a way to do file encryption in Edgy (I've given up on Feisty:  too many problems).  I'm thiniking of converting my office to Ubuntu, but I need to be HIPAA compliant (federal regulations governing file security in health service settings).

Currently, on Windows XP, there are a number of programs I use to encrypt files individually (e.g., AxCrypt) or in mounted volumes.  I'm not finding anything like this in Ubuntu.

I've tried running AxCrypt in Wine, but for the life of me I can't get it to work (I get an error that says "wine: could not load L"c:j\\windows\\system32\\axcrypt.exe": Module not found").

If anyone could help me get Axcrypt running under Wine I'd be a happy camper (I've heard it's been done).  OR, are there other encryption programs that can encrypt my data for me so I can, for e.g., store it securely on a flash drive or something?

Thanks,
Tesgin

Truecrypt or LUKS can deal with encrypted containters.
GnuPG (GPG) can encrypt files individually, seahorse integrates this into Nautilus.

---

### Post by Gotit on 2008-01-17
Yes, I tried Scramdisk and really like that program.  Unfortunately, it&#8217;s not supported in XP.  Truecrypt is a little too involved for my needs.  I was looking for an encryption program I could use on my dual-boot machine so I could access encrypted files regardless of which OS I booted.  

AxCrypt for Windows is nice as it allows you to encrypt single files and with a simple &#8220;click&#8221; and password entry it temporarily de-crypts the file and calls the associated application to open the file.  When you close the file it automatically re-encrypts it again. It&#8217;s pretty slick!  

Now that I got it to work in Wine, (it couldn&#8217;t resolve the linux portion of a path without the scripts [Thanks! to L. Rahyen!]) I can access my encrypted files on both OS&#8217;s.

AxCrypt is GNU Open Source, if I had the expertise I would provide a linux version, but&#8230;  maybe some one with the knowledge, skill set and &#8220;spare time&#8221; can pick up the code and &#8220;tweak&#8221; it into a linux version.  The code is available at: [http://sourceforge.net/projects/axcrypt]("http://sourceforge.net/projects/axcrypt")

---

