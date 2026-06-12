---
title: "Emacs: print to ps/pdf-file"
date: 2008-03-15
forum: General Help
---

### Post by fubar0 on 2008-03-15
Hello, 

I would like to save a buffer as a postscript (or pdf) file, e.g. print that buffer to a file.

Is there an other (more direct) way than typing
```
M-x ps-spool-buffer-with-faces
```?

This command essentially converts the current buffer to postscript and displays its content in a new buffer, which you can save and convert to pdf.

I mean, the built-in functions in the 'file'-menu (Print, Postscript print, ...) do convert the buffer to postscript, but send it directly to CUPS via lpr. There is no option to 'save to a ps file'.

Thanks for your comment

---

### Post by cmnorton on 2008-03-16
I am probably missing the point, but why not install cups-pdf, and print to it from Emacs? I've got Epsilon installed, and have cups-pdf as my default printer. I can alter the print command line if I want to use an actual physical printer.

---

### Post by hrkljush on 2008-03-29
Ok, here's what I did:

Add this to ~/.emacs

```

(defun print-to-pdf ()
  (interactive)
  (ps-spool-buffer-with-faces)
  (switch-to-buffer "*PostScript*")
  (write-file "/tmp/tmp.ps")
  (kill-buffer "tmp.ps")
  (setq cmd (concat "ps2pdf14 /tmp/tmp.ps " (buffer-name) ".pdf"))
  (shell-command cmd)
  (shell-command "rm /tmp/tmp.ps")
  (message (concat "Saved to:  " (buffer-name) ".pdf"))

  
  )

```

now M-x print-to-pdf
will print a <buffer name>.pdf in the same folder with your text file.

Hope this helps...

---

