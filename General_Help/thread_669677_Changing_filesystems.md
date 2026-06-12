---
title: "Changing filesystems"
date: 2008-01-16
forum: General Help
---

### Post by Washer on 2008-01-16
What's the easiest way to switch out of ext3 to reiser4 or something? Just copy all files into the new partition?

---

### Post by Nano Geek on 2008-01-16
If you want to do that for the partition that Ubuntu's installed on, then you are going to need to reinstall.

But make sure you back up any data that you don't want to lose before you start.

---

### Post by Washer on 2008-01-16
Were there any options for filesystems during the ubuntu install? I don't remember. 

Anyway it's a moot point. I'd reinstall, but 7.10's kernel doesn't support reiser4. I've patched my current one to support it.

---

### Post by kellemes on 2008-01-16
It does support reiserfs.

---

### Post by Washer on 2008-01-16
Cmon guys put a bit more effort into the replies. What I want to know is

- do I have to create a boot partition if reiser4 in my kernel isn't a module
- do I have to worry about preserving permissions etc during the copy
- GRUB can be a bitch. Do I just edit it for /dev/hdaX where hdaX is my new partition?
- Can I somehow create a new livecd with this kernel & my installed programs
- etc

---

### Post by Nano Geek on 2008-01-16
- I'm not sure I know exactly what you mean, but I don't think you will need to.
- No
- Ubuntu will automatically set it up when you reinstall.
- Yes, there's a program that can do that. I'm not sure what it's called so you'll need to Google it.

By the way, it's not considered polite to tell people to put more effort into their replies when they already answered your first question.

---

