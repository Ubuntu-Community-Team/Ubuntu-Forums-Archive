---
title: "rsync Edgy RC1, Simon Law email call for testing"
date: 2006-10-18
forum: General Help
---

### Post by dannyboy79 on 2006-10-18
I got an email from Simon Law about RC1 coming out tomorrow and that I could use rsync to download it today and then update it tomorrow. he wants to get feedback on it's installation process. when i typed in
rsync -vPz rsync://cdimage.ubuntu.com/cdimage/daily-live/curren t/*i386.iso

i got back this in less than a second?

-rw-r--r--   704937984 2006/10/17 16:46:48 edgy-desktop-i386.iso

sent 120 bytes  received 80 bytes  80.00 bytes/sec
total size is 704937984  speedup is 3524689.92

and then when i used sudo find / -name *.iso, i can't seem to find the iso file of edgy rc1? can onyone explain to me what happened and why it isn't working? I am using the rsync command that's in the email.  I have never used rsync before so I am not sure if -vPz is correct? Thanks for any help.

---

### Post by dannyboy79 on 2006-10-20
Hello, isn't there one person that can explain this to me. No one here knows about rsync?

---

### Post by angrykeyboarder on 2006-11-11
> **dannyboy79 said:**
> Hello, isn't there one person that can explain this to me. No one here knows about rsync?

Apparently not. I have (had) (more or less) preciesly the same situation as you.

---

