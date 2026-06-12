---
title: "I want rid - but there is a problem"
date: 2007-09-06
forum: General Help
---

### Post by demonmagus on 2007-09-06
Hi, I am running windows vista and ubuntu - basically I want to get rid of ubuntu since I don't really use it all that much. I thought I could just use windows partition manager  to delete all partitions and combine them to make one (windows) therefore deleting ubuntu and the rest of it? however when I turn the computer on I get GRUB loading and then error 22.

However I have deleted ubuntu (by killing the partition) 3 times before, and this error always happens, I can use the live CD to install ubuntu then go back to windows, and it will work fine but tbh I just dont need it any more and would like to 'eradicate' it


thanks

---

### Post by p_quarles on 2007-09-06
You need to restore the Windows MBR. Good step by step here:
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by Amof on 2007-09-06
That seems like alot of steps for just restoring the MBR. 

I'll give you a crash course. Put the windows CD in your machine, boot off it. Start the recovery cosole and type "fixmbr". The linux partition will still be there but it will boot to windows.

If you need a more in depth walk through then do what that guy said ^^^^^^

---

