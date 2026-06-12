---
title: "Grub_is this correct?"
date: 2019-11-27
forum: General Help
---

### Post by carusoswi on 2019-11-27
I have been experiencing slow or no boot (freeze on grayish blank screen) since I updated to Ubuntu 19.10.  My computer is an Asus g74sx, plenty of disk space and memory.  I read the following thread posted by OldFred on 7/16/19.  Edited my grub per his suggestion.  I have only booted once since, but the process was completed in 30 seconds or less, which is acceptable to me.  What I would ask now is for someone knowledgeable to review the contents of my Grub file and let me know if my edit is correct (OldFred posted the required edit lines, but did not post the entire contents of Grub).  My machines boot time is much improved after the edit, so, at least, I did not break my installation.

I appreciate any advise.

Caruso

---

### Post by carusoswi on 2019-11-27
Sorry, I forgot to post the contents of my Grub file.  Here it is.

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"
GRUB_CMDLINE_LINUX=""

Thanks.

Caruso

---

### Post by oldfred on 2019-11-27
Oldfred has no clue what he posted yesterday, much less last July.  Post several times on slow boot.

If you want to refer to a specific thread that would help.
And post the usual, only first few lines on longer ones or use code tags (# in forum's advanced editor):

       systemd-analyze
systemd-analyze blame
systemd-analyze critical-chain

---

### Post by carusoswi on 2019-11-27
> **oldfred said:**
> Oldfred has no clue what he posted yesterday, much less last July.  Post several times on slow boot.

If you want to refer to a specific thread that would help.
And post the usual, only first few lines on longer ones or use code tags (# in forum's advanced editor):

       systemd-analyze
systemd-analyze blame
systemd-analyze critical-chain

I didn't think it particularly important that Oldfred would need to refer back to the referenced post.  "He" is clearly very knowledgeable and also very helpful, as his suggested bit of code seems to have solved my problem: 

GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"

"He" also advised to add # before:  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" so that if I wanted to switch Grub back to its normal state, it would be easier for a novice such as me.  What wasn't clear was whether I should keep that last line: GRUB_CMDLINE_LINUX="".  I took a chance and kept it.  I figured listing my Grub as it currently exists would allow someone to ascertain if it is valid in its current state.  Since boot did what was suggested it would do (scroll all the commands as they were executed), and, since my computer, which was nearly revolting at my attempts to boot it, is now behaving civilly, I am one happy camper.  If you see Oldfred around or happen to know "him", please pass along my sincere appreciation.

This forum has always been a wonderful source of information for solving problems.

Caruso

---

### Post by oldfred on 2019-11-27
Thanks.

Just for reference from grub. There does not seem to be a man page, but I either copied from on-line manual or info grub (which is too long to review).

>         GRUB_CMD_LINUX


[LIST]
[*]Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel.
[/LIST]
 GRUB_CMD_LINUX_DEFAULT="quiet splash"

[LIST]
[*]This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only.
[/LIST]
     o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash".  
     

---

### Post by uRock on 2019-11-27
> **oldfred said:**
> Thanks.

Just for reference from grub. There does not seem to be a man page, but I either copied from on-line manual or info grub (which is too long to review).

I found this, [https://www.gnu.org/software/grub/manual/grub/grub.html](https://www.gnu.org/software/grub/manual/grub/grub.html) though it's not the typical "man page".

---

