---
title: "Snap installation fails"
date: 2019-02-28
forum: General Help
---

### Post by danielsender on 2019-02-28
I'm not sure if this is the right forum for this issue, but perhaps I can get some guidance on it. I have two similar Dell machines, a M6500 and a M6800, both running 18.04.2. The M6500 was updated from 16.04 to 18.04 while the M6800 was a fresh install. Using snap I installed Acestreamplayer on the M6800 without any problems, however on the M6500 the installation fails, giving me the following messages:
```

- Setup snap "acestreamplayer" (8) security profiles (cannot setup udev for snap "acestreamplayer": cannot reload udev rules: exit status 2 [FONT=Arial]udev output:[/FONT][FONT=Arial])[/FONT]
[FONT=Arial]- Setup snap "acestreamplayer" (8) security profiles (cannot reload udev rules: exit status 2 [/FONT][FONT=Arial]udev output:[/FONT][FONT=Arial])[/FONT]
[FONT=Arial]- Connect acestreamplayer:opengl to core:opengl (cannot setup udev for snap "acestreamplayer": cannot reload udev rules: exit status 2 [/FONT][FONT=Arial]udev output:[/FONT][FONT=Arial])[/FONT]
[FONT=Arial]- Connect acestreamplayer:opengl to core:opengl (cannot reload udev rules: exit status 2 [/FONT][FONT=Arial]udev output:[/FONT])
```
Can some guru help me on this?

Thanks

---

### Post by danielsender on 2019-03-06
bump - should be this posted on another forum?

---

### Post by arm-c on 2019-03-12
Bump -- Same issue here for me.  

Not same SNAP package... but same fail.  My installation attempt was with:  vidcutter

---

### Post by wildmanne39 on 2019-03-12
Hello arm-c, please do not bump some one else's thread, it is best to create your own so you and the OP of this thread can both get the help you need.

Thanks

---

### Post by arm-c on 2019-03-12
I figured that given it is the same issue -- " cannot reload udev rules: exit status 2 udev output" that a solution would be the same for both of us....  

Generally, when there is a perceived similarity between issues / bugs, the protocol as I understand it is to NOT create a separate thread/bug report.  Not trying to "pick a fight"... simply explaining why my post was here and not elsewhere or in new thread.  My apologies for using the word "bump".

---

### Post by sisco311 on 2019-03-12
Is the core snap installed on the machine:
```
snap list
```?

Some details about the interfaces and slots and plugs would be helpful as well:
```
snap interface
snap interfaces
```

---

### Post by danielsender on 2019-03-12
> **sisco311 said:**
> Is the core snap installed on the machine:
```
snap list
```?

Some details about the interfaces and slots and plugs would be helpful as well:
```
snap interface
snap interfaces
```

With the help of the people at snapcraft.io we found that executing 'journalctl --unit systemd-udevd' resulted in a huge file due to spamming by a line saying:
```
Mar 08 09:32:28 bach systemd-udevd[1886]: Process 'hid2hci --method=dell --devpath=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6.2/1-1.6.2:1.0' failed with exit code 1.
```

There was no way to get rid of that junk, even after disabling bluetooth in the BIOS. However after disabling bluetooth, I was able to install acestreamplayer with snap. This hid2hci sticks even after disabling 97-hid2hci.rules.

---

### Post by wildmanne39 on 2019-03-12
> **arm-c said:**
> I figured that given it is the same issue -- " cannot reload udev rules: exit status 2 udev output" that a solution would be the same for both of us....  

Generally, when there is a perceived similarity between issues / bugs, the protocol as I understand it is to NOT create a separate thread/bug report.  Not trying to "pick a fight"... simply explaining why my post was here and not elsewhere or in new thread.  My apologies for using the word "bump".
Even if it was protocol at one time which I do not think it was, it is not anymore, it is considered rude hijacking someone else's thread and it makes it confusing for the OP of this thread and the people helping so we always want users that need help to start there own thread, most of the time the cause of one users issue is not the same for another, you are welcome to follow this thread and see if it helps you solve your issue but for personalized help, which means to ask another question please start your own thread, no need to reply to me in this thread again, I do not want to drag it any further off topic.

Thanks

---

### Post by amelia26 on 2019-04-02
Hi, 
[FONT=Helvetica]This seems to be related to:[/FONT]
[FONT=Helvetica][https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1759836](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1759836)[/FONT][COLOR=#000000][FONT=Arial][Dafont]("https://appsync.biz/dafont/")[192.168.l.l]("https://192168ll.onl/")[FileHippo]("https://appsync.biz/filehippo/")[/FONT][/COLOR]

---

