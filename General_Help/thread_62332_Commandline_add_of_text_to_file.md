---
title: "Commandline add of text to file"
date: 2005-09-04
forum: General Help
---

### Post by ManLord on 2005-09-04
Is there any program that supports something like this from the command line:

$<program> <file> <add text entered> <line number> -first/last -clipboard

Like:
sudo kedit /etc/fstab "deb [ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.4.2/kubuntu](ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.4.2/kubuntu) hoary-updates main" -last

This imaginary commandline adds the repository to the end of the file /etc/fstab

or:
sudo kedit /etc/fstab -first -clipboard

This adds whatever text that is in the clipboard to the beginning of /etc/fstab



Is there any program that supports something like this?

---

### Post by plb on 2005-09-04
well to append something to the end of a file simply use >> for example:

echo "foo" >> bar

that will put the text foo at the end of the file bar...as far as putting it at the top I'm not sure but I'm sure it can be done.

---

