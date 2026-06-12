---
title: "Ubuntu won't boot after adding tmpfs ,  please please HELP emergency !"
date: 2015-08-11
forum: General Help
---

### Post by liam25 on 2015-08-11
Guys , I ran into trouble . Here are things I did before the problem start .I added line 'tmpfs  /var/log/apt                                         tmpfs defaults,noatime,nodiratime 0 0'  into /etc/fstab When I reboot , it brings me to the emergency mode , which is kinda like command prompt thing .I ran the filesystem check , it says mountpoint /var/log/apt couldn't be found I seriously need help , my exam is coming soon & the files inside Ubuntu is really important to me .Please if anyone see this , please guide me what to do . For now I can do nothing but crying alone in the corner T___TUbuntu 15.04

---

### Post by howefield on 2015-08-11
Assuming you tried taking the line back out of /etc/fstab ?

---

### Post by liam25 on 2015-08-11
> **howefield said:**
> Assuming you tried taking the line back out of /etc/fstab ?

Hi , thanks for ur quick reply , I haven't tried that , can you guide me how to do that ?

---

### Post by Paul_Cambal on 2015-08-11
Everytime I run into this kind of problem, I just live image any linux version, download the 1-click-boot-repair-thingy, run it, and everything goes back to normal. Just google it if you want, you'll probably find it

---

### Post by howefield on 2015-08-11
Try 

```
nano /etc/fstab
```

You might need to preface the command with sudo, then cursor down to the offending line and remove it or put a # sign at the beginning of the line.

Ctrl + o (to write out).
Press Enter
Crtl + x (to exit)

then reboot with

```
sudo reboot
```

You shouldn't really mess with system files without first taking a copy of them so you can put them back if required.

---

### Post by liam25 on 2015-08-11
> **howefield said:**
> Try 

```
nano /etc/fstab
```

You might need to preface the command with sudo, then cursor down to the offending line and remove it or put a # sign at the beginning of the line.

Ctrl + o (to write out).
Press Enter
Crtl + x (to exit)

then reboot with

```
sudo reboot
```

You shouldn't really mess with system files without first taking a copy of them so you can put them back if required.

Thanks Sir , you're my life saver .
Now the problems solved . At least I learnt something today .
Once again , thank you so much for ur help .

---

### Post by howefield on 2015-08-11
You are very welcome.

Just out of interest, were you doing this because you have an SSD ?

---

### Post by liam25 on 2015-08-11
> **howefield said:**
> You are very welcome.

Just out of interest, were you doing this because you have an SSD ?

Yeah .

---

### Post by howefield on 2015-08-11
What I add to /etc/fstab is ...

```
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
```

via the following command..

```
echo "tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0" | sudo tee -a /etc/fstab
```

Not saying it is right or wrong, just works for me.

Good luck with the exams. :)

---

### Post by pqwoerituytrueiwoq on 2015-08-11
you can apply a new line added to /etc/fstab without a reboot by using this command
```
sudo mount -a
```
it will give you a error message if there is a typo in it

[**[COLOR=#990303][B]howefield**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=186490") uses the same line as i do

keep in mind that by doing this /tmp/ will max out at 1/2 your ram's capacity
there was one system i worked on that required me to define the size manually for it to work
eg (4GB ram disk, 2gb would be 2048M):
```
tmpfs                                     /tmp          tmpfs   defaults,noatime,size=4096M,mode=1777 0       0
```

---

### Post by liam25 on 2015-08-11
Alright i'll try it out :KS
You guys are awesome , have a nice day .

---

### Post by echotech2 on 2015-08-12
Sidebar:  I see in Howefield's answer the options are separated with commas, eg. defaults,noatime,mode=1777.  In my fstab from a fresh install the hard drive options are separated by several spaces (tabs?), no commas.  Does it make any difference?

---

### Post by howefield on 2015-08-12
> **echotech2 said:**
> Sidebar:  I see in Howefield's answer the options are separated with commas, eg. defaults,noatime,mode=1777.  In my fstab from a fresh install the hard drive options are separated by several spaces (tabs?), no commas.  Does it make any difference?

Have a look at what the documentation says about the fstab options field :

```
man fstab
```

---

### Post by echotech2 on 2015-08-13
From man fstab:

> Each filesystem is described on a separate line; fields on  each
       line are separated by **tabs** or **spaces**.

  Thanks.  I'm still a little confused about the commas, lol.

---

### Post by howefield on 2015-08-13
> **echotech2 said:**
> Thanks.  I'm still a little confused about the commas, lol.

Fields are separated by tabs/spaces but the options field is a comma separated list.

---

### Post by echotech2 on 2015-08-14
Thanks for the info.

---

