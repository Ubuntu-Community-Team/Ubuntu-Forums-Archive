---
title: "Bootstrap - How to run a .cpp program on startup"
date: 2015-04-16
forum: General Help
---

### Post by carr3 on 2015-04-16
Hi,

I have a NVIDIA Jetson TK1 that has Ubuntu 14.04.  I need to bootstrap the Jetson so that it runs a .cpp program upon startup.  Is it possible to add the .cpp file or its executable to the startup applications manager so that the program is run on boot up?  Any suggestions or other approaches would be greatly appreciated.

Thanks,
Carr

---

### Post by Keith_Helms on 2015-04-16
Yes, it's possible.   You want to add the compiled executable not the source .cpp file.

---

### Post by kjohri on 2015-04-16
You can create an init script that runs the program at startup. Look at the link, [http://www.softprayog.in/tutorials/starting-linux-services-with-init-scripts]("http://www.softprayog.in/tutorials/starting-linux-services-with-init-scripts").

---

### Post by carr3 on 2015-04-17
> **Keith_Helms said:**
> Yes, it's possible.   You want to add the compiled executable not the source .cpp file.

Thanks for the feedback Kieth.  I just tried adding my executable to the startup applications preferences without much success.  I believe I may be entering the command incorrectly to the Add Startup Program dialog.  Currently I have just the path as the command, which is what is filled in when I browse for my executable.  Should I be calling the program the same way as in the terminal (./myProgram --arg1 --arg2)?

[IMG]https://mail.google.com/mail/u/0/?ui=2&ik=32710976cb&view=fimg&th=14cc7a125055a5eb&attid=0.1&disp=emb&realattid=ii_14cc7a0a4e598d06&attbid=ANGjdJ-5lml-8tuJwLPgx5WZL-Qvvx1hfaTQOfVCN20Ss2wbrZTIUpdg4OoQosc6TAyK6trFuM2S9HO7hmO75NtIkJUeGxPVh7qMCZOet3dKCcAdEdF6kEQBNWgSgLw&sz=w790-h470&ats=1429278373671&rm=14cc7a125055a5eb&zw&atsh=1[/IMG]

Thanks,
 Carr

---

### Post by carr3 on 2015-04-17
> **kjohri said:**
> You can create an init script that runs the program at startup. Look at the link, [http://www.softprayog.in/tutorials/starting-linux-services-with-init-scripts](http://www.softprayog.in/tutorials/starting-linux-services-with-init-scripts).

Thanks Kjohri.  I will look into this if I cannot get startup applications to work.

---

### Post by Keith_Helms on 2015-04-17
Yes, you want to enter

/path/to/program/executable-name  -option1  -option2

Those startup commands won't be running with the same path as your userid, so you have to explicitly give the full path, such as /home/userid.   Whatever program you're executing and what options it needs also needs to come after the path to it.

---

### Post by carr3 on 2015-04-17
> **Keith_Helms said:**
> Yes, you want to enter

/path/to/program/executable-name  -option1  -option2

Those startup commands won't be running with the same path as your userid, so you have to explicitly give the full path, such as /home/userid.   Whatever program you're executing and what options it needs also needs to come after the path to it.

Thanks Keith.  Works great!

---

