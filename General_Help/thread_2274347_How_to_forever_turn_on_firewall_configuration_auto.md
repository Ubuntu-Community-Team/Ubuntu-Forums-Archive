---
title: "How to forever turn on firewall configuration automatically?"
date: 2015-04-19
forum: General Help
---

### Post by luke40 on 2015-04-19
The firewall configuration of system settings  would turn off and every time when I login the system I must turn it on again.

 How to turn on it permanently?

Thanks.

---

### Post by sammiev on 2015-04-19
What does this display?
> sudo ufw status

---

### Post by luke40 on 2015-04-19
The display of the command is:
[B]
Status: active[/B]

But it's bcoz I already turn it on now? What to do next?

---

### Post by sammiev on 2015-04-19
> **luke40 said:**
> The display of the command is:
[B]
Status: active[/B]

But it's bcoz I already turn it on now? What to do next?

Reboot your computer and try it again.

---

### Post by luke40 on 2015-04-23
the terminal display:

[I]Firewall is active and enabled on system startup
[/I]
but the firewall still not enabled when system startup again.

---

### Post by cariboo on 2015-04-23
What message do you get when you run:

```
sudo ufw status
```

after a restart?

---

### Post by luke40 on 2015-04-26
the message says:

[I][B]Status: inactive

[/B][/I]after a restart.

---

### Post by sammiev on 2015-04-26
> **luke40 said:**
> the message says:

[I][B]Status: inactive

[/B][/I]after a restart.

Try this command and reboot.

```
sudo ufw enable
```

Then try

```
sudo ufw status
```

---

### Post by luke40 on 2015-04-28
i did it before.

sudo ufw enable

reboot

then 

sudo ufw status

the terminal display

[I][B]Status: inactive

[/B][/I]

---

### Post by sammiev on 2015-04-28
> **luke40 said:**
> i did it before.

sudo ufw enable

reboot

then 

sudo ufw status

the terminal display

[I][B]Status: inactive

[/B][/I]

Very strange, have you tried installing GUFW and turning on your firewall that way? 

I never ran into this problem on Ubuntu before but had it happen on other OS.

What OS are you running and version please?

---

### Post by luke40 on 2015-05-01
Yes. I have tried GUFW. The result are all the same.
My version is 14.01.

Many thanks.

---

### Post by sammiev on 2015-05-01
After your firewall is active and enabled try this command in terminal and reboot.

```
sudo invoke-rc.d iptables-persistent save
```

Best check your version again, it should be 14.04 or 14.10

---

### Post by luke40 on 2015-05-02
Yeah, it's 14.04. Sorry.

The output of the instruction says:

***invoke-rc.d: unknown initscript, /etc/init.d/iptables-persistent not found.***

What should I do now?

Thanks.

---

### Post by sammiev on 2015-05-02
Came across [this]("http://askubuntu.com/questions/474216/14-04-missing-etc-init-d-ufw-my-firewall-never-auto-starts"), not sure if it will help as I never had this problem.

---

### Post by luke40 on 2015-05-03
Thanks anyway.
Maybe I can create this file(*** /etc/init.d/iptables-persistent)*** with empty contents first.
How to create a empty file?

---

### Post by sammiev on 2015-05-04
Create a rule and save it.

---

