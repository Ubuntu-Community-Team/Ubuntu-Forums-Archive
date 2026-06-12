---
title: "System not starting after Nvidia upgrade"
date: 2014-01-07
forum: General Help
---

### Post by pa.ghorpade on 2014-01-07
Hi,

I am very new to Linux. I am shifting from Windows to Linux and trying to learn it.

I have installed Ubuntu 12.04 LTS on my machine and trying to lean new commands and basic thing. 
My system is AMD Athlon X2 processor and M2N68-AM motherboard with 2GB RAM.

While checking the System details, I found that under graphics it is showing Unknown. I searched how can I install the graphics driver and found this command to install Nvidia drivers.

**sudo apt-get install nvidia-current-updates**

when I used this command it downloaded and installed the drivers for me. But now when I start my system it is not starting. It is showing many things as started and stopping. Among this it is showing 
Starting load fallback graphics devices     [fail]
and all other [ok]

the final line is 
Stopping Userspace bootsplash  

but it is not moving ahead. Computer is not responding to anything after here. Keyboard not working... the only option is to switch off and start again...

please help to solve this...

Thanks in advance..

---

### Post by jeanjd63 on 2014-01-07
Hello, 
You can try this :
When you have a black screen, you do CTRL+ALT+F1 
If a console is opened you give your name and password and you do :
[B]sudo  apt-get  purge "nvidia *"
[/B]
Then you try to reboot :
**sudo  reboot**

---

### Post by efflandt on 2014-01-07
What specific video card or chip do you have? Or once you get to a terminal what do you get for: lspci | grep VGA

I saw someone else trying to install nvidia drivers when all he had was integrated Intel graphics. Although, newer laptops now sometimes have both Intel and Nvidia graphics. In that case you may need to look through the output of lspci for more than one video device, one of which may contain something other than "VGA". Even with the dual types of graphics, the system should still boot after installing nvidia drivers as long as you use **nomodeset** kernel boot parameter.

---

### Post by pa.ghorpade on 2014-01-07
Thank you for your reply.
I will try to do this.

My motherboard has Nvidia Chip its [COLOR=#333333][FONT=Arial]NVIDIA Geforce 7025/nForce 630a  chipset.[/FONT][/COLOR]

---

### Post by cincibluer6 on 2014-01-08
It's possible too that you have too old of a card for the current drivers. I remember there being a cutoff where you would need 173 for older ones. Might look into that too.
But yes, purge the drivers and give the stock ones a go anyway. I've found that they can work with Nvidia just fine sometimes.

---

### Post by pa.ghorpade on 2014-01-09
I tried this option it is showing this to me

ubuntu@ubuntu:~$ lspci | grep -i vga
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 7025 / nForce 630a] (rev a2)

So what should I do after this..

---

