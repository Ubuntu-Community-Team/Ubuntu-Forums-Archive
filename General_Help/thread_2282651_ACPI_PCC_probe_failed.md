---
title: "ACPI PCC probe failed"
date: 2015-06-15
forum: General Help
---

### Post by varun10 on 2015-06-15
The picture show the error when I restarted my computer. Before I restarted I was encountering a problem that didn't let me add files or delete them because my system was in read only state.


[http://i.imgur.com/CywhD0J.jpg](http://i.imgur.com/CywhD0J.jpg)

---

### Post by sandyd on 2015-06-15
Hi, can you post the output of
```

mount
cat /etc/fstab

```

Could be that a partition is being mounted incorrectly.

---

### Post by varun10 on 2015-06-16
> **sandyd said:**
> Hi, can you post the output of
```

mount
cat /etc/fstab

```

Could be that a partition is being mounted incorrectly.

thank you, here's a picture of the output: [http://i.imgur.com/vfyPpew.jpg](http://i.imgur.com/vfyPpew.jpg)

---

### Post by QIII on 2015-06-16
Hello!

Rather than an image, it would be far better to copy the output from the terminal by highlight it and pressing ctrl +shift+C and then pasting it here between code tags by clicking the # button above the text input box, placing your cursor between the tags and pressing ctrl+V.

Thanks.

---

### Post by grahammechanical on 2015-06-16
What makes you think that the two problems are related?

ACPI PCC probe failed is a common system message that appeared about half way through the 26 week development cycle of 15.04 and I still see it when I load the development version of 15.10.

Starting version 219 refers to the version of SystemD that is being loaded. Ubuntu switched from using Upstart as an init system to SystemD part way through the 15.04 development period. And that is when we started seeing that message. The development version of 15.10 has later versions of SystemD and that message does not appear any more.

It is the switch to emergency mode that is the issue to be investigated. I guess that going into emergency mode would put the file system into read only mode.

Some details about your hardware might prove useful. Have you installed and removed anything that might cause the OS loading process to go into emergency mode?

Regards.

---

### Post by varun10 on 2015-06-17
I haven't really installed anything new other than my regular updates. I installed Windows 10 preview, but that was after I was getting this error on ubuntu. 

I was trying to drag a a few files from my other hard drive, but it was locked because of windows 8.1 "fast reboot" setting which "locks" ( not really) that hard drive. I ran a few sudo codes in terminal to try to "unlock" the windows hdd. (I'm gonna try to find the code again).

I think the hard drive read only problem may be related because that's the only problem I had with the computer before I restarted only to see this ACPI error

---

