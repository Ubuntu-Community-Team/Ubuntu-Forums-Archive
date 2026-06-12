---
title: "killed firefox"
date: 2008-02-02
forum: General Help
---

### Post by Speedy162005 on 2008-02-02
So I managed to kill my firefox when I was rolling back from firefox 3 beta to Firefox 2.0.11

I click the launch icon and get the error message 

"Could not launch menu Item. Failed to execute child process. "Firefox" no such file or directory.

Anyways, I tried reinstalling through synaptic, it didn't work, I tried to manually download and follow instructions, nothing, I completely uninstalled and reinstalled, still nothing.

There is nothing in the /usr/bin file about Firefox and I'm still too new to figure out how to get it back in. Please help

---

### Post by SpiderGorilla on 2008-02-02
What version of Ubuntu are you running?

And have you tried to go into Synaptic Package Manager, click the "Status" button at the lower-right and checked to make sure Firefox 3 isn't still in the "Non installed (residual config)"?

Have you tried:

sudo apt-get autoremove
sudo apt-get autoclean

At all? Might help. I dunno. I just discovered autoclean and the Synaptic thing earlier tonight. So you might want to consider waiting for a better response.

---

### Post by Speedy162005 on 2008-02-02
Ubuntu 7.10.

I've looked through that stuff already, I think my problem lies with the /usr/bin folder where it is looking for the script that isn't there.

---

### Post by SpiderGorilla on 2008-02-02
This might be helpful:

[http://ubuntuforums.org/showpost.php?p=4162930&postcount=6](http://ubuntuforums.org/showpost.php?p=4162930&postcount=6)

---

### Post by Speedy162005 on 2008-02-02
Thanks for your help.

I got it working and figured out how soft links work in the process.

---

