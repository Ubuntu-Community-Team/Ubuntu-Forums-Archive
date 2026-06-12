---
title: "BASH syntax error"
date: 2019-01-30
forum: General Help
---

### Post by webmanoffesto on 2019-01-30
I have a 32 GB SSD and I want to install Ubuntu (reinstall). It is SDB1 and 2.
Why am I getting a syntax error?

```
# sudo mount /dev/sdb1 /mnt/boot/efi for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
bash: syntax error near unexpected token `do'
```

---

### Post by TheFu on 2019-01-31
I always simplify and test. By putting newlines where needed, missing ; are easily seen.

```
sudo mount /dev/sdb1 /mnt/boot/efi 
for i in /dev /dev/pts /proc /sys /run; do 
    echo sudo mount -B $i /mnt$i; 
done
```

Now, but that back into a single line, if you must.

---

