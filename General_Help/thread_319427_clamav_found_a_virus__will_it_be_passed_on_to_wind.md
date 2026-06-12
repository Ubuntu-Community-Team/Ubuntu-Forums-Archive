---
title: "clamav found a virus?  will it be passed on to windows?"
date: 2006-12-15
forum: General Help
---

### Post by shane2peru on 2006-12-15
Ok, here is the deal.  I have virus protection, not because I'm concerned about my computer, but I don't want to be passing them on.  Sorry if this is a dumb question, I really am not that informed about Linux and Viruses.  In windows you HAD to be concerned about them.  Anyway, here is the output from my clamscan ```
clamscan -ir /home/shane/
LibClamAV Warning: ********************************************************
LibClamAV Warning: ***  This version of the ClamAV engine is outdated.  ***
LibClamAV Warning: *** DON'T PANIC! Read http://www.clamav.net/faq.html ***
LibClamAV Warning: ********************************************************
LibClamAV Warning: ********************************************************
LibClamAV Warning: ***  This version of the ClamAV engine is outdated.  ***
LibClamAV Warning: *** DON'T PANIC! Read http://www.clamav.net/faq.html ***
LibClamAV Warning: ********************************************************
/home/shane/temp/clamav-0.88.7.tar.gz: ClamAV-Test-File FOUND
/home/shane/temp/clamav-0.88.7/test/clam.cab: ClamAV-Test-File FOUND
/home/shane/temp/clamav-0.88.7/test/clam.exe: ClamAV-Test-File FOUND
/home/shane/temp/clamav-0.88.7/test/clam.rar: ClamAV-Test-File FOUND
/home/shane/temp/clamav-0.88.7/test/clam.zip: ClamAV-Test-File FOUND
/home/shane/temp/clamav-0.88.7/test/clam.exe.bz2: ClamAV-Test-File FOUND
/home/shane/.mozilla/firefox/3fgn3shk.default/Cache/B91504B6d01: HTML.Phishing.Gold FOUND
/home/shane/.mozilla/firefox/njkjpw7c.default/Cache/B91504B6d01: HTML.Phishing.Gold FOUND
/home/shane/.mozilla/firefox/2t8iniy1.default/Cache/2469E2EFd01: ClamAV-Test-File FOUND
/home/shane/.mozilla-thunderbird/2pvy3x2d.default/Mail/Local Folders-1/Inbox: Worm.SomeFool.P FOUND
LibClamAV Warning: messageFindArgument: no '=' sign found in MIME header
LibClamAV Warning: messageFindArgument: no '=' sign found in MIME header
LibClamAV Warning: messageFindArgument: no '=' sign found in MIME header
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: messageFindArgument: no '=' sign found in MIME header
LibClamAV Warning: messageFindArgument: no '=' sign found in MIME header
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: messageFindArgument: no '=' sign found in MIME header
LibClamAV Warning: messageFindArgument: no '=' sign found in MIME header
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: messageFindArgument: no '=' sign found in MIME header
LibClamAV Warning: messageFindArgument: no '=' sign found in MIME header
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
LibClamAV Warning: Multipart MIME message contains no boundaries
/home/shane/.mozilla-thunderbird/2pvy3x2d.default/ImapMail/mail.rices2peru.com/INBOX: Worm.SomeFool.P FOUND
LibClamAV Error: cli_untar: only standard TAR files are currently supported

----------- SCAN SUMMARY -----------
Known viruses: 82937
Engine version: 0.88.4
Scanned directories: 1558
Scanned files: 17674
Infected files: 11
Data scanned: 3045.00 MB
Time: 2961.260 sec (49 m 21 s)

```  It is my inbox that I am concerned about.  Can this be passed on to others via email?  Thanks.  I know I am probably just paranoid, but that is what 10 years of Windows will do to you.

Shane

---

### Post by lyceum on 2006-12-15
Short answer, yes. IF you have a Windows virus, you are a carryer, even if you are not affected.

---

### Post by mcduck on 2006-12-15
Not by itself, but if you send the email containing the virus to some windows user the virus will of course go with the mail.

---

### Post by Shatrat on 2006-12-15
> Short answer, yes. IF you have a Windows virus, you are a carryer, even if you are not affected.
How do you figure that?
I could have every worm and virus ever written for windows in a tarball on my desktop and as long as I dont do anything with it, Im not exactly contagious now am I?
As long as he doesn't forward that to anybody there isnt a problem.  
It can't forward itself on a linux system.

Personally, I would forward it to John C Dvorak and then delete it.

---

### Post by lyceum on 2006-12-15
> **Shatrat said:**
> How do you figure that?
I could have every worm and virus ever written for windows in a tarball on my desktop and as long as I dont do anything with it, Im not exactly contagious now am I?
As long as he doesn't forward that to anybody there isnt a problem.  
It can't forward itself on a linux system.

Personally, I would forward it to John C Dvorak and then delete it.

That is right, you would have to forward it in an e-mail or on a disk. It will/should not open and "infect" your machine. That would be the "longer answer." That is why Linux servers have virus stoppers/blockers etc.., to stop the file from getting on Windows machine. You are a carryer, as it is on the machine, as long as the file that has the virus is on the PC. I have heard of wine helping the virus, but do not know enought to say any more than that.

---

### Post by shane2peru on 2006-12-15
Is there a way to narrow it down and find out what file it is so that I can delete it?  And to make sure I understand.  The gist of it is that it will not pass itself on to other computers, only **IF** I forward the email in which the virus is contained.  Is that correct?  Thanks, I appreciate the help!

Shane

---

### Post by mcduck on 2006-12-15
> **shane2peru said:**
> Is there a way to narrow it down and find out what file it is so that I can delete it?  And to make sure I understand.  The gist of it is that it will not pass itself on to other computers, only **IF** I forward the email in which the virus is contained.  Is that correct?  Thanks, I appreciate the help!

Shane

that's correct. And ClamAV seems to tell you path to the file..

---

### Post by SuperMike on 2006-12-15
**shane2peru:** I believe there's no reason to be alarmed here, and I'll explain why.

Let's look at the output...

home/shane/temp/clamav-0.88.7.tar.gz: ClamAV-Test-File FOUND
/home/shane/temp/clamav-0.88.7/test/clam.cab: ClamAV-Test-File FOUND
/home/shane/temp/clamav-0.88.7/test/clam.exe: ClamAV-Test-File FOUND
/home/shane/temp/clamav-0.88.7/test/clam.rar: ClamAV-Test-File FOUND
/home/shane/temp/clamav-0.88.7/test/clam.zip: ClamAV-Test-File FOUND
/home/shane/temp/clamav-0.88.7/test/clam.exe.bz2: ClamAV-Test-File FOUND

These first few here are standard and are test files. That tells you that ClamAV is working properly. Good news for you.

/home/shane/.mozilla/firefox/3fgn3shk.default/Cache/B91504B6d01: HTML.Phishing.Gold FOUND
/home/shane/.mozilla/firefox/njkjpw7c.default/Cache/B91504B6d01: HTML.Phishing.Gold FOUND
/home/shane/.mozilla/firefox/2t8iniy1.default/Cache/2469E2EFd01: ClamAV-Test-File FOUND

These are in your Firefox cache that Ubuntu sees. Besides the ClamAV test file, these will only work in a browser like IE. Since you won't be opening these in your IE, even if you dual boot, then it's a non-issue.

/home/shane/.mozilla-thunderbird/2pvy3x2d.default/Mail/Local Folders-1/Inbox: Worm.SomeFool.P FOUND
/home/shane/.mozilla-thunderbird/2pvy3x2d.default/ImapMail/mail.rices2peru.com/INBOX: Worm.SomeFool.P FOUND

These reflect what's in your Thunderbird inbox. These in particular are designed to infect Windows Outlook Express, not Thunderbird. Much of anyone's spam coming into their Ubuntu email system is going to likely have all these exploits, worms, viruses, and so on in them. They're designed for unpatched workstations, and mostly for Windows. There are few of these in the wild designed for Thunderbird on Linux. And if there were, you can surely bet that the Linux gurus would be thwarting it rapidly. 

This is why I don't even bother with having my ClamAV scan my browser cache or inbox. I have it scan other things. Look in the howto guide **[here]("http://ubuntuforums.org/showthread.php?t=318091")** and you'll find I have a way to configure ClamAV to only notify you of the really important stuff, not these false positives. As well, I have my system updated every day as soon as I get the notices (or a couple hours later), and I always update my system before opening my browser or mail program.

I also have a howto **[here]("http://ubuntuforums.org/showthread.php?t=318207")** where you can add a firewall easily on your workstation for even more security.

---

### Post by shane2peru on 2006-12-15
Ok, thanks.  I appreciate the info.  I do dual boot, and understand the risk (for windows users) very well.  I scan my home regularly because I do dual boot, and go have a FAT32 partition that is linked to both, so an infected file in there **could** be a problem.  Although, I don't remember the last time I logged into windows.  :-k   Oh, well at any rate, I don't want to be passing viruses via email to my friends either.  I appreciate the help, and that is a relief!  I will read your how to's  I like the how to section, very helpful!

Shane

---

### Post by bodhi.zazen on 2006-12-15
IMO:

1. No, as of yet Windows viruses and worms can not propagate through Linux to Windows.

2. See here for [Running windows viruses on Wine](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

3. I do not feel obligated to protect windows computers from my Linux Desktop. If you choose to run windows it goes without saying you should run antivirus software. If you transfer files to Windows from Linux you should scan them with your windows antivirus, which is likely to be more sophisticated then Linux AV at the moment.

---

