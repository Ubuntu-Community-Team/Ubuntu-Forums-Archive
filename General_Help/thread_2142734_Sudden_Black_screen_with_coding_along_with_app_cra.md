---
title: "Sudden Black screen with coding along with app crash"
date: 2013-05-06
forum: General Help
---

### Post by Nalin Khurb on 2013-05-06
Hello,
I am new to this forum but not to ubuntu ! I have recently installed ubuntu 12.04 on my laptop and I am facing some issues which are as under.
1. There is a random dendency of the system to show a black screen with coding written
2. Firefox 20 version crashes very frequently
3. Chromium web browser also crashes
For problem 1 when the code was displayed i used the shortcut [ctrl+alt+delete] and got logged out and I could use my system once again after logging in. But it helped me only once. I am not sure what is the cause of this problem. 
for better diagnosis i am attaching a picture taken from my phone of the screen that appeared the last time.
and please see the 15th last line. call trace??
is that some kind of malware.?
PLease help[ATTACH=CONFIG]242270[/ATTACH]

---

### Post by matt_symes on 2013-05-06
Hi

Malware ? I don't think so. That is your kernel crashing though.

Install another kernel and boot into that. See if you get the same problem.

Kind regards

---

### Post by Nalin Khurb on 2013-05-08
Hey matt,
I updated the kernel from 3.2 to 3.9 raring but I am facing a new problem here !! I am unable to put the machine on suspend and i cannot shut it down, it just freezes. And the apps are still crashing.
what to do now?

---

### Post by matt_symes on 2013-05-08
Hi

Are you running Ubuntu in a virtual machine ?

Kind regards

---

### Post by Nalin Khurb on 2013-05-08
no, and I don't know how to run a virtual machine.!!#-o

And one more thing, there are no random kernel crashes now ^_^

---

### Post by matt_symes on 2013-05-08
Hi

> **Nalin Khurb said:**
> no, and I don't know how to run a virtual machine.!!#-o

The reason why i asked is because you have Virtualbox drivers running.

> And one more thing, there are no random kernel crashes now ^_^

Wow ! Excellent ! Did you have any updates come down ?

 Post back if it happens again.

Kind regards

---

### Post by Nalin Khurb on 2013-05-21
Hi matt,
sorry for the late reply, as I was busy preparing for my entrance exams. 
n
Now, I changed the kernel to 3.5 generic and now there were no kernel crashes and I could as well shut down and put the machine on suspend.
But I was unable to change the default kernel version in GRUB.
So, I thought to install ubuntu 13.04, but unfortunately it is also crashing.
The machine is a 2007 model. Maybe the old hardware is causing the problem?
What do you say?

---

### Post by matt_symes on 2013-05-21
Hi

> **Nalin Khurb said:**
> Hi matt,
sorry for the late reply, as I was busy preparing for my entrance exams. 
n
Now, I changed the kernel to 3.5 generic and now there were no kernel crashes and I could as well shut down and put the machine on suspend.
But I was unable to change the default kernel version in GRUB.
So, I thought to install ubuntu 13.04, but unfortunately it is also crashing.
The machine is a 2007 model. Maybe the old hardware is causing the problem?
What do you say?

It could be a whole number of things and without an exhaustive list of your hardware and logs, it would just be stabbing in the dark.

The GRUB issue with your old kernel should have been easy to fix.

If i were you i would roll back to the stable working version you had with the 3.5 kernel, then we can look at making sure that grub sticks with a kernel.

How did you install the new kernels ?

Kind regards

---

### Post by Nalin Khurb on 2013-05-21
well ok then, we'll rule out the harware for the moment.
I also tried 11.04[working fine] and before using 12.04 I had used 10.04 and 9.10 without even a single problem. The new versions are causing problems.
Can I fix the 13.04[crash ; firefox=many times; kernel= a few times; vlc player = every time]??
And now I don't have a copy of 12.04 with me. So, should I use 11.04[reluctant coz its old] or 13.04[try fixing]
Yes one very important thing installed a 2 Gb ram stick when I installed 12.04. Could that cause problems with the new versions?

I forgot to mention how  i installed the new kernels!!
3.9 by downlaoding from kernel.ubuntu.com [mainline][saw it from a youtube video]
3.5 generic from Synaptic Package manager...

---

