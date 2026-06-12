---
title: "Firewall"
date: 2005-11-02
forum: General Help
---

### Post by Randy Sparks on 2005-11-02
I understand that Ubuntu doesn't include firewall software. 

Does this mean that the required components (iptables etc) aren't in the kernel, or does it mean that they're present but there's simply no software to administrate them?

---

### Post by dbott67 on 2005-11-02
iptables is there (afaik, anyhow --- I installed a firestarter without any problems)

You can download 'firestarter' via apt-get or Synaptic. There are a few others that have been posted in the forums, but I am using firestarter.

-Dave

---

### Post by wylfing on 2005-11-02
Firewalling is "naturally" part of how network traffic is managed in Linux. It's really not necessary to install anything at all if you want to learn how to edit your iptables by hand. 

If you're like me and that's not appealing, you can install the firestarter package (as dbott67 wisely recommended). You will get a nice interface for customizing how the native iptables block or allow various kinds of traffic. It isn't necessary for the firestarter graphical interface to be running for the firewall to be doing its job -- remember, firestarter just makes changes to how Linux "naturally" manages its network traffic -- so you can safely close it after you're done making your changes.

---

### Post by Randy Sparks on 2005-11-02
Thanks for your help. That's just what I needed to know.

But I'm sure that when I tried compiling my own kernel there was an option not to include iptables...

---

