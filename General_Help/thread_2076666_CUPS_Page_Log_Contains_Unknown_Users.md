---
title: "CUPS Page_Log Contains Unknown Users"
date: 2012-10-26
forum: General Help
---

### Post by Kirk Schnable on 2012-10-26
I am currently trying to setup some reporting for our CUPS server at our organization, so we can generate reports by user and by printer indicating how many documents are printed, etc.

I created a script to parse the CUPS logs and put them in SQL, then I found something strange.  We have 14,100 records of printed documents accumulated.  Of those, I have 809 records printed by the user "unknown".

Our computers are managed by the IT department, and I know some of our staff laptops are single-user machines.  However, I have records of print jobs coming from their IPs as "unknown", and I have other jobs that come through with their actual username listed.

It's weird.

Here's the type of log data I'm talking about:
[img]http://www.epecweb.com/pub/ubuntu-cups-log-unknown-users.png[/img]

Right now, I'm trying to get this nailed down, and figure out why the users are being logged as unknown.

Has anyone ever seen this before, or does anyone have any input?

Thanks
Kirk

---

### Post by dino99 on 2012-10-26
if you know who own that 10.9.20.53 address then you need to investigate why it cant answer to cups request (misconfiguration i suppose, or shutdown)

---

### Post by Kirk Schnable on 2012-10-26
> **dino99 said:**
> if you know who own that 10.9.20.53 address then you need to investigate why it cant answer to cups request (misconfiguration i suppose, or shutdown)

The 10.9.20.53 client was configured to directly connect to our CUPS server (Ivory).

We have in the client.conf:
ServerName ivory

Many of our computers are configured this way, and only a select few have ever had this problem.  Since we are not using the local CUPS server, this problem doesn't exist on the machine.

The problem is also not consistent.  The user of this particular computer has actually had logged print jobs for their username today.  

I have seen the issue on several different users' laptops, but all of those users DO have jobs logged from them too (as their username, not as unknown).  It's not a persistent problem, I am still working on figuring out the root cause.

---

### Post by dino99 on 2012-10-26
have no clue, but maybe something to glance at: how that user name is written ? i mean maybe its a stupid character (space/uppercase/accent/comma/period/non utf-8 symbol  etc) that is not recognized. Are you having unicode errors logged also ?  How are the logs of that user ?

---

### Post by Kirk Schnable on 2012-10-26
> **dino99 said:**
> have no clue, but maybe something to glance at: how that user name is written ? i mean maybe its a stupid character (space/uppercase/accent/comma/period/non utf-8 symbol  etc) that is not recognized.

Nope, our users are all authenticated via Active Directory so we keep the crazy characters at bay.  The username was just 6 conventional English letters.

Since we're directing the printing straight to Ivory, there are no logs on the client for CUPS either.

Kirk

---

### Post by dino99 on 2012-10-26
hm, i've no more idea right now to help you, maybe you should ask devs on askubuntu, to get better way to debug that issue.
About that printer, is it a unique model that could explain the problem ?

---

### Post by Kirk Schnable on 2012-10-26
> **dino99 said:**
> hm, i've no more idea right now to help you, maybe you should ask devs on askubuntu, to get better way to debug that issue.
About that printer, is it a unique model that could explain the problem ?

Nah, all but two of our labs are HP LaserJet 4200 series.  All of them are HP LaserJets of some kind.  We're using the same Generic PCL driver for all of our lab printers.

Kirk

---

### Post by dino99 on 2012-10-26
> **Kirk Schnable said:**
> Nah, all but two of our labs are HP LaserJet 4200 series.  All of them are HP LaserJets of some kind.  We're using the same Generic PCL driver for all of our lab printers.

Kirk

Sorry i'm off, good luck .

---

### Post by Kirk Schnable on 2012-10-29
Does anyone else have any suggestions on this?  We have already had 7 unknown print jobs today.

---

