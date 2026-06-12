---
title: "Ghostscript problem:**** Unable to open the initial device, quitting"
date: 2013-11-03
forum: General Help
---

### Post by Jpox on 2013-11-03
Hallo everyone,

I have a little problem with the Device of Ghostscript; I want to modify the dimension of  a file and I tried to use gs:

```

gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputfile=output.pdf input.pdf
```

but I get the following error:

```
**** Unable to open the initial device, quitting.
```

If I don't specify -sDEVICE, it seems to work (I see in a temporary display processing the file), but it doesn't create any file.pdf.

I tried also to set my default device in this way:

```
gs -sDEVICE=X11alpha -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputfile=prova.pdf tesino.pdf
```

but I get still an error like this:

```

Unknown device: X11alpha
Unrecoverable error: undefined in .uninstallpagedevice
Operand stack:
    defaultdevice
```

Could anyone help me please?

---

### Post by Jpox on 2013-11-03
Sorry, I am stupid

I wrote:

-sOutputfile=prova.pdf

instead of

-sOutputFile=prova.pdf

I am very sorry!!
Now it works!!

---

