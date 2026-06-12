---
title: "How to monitor rsync and logins"
date: 2016-06-18
forum: General Help
---

### Post by EDamien on 2016-06-18
I noticed last night that rsync was running on it's own. And, it was running for quite a while.

Is there a utility or command to view rsync activity?

I do have a copy of dropbox on my PC. I know there weren't any new files or directories created to warrant 2 hours of file transfers.

Last, is there a utility to monitor and prevent remote logins?

---

### Post by QDR06VV9 on 2016-06-18
It sounds like you're looking for a "progress meter" or the like which would say you've moved 53% of the files or give the number of bytes transferred and remaining. Rsync doesn't support this function as far as I know.

If you use "-v" you'll get a list of files as they are sent that you can track with "tail -f /var/log/rsync" or wherever you direct the output. The "--stats" parameter provides summary statistics but not a progress measure. 

Credit to  SeijiSensei

---

### Post by HermanAB on 2016-06-18
You can also look at the network packets with tcpdump, or at the process and network activity with htop and ntop.

Otherwise, if you want to be hacked, run VNC and if you don't want to be hacked, run sshd...

---

### Post by QDR06VV9 on 2016-06-18
> **HermanAB said:**
> if you want to be hacked, run VNC and if you don't want to be hacked, run sshd...
Thanks for pointing me to this..I was not aware it was such a bad security hole. But i have only used  it locally.
But now I am.
Regards

---

