---
title: "How can you tell if a box is in recovery mode?"
date: 2007-08-07
forum: General Help
---

### Post by apoth on 2007-08-07
I've got SSH access to a box which didn't start any services after a power cut, though someone else has manually started some now. I've got a feeling it might've booted to recovery mode (I know there was a power cut) - how can I tell for sure if it booted to recovery mode?

---

### Post by aysiu on 2007-08-08
Type ```
apt-get update
``` If it updates, you're in recovery mode. If it tells you permission is denied, you're not in recovery mode.

---

