---
title: "What is the proper way to uninstall wine and reinstall wine x86. and uninstall ruby"
date: 2014-09-26
forum: General Help
---

### Post by andreadixon825 on 2014-09-26
What is the propar way to uninstall wine and reinstall wine x86. and uninstall ruby and reinstall ruby 2.0.0 x86. Please help me. Thanks

Andrea

---

### Post by TheFu on 2014-09-26
Ruby is a development language - if you just want to use ruby tools, not write any scripts, 

sudo aptitude purge ruby*
sudo aptitude purge wine*

rm -rf ~/.wine*

Then use **sudo aptitude install wine ruby** to get those installed again.

I don't knwo the exact package names - they change from time to time and often more than 1 is available so a different version can be installed on a single system.

I use aptitude over apt-get. It is smarter for dependencies and cleaning up than apt-get or synaptic or software center. In theory, it shouldn't matter which of these tools are used.  Also - I don't recall whether aptitude works with wildcards either. Sorry.

---

### Post by andreadixon825 on 2014-09-26
Thats ok this will work thank you vary much :)

---

