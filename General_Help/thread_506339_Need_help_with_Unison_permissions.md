---
title: "Need help with Unison permissions"
date: 2007-07-21
forum: General Help
---

### Post by ronald_stall on 2007-07-21
Installed Unison and set up a test directory but when I try to sync between to computers I get this in my unison.log

any ideas?

```
[BGN] Copying .gdesklets
  from //family//home/test
  to /home/test
[BGN] Copying .kde
  from //family//home/test
  to /home/test
[BGN] Copying .nautilus/saved-session-PY1AWT
  from //family//home/test
  to /home/test
[BGN] Copying .unison
  from //family//home/test
  to /home/test
[BGN] Copying new file
  from //family//home/test
  to /home/test
[BGN] Copying untitled folder
  from //family//home/test
  to /home/test
Failed: Error in creating directory:
Permission denied [mkdir(/home/test/.#.gdesklets.8b9769ccc7cf32f7dd9341a51955d44c.unison.tmp)]
Failed: Error in creating directory:
Permission denied [mkdir(/home/test/.#.kde.8b9769ccc7cf32f7dd9341a51955d44c.unison.tmp)]
Failed: Error in creating directory:
Permission denied [mkdir(/home/test/.#.unison.8b9769ccc7cf32f7dd9341a51955d44c.unison.tmp)]
Failed: Error in creating directory:
Permission denied [mkdir(/home/test/.#untitled folder.8b9769ccc7cf32f7dd9341a51955d44c.unison.tmp)]
Failed: Error in processing a transfer instruction:
Permission denied [open(/home/test/.nautilus/.#saved-session-PY1AWT.8b9769ccc7cf32f7dd9341a51955d44c.unison.tmp)]
Failed: Error in processing a transfer instruction:
Permission denied [open(/home/test/.#new file.8b9769ccc7cf32f7dd9341a51955d44c.unison.tmp)]
UNISON finished propagating changes at 13:18:22 on 21 Jul 2007

```

---

### Post by testube_babies on 2007-07-21
Do you have access to the 'test' user's home directory?

Maybe you want to set up a test folder in your own home directory: /home/[user_name]/test

---

