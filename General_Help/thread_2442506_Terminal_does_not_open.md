---
title: "Terminal does not open"
date: 2020-05-04
forum: General Help
---

### Post by floxhav on 2020-05-04
Hello everybody,

I use Ubuntu 18.04.4.
After updating Python, I wasn't able to open a jupyter-notebook file.
I wanted to reinstall Python but I did it the dumb way: I deleted all python folder in /usr/lib/.
Since, I cannot open my terminal.
I tried with XTerm, and when I try with the command 'gnome-terminal', it returns:
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
Fatal Python error: initfsencoding: Unable to get the locale encoding
ModuleNotFoundError: No module name 'encodings'

Current thread 0x00007fb0729a1740 (most recent call first):
Aborted (core dumped)

When I try apt-get --reinstall install gnome-terminal, it leads to 
[https://www.dropbox.com/s/y84d48pccea28cw/output_1.png?dl=0](https://www.dropbox.com/s/y84d48pccea28cw/output_1.png?dl=0)
(sorry, XTerm does not allow copy/paste)

Does someone have an idea?
Thank you!

---

### Post by CatKiller on 2020-05-04
I think your system is even more broken than you think. A whole bunch of Ubuntu's functionality is done using python, which you've simply deleted.

---

### Post by floxhav on 2020-05-04
Thank you CatKiller for your answer.
That is what I was thinking... Do you know if there is something I can do to not reinstall everything ?

EDIT: 
I tried python -V and it shows me Python 2.7.17.
So it looks like I still have Python somehow.

---

### Post by ActionParsnip on 2020-05-04
Why a screenshot when the output is text? Just copy and paste the text as an update..... It's far easier to read and use

---

### Post by floxhav on 2020-05-04
Hello ActionParsnip,

Thank you for your reply.
You can't copy and paste in XTerm, that is why I posted a screenshot.

---

### Post by mIk3_08 on 2020-05-04
I think system is nearly dead. back up all your data and format the system for best result.

---

### Post by Impavidus on 2020-05-04
You still have the Python executable, but deleted every module, so there's not much use in it. You have to reinstall every package that has some Python modules bundled with it, which means a lot of packages. Worse, the package manager itself depends on Python, so you've broken that too.

Basically, you have to reinstall all software using a livedisk. The easiest way is just reinstall all of Ubuntu.

Messing with Python versions is usually a bad idea.

---

### Post by floxhav on 2020-05-04
Oh god... Thank you all for your reply!

---

### Post by HermanAB on 2020-05-04
Ayup - Linux and BSD depend heavily on Perl and Python, so you pulled the rug out under the system wizards.

Fixing it will take much longer than re-installing.  So backup your data and install yourself a lovely, shiny, new system.

However, if you want to try something - you could boot with a live disk and then copy all the python files from the live disk to your system and see whether you get sufficient functionality to then run the software installer.  Note that I haven't tried it - YMMV.

---

### Post by ActionParsnip on 2020-05-04
Yeah when things mess with python I back away slowly

---

### Post by Impavidus on 2020-05-04
> **HermanAB said:**
> 
However, if you want to try something - you could boot with a live disk and then copy all the python files from the live disk to your system and see whether you get sufficient functionality to then run the software installer.  Note that I haven't tried it - YMMV.
You can also use a live disk, then use dpkg with the --root=/path/to/rootdir option to act on the installed system. Use dpkg --search to find all packages that have anything stored in /usr/lib/python*, then reinstall all those packages. Some will fail initially because they depend on other packages that have to be reinstalled too, but eventually it should work. Unless the "updating Python" before deleting the directory caused too much damage. I haven't tried it myself.

---

