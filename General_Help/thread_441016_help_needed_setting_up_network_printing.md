---
title: "help needed setting up network printing"
date: 2007-05-12
forum: General Help
---

### Post by night116 on 2007-05-12
I have just upgraded to 7.04 and now my network printing and network have disappeared and do not work.
I have a brother hl-1230 connected to my windows machine running xp and for the love or money linux will not see my printer or whats on my windows networks. Can anyone please help me of how to setup or point me in the right direction.

---

### Post by cmost on 2007-05-12
My Windows network disappeared upon upgrade to Fesity as well.  I wonder if it has something to do with the new automagic network discovery system (similar to Apple's Bonjour) that is implemented in Feisty.  Fortunately, my server is both a Samba and a NIS server so i've attached my network shares with NFS for the time being.

---

### Post by tagra123 on 2007-05-13
I have no problems with the samba sharing. Make sure your domain is set to mshome or whatever you actually use. Another way is to edit the hosts file and do add something similar to this:

192.168.1.55 yourcomputername yourcomputername.mshome


As for printing -- good luck via network. It's really, I mean really messed up now. No one seems to give a legit answer to the problem either. Here an ugly way of getting network printing to work.  [http://ubuntuforums.org/showpost.php?p=2591426&postcount=8](http://ubuntuforums.org/showpost.php?p=2591426&postcount=8)

I hope someone fixes it soon!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by strabes on 2007-05-13
I had no problems setting up printing from my kubuntu laptop to a shared printer on my desktop ubuntu computer (both running feisty).
You simply share the printer on the host PC and add the printer on the computer to which the printer is not attached using the line: > http://host.computer's.ip/printers/printername

I can't help you if the printer is connected to a windows host because I've never dealt with that.

---

### Post by tagra123 on 2007-05-13
What brand is your printer -- From what I've read most of the problems are occuring on Hp's

---

