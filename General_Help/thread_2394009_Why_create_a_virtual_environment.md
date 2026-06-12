---
title: "Why create a virtual environment ?"
date: 2018-06-11
forum: General Help
---

### Post by Lou Reed on 2018-06-11
I am trying to install jupyter and jupyter notebook on Ubuntu 16.0 (64 bit).

I know that I must use pip, my OS version is Windows 10**.  However, when I type sudo pip install jupyter
it will at first give me a lot of output (see attached out.txt.txt file) followed by some red lettering
with a message that ends in permission denied (see attached screenshot.png). I did type in sudo and my password. 

It suggests using a virtual environment. Why must I do that?  I see on youtube users installing jupyter on Ubuntu 16.04
64 bit all the time and they never use a virtual environment. 

Respectfully,

ernest-t-bass

---

### Post by TheFu on 2018-06-12
I waited a day before responding, hoping that someone else would understand the question.     I'm not sure if you are asking an Ubuntu question, Windows10 question, pip question, or virtual machine question. Please clarify.

But here are some shotgun answers. Maybe 1 will help?

I clicked this thread because of the thread title assuming you wanted a few reasons why a virtual machine or container is almost always a good idea these days, instead of running directly on the hardware.  Abstraction  away from  funky hardware, flexibility to increase resources without needing to reinstall everything, and the ability to partition different types of work and all those dependencies into a self-contained bundle are the main reasons to using VMs or containers.

If "virtual environment" means being able to have multiple versions of python or perl or php or ruby, then that is a "best practice" for script developers.  Not using the OS version of these scripting tools for non-trivial script development  is something I do. I'm a perl dev and what I need in the version of perl used for the programs and webapps I create is different than what the Canonical/Ubuntu OS needs from the perl version they setup by default.  The OS version needs stability and security patches, nothing more.  As a developer, I need easy dependency management, patches for fixes and security for each perl version while not impacting any of the other perl versions on the system (until I'm ready to patch/fix those myself).  This setup is sorta a "virtual environment".  Changing to a different version of perl (or python or ruby or ...) is 1 command that just manages a few environment variables behind the scenes.

But I'm not certain that is your question.  

Why does Windows do things different from Unix/Ubuntu?   Python devs work on Unix mostly. Making things work on Windows often takes a little finagling. I've ported some perl to Windows and the slight difference in file system stuff mattered.

For policy questions about any specific project, ask that project the question.  I've never heard of jupyter before yesterday.  

BTW, I couldn't read the image.  The txt file seems fine.  Nothing odd jumped out.

---

### Post by dragonfly41 on 2018-06-12
Reading the OP's image it seems that "virtual environment" has been interpreted as installing within VirtualBox?

A framework such as Anaconda refers to virtual environment. Here is an example.

[https://medium.com/codingthesmartway-com-blog/getting-started-with-jupyter-notebook-for-python-4e7082bd5d46](https://medium.com/codingthesmartway-com-blog/getting-started-with-jupyter-notebook-for-python-4e7082bd5d46)

So you can have a virtual environment for different versions of python.

And another example ...

[https://uoa-eresearch.github.io/eresearch-cookbook/recipe/2014/11/20/conda/](https://uoa-eresearch.github.io/eresearch-cookbook/recipe/2014/11/20/conda/)

---

### Post by Lou Reed on 2018-06-12
Excuse me it is an Ubuntu question. I have both Ubuntu and Wihdows 10 all 64 bit).Sorry about the confusion. 

I am trying to install Jupyter on Ubuntu 16,04. Windows is not involved.

Respectfully,

ernest-t-bass

---

