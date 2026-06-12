---
title: "Emacs Question"
date: 2008-04-08
forum: General Help
---

### Post by dstein on 2008-04-08
This is not an Ubuntu question, but I could think of no better place to ask. Anyhow, in e-macs, for just standard text editing (not programming, just writing random notes or whatever), should I use Fundamental mode or text mode. Also, when using a mode with highlighting and such, is there any way to save or print the color version. That is, if I am editing a Lisp file or Matlab file, and emacs is highlighting because I am in a relevant mode, how can I output this highlighted version in color? Thanks.

---

### Post by mali2297 on 2008-04-08
From the [Emacs manual]("http://www.fnal.gov/docs/products/emacs/emacs/emacs_33.html#SEC386"):
> 
If you are using a color display, you can print a buffer of program code with color highlighting by turning on Font-Lock mode in that buffer, and using ps-print-buffer-with-faces.

I have not tried it myself though.

---

### Post by dstein on 2008-04-10
Oh perfect. Another question I just thought of regards the entering of functions. It seems that some functions take optional arguments. When I type M-x function-name, I am not able to enter a space and then the arguments. How am I supposed to enter additional arguments? Thanks.

---

### Post by mali2297 on 2008-04-10
> **dstein said:**
> Oh perfect. Another question I just thought of regards the entering of functions. It seems that some functions take optional arguments. When I type M-x function-name, I am not able to enter a space and then the arguments. How am I supposed to enter additional arguments? Thanks.

Can ypu give an example?

---

### Post by dstein on 2008-04-10
An example is the ps-print-buffer function, whose form is (ps-print-buffer &optional filename). "Noninteractively, the argument filename is treated as follows: if it is nil,
send the image to the printer.  If filename is a string, save the PostScript
image in a file with that name." However, I am unsure how I can use M-x and also provide an argument for such a function. Therefore, I am left with only the default functionality, in this case - which sends the output to my printer rather than a file.

---

### Post by mali2297 on 2008-04-10
I'm sorry, but I don't know the answer to your question. 

A workaround for the specific print-to-file issue is to use 
```

M-x ps-spool-buffer-with-faces

```
This will give you the Postscript output in an Emacs buffer.  You can then save that buffer as a PS file.

---

