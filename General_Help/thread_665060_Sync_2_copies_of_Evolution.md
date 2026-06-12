---
title: "Sync 2 copies of Evolution"
date: 2008-01-11
forum: General Help
---

### Post by Spenzer4Hire on 2008-01-11
I have Evolution 2.12 on 2 Ubuntu 7.10 boxes on the same Lan.  One is a work computer and one is personal.  On my personal computer I have a "Personal" address book and calendar.  On my business PC I have a "Personal" address book and calendar as well as a "Business" address book and calendar.  Is it possible to sync the 2 sets of "Personal" information?

Can it be done without relying on some sort of groupware server or Google?

Is it easier if I sync up all the data, not just "Personal" data?

Thanks in advance!

---

### Post by dcstar on 2008-01-12
> **Spenzer4Hire said:**
> I have Evolution 2.12 on 2 Ubuntu 7.10 boxes on the same Lan.  One is a work computer and one is personal.  On my personal computer I have a "Personal" address book and calendar.  On my business PC I have a "Personal" address book and calendar as well as a "Business" address book and calendar.  Is it possible to sync the 2 sets of "Personal" information?

Can it be done without relying on some sort of groupware server or Google?

Is it easier if I sync up all the data, not just "Personal" data?

Thanks in advance!

All the data is stored in the (hidden) .evolution directory on your home drive, you may be able to copy the relevant data from one PC to the other - either manually or figure out an automatic method.

---

### Post by Spenzer4Hire on 2008-01-12
Although I haven't tried to hack anything together, it seems Evolution appends the System Name on to its folders (and perhaps other settings).  Does anyone have any experience with this?

---

### Post by dcstar on 2008-01-12
> **Spenzer4Hire said:**
> Although I haven't tried to hack anything together, it seems Evolution appends the System Name on to its folders (and perhaps other settings).  Does anyone have any experience with this?

It does no such thing on my system.

---

### Post by HermanAB on 2008-01-13
The real solution is to install your own mail server so that you can use IMAP.  That way, all your mail, addresses and stuff resides on a central server and then it doesn't matter whether you use Thunderbird, Evolution, webmail or Outlook from 10 different machines, they will all have the same information.

Have a look at Citadel: [http://www.citadel.org/doku.php/installation:easyinstall:easyinstall](http://www.citadel.org/doku.php/installation:easyinstall:easyinstall)

Cheers,

Herman

---

### Post by Spenzer4Hire on 2008-01-13
I was hoping I wouldn't have to use groupware to keep 2 copies in sync, but it looks like I will.  Thanks.

---

### Post by erpo on 2008-01-13
You might be able to uae a program called multisync to do this.

---

### Post by Spenzer4Hire on 2008-01-13
Thanks erpo!  I should be able to get MultiSync to do the job.  The 2 computers on the LAN already share a NFS directory.  Using MultiSync I can sync to and from a file.  If I place this file on the NFS share both computers should be able to sync to and from it.

Now, if I leave MultiSync open on both systems it will synchronize at regular intervals.  What will happen if they both try to access the shared file at the same time?  I know Windows usually locks files during access.  I'm guessing Linux does not.  Could I be risking data corruption?  I'll keep backups for safety's sake, but I'm just curious.

Thanks again!

---

