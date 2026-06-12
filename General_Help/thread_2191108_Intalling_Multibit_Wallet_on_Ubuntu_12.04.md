---
title: "Intalling Multibit Wallet on Ubuntu 12.04"
date: 2013-11-30
forum: General Help
---

### Post by rbscairns on 2013-11-30
I am trying to install the Multibit Bitcoin wallet on my PC using Ubuntu 12.04. My problem starts very early.

[LIST=1]
[*]I downloaded multibit-0.5.15-linux.jar from the Multibit web site.
[*]I check my Downloads folder and found that the file multibit-0.5.15-linux.jar had been saved there.
[*]Following the Multibit installation instructions for Linux, I then opened a terminal window and typed ```
chmod +x multibit-0.5.15-linux.jar
```
[*]This then returned the message ```
chmod: cannot access `multibit-0.5.15-linux.jar': No such file or directory
```
[/LIST]
Where do I go from here?

---

### Post by claracc on 2013-12-01
When you open your terminal window, have you changed to the directory where downloads are?, I suppose it will be /home/your_personal_folder/Downloads, then in this directory you execute the chmod command.

---

### Post by rbscairns on 2013-12-02
> **claracc said:**
> When you open your terminal window, have you changed to the directory where downloads are?, I suppose it will be /home/your_personal_folder/Downloads, then in this directory you execute the chmod command.

Thanbk you Claracc. I solved the problem by opening Terminal and entering ```
cd ~/Downloads
```
This changed my directory (cd) to my Downloads folder where my multibit-0.5.15-linux.jar file was located. I then proceeded with the installation as given in the Multibit web site and all worked well.

I now have Multibit installed.

---

### Post by claracc on 2013-12-03
You are very welcome. Glad you got fixed your problem.

---

