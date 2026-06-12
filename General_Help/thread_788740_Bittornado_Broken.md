---
title: "Bittornado Broken"
date: 2008-05-10
forum: General Help
---

### Post by joeinazyes on 2008-05-10
After upgrading from Gutsy to Hardy, Bittornado will no longer launch.  I have uninstalled it through synaptic, rebooted, and reinstalled through synaptic with no change in the result.  I must be conditioned by Windows to think that such an operation would fix the problem.

I used to launch a bittorrent file by right clicking, then choosing open with bittornado.  Now, absolutely nothing happens when I do this.  I've also tried launching bittornado from the Applications>Internet toolbar, but once again absolutely nothings happens as if I never executed the operation.

Please help, this only has happened since upgrading to Hardy.

Thanks.

---

### Post by joeinazyes on 2008-05-17
So nobody has a clue about this problem, which has been reported by others besides myself?...

---

### Post by messelink on 2008-05-19
Having problems with TorrentFlux, which is a WebGUI for BitTornado. Torrents seem to start fine but the whole box crashes after a while.

---

### Post by daki on 2008-06-20
The problem is with wxpython.  The program is trying to import * from wxpython.wx, but can't, so it breaks.  I'll post when I figure more out.

---

### Post by daki on 2008-06-20
[https://bugs.launchpad.net/ubuntu/+source/bittornado/+bug/206898]("https://bugs.launchpad.net/ubuntu/+source/bittornado/+bug/206898")
I had to remove ubuntu's bittornado and bittornado-gui package and download and install bittornado and bittornado-gui from debian unstable repositories.

---

