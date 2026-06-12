---
title: "Error message during shutdown"
date: 2018-10-20
forum: General Help
---

### Post by manmath on 2018-10-20
I see this error message during shutdown of Cosmic Ubuntu:

> failed to parse (null): no such file or directory
failed to deactivate swap: no such file or directory

I don't have a swap partition (I don't want one). I believe the error message is related to unmounting of swap (I'm not sure though). What can I do to suppress this message?

---

### Post by dino99 on 2018-10-20
Can you check that fstab does not have a swap entry ?

---

### Post by manmath on 2018-10-21
Checked, it doesn't have one.

manmath@manmath-H61M-DS2:~$ cat /etc/fstab
# <file system>					<mount point>	<type>	<options>		<dump>	<pass>
UUID=90bd760a-afbc-4378-9ca6-e9431d637584	/		ext4	defaults,noatime	0	1
UUID=c586c909-4c88-4da2-8570-21510d17804f	/home	ext4	defaults,noatime	0	2

Well, I forgot to tell that the shutdown error message is not a problem in itself. My system boots up and shuts down just fine. I think somewhere in some systemd script there's some instruction to check for the swap points whether there's a swap partition or file present or not. And it's a matter of making some changes in those text/scripts. I may be wrong in my assumption though.

---

### Post by manmath on 2018-10-21
Nothing is solved. But I must mark it solved cos it's not pragmatic to waste time on such a silly issue for so long and yet not reach at a solution.
Thank you all. Love you.

---

