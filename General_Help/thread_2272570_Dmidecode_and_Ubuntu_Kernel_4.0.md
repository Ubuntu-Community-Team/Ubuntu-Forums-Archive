---
title: "Dmidecode and Ubuntu Kernel 4.0"
date: 2015-04-07
forum: General Help
---

### Post by giraffe2 on 2015-04-07
Hi,

I'm not sure if this is the right please to get help / advise for my problem but i don't really knows where else to turn, if someone knows a (sub) forum more suitable please let me know.

_The Problem_:

I'm using Linux 4.0-rc7 downloaded and installed from the Ubuntu kernel PPA. Ever Since using Kernel 4.0 release candidates i've been unable to read the SMBIOS of my laptop by means of running the DMIDECODE command. 

When i issue the command in the terminal for instance ```
sudo dmidecode --type 17
``` i get the following error: 

# dmidecode 2.12
/dev/mem: No such file or directory


And indeed the /dev/mem direct or file is not present in the /dev/ directory. 

When booting Linux Kernel 3.19.3 i can run dmidecode just fine and there is a mem file in the /dev/ directory. 

[U]My question:

[/U]Is the fact that i'm unable to use the dmidecode tool a bug or a feature?  
If it's a bug: is this something i should report? 

If this is a feature: how will i be able to read the SMBIOS in the future without using dmidecode?

I hope someone can help.

---

### Post by Gannet on 2015-04-20
Same thing with 4.0. Seems it's a bug.

---

### Post by dodger-forum on 2015-05-21
If it is a bug is it a Kernel bug or is it related to DMIDECODE?

---

### Post by monkeybrain20122 on 2015-05-21
> **dodger-forum said:**
> If it is a bug is it a Kernel bug or is it related to DMIDECODE?

Kernel bug. it works in 3.19

---

### Post by ki-ustc on 2015-05-24
It seems like a feature in kernel 4.0?

[http://kernelnewbies.org/Linux_4.0](http://kernelnewbies.org/Linux_4.0)
[COLOR=#000000][FONT=Arial]Memory management[/FONT][/COLOR]
[LIST]
[*]Make /dev/mem an optional device [commit]("https://git.kernel.org/linus/73f0718e74e25ac7381450a7a21257b8f26f43f0")
[/LIST]

---

### Post by wryfi on 2015-06-03
Does anyone know how to reactivate /dev/mem on 4.0 so that it's possible to use dmidecode?

---

### Post by Doug S on 2015-06-03
> **wryfi said:**
> Does anyone know how to reactivate /dev/mem on 4.0 so that it's possible to use dmidecode?If I understand correctly, you would have to re-compile the kernel with the .config file changed so that this line:
```
# CONFIG_DEVMEM is not set
```Is changed to this:```
CONFIG_DEVMEM=y
```It is not clear to me why Ubuntu has set this one the way they have.

---

### Post by Doug S on 2015-06-07
I am reasonably certain that is is a mistake / oversight that CONFIG_DEVMEM is not set in the Ubuntu kernel configuration.
I found an older e-mail where it was suggested that it would be changed.
After inquiring about it on IRC, I have entered a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1462822").

---

### Post by monkeybrain20122 on 2015-06-07
I added an affect me too to your bug for what it is worth. But with the speed that these bug fixes go OP may as well just grab kernel 4.1rc6 from mainline. The stable release will arrive in a few weeks.

---

### Post by Doug S on 2015-06-07
> **monkeybrain20122 said:**
> I added an affect me too to your bug for what it is worth. But with the speed that these bug fixes go OP may as well just grab kernel 4.1rc6 from mainline. The stable release will arrive in a few weeks.Thanks. I did the change to 4.1RC1 config myself, as a test. I have edited the bug report so that hopefully it is clearer.

---

### Post by Doug S on 2015-06-24
The [Ubuntu version of Kernel 4.1]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.1-unstable/") now has the proper configuration and dmidecode works.

---

