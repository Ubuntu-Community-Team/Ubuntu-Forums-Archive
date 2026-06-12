---
title: "Samba share no longer accessible"
date: 2006-11-25
forum: General Help
---

### Post by HereInOz on 2006-11-25
Hi All,

Until recently I had a Samba share on my Ubuntu machine which was accessible from all the Windows machines on the network.  I found today that the Samba share was no longer accessible from any of the Windows machines, although I have not knowingly changed anything.  Not only is it not accessibel, but to be more accurate, it is not even showing on the network.  It is as if Samba is not even running.

I have checked the Firewall settings to make sure that the machines had correct permissions, and I have disabled the firewall just in case, I have re-set the samba password, I have deleted the samba shares and re-installed Samba, re-created the Samba shares and again re-set the Samba password.

I have checked that the Samba service is running, and I am able to connect to the windows shares from my Ubuntu machine without difficulty.

I can ping the Ubuntu box without any problem from the Windows machines.

Can anyone come up with something that I may have missed, or something that may have been in the last round of updates that could be causing this problem.

Hope someone can assist.

Cheers,

Alan.

---

### Post by HereInOz on 2006-11-25
I solved this one, but caused more problems with accessing my windows shares from ubuntu.  Will post again in Networking

---

### Post by HereInOz on 2006-11-25
I uninstalled and re-installed Samba components, and that got the Samba server working again, but clearly the uninstall took out something that has not been put back.

I should have read the list - Damn!

---

### Post by dbbolton on 2006-11-27
how can you check to see if samba is running ?

---

### Post by scrooge_74 on 2006-11-27
type smbtree

---

### Post by marx2k on 2006-11-28
You can also just restart it in case it ISNT running:

'sudo /etc/init.d/samba restart'

---

### Post by scrooge_74 on 2006-11-28
sometimes that command does not work for me so I prefer the old way

sudo smbd restart
sudo nmbd restart

---

