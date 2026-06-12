---
title: "Huge numbers of printk messages supressed"
date: 2007-12-19
forum: General Help
---

### Post by growse on 2007-12-19
Running Gutsy on a T42 Thinkpad here, and I'm getting huge numbers of suppressed printk messages in the kernel log. Here's a recent extract:

```

Dec 19 11:58:23 bob kernel: [81390.340000] printk: 2 messages suppressed.
Dec 19 11:58:29 bob kernel: [81396.340000] printk: 2 messages suppressed.
Dec 19 11:58:33 bob kernel: [81400.340000] printk: 1 messages suppressed.
Dec 19 11:58:39 bob kernel: [81406.340000] printk: 2 messages suppressed.
Dec 19 11:58:43 bob kernel: [81410.340000] printk: 1 messages suppressed.
Dec 19 11:58:49 bob kernel: [81416.340000] printk: 2 messages suppressed.
Dec 19 11:58:53 bob kernel: [81420.340000] printk: 1 messages suppressed.
Dec 19 11:58:59 bob kernel: [81426.340000] printk: 3 messages suppressed.
Dec 19 11:59:03 bob kernel: [81429.864000] printk: 2 messages suppressed.
Dec 19 11:59:14 bob kernel: [81440.340000] printk: 3 messages suppressed.
Dec 19 11:59:19 bob kernel: [81446.340000] printk: 1 messages suppressed.
Dec 19 11:59:23 bob kernel: [81449.724000] printk: 1 messages suppressed.
Dec 19 11:59:29 bob kernel: [81455.948000] printk: 4 messages suppressed.
Dec 19 11:59:33 bob kernel: [81460.340000] printk: 2 messages suppressed.
Dec 19 11:59:39 bob kernel: [81466.340000] printk: 2 messages suppressed.
Dec 19 11:59:43 bob kernel: [81470.340000] printk: 1 messages suppressed.
Dec 19 11:59:48 bob kernel: [81474.916000] printk: 2 messages suppressed.
Dec 19 11:59:53 bob kernel: [81480.340000] printk: 2 messages suppressed.
Dec 19 11:59:59 bob kernel: [81486.336000] printk: 2 messages suppressed.
Dec 19 12:00:04 bob kernel: [81490.336000] printk: 1 messages suppressed.
Dec 19 12:00:09 bob kernel: [81496.336000] printk: 3 messages suppressed.
Dec 19 12:00:13 bob kernel: [81500.336000] printk: 2 messages suppressed.
Dec 19 12:00:19 bob kernel: [81506.336000] printk: 2 messages suppressed.
Dec 19 12:00:23 bob kernel: [81510.336000] printk: 2 messages suppressed.
Dec 19 12:00:31 bob kernel: [81518.336000] printk: 2 messages suppressed.
Dec 19 12:00:39 bob kernel: [81526.336000] printk: 1 messages suppressed.
Dec 19 12:00:43 bob kernel: [81530.336000] printk: 2 messages suppressed.
Dec 19 12:00:49 bob kernel: [81536.336000] printk: 3 messages suppressed.
Dec 19 12:00:59 bob kernel: [81546.336000] printk: 2 messages suppressed.
Dec 19 12:01:03 bob kernel: [81550.336000] printk: 1 messages suppressed.
Dec 19 12:01:09 bob kernel: [81556.336000] printk: 2 messages suppressed.
Dec 19 12:01:13 bob kernel: [81560.336000] printk: 1 messages suppressed.
Dec 19 12:01:19 bob kernel: [81566.336000] printk: 1 messages suppressed.
Dec 19 12:01:24 bob kernel: [81570.332000] printk: 1 messages suppressed.
Dec 19 12:01:29 bob kernel: [81576.332000] printk: 2 messages suppressed.
Dec 19 12:01:33 bob kernel: [81580.332000] printk: 1 messages suppressed.
Dec 19 12:01:38 bob kernel: [81584.956000] printk: 1 messages suppressed.
Dec 19 12:01:43 bob kernel: [81590.332000] printk: 3 messages suppressed.

```

How do I get it to stop suppressing these and actually tell me what's going on?

---

### Post by aurelieng on 2007-12-21
I have the same problem on my XPS Gen2 laptop (Pentium M plateform, running Linux c2000 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux)

Idea anyone ?

---

### Post by NETabuse on 2007-12-30
wow, that reply page took a bit of loading,, 

anyway, having "printk:6 messages suppressed" over and over again here.. on HP nx6110 laptop.

---

