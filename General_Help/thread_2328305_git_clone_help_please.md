---
title: "git clone help please"
date: 2016-06-19
forum: General Help
---

### Post by davaweb on 2016-06-19
For a couple of years I've been obtaining firewall software with the command:
git clone [https://github.com/](https://github.com/)....

This years the package changed considerably and seems not suitable for Ubuntu.

1. Could somebody please explain simplistically what 'git clone [https://github.com/](https://github.com/)...' does - I am not sure if it runs code or simply downloads software.

2. I have a zip of the original version from the site. Can I unpack it and git clone it myself and if so how?

Thanks

---

### Post by &amp;KyT$0P# on 2016-06-19
1) [FONT=Courier New]git clone httpxx//[/FONT]... downloads the entire git repository, including all change history, to your computer; saving it to a local git repository in an automatically-determined directory name.

2) You can't git clone a .zip file's contents as far as I know, certainly not if it's not a git repository.  Two things you can do though: A) just unzip it and use the result, B) use your local git repository (the result of the git clone) and [FONT=Courier New]git checkout[/FONT] the last "good" revision (see [FONT=Courier New]man git-checkout[/FONT] for more information on how that works).

---

### Post by davaweb on 2016-06-19
> [FONT=Courier New]git clone httpxx//[/FONT]...  downloads the entire git repository, including all change history, to  your computer; saving it to a local git repository in an  automatically-determined directory name.

Yes, a directory with sub-folders is created in my home folder from which there are scripts I put into specific locations and modify.

To me it is just a folder. What distinguishes it as a 'git' repository? I think I'm not understanding 'git'. I've read man git and google but not understood why it is different from any other folder - except that it and its contents were downloaded. I see git clone and assume it downloads *just* a copy of the folder from the website?

---

### Post by &amp;KyT$0P# on 2016-06-19
If you don't see how it's different then you haven't selected to show hidden files and folders in your file manager.  A "git repository" consists of a "working directory" (this is the folder you see) containing a folder named '.git' which contains the repository configuration and change history.  If you open the folder in a terminal, there are several ways to check if it's part of a git repository, e.g. run a "harmless" git command, such as
```
git status
```
If you are *not* in a git repository, you'll see this:
```
fatal: Not a git repository (or any of the parent directories): .git
```

Another way to check if you're in a git repository is to run
```
ls -A
```
and look for a '.git' entry


For more information about git, this might be a nicer introduction than the man pages: [https://git-scm.com/book/en/v2]("https://git-scm.com/book/en/v2")

---

### Post by davaweb on 2016-06-20
I could see the .git folder but did not know what it's function was. Now I think do - thanks for the link.

Many thanks.

---

### Post by &amp;KyT$0P# on 2016-06-20
You're welcome! :KS

(If your questions here are resolved to your satisfaction, please use Thread Tools > "Mark this thread as solved...")

---

