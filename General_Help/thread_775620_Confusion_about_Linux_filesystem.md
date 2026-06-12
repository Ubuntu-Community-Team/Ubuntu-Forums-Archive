---
title: "Confusion about Linux filesystem"
date: 2008-04-30
forum: General Help
---

### Post by geemcd on 2008-04-30
Hi there,

I have a 40gig HD split into two partitions which which Linux reports as having 49.3gig of total filesystem capacity, any idea what's going on here? attached two photos, one of Disk Usage Analyzer and one of XP disc properties... the XP one matches what is installed.

---

### Post by kesman on 2008-04-30
What? Reports as what?

---

### Post by TeoBigusGeekus on 2008-04-30
Something missing here?

---

### Post by twright on 2008-04-30
is it including externel drives?

---

### Post by forrestcupp on 2008-04-30
I think it might be because Linux measures a megabyte as 1,000,000 bytes and Windows measures a megabyte as 2^20 bytes which is 1,048,576 bytes.  So the same amount of space looks bigger in Linux than it does in Windows.

---

### Post by geemcd on 2008-04-30
@twright - no external drives, no USB or firewire drives, not even a CD/DVD drive on this laptop

@forestcupp - total bytes according to XP is 39,990,157,322 so divide that by 1,048,576 and it gives *wheres the damn calculator* 38137.585947037 megabytes by Windows standards or divide by 1,000,000 to get 39990.157322 by linux standards...

Still a whole 10gig unaccounted for. Does Linux automatically compress stuff? Maybe it is doing some estimation of how much you could *theoretically* cram into the drive...

---

