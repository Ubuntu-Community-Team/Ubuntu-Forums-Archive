---
title: "Can't access my NTFS drives without sudo"
date: 2008-05-28
forum: General Help
---

### Post by Sirron on 2008-05-28
Today I tried to open my NTFS partitions with nautilus, only to find they wouldn't mount. It doesn't give any errors or anything.

Just nothing happens.

If I run Nautilus as root, it works fine.

I have Authorizations set so I could mount them as a normal user. When I turned that off, and tried again, it came up with the box asking for my password, which I gave it. It then put the authorisation back and still didn't work.

What on earth can I do to fix this? It's completely random, mebe it was an update that broke it?

---

### Post by pointone on 2008-05-28
Please post your "/etc/fstab".

---

### Post by wkulecz on 2008-05-28
You won't likely find the answer in his /etc/fstab.  Mine has no mention of the ntfs partition and I have it automatically mount in nautilus as a normal user and have rw support enabled.

Install the NTFS Configuration Tool with synaptic. Its what I did to get mine to work.

It appears to be handled same as CD/DVD drives and USB storage getting mounted under /media instead of /mnt.

--wally.

---

### Post by Sirron on 2008-05-30
Now it's randomly started working again.

You know when windows doesn't shut down properly and you can access your drives until it does? (without forcing it) It was like that, only windows DID shut down properly, and I didn't get any error message. I did restart the computer before posting here, but I didn't startup and shutdown windows, I just went straight back to ubuntu.

Thanks for the help anyway. I'll ignore the problem unless it happens again.

---

