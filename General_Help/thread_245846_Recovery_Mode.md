---
title: "Recovery Mode"
date: 2006-08-28
forum: General Help
---

### Post by Irony on 2006-08-28
I booted into Recovery Mode today by way of experimentation - it boots straight into root@ubuntu

Should it do this? It seems to me that it should go to username@ubuntu or require some logging in to my username.

---

### Post by Ramses de Norre on 2006-08-28
No this is normal, it is called single user mode and that single user is always root.
You can remove the recovery mode from grub by removing the line starting with ```
#alternative
``` from /boot/grub/menu.lst.
You can then still enter it by pressing 'e' in grub to edit your kernel line and then adding 'single' to the end.

---

### Post by spin2cool on 2006-08-28
Yes, that's the standard behavior.

---

### Post by Irony on 2006-08-28
Thanks for replies.

I did a Ctrl+F in the menu.lst but I couldn't find #alternative, there is this however;

[PHP]## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single[/PHP]

I assume I can do something with this to stop someone booting accidently into root recovery but still allowing me to do so.

Ahh!! It just occurs to me that I would delete that last line and do what Ramses suggested and go to e for edit and type single in place of quiet splash vga=0x31A thus;

[PHP]/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash vga=0x31A[/PHP]

becomes;

[PHP]/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro single[/PHP]

---

### Post by Ramses de Norre on 2006-08-28
Oh yes that's what I meant =)
When you delete the last line (the whole line, it wont work otherwise) and run `sudo update-grub` afterwards your recovery mode entries will be gone. This is what I did here and I can succesfully get to a recovery mode when needed like I said before.

---

### Post by Irony on 2006-08-28
Thanks Ramses - I edited my previous reply before seeing your reply.

---

### Post by Irony on 2006-09-02
It didn't work!

I deleted;

[PHP]# altoptions=(recovery mode) single[/PHP]

Then ran;

[PHP]sudo update-grub[/PHP]

But this just adds the deleted entry back in.

---

