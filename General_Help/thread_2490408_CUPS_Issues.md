---
title: "CUPS Issues"
date: 2023-09-02
forum: General Help
---

### Post by sabale on 2023-09-02
Hello,

I have been trying to instal a Canon MG6120 printer in my computer and I am not able to do it. Currently, I have Ubuntu 22.04.03 LTS jammy.

If I try to add my printer from configuration / printers, I get "the printing system service seems to be unavailable".

Then, If i try to to start cups with the command (sudo systemctl start cups) I get this "Job for cups.service failed because the service did not take the steps required by its unit configuration. See "systemctl status cups.service" and "journalctl -xeu cups.service" for details".

Finally, I tried to go through [http://localhost:631/](http://localhost:631/) but it impossible to do so. I got this "ERR_CONNECTION_REFUSED"

What should I do in order to install my printer? Is it possible to restart CUPS configuraton?


Thanks so much.

---

### Post by sabale on 2023-09-03
Hello, 

I managed to go trough  [http://localhost:631/](http://localhost:631/) and see the printrer installed. Unfortunatelly I still have the same problem. I am not able to print becouse it is look like the printer is disable. At the [http://localhost:631/](http://localhost:631/) webpage I can see: 


[TABLE="class: list, width: 1414"]
[TR]
[TD][MG6100]("http://localhost:631/printers/MG6100")[/TD]
[TD]Canon MG6100 series[/TD]
[TD][/TD]
[TD]DYMO Label Printer[/TD]
[TD]Idle - "Rejecting Jobs"[/TD]
[/TR]
[/TABLE]

Any ideas?

Thanks so much.

---

### Post by sabale on 2023-09-03
[SIZE=4]Following with this issue, I've just realized that the main problem is that I do not have the Canon drivers installed in my computer. I tryied to install the same printer in Linux Mint and it works perfect. 
Now, I did some more digging around this and found the following repository which I installed:

sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update

The problem is that when I try to install the printer with [http://localhost:631/admin](http://localhost:631/admin), I do not see the drivers. Thus, I am not able to installed it properly. 

I attached a picture with de CUPS's currently drivers. 

Any idea, please?[/SIZE]

---

