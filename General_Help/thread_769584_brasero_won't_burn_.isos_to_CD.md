---
title: "brasero won't burn .isos to CD"
date: 2008-04-26
forum: General Help
---

### Post by logos34 on 2008-04-26
I'm getting this error message when I try to burn an image to CD-RW:

> Checking session consistency (brasero_burn_check_session_consistency burn.c:1714)
[COLOR="Red"]**Inconsistent flag: you can't use flag on_the_fly **[/COLOR](brasero_burn_check_session_consistency burn.c:1810)
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum deactivating
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum stopping
Session error : a temporary file can't be created: Permission denied (brasero_burn_record burn.c:2270)

Checked gconf-editor and don't see a configuration parameter for on-the-fly, nor anything seemingly related.

Any ideas?

---

### Post by logos34 on 2008-04-27
bump

---

### Post by danbuter on 2008-04-27
I'd submit a bug report, if you haven't already. Unfortunately, I don't know how to help on this.

---

### Post by ptn107 on 2008-04-27
I get the same error during the checks after trying to burn an iso to dvd.

---

### Post by cleopete on 2008-09-23
This thread is old, but this problem drove me nuts and I just figured it out.

For whatever stupid reason, Brasero switched its temp file to 'Filesystem' instead of the home directory, where it actually has permission to write.

What gave me the most trouble was changing the temp directory.  Turns out you can set it by clicking the 'Properties' button next to the selected CD/DVD burner, right after you click 'Burn'.

I hope this helps someone, 'cause there ain't squat about this posted.

---

### Post by skintythe1andonly on 2008-11-07
Thanks for that. This didnt happen in hardy to me... updated to intrepid and it started there....wierd.

---

### Post by gcbzzzz on 2008-12-20
you can check the temporary dir it uses... weird that it does not mention on the log.

on the burn dialog, click preferences button next to the driver dropdown. there's an option for temporary dir there. make sure you're using the dir you think you are using.

---

