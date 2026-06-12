---
title: "Sharing a notebook's keyboard over bluetooth. Is it possible?"
date: 2017-12-21
forum: General Help
---

### Post by fparri on 2017-12-21
I was wondering if it is possibile to share my notebook's keyboard with my iPad and Android smartphone over bluetooth. If so, can you please point me to a good tutorial or to good information about it?

Thanks a lot and best wishes in advance!

---

### Post by DuckHook on 2017-12-21
:confused:

What version and flavour? What HW? Are you really still using Raring? It has been obsolete for years and nothing can be downloaded on it because the repos are no longer available. It would be impossible to modify or add anything.

---

### Post by fparri on 2017-12-22
Ah sorry, no, I just forgot to update my profile. I'm on 16.04 LTS ;)

---

### Post by DuckHook on 2017-12-22
Firstly, there's this: [https://play.google.com/store/apps/details?id=de.onyxbits.remotekeyboard&hl=en](https://play.google.com/store/apps/details?id=de.onyxbits.remotekeyboard&hl=en)

It has the advantage of being dirt-simple, efficient, well-tested and therefore robust. It's huge major disadvantage is that it runs on top of telnet. Telnet is likely the biggest security risk in computing. It has absolutely no security safeguards except common passphrases, which, if you take no further measures, is broadcast across the network in the clear. Personally, I don't want anything to do with telnet and have disabled it in all of my servers and workstations. Your risk tolerance will vary.

Then there's this: [https://serverfault.com/questions/43615/setup-a-linux-computer-to-act-as-a-bluetooth-keyboard-mouse](https://serverfault.com/questions/43615/setup-a-linux-computer-to-act-as-a-bluetooth-keyboard-mouse)

The thread is very old and possibly obsolete. However, it provides directions about how to manipulate the bluetooth stack to make it an outgoing HID device. I will warn you now in bold print that **fooling around with your bluetooth stack risks gumming up your whole wireless subsystem.** You are on your own if you decide to try this. The potential complexities involved in trying to fix things will likely leave a virgin re-install as the best recovery option. Make sure you have all of your data properly backed up.

In light of the difficulties, I can only wonder why you don't buy a cheap foldable bluetooth keyboard for your phones and tablets? I bought one on ebay for US$12. It charges by micro USB, lasts about four hours on one charge and folds in half into something not much larger than a cell phone. One of the best $12 I've ever spent.

---

