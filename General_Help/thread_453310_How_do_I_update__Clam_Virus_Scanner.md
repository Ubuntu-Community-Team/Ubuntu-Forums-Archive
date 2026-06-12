---
title: "How do I update  Clam Virus Scanner?"
date: 2007-05-24
forum: General Help
---

### Post by explorer716 on 2007-05-24
When I open Clam TK  Virus Scanner, I get this message, "Warning! Your virus signatures are 42 days old!"

When I click on Help>Update Signatures  I get another message stating, "You must be root to install updates."

I am a recent convert from Windows XP to Ubuntu and I am still feeling my way around.  I would appreciate very  much if someone would explain how to proceed.

Thank you in advance

---

### Post by fanatik on 2007-05-24
well you should really be running clam as root anyway, else the only files you will scan will be the ones you have read access to... this won't necessarily be all files on your system.

how do you start clam in the 1st place?

if its via the command line run it with:

$ sudo clamscan

or whatever it's called. enter your own password, and it will allow you to run it as root. then you should be able to update your virus defs etc.

---

### Post by vtel57 on 2007-05-24
To update ClamAV:

```
$ sudo freshclam
```

Note: If you'll open the GUI (graphic frontend) for ClamAV, I believe there are settings to allow for automatic updating. It's been a while since I set mine up... don't remember for sure.

---

### Post by ikonia on 2007-05-24
the command "freshclam" will also get you the virus definitions you require.

---

### Post by explorer716 on 2007-05-24
Thank you very for your help.

---

### Post by Nezing on 2007-06-26
I also have clamav installed.When I tried  **sudo freshclam** it did not work.Terminal just said:
"command not found"

But when I tried:

 sudo apt-get install clamav-freshclam

It updated.All is now fine.Funny old beast Ubuntu. :)

---

### Post by vtel57 on 2007-06-27
Indeed. You had to install the Freshclam application before you could initiate it. You did good. Glad to see you got it working. :)

Luck!

---

### Post by Qu4k3R on 2007-06-28
You can also update clamtk with

> 
gksudo clamtk


Then go to "Help menu" tab and then Update.

---

### Post by YMS_1975 on 2007-11-08
I've followed your directions to upgrade my definitions, but when I do that, while it does accept the terminal command & my password, it fails to update the signatures.

Instead, the window goes dark grey for about 30 seconds white it reads : 

"**Please wait, checking for updates...**" and then a new message appears and it returns to it's normal white color. The new message then reads : 

"**Unable to retrieve updates. Try again later.**"

I know my internet connection is fine because I'm online here typing you this message, and everything else is ok, so what gives?  :confused:

---

### Post by dragon3700 on 2008-04-09
Re: How do I update Clam Virus Scanner?
I've followed your directions to upgrade my definitions, but when I do that, while it does accept the terminal command & my password, it fails to update the signatures.

Instead, the window goes dark grey for about 30 seconds white it reads :

"Please wait, checking for updates..." and then a new message appears and it returns to it's normal white color. The new message then reads :

"Unable to retrieve updates. Try again later."

I know my internet connection is fine because I'm online here typing you this message, and everything else is ok, so what gives? 

Use Qu4k3R Help

---

### Post by geezerone on 2008-04-10
```
Warning: No virus definitions found! If you are sure you have definitions installed, please inform the developer where your definitions are held so the paths can be added.
```I have installed clam, clam daemon and clamtk but get the above msg. I have started clamtk as root and updated signatures but still get this message when opening clamtk?

---

### Post by japsai on 2008-04-14
I had the same problem. This worked for me:

From a terminal: sudo freshclam -v

You should now see some copying of definition files, and afterwards, in "Virus Scanner"/ClamTK under system information, there should be a number of definitions and a date (14 april 2008 i think)

---

### Post by Gripp on 2008-04-20
thanks for the help guys :)

i'm also curious, one of my goals is to troubleshoot my XP install and i'm thinking running a virus scan on that drive from linux would be good to catch those codes that are hiding from my XP scanner

this scanner doesn't seem to perform well in that regard.  are there any programs out there that would be good for what i'm looking for here?

---

### Post by mckinneycm on 2008-05-12
This is what I get when I try to update ClamAV:

mckinneycm@mckinneycm-desktop:~$ sudo freshclam -v
Current working dir is /var/lib/clamav/
Max retries == 5
ClamAV update process started at Mon May 12 08:59:57 2008
Querying current.cvd.clamav.net
TTL: 16
Software version from DNS: 0.93
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.92.1 Recommended version: 0.93
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cvd version from DNS: 46
main.inc is up to date (version: 46, sigs: 231834, f-level: 26, builder: sven)
daily.cvd version from DNS: 7102
daily.cvd is up to date (version: 7102, sigs: 53034, f-level: 26, builder: ccordes)


I went to the site that it says and used the install package there.  And this is still what I receive.  Any help???

---

### Post by japsai on 2008-05-12
This looks just like a fine result.

The Ubuntu package is ofcourse slightly behind, but this is not a problem.

---

### Post by Nullack on 2008-05-27
How is it not a problem?

Have you reviewed the changelog on the clamav site?

How do we get an updated package into the ubuntu repository?

---

### Post by japsai on 2008-06-04
> **Nullack said:**
> How is it not a problem?

Have you reviewed the [changelog]("http://svn.clamav.net/svn/clamav-devel/trunk/ChangeLog") on the clamav site? 

yes, 0.93 is RC as far as i can see.

> **Nullack said:**
> How do we get an updated package into the ubuntu repository?

[they're working on it.]("https://wiki.ubuntu.com/MOTU/Clamav?highlight=(clamav)")

---

### Post by Nullack on 2008-06-07
[http://www.clamav.net/download/sources](http://www.clamav.net/download/sources)

Seems 0.93 is a production stable release version not sure why you think its an RC :)

---

