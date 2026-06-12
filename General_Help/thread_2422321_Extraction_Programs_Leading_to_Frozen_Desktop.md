---
title: "Extraction Programs Leading to Frozen Desktop"
date: 2019-07-05
forum: General Help
---

### Post by robfeight on 2019-07-05
Greetings.

I'll get right to it. Been having a considerable amount of trouble with Ubuntu 19.04 locking up on the desktop--around thirty seconds after logging in. This typically happens the first time restarting after extracting files from a compressed folder. Ubuntu will continue to do this every time I try to restart, hence, leaving the OS unusable. Not even CTRL-ALT-F1 or any of the other F keys will respond. I just have to hard shutdown the machine.

The work-around I discovered is that if I log in with Ubuntu Live USB and delete the files that were extracted as-well-as the extraction program I used to do so (EDIT: via sudo nautilus), the system works fine again. This has been repeated twice. Once with P7zip, and once with B1freearchive.

I did read a post somewhere in a Google search that a user had almost the exact same situation. He'd narrowed it down to something along the lines of there being a compressed user password file of some sorts that was being effected by the extraction program. But, I'm not sure how much merit it deserves. I've also been having an issue with wifi slowing to trickle-speed randomly. But, if I restart it's fine again. Not sure if that's related.

I know I need to paste some system logs to get accurate troubleshooting done, so let me know what's needed. In the meanwhile, here's the Ubuntu log file that might get the ball rolling. Cheers.

19:55:20 gnome-session-b: Unrecoverable failure in required component org.gnome.Shell.desktop
19:49:50 spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
19:39:56 kernel: sd 1:0:0:0: rejecting I/O to offline device
19:39:09 kernel: Couldn't get size: 0x800000000000000e
19:39:09 kernel: MODSIGN: Couldn't get UEFI db list
19:39:09 kernel: Couldn't get size: 0x800000000000000e
19:39:09 kernel: ACPI Error: Method parse/execution failed \_TZ.TZ00._TMP, AE_NOT_FOUND (20181213/psparse-531)

---

### Post by SeijiSensei on 2019-07-05
What if you extract the files from the command prompt with unzip (traditional ZIP) or gunzip (gzip) or bunzip2 (bzip2) depending on the compression format? Same problems?

---

### Post by HermanAB on 2019-07-06
Ayup, some of the GUI zippers consume all available RAM and doesn't release it cleanly.  The command line utilities work properly.

---

### Post by robfeight on 2019-07-06
Will give the terminal method a go next time. What about that system log message? That doesn't seem good. Also, could the fact that Ubuntu asks for my password to log-on even though I have it set to log-on automatically be part of this problem? Remember, I mentioned before someone posted having the same issue, saying that he or she tracked it down to some compressed password protocol in the Ubuntu OS. And, went on to mention that it was caused by an extraction program.

---

### Post by SeijiSensei on 2019-07-06
Before delving into any of those things, do some tests with the command-line tools.

I don't know what "compressed password protocol" you could be talking about. By default Ubuntu uses the standard "shadow" password system that *nix systems have used for decades. Encrypted passwords are stored in /etc/shadow. On my system that is read/write to root and read-only to the shadow group. There are other methods of authentication available via [PAM]("http://www.linux-pam.org/"), but you would have had to do some serious customization to switch to one of those.

---

### Post by robfeight on 2019-07-07
Alright, well, thanks again. Used the terminal to an extraction, yesterday. So far, so good. I'll just let the password thing ride, I guess. I would like to get my boot-up time down to under four minutes, though. #-o

---

