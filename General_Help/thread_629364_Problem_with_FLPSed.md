---
title: "Problem with FLPSed"
date: 2007-12-02
forum: General Help
---

### Post by LSMadsen on 2007-12-02
I am trying to edit a PDF-file with FLPSed, but the output is (I start it from a konsole to get an output):
exec: No such file or directory
Please install ghostscript and make sure 'gs' is in the PATH. 

And Ghostscript is installed, but I do not know, if it is in the Path, but what could else went wrong?

I do not know, if it is the right place to post this post

---

### Post by nibsa1242 on 2007-12-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/flpsed/+bug/140978](https://bugs.launchpad.net/ubuntu/+source/flpsed/+bug/140978) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have the same error. It used to work fine pre-Gusty. Don't know exactly when it broke. Anyhow, according to the bug report "sudo ln -s /usr/bin/gs /usr/bin/gs-esp" will fix it. I tried that and everything works properly now.

---

