---
title: "Fiesty Fawn - Firestarter doesn't survive"
date: 2007-09-08
forum: General Help
---

### Post by A_Nonny_Moose on 2007-09-08
Tried a search but nothing seems to fit.

Firestarter doesn't survive the hibernate process.  Is the best work around to terminate it before hibernation?

Frankly, I was only testing, because I have the startup session to get it going anyway.  I was hoping the avoid the password requirement when starting it.

Would this go away if I changed my group id to root?

---

### Post by TheExplorer on 2007-09-08
Seems that ubuntu has got problems with hibernation. Better not use it until it is properly fixed by programmers.

---

### Post by A_Nonny_Moose on 2007-09-08
Thanks.  I had a suspicion that all was not well.  Firestarter actually hung.  So, since come up is pretty quick (compared to XP it is instantaneous), I'll just stick to ordinary operations.

---

### Post by JBAlaska on 2007-09-08
The way I understand firestarter, It just modifies the iptables rules, so it does not have to be running all the time. When you have your firewall configured the way you want it, you should be able to close firestarter.

Also I beleive you should run firestarter as root.

Someone please correct me if I'm wrong.

---

### Post by Vadi on 2007-09-08
Yeah, firestarted is just a GUI for the iptables - and Ubuntu Fiesty already comes with iptables pre-configured just fine.

To test, just go to the S[hields UP! website]("https://www.grc.com/x/ne.dll?bh0bkyd2"), and test your machine.

You'll find that it's firewalled already out of the box :)

---

### Post by A_Nonny_Moose on 2007-09-10
Yes, I had that impression.  I guess I'll discontinue firestarter, but it did catch a couple of hits on TCP by Microsoft trying to send me XP updates, I think.  The IP definitely was MS.

---

