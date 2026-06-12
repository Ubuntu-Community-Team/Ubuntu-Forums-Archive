---
title: "Kernel Panic Ubuntu 12.04"
date: 2013-07-30
forum: General Help
---

### Post by Windowjunk on 2013-07-30
My Dell Vostro 1015, after leaving it untouched for about a month, had recently booted it up to find this happen:
[IMG]http://i.imgur.com/RJ185nj.jpg?2[/IMG]
This seems quite odd as it was working just fine the last time I used it.

---

### Post by mojo706 on 2013-07-30
Hi is this the first boot after that month or so?

---

### Post by Windowjunk on 2013-07-30
> **mojo706 said:**
> Hi is this the first boot after that month or so?
This is the 3rd boot up after this month (I've tried first to boot up the "Recovery" option on the Grub screen, as well as "other versions" and no luck).

---

### Post by mojo706 on 2013-07-30
Do you have the output from recovery(must have some output) ? Please capture it and share the image.

---

### Post by Windowjunk on 2013-07-30
> **mojo706 said:**
> Do you have the output from recovery(must have some output) ? Please capture it and share the image.
It stopped on this:
[IMG]http://i.imgur.com/T8x46ww.jpg?1[/IMG]

---

### Post by mojo706 on 2013-07-30
I currently cannot answer your question not because of lack of information but the output is different than what I expected and have seen. I am searching vigourously. If you find something please inform us as I will if I get a solution :).

---

### Post by Windowjunk on 2013-07-30
> **mojo706 said:**
> I currently cannot answer your question not because of lack of information but the output is different than what I expected and have seen. I am searching vigourously. If you find something please inform us as I will if I get a solution :).
Thank you, I appreciate your help very much! Would be a shame if my files are compromised...hopefully that's not the case.

---

### Post by mojo706 on 2013-07-30
You are welcome also pass by [DebuggingKernelBoot]("https://wiki.ubuntu.com/DebuggingKernelBoot") see if you can try some of their procedures or visit the #ubuntu-kernel IRC channel to ask for some help from the Kernel Team! 
[h=2][/h]

---

### Post by lah7 on 2013-07-30
> **Windowjunk said:**
> Would be a shame if my files are compromised...hopefully that's not the case.

Have you tried booting a Live CD/USB session of Ubuntu? If you're able to access your partition Ubuntu resides on, you may be able to recover any important files before it's too late. You may be able to read logs stored on the system as well.

If you're unable to enter a live session environment and you still get a kernel panic, it could be signs of hardware failure or a corrupt hard drive :(

---

### Post by Windowjunk on 2013-07-30
> **mojo706 said:**
> You are welcome also pass by [DebuggingKernelBoot]("https://wiki.ubuntu.com/DebuggingKernelBoot") see if you can try some of their procedures or visit the #ubuntu-kernel IRC channel to ask for some help from the Kernel Team! 

Thanks, I followed the steps and here's an image of the [result]("http://i.imgur.com/TCIhqzU.jpg").
> **lah7 said:**
> Have you tried booting a Live CD/USB session of Ubuntu? If you're able to access your partition Ubuntu resides on, you may be able to recover any important files before it's too late. You may be able to read logs stored on the system as well.

If you're unable to enter a live session environment and you still get a kernel panic, it could be signs of hardware failure or a corrupt hard drive :(

I did try this. I'm not quite sure if my files are really corrupt/gone, but when I tried browsing through my computer's filesytem (yes, made sure it wasn't the filesystem for the live CD), it didn't really show much of anything but a few "README"'s and "PRIVATE" executables.

---

### Post by mojo706 on 2013-07-31
Which of the steps did you follow? So that we can eliminate them one by one.

---

### Post by Windowjunk on 2013-07-31
> **mojo706 said:**
> Which of the steps did you follow? So that we can eliminate them one by one.
In the Boot Options section, I did all of steps 1-6.

---

### Post by Windowjunk on 2013-08-02
Bump

---

