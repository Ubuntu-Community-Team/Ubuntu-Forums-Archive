---
title: "modified /usr permissions; now locked out"
date: 2017-06-16
forum: General Help
---

### Post by navonod on 2017-06-16
Hi

In a fit of carelessness&#8203; while attempting to get Apache permissions correct for localhost development, I accidentally changed the permissions of my /usr directory with "sudo chmod o-r usr" and "sudo chmod o-x usr".

The result has been catastrophic, as I'm now unable to boot into Ubuntu- this after applications started dying on me the minute I made those changes, and I lost access to the sudo command to be able to revert them &#128529;

My feeling is that I'll probably be having to cut my losses and do a system reinstall, but if anyone can advise of a better way for this noob to&#8203; regain access, it'll be greatly appreciated.

---

### Post by navonod on 2017-06-16
I managed to fix this by booting into recovery mode, dropping to the terminal as root, remuonting the primary drive with write permissions, and then reassigning the rx permissions to other on the /usr directory... whew!

---

### Post by Impavidus on 2017-06-17
That would solve it. Be glad that you didn't do a recursive chmod on /usr, as that would have required a reinstall. Could you mark this thread as solved?

---

