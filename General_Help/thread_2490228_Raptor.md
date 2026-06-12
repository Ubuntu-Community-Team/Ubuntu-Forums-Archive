---
title: "Raptor"
date: 2023-08-27
forum: General Help
---

### Post by shane_faulkinbury2 on 2023-08-27
Can anyone help me get Raptor running on my Ubuntu 22.04.3 LTS 64 bit system?  I've seen many say run it in Wine, but I cannot even get Wine running.  I primarily run Ubuntu, but have Windows 10 Pro as backup and I'm going to go install the .exe on it.

---

### Post by yancek on 2023-08-27
It is generally a good idea to post a link to software you need help with.  I did a quick online search and the 2 links below were the first I got and they are not the same.  The 2nd link indicates a Linux version if that's the software you want.

[https://raptortech.com/](https://raptortech.com/)

[https://raptor.martincarlisle.com/](https://raptor.martincarlisle.com/)

Found several other sites with Raptor software.  Best post a link to whatever you want.

[https://neweagle.net/raptor/](https://neweagle.net/raptor/)

[https://software.rcc.uchicago.edu/raptor/home.php](https://software.rcc.uchicago.edu/raptor/home.php)

---

### Post by shane_faulkinbury2 on 2023-08-27
Yes, this is the one I am trying to install - [HTML]https://raptor.martincarlisle.com/[/HTML]

---

### Post by yancek on 2023-08-28
So what is the problem?  Did you try to install wine and then the windows version of Raptor?  There is a Linux version available if you scroll down the page, have you tried that?  If so, what happened, error messages?

---

### Post by shane_faulkinbury2 on 2023-09-03
I didn't get an error message.  I installed it fine, but it is not listed in my apps and I cannot start it in terminal.```
shane@shane-OptiPlex-3020:~$ raptorCommand 'raptor' not found, did you mean:
  command 'raptr' from snap raptr (0.2.0)
  command 'kraptor' from deb kraptor (0.0.20040403+ds-2)
See 'snap info <snapname>' for additional versions.
shane@shane-OptiPlex-3020:~$ raptor_avalone
raptor_avalone: command not found
```

---

### Post by yancek on 2023-09-04
The page you indicate you got it from is a third party site so it would probably not show in any application menu.  Exactly how are you trying to show that it is installed?  If you open a terminal and run the command below, it will list programs installed in alphabetical order:

```
 apt list --installed
``` 

Did you download the zip file for Linux?  Is there a README file available or any other instructions?  The link below has some information which might be helpful.

[https://www.testingdocs.com/running-raptor-flowchart-on-ubuntu/](https://www.testingdocs.com/running-raptor-flowchart-on-ubuntu/)

---

