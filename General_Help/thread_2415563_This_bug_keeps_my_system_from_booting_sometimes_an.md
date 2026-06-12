---
title: "This bug keeps my system from booting sometimes and solution for info Ubuntu 18.04 LT"
date: 2019-03-27
forum: General Help
---

### Post by richard378 on 2019-03-27
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/1579580](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/1579580)

I fix my no boot problem by booting into recovery and droping to root prompt and follow step #19 in the bug report.
1. run 'sudo ureadahead --force-trace --verbose /'
2. wait a little and press CRTL-C
3. reload system - messages should disappear.

I wait 5 minutes during step 2 and then type CTRL-C then reboot and my system boots up.
This is info for anyone who has problem booting Ubuntu 18.04.02 LTS 

I get this problem frequently over serveral installs.

---

