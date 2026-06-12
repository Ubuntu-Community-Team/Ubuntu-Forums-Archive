---
title: "Dual-core GCC support?"
date: 2008-05-25
forum: General Help
---

### Post by lackofcreativity on 2008-05-25
Does GCC support dual-core processors in any way? If so, how?

---

### Post by fsmithred on 2008-05-25
```
make -j N
```

where N is number of cores plus one.

---

### Post by lackofcreativity on 2008-05-26
Cool.

---

### Post by inportb on 2008-05-26
> **fsmithred said:**
> ```
make -j N
```

where N is number of cores plus one.

Hm... what is the reasoning behind that?

>        -j [jobs], --jobs[=jobs]
            Specifies the number of jobs (commands) to run simultaneously.  If there is more than one -j
            option, the last one is effective.  If the -j option is given without an argument, make will
            not limit the number of jobs that can run simultaneously.

---

### Post by fsmithred on 2008-05-27
It speeds up compiling by keeping both cores busy. (assuming dual core)

Here are some benchmarks -
[http://techgage.com/article/intel_core_2_quad_q9450_266ghz/11](http://techgage.com/article/intel_core_2_quad_q9450_266ghz/11)

---

### Post by Joeb454 on 2008-05-27
So for dual core processors I assume you would run something like ```
make -j 3

OR

gcc some-random-long-c-file.c -j 3 -o this-is-my-app
```

---

### Post by fsmithred on 2008-05-28
> **Joeb454 said:**
> So for dual core processors I assume you would run something like ```
make -j 3

OR

gcc some-random-long-c-file.c -j 3 -o this-is-my-app
```


Yeah 'make -j3' is right for dual core. I have no idea what the other line says.

---

### Post by andrew.46 on 2008-11-09
Hi,

I believe that the idea of 'processor number + 1' is a little flawed for jobs number. A uniprocessor can also run multiple processes and can benefit from the --jobs=n option.

An interesting discussion of this:

[http://oreilly.com/catalog/make3/book/ch10.pdf](http://oreilly.com/catalog/make3/book/ch10.pdf)

  Andrew

---

