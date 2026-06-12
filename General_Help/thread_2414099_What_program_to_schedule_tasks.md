---
title: "What program to schedule tasks?"
date: 2019-03-05
forum: General Help
---

### Post by ProDigit on 2019-03-05
Hi,

2 things I want to do:
1- Start a terminal command at every bootup (basically a command that will start a program)
2- Start a command to shut down this program, and reboot the computer at a specific time.

I know the command, I just need to know how what program I can use, that will automatically run the commands at the right time?

---

### Post by 0tyugh on 2019-03-06
Cron.
For "every bootup", use @reboot. Don't forget to export variable environements to be able to use Xorg.

---

### Post by SeijiSensei on 2019-03-06
If you place commands in /etc/rc.local, they will be run with root privileges at the end of the boot sequence.

Cron runs once each minute and runs commands found /etc/crontab and other files. You could reboot the machine each day at 4 am with the entry in /etc/crontab:

```
0 4 * * * root /sbin/reboot
```

See "[man crontab](https://linux.die.net/man/5/crontab)" for details.

---

### Post by ProDigit on 2019-04-08
Thanks.
I merely want to run a few terminal commands.
Can they be inserted in the /etc/rc.local file?

Like, I would like my graphics cards to be power limited with each reboot to start up Folding at home,

```
sudo nvidia-smi -i 1 -pl 135
sudo /etc/intit.d/FAHclient start

```

I also need to add a simple code on how to change the fanspeed on my Nvidia GPU.
I've tried some things like:

```
Sudo nvidia-settings -a "[gpu:0]/GPUFanControlState=1" -a "[fan:0]/GPUCurrentFanSpeed=55"
```

But without success. It's saying something like 'GPU fan speed read only error'; or something.

---

