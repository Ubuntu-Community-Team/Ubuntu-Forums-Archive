---
title: "Run a Perl app"
date: 2007-07-10
forum: General Help
---

### Post by Krepta3000 on 2007-07-10
Hello, I am trying to run a Perl app called Perl Cyan Chat Client, PCCC, on Ubuntu.  I can run it perfectly fine on XP, after installing ActivePerl and telling it to install the Win32/API package.  But I can't get it to run at all on Ubuntu.  If anyone has any knowledge about Perl on Ubuntu, can you help me?  It's not a serious issue, I'm just curious about getting it running.

---

### Post by DoktorSeven on 2007-07-10
What problems are you having?  Seems to run just fine here after downloading the Linux version and extracting to a directory in my home directory, then running PCCC.

(Try running from a terminal - Applications->Accessories->Terminal - assuming you extracted to PCCC-3.0_linux in your home directory, **cd PCCC-3.0_linux** then **./PCCC**, and see what it outputs.)

---

### Post by pjkoczan on 2007-07-10
> **Krepta3000 said:**
> Hello, I am trying to run a Perl app called Perl Cyan Chat Client, PCCC, on Ubuntu.  I can run it perfectly fine on XP, after installing ActivePerl and telling it to install the Win32/API package.  But I can't get it to run at all on Ubuntu.  If anyone has any knowledge about Perl on Ubuntu, can you help me?  It's not a serious issue, I'm just curious about getting it running.

I think perl is installed by default (if not you can always use synaptic or apt-get), but the problem may be that you don't have a proper module installed. Unfortunately, I don't know which modules are missing, and I don't know which packages may correspond to it.

One way to debug what's going on is to run perl with the application as the argument (e.g. /usr/bin/perl /usr/bin/pccc, appropriately substituting the correct paths and commands) and try to interpret any error output. Or, install and run the perl debugger.

The only other thing I can think of is that you're trying to run the windows version on linux. Although perl is very portable, if there are windows-specific paths, you're going to run into trouble.

In short, debug, possibly download a new version, and google any error messages that arise.

---

