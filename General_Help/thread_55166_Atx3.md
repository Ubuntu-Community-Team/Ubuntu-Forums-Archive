---
title: "Atx3"
date: 2005-08-07
forum: General Help
---

### Post by Zalbor on 2005-08-07
I'm currently using Fedora Core 3, and I want to change to Ubuntu. However, before installing it I decided to try the live edition to see if everything works ok.
To connect to the internet, I use a PSTN dial-up connection. Since the dial tone over here isn't the kind that the modem would recognize as a dial tone, I need to initialize it with the ATX3 command. Currently, I do that by unselecting the "Wait for dial tone" box when I use KPPP, or adding "ATX3" to the "modem initialization string" in GNOME's tool (version 2.8).
But in Ubuntu the graphical tool has neither of these options. So I tried to find which file contains the script and add the command there. I think that file is /etc/chatscripts/ppp0. So I tried adding ATX3 at various points in it, even replacing ATZ with it, and none of these worked: the modem still doens't dial because it thinks there's no dial tone. And when I check that file again, I see that "ATX3" has been changed with "ATX3L2".

So how do I connect to the internet? Am I trying to change the wrong file? Is there only a problem because it's the live edition and not one I've installed to the hard drive? Or is it something else?
Internet connection is one of the basic things (if not THE thing) that I need my computer to do.

Thanks in advance for your help.

---

### Post by Zalbor on 2005-08-11
Please! Does no one know of a way to do this? I need to have it fixed!

---

### Post by Zalbor on 2005-08-12
Well, they told me to use "sudo pppconfig" and this one worked.

---

