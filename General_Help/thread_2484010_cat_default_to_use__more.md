---
title: "cat default to use | more"
date: 2023-02-15
forum: General Help
---

### Post by peter211 on 2023-02-15
Hi is it possible to make the cat command always by default use | more at the end of every time its used? and if I dont want more i could put | no-more?

---

### Post by Holger_Gehrke on 2023-02-15
You could put a function definition for cat into your ~/.bashrc
```

function cat () {
cat $* | more
}

```
Functions are searched before executables when the shell searches for what to execute so a function can overrule an external program. You can't use an alias for this because you need the parameters and you can't pass parameters to an alias. To use standard cat without piping the output through 'more' you would simply call cat with the full path ('/usr/bin/cat').

Alternatively you could just call 'more' with the file name and forget about cat. This is actually the better way to do things because the intended use of cat is to con**cat**enate multiple files (cat file1 file2 file3>newfile) and redefining cat will obviously break that functionality.

Holger

---

### Post by peter211 on 2023-02-15
Oh lol, yes more is exactly what i need ha. Thank you!

---

### Post by mIk3_08 on 2023-02-16
> **peter211 said:**
> Oh lol, yes more is exactly what i need ha. Thank you!
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

