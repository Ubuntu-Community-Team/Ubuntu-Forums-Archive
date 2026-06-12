---
title: "[SOLVED] Determine Execution Speed (CLI) Linux : Find a program?"
date: 2008-07-01
forum: General Help
---

### Post by timo1023 on 2008-07-01
I need to see how long it takes a program to run using the command line. I've searched and I cannot find anything. Ideally, it would work like this

```

$ timeprogram actualprogram
$ PRINTOUT
  Completed in 152 ms

```

Thanks for the help.

---

### Post by soccerboy on 2008-07-01
you could use python and use the time module.

---

### Post by ModelM on 2008-07-01
This is one of the things the time program was designed to do. The command

man time

should tell you all you need to know.

---

### Post by ilrudie on 2008-07-01
time actualprogram

---

