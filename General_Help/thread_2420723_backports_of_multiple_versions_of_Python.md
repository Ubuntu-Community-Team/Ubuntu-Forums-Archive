---
title: "backports of multiple versions of Python"
date: 2019-06-09
forum: General Help
---

### Post by Skaperen on 2019-06-09
i'm still on 16.04 (16.04.6 last upgraded this afternoon) and am interested in using newer versions of Python.  it is my understanding that Python can be placed in version specific file system locations (file and directory names with version numbers on them) allowing users to manually (or in the script's #!) choose the version of Python they want to run.

i'm curious if backports of Python can do this or if i need to build various versions of Python from source.

having looked over the documents of building backports, maybe that is the way to go.  maybe i can build debs of many versions (targeted for 16.04 x86_64 and maybe also for 18.04 x86_64 and arm64 built in AWS and 20.04 in the future).

---

### Post by TheFu on 2019-06-10
Don't use deb files to install specific versions of python.  Use a python environment management tool. [https://www.freecodecamp.org/news/manage-multiple-python-versions-and-virtual-environments-venv-pyenv-pyvenv-a29fb00c296f/](https://www.freecodecamp.org/news/manage-multiple-python-versions-and-virtual-environments-venv-pyenv-pyvenv-a29fb00c296f/)
[https://hackernoon.com/reaching-python-development-nirvana-bb5692adf30c](https://hackernoon.com/reaching-python-development-nirvana-bb5692adf30c)
[https://realpython.com/python-virtual-environments-a-primer/](https://realpython.com/python-virtual-environments-a-primer/)

Pretty much every scripting language should be managed this way if the normal, default, standard, included version of the language doesn't work for your needs.  Many have deployment tools so your development environment can be packaged and deployed to similar, but not exactly the same systems. 

I'm a perl guy. I use many different perl versions daily and deploy those different versions for perl web-apps on many different servers without much regard to how the base OS is managed. My web-apps are separate.  Python can do the same stuff, I'm positive.

---

### Post by Skaperen on 2019-06-10
the normal, default, standard, included version of the language *does* work for my needs, in general.  i just want to have the option to explicitly run other versions by appending the version number to "python", such as "python3.6".  this is for testing scripts i write under many versions or coding an explicit version on the #! line.

one script might have _[FONT=courier new]#!/usr/bin/env python3.6[/FONT]_ while another has _[FONT=courier new]#!/usr/bin/env python3.7[/FONT]_ because each script works best with different versions of Python or that happens to be the version i'm testing that script with.

---

### Post by #&amp;thj^% on 2019-06-10
Yep, I now have a good idea now with what your after, and I don't see how this will work with backporting versions of critical system environments for the specific OS platform.
However dose not mean you won't come up with something.
I'm just so spread thin as of late, I don't even have proper time to spend with family. (Thankfully they are an understanding bunch)

---

