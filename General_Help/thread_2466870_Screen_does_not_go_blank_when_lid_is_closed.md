---
title: "Screen does not go blank when lid is closed"
date: 2021-09-08
forum: General Help
---

### Post by davy jones on 2021-09-08
I've recently installed Ubuntu 20.04.3 on a new Dell Vostro 3500 (11th gen processor). I was previously using 20.04.2 on an older Inspiron. On my old laptop, when I shut the lid, the screen would automatically go blank. I didn't have to do anything in Settings or Tweaks for this to happen. But in my new laptop, the screen stays on. I've seen a bunch of long threads with the same problem but I haven't been able to find a single solution that works. Settings or Tweaks don't have anything that can control this. I tried editing /etc/systemd/logind.conf and that didn't work either. The only thing that gives an option for this is Dconf Editor. I changed lid-close-ac-action and lid-close-battery-action to 'blank' but it doesn't work. What is overriding this? What do I have to do to ensure the screen goes blank when I shut the lid? I don't want it to lock or suspend, I just want it to go blank. Always assumed this was a very natural and intuitive thing for any laptop regardless of OS, but clearly not.

---

