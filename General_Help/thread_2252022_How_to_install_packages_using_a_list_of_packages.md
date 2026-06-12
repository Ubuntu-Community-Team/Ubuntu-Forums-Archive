---
title: "How to install packages using a list of packages?"
date: 2014-11-08
forum: General Help
---

### Post by lieven-debels on 2014-11-08
Hello

I used to install packages using a packagelist in the following way:
```
cat packages.txt | sudo xargs apt-get install --yes
```
In the above code packages.txt is the file containing all the packages I want to install, one per line.
Somewhere else I was suggested to try:
```
sudo apt-get install --yes $(< packages.txt)
```
Assuming the first package in the list i want to install is synaptic, both commands fail with an error: couldn't locate package synaptic.
However, ```
sudo apt-get install synaptic
``` works fine. I don't have a clue about what the mistake might be, as the first command in this post has worked very well in the past, but not any more, it seems.
Does anyone know what the problem might be?

I'm using ubuntu 14.04.1, kernel 3.13.0-39, and bash 4.3.11.

---

### Post by steeldriver on 2014-11-08
How did you create the packages.txt file? is it possible some non-printing characters crept in there (such as Windows line endings)? you can check with

```

cat -A packages.txt

```

---

### Post by lieven-debels on 2014-11-08
Ok, thanks, I' ll try that. I figured out myself already it's a problem with the file in question.

Edit: The output of the command:
```
cat -A packages.txt
```
gives the following:

M-oM-;M-?package1$
package2$
package3$
and so on

I think this might be because I edited the file with libreoffice instead of leafpad.
Anyway, I'll recreate the file with nano or leafpad only, I guess it should work then...

---

### Post by whitesmith on 2014-11-08
LibreOffice is fine for general purpose word processing. For text, you need a **text editor** that doesn't pepper your document with funny invisible characters. (You just have to know that's bad news.) If I'm in GUI mode (not too often!) my choice is gedit. Since I tend to live in the shell, nano gets my vote. Sure, it's visually primitive compared to gedit, but who cares? More than 99 times out of a hundred I'm using it to edit a system file like /etc/fstab. Anyway, **what** got the job done is always immaterial. Regards.

---

### Post by steeldriver on 2014-11-08
yes it's likely the M-oM-;M-? (byte order mark) that's causing the problem

---

### Post by lieven-debels on 2014-11-08
Ok, thanks again for all the help. I'll mark this thread as solved.

---

