---
title: "How safe is it to download fonts?"
date: 2020-02-01
forum: General Help
---

### Post by roseruby on 2020-02-01
Hi, this may or may not be a silly question, but I'd like to download some more fonts into my system, but unsure how safe it is.
I've looked online and keep getting conflicting information such as it's not possible to get a virus from a font file since it's read only, and others that say the opposite.
 Is there a few rules of thumb I should be following to make sure I don't download anything malicious?
Mainly I want to download from these sites:
 [https://www.dafont.com/](https://www.dafont.com/)

                  [https://fonts.google.com/](https://fonts.google.com/)

---

### Post by Artim on 2020-02-01
Anything you download from outside the Ubuntu repositories is potentially unsafe.  Ubuntu has tons and tons of supercool fonts to choose from, so check those first!

---

### Post by roseruby on 2020-02-01
Where abouts can I find them? I type in fonts in the ubuntu software center and nothing turns up.

---

### Post by Artim on 2020-02-01
Look for **Synaptic Package Manager** and install it (it's the "old" way of getting software for Ubuntu).  You'll need your root password to open it, then you can search for "fonts" in the search bar and find about a zillion and twelve of them.

Or you can open open a terminal and type
```
sudo apt-get install synaptic
```

to install it.

---

### Post by roseruby on 2020-02-01
Thank you! I'll check it out.

---

### Post by Impavidus on 2020-02-01
> **Artim said:**
> You'll need your root password to open it, ...
Let's not confuse people. There's no root password on Ubuntu, unless you created one. You need the personal password of the user who has admin rights.

---

### Post by CatKiller on 2020-02-01
> **roseruby said:**
> I've looked online and keep getting conflicting information such as it's not possible to get a virus from a font file since it's read only, and others that say the opposite.

Fonts themselves can't contain viruses, although malformed fonts have been used in exploits the same way any other malformed data can be, since they put the computer in an unexpected state. The malformed data isn't the issue, it's that it's being used as part of an exploit. The ability for malformed data to be used in an exploit is patched out whenever it's discovered. 

Rather than being an archive of fonts, some kind of GeTnEwFoNtSiNsTaLlEr.exe is likely to be malware for Windows, like any random executable downloaded from the Internet. Linux doesn't rely on downloading random executables from the Internet like Windows does, since we have package managers.

Fonts downloaded through Synaptic will be fine, and there are a lot of them available, and (assuming the sites themselves haven't been compromised) fonts from the sites you listed will also be fine. There's a directory in your Home folder you can put them (~/.local/share/fonts, I think) if you just want them for your user, or you can put them in /usr/share/fonts to use them system-wide, for which you'd need elevated privileges.

---

### Post by yancek on 2020-02-01
The thread at the site below discusses malware in fonts.  See in particular post 7 and post 8, the latter has several links describing the possible problem.  Also note that all are on windows.

[https://www.linuxquestions.org/questions/linux-security-4/can-a-font-blob-contain-code-that-spies-4175668684/](https://www.linuxquestions.org/questions/linux-security-4/can-a-font-blob-contain-code-that-spies-4175668684/)

---

