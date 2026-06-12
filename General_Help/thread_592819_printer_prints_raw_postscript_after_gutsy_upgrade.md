---
title: "printer prints raw postscript after gutsy upgrade"
date: 2007-10-26
forum: General Help
---

### Post by bcrowell on 2007-10-26
After an upgrade to gutsy, I have a new problem with printing. It looks like cups no longer knows what to do with postscript. The symptom is that when I print over the network from a mac, I get raw postscript output. It used to work fine before the upgrade. I don't think it's really specifically a problem with network printing; probably the issue is just that the mac happens to send its output in postscript format. When Update Manager asked me whether it was OK to replace my old cupsd.conf file, I said yes, but I kept a copy of the old cupsd.conf file. Changing the cupsd.conf file back to the old version didn't cure the problem, so I don't think it's a misconfiguration there.

Any suggestions would be much appreciated.

---

