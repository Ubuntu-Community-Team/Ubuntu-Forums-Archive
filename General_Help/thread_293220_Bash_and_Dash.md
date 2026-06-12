---
title: "Bash and Dash"
date: 2006-11-04
forum: General Help
---

### Post by BorgHunter on 2006-11-04
After upgrading to Edgy, I never could get FrostWire to work. After a bit of looking around, I discovered that Edgy's switch to Dash was the culprit causing runFrost.sh to choke. I followed the advice given here to run "sudo ln -sf /bin/bash /bin/sh" to make Bash my default shell. Big mistake. After doing this, my main problem is now that Edgy simply will not connect with my network, at all. Also, I can no longer access previous shell commands by using the up arrow. And finally, mentioned here more as an oddity than anything else, rather than seeing "borghunter@ares $" as my prompt, I have a naked "$".

I attempted to fix the problem by running "sudo dpkg-reconfigure dash", but it didn't alter things a bit. Looking in /bin, the files bash and sh both happen to link to /bin/dash. What's the fix to convince Edgy to act normally again?

---

### Post by taurus on 2006-11-04
Maybe try to boot into a recovery mode and remove the link from /bin/bash to /bin/dash.  Then reinstall bash again with aptitude!!!

Otherwise, you can boot from the LiveCD, mount your harddrive where / is.  Then remove /bin/bash from your harddrive and copy /bin/bash from the LiveCD to your harddrive again...

---

### Post by LenzM on 2006-11-05
Are you sure you didn't accidently link bash to sh, that would explain why just '$' appears on the prompt.

---

### Post by jocko on 2006-11-05
> **BorgHunter said:**
> Looking in /bin, the files bash and sh both happen to link to /bin/dash. What's the fix to convince Edgy to act normally again?

/bin/bash should not be a link, it should be an executable file. If you've managed to replace bash with a link, try to replace it with a real /bin/bash from a live cd. Or you could delete the link /bin/bash and reinstall bash (if aptitude or synaptic works in your current situaton?)

---

