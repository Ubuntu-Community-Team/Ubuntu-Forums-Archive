---
title: "Hard drive clicking noise on Ubuntu (dual boot W10)"
date: 2016-10-20
forum: General Help
---

### Post by &amp;*kRegWq on 2016-10-20
Hello, I'm new here, a student from Croatia. I have a problem with my dual-booted Ubuntu 16.04 on Dell Latitude E5540. Weird click noise, I suppose it comes from hard drive, happens only while booting (just before Ubuntu "enters" desktop). It happens only once, on Ubuntu only, not on Windows 10 that I have installed on another partition. I can't find the solution for this problem and I'm scared that it will damage my hard drive. I've already tried this : [http://www.computercorrect.com/2011/operating-systems/linux/ubuntu/fix-for-constant-hard-drive-clicking-in-ubuntu/](http://www.computercorrect.com/2011/operating-systems/linux/ubuntu/fix-for-constant-hard-drive-clicking-in-ubuntu/)

It didn't help. Any ideas? Thanks.

---

### Post by SeijiSensei on 2016-10-20
Replace the hard drive.  When you start hearing clicks, it's on its way to failure.

---

### Post by &amp;*kRegWq on 2016-10-20
Really no other solution? Because it works fine on Windows and Dell Diagnostics program says it's excellent. Laptop is 2 years old and it's not used at all, everything works perfect on Windows. Before this laptop I had HP which had those clicking noises too when I installed Windows. They somehow got fixed by itself after few boot times, but this one sounds stronger.

---

### Post by RobGoss on 2016-10-20
I would say as long as it's running OK keep anything that's important backed up just in case that hard drive fails it may just be something  Ubuntu I'm not really sure what would cause that clicking noise someone else may have better knowledge

---

### Post by &amp;*kRegWq on 2016-10-20
It's only one click, but strong. Already backed up all my data. There are lots of common problems on the internet but nobody has the solution. Also I know 2 other guys from my college group with the same issue, so I don't think that's hardware failure.

---

### Post by RobGoss on 2016-10-20
Yeah it sound to me like it has to do with the Ubuntu installation not the hardware if the hard drive is failing I would think you would get some kind of indication. As you mentioned it's  a fairly new machine

Did you hear that noise when ran the live media of Ubuntu

---

### Post by &amp;*kRegWq on 2016-10-20
Yes, I did. Sorry I didn't write that before. I've installed it with USB, made bootable with Universal USB Installer, installation passed smooth.

What do you suggest? New installation?

---

### Post by RobGoss on 2016-10-20
> **istignedec said:**
> Yes, I did. Sorry I didn't write that before. I've installed it with USB, made bootable with Universal USB Installer, installation passed smooth.

What do you suggest? New installation?

Try running the live desktop environment to see if that clicking noise is present

---

### Post by &amp;*kRegWq on 2016-10-20
Yup, everything works awesome except that click on the beginning. Thanks a lot for the answers, I'll use it for few days and write the "update" here. :)

Ok, I'll try that too, thanks once again.

---

### Post by RobGoss on 2016-10-20
Sounds good let us know how it goes, if that noise is not there when using Windows then I don't feel like it's failing hardware just my opinion

---

### Post by &amp;*kRegWq on 2016-10-23
So, here are the "results". After update the problem still occurs. It happens when I boot Ubuntu from Live USB too. And also, I hear the click when I wake up laptop from standby (and when booting as before).

---

### Post by RobGoss on 2016-10-23
Have you tried any other distribution on this machine like Ubuntu mate 16.04 ? I have it installed on one of my test machines and it runs very well

---

### Post by &amp;*kRegWq on 2016-10-23
Ok, thanks! I'll try it tommorow.

---

### Post by oldos2er on 2016-10-23
Have you run smartctl on the drive? [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

