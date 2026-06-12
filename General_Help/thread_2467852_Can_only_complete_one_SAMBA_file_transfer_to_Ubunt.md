---
title: "Can only complete one SAMBA file transfer to Ubuntu 20.04 a time without resetting"
date: 2021-10-09
forum: General Help
---

### Post by donaldlear on 2021-10-09
Using Ubuntu 20.04 as a Plex server on a home network otherwise populated with Windows machines and android devices. The Ub machine is headless, access via RDP. I am having a problem moving files from Windows 10 machines to the Ubuntu machine. I can only do one copy job at at time without resetting.  

Samba is set up and working on Ubuntu and I am sharing two directories. The Windows PC can access Ub's two shared directories and I can complete a copy job from Windows to Ubuntu. But just one. Attempting a second copy job to the same directory results in Windows displaying an error message ("The parameter is incorrect") and no connection can be established. If I reset either machine (doesn't matter which one) I can do another copy job. But just one. And if I wait long enough, say a couple of hours, I can do another copy job. But just one. Reset required. 

Added wrinkle #1: the connection error occurs independently for each of the two shared directories. A second copy job to the second shared directory will complete successfully. But just once. After that neither of the two directories can be copied to and a reset is required. 

Added wrinkle #2: the connection error occurs independently for each Windows machine on the LAN. Once I can no longer connect to either shared directory from my usual Win10 workstation I can go to another Win 10 machine and complete a copy job. But just one. 

Thank-you for any light that can be shed on this problem.

---

### Post by TheFu on 2021-10-09
Until you figure out the samba issue, could I recommend using WinSCP and ssh/sftp/scp instead?  If the ubuntu system is headless, then you probably manage it using ssh, so sftp is already working.

For someone to help, they'll need more facts ... like the smb.conf file that you modified.  Actually, the output from **testparm** would be better.
When you authenticate from Windows to Linux for samba, did you setup how long the credentials should be remembered?  I vaguely remember there are 3 choices.
[LIST]
[*]forget immediately
[*]remember for this session
[*]remember forever
[/LIST]

Perhaps you have the first selected?  What do the samba logs show for each connection?

BTW, what does "reset" mean?  Do you mean reboot or shutdown?  Have you tried restarting the smb daemon instead?  Did you modify any security settings for cifs connections in Windows?  Did you follow Morbius1's samba setup guide?

---

