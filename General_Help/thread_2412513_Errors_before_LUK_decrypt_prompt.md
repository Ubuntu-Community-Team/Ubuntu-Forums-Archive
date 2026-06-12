---
title: "Errors before LUK decrypt prompt"
date: 2019-02-14
forum: General Help
---

### Post by toad007toad007 on 2019-02-14
I'm running Ubuntu 18.04 bionic...So I recently got plymouth installed and working and it prompts me for my passkey to decrypt my drive, however, before that screen I get a series of errors that show up, then disappear, then show up again, then disappear before plymouth takes overs. This all happens in maybe 2 seconds. Is there a way to log these errors, or read where they are logged at and figure out what is causing them? They unnecessarily delay my boot time and are a minor annoyance. Prior to my install of plymouth I never got (or saw) these errors...Any help is appreciated!!!

EDIT: 
I opened my /var/log/boot.log and it's empty...
Any ideas?

---

### Post by TheFu on 2019-02-14
Check the other log files in /var/log/ ... also check dmesg and journalctl for older logs. You can tell journalctl to output entries from a specific time, so keep accurate track of what time your computer thinks it is.

And please be 100% certain you have excellent backups for any encrypted data you don't want to loose.  Anytime encryption is involved, there isn't any data recovery for HW or serious logical errors except what is provided though backups.

---

### Post by toad007toad007 on 2019-02-14
Thanks for the tips! I keep most of my data on an unencrypted 2tb drive and also have an external 2tb backup drive i use for backups. I will check over the logs when I have time and try to pin this down so I know where to focus my efforts. Didn't find any errors with dmesg or journalctl. Stupid question, the errors flashing couldn't just be because my root partition is encrypted and it needs to be decrypted first? If so, how do I disable the text from flashing? It annoys me... Thanks again.

---

### Post by toad007toad007 on 2019-02-14
Ok so I reread the log wit journalctl and I found the following error. Which I confirmed is the one that I am seeing on bootup...

tpm tpm0: TPM error (378) occurred get tpm pcr allocation

So I ran dmesg | grep -i tpm

And I get this:

 0.000000] ACPI: TPM2 0x000000007F3FFB90 000034 (v04 DELL\x CBX3     00000001 AMI  00000000)
 0.928398] tpm tpm0: A TPM error (378) occurred get tpm pcr allocation
 1.019704] ima: No TPM chip found, activating TPM-bypass! (rc=-19)

So knowing nothing about TPM other than what I briefly read on Wikipedia, I don't know what to do here? I also booted to a live disk and used gparted to check/repair the drives and they came back with nothing wrong with them. Any suggestions Ubuntu world?

EDIT: After doing some reading on the 'net it seems that this is a bug with the version of the kernel used in 18.04 in that it doesn't support Intel Platform Trust Technology. Apparently 18.10 doesn't have this problem...oh well, minor annoyance. Hopefully Canonical will release a kernel update for 18.04 soon. Thanks all.

---

### Post by TheFu on 2019-02-19
18.04.2 was released with an HWE kernel this week.

I know little about TPM, but think it is completely optional to add a HW connection to signed boot programs and for maintaining keys in a secure way outside RAM or storage.

---

