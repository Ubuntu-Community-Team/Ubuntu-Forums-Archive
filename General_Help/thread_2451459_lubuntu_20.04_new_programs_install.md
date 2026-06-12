---
title: "lubuntu 20.04 new programs install"
date: 2020-10-05
forum: General Help
---

### Post by Vesa_Vilkki on 2020-10-05
Hello i just upgrade my lubuntu 18:04 to 20.04 (new full install). Im now finding how install new programs. 

Have tryed this: sudo add-apt-repository ppa:lubuntu-desktop/ppa && sudo apt-get  update && sudo apt-get install lubuntu-software-center

and i get response this: tag:launchpad.net:2008:redacted
 More info: [https://launchpad.net/~lubuntu-desktop/+archive/ubuntu/ppa](https://launchpad.net/~lubuntu-desktop/+archive/ubuntu/ppa)
Press [ENTER] to continue or Ctrl-c to cancel adding it.

'Error reading [https://launchpad.net/api/devel/~lubuntu-desktop/+archive/ubuntu/ppa?ws.op=getSigningKeyData](https://launchpad.net/api/devel/~lubuntu-desktop/+archive/ubuntu/ppa?ws.op=getSigningKeyData) (4 tries): Unauthorized'

Edit: Sorry my bad english

---

### Post by guiverc on 2020-10-05
The PPA you mention is currently not in use (*it's disabled*), and is of no benefit for a Lubuntu 20.04 LTS system.

I would remove it.

As for adding programs/applications/packages, I'll refer you to the Lubuntu manaul.

[Chapter 2 - Applications]("https://manual.lubuntu.me/stable/2/Applications.html")
[Chapter 4 - Installing, Updating, and Removing Software]("https://manual.lubuntu.me/stable/4/Installing_Updating_and_Removing_Software.html")

Lubuntu 20.04 LTS uses LXQt and provides

- `muon` package manager (*the Qt equivalent of `synaptic` with Lubuntu 18.04 LTS which was GTK based*), plus
- Discover Software Centre (*the Qt equivalent of Ubuntu Software with GTK based releases such as Lubuntu 18.04 LTS*)

---

