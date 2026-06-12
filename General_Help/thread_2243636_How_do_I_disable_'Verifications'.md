---
title: "How do I disable 'Verifications'?"
date: 2014-09-10
forum: General Help
---

### Post by daka on 2014-09-10
I have carpal tunnel syndrome and I spend too much time double clicking or triple clicking to accomplish things like erasing files.  It seems every time I try to do most things, erasing files, shutting down, closing programs.... I am asked 'Are you sure.... blah blah.'  I understand the risks and am willing to take them if I choose to dispense with these warnings;  sometimes I will do something and regret it...BUT that is my right as a free human being, no?  Does anyone else have this issue?  Is there a way to stop all these verifications?

Thanks

Sean

---

### Post by buzzingrobot on 2014-09-10
I'm not aware of any single blanket way to eliminate the "Are You Sure?" dialogues. Occasionally, they are configurable in individual apps and tools.

That said, installing and exploring the settings in dconf-editor might uncover some of them. Tedious work, though.

Prompts requesting privilege escalation -- the GUI equivalent of prefacing a command with 'sudo' to temporarily acquire the necessary rights -- are there to stay.

---

### Post by ian-weisser on 2014-09-10
You can edit the sudoers file using the 'visudo' application to disable verifications.

Warning: A typo in the sudoers file _will_ break your system. Backup first, and pay close attention to the visudo warning messages.

---

