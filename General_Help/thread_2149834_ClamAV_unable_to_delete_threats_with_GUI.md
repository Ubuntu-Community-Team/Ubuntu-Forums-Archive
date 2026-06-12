---
title: "ClamAV unable to delete threats with GUI"
date: 2013-05-30
forum: General Help
---

### Post by Handssolow on 2013-05-30
A ClamAV scan found about 27 threats, mostly associated with spam emails it seems. Having highlighted the threats I am unable to delete or quarantine them using the ClamAV GUI. ClamAV is up to date.

I know the virus/Trojan threat is minimal but I run some programs under Wine and I would like to delete the offending files even if they are sitting in Evolution.

Suggestions please

---

### Post by SeijiSensei on 2013-05-30
If the files are email attachments, you're much better off deleting the messages themselves via Evolution.  If you mail is stored in mbox format, where all the messages are in a single file, then there really is no other way to delete just the viruses without having to delete all your mail.

That said, it's very rare nowadays for viruses to appear in emails since nearly every mail provider quarantines them before delivery.  If you are still getting messages with viruses attached, I suggest you ask your provider why they haven't been blocked at the source.  

If you're running your own mail server, then you should be scanning every message that arrives using something like amavisd or, my favorite, the comprehensive virus and spam scanning tool called [MailScanner](http://www.mailscanner.info/).

Also be aware that ClamAV has a tendency to generate false positives for certain types of "trojans."  Clam routinely identifies some files from places like WindowsUpdate as containing "trojans," when that is obviously not the case.  I suspect that the virus submission system with ClamAV may play a role.  It makes it easy for anti-Microsoft types to upload alleged virus "signatures" to the Clam maintainers.  Given the sheer volume of submissions each day, false positives can remain in the signature list for quite some time.

---

### Post by Handssolow on 2013-05-30
Thanks

I was able to manually delete individual emails with their trojan attachments. Unsurprisingly they were spam/phishing emails I'd previously deleted in Evolution and are still there despite me emptying Evolution's Rubbish Bin. (I don't open emails with html, only text format)

There were a few false positives from pdf  files but a program I'm intending to run under Wine shows to have a Trojan Dropper. I'm not sure how I can separate the Trojan from the exe file. It's possibly a low risk threat but I'm not certain. It does appear I can delete both the pdf files and the program file using the ClamAV GUI but not the evolution files probably for reasons you've suggested.

---

### Post by SeijiSensei on 2013-05-31
If you are going to run the program with WINE, then there is little cause for concern.  I'd first create a tarball snapshot of /home/username/.wine/ so you can save the complete environment before running the file.  If you run the program and begin detecting something engaged in bad behavior, you can just blow away /home/username/.wine and recreate it from the clean snapshot.

```

cd 
tar cjvpf wine-backup.tar.bz2 .wine

```

Running Windows in a [VirtualBox]("http://www.virtualbox.org/") virtual machine is another good method for testing.  Again, you can create a snapshot of the virtual machine's state before running the suspect program so you can revert if necessary.  I generally do not use WINE for Windows programs but prefer using a VM with a complete Windows environment.

---

