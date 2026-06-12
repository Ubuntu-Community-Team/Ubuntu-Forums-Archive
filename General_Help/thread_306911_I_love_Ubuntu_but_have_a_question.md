---
title: "I love Ubuntu but have a question"
date: 2006-11-25
forum: General Help
---

### Post by rioghal on 2006-11-25
Hi all, my name is Donna and I am new to Ubuntu.

I am using Ubuntu 6.06.1 LTS, with WindowMaker, on an AMD Sempron 2800+ with 1Gb ram, a 200Gb hard drive and I am loving this awesome distro. I have been using Linux for about three months, this is the 7th distro I have tried, and I'm sticking with Ubuntu :)

I have noticed that after working in Ubuntu and closing the apps, my ram (?) isn't being freed up so it can be used by other apps. I was always under the impression that when an app was closed, the memory it used was freed up to be available to other apps.. but I am finding this isn't always the case.


Have a look at the screenshots and you'll see what I mean. As far as I know, the same exact apps were running during both screenshots.

My questions are:

1) Why isn't the ram being freed up when apps are closed?
2) How can I force the ram to free itself after an apps is closed?
3) Is this problem due to something I am doing wrong or something I am missing?
4) My boyfriend built this machine, is there something we should know?
5) What happens when I run out of ram? Will apps no longer work?

I realise that was a load of questions but I am new to Linux and I want to do everything right because I don't want to ever have to use Windows again.

Thanks in advance for the replies :)

---

### Post by junglepeanut on 2006-11-25
Hope this helps.
[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

---

### Post by pay on 2006-11-25
The only thing that I can think of is if the programs are still running in the background. When you run out of ram to use the operating system starts to use the harddrive (which is much slower).

---

### Post by rioghal on 2006-11-25
junglepeanut, that link is great! Thanks for posting your reply. That explained a lot to me and from what I understand from that link, I still have almost all my ram available. I was looking at the free column under Mem: when I should have been looking at the free column under -/+ buffers/cache:

that was a huge help, thanks junglepeanut :)

Answers to my questions:
1) The memory is being freed up, I was looking at the wrong part of the output of free.
2) The system takes care of this for me.
3) Learned a bit about the kernel and how memory is managed, so it's not a problem anymore.
4) Learn more about Linux :)
5) I seriously doubt I would ever run out of ram, and if I did, the system would just use the swap partition - which I've never seen it use.

---

