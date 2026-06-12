---
title: "How to execute a command as root on user live session login on live usb pen"
date: 2017-07-17
forum: General Help
---

### Post by kerrygee on 2017-07-17
Hi,

i am currently fighting this issue on my self made usb pen with persistence:
[URL="https://askubuntu.com/questions/761592/unable-to-apt-get-dist-upgrade-on-a-persistent-ubuntu-16-04-usb"]https://askubuntu.com/questions/761592/unable-to-apt-get-dist-upgrade-on-a-persistent-ubuntu-16-04-usb
[/URL]
the iso image is customized with Cubic and repacked with it. after installing the iso on my pen and run it with persistence (persistence isnt the issue, i just tell you what kind of pen it is), whenever i run a "apt-get update", i am gettin the same error as in the post. the fix is provided there, too, but it has to be run manually and only once in a live sessions terminal. i just want to run it only once on the first login on the live session to fix the issue and then delete the command/script/job or whatever could be the best solution for this. it has to run as root to fix that issue. much better would be to run it in the Cubic chroot environment. first i did try it in the Cibic chroot, but it didnt fix it on the final iso file. after installing it on a pen, the issue still persist. i am not sure what exactly leads to this.

what would be the best way to fix that problem without the need to manually enter the chmod command on the first login? it should be automated, silently with no terminal or gui showing and run only once. a job, a service, a script? the target system is a kubuntu 16.04.2 x64.

any help would be very nice.

tia 

K.

---

### Post by TheFu on 2017-07-17
I would run it at boot, in a startup file.  Something placed into /etc/init/ .... just follow the examples there already.  There are 3 different techniques for doing it:
* old-style init scripts
* 6 yr old "upstart scripts"
* 3 yr old "systemd stuff

Pick one. Read up on it.  Follow one of the 50 examples already on the machine.

---

### Post by kerrygee on 2017-07-17
> **TheFu said:**
> I would run it at boot, in a startup file.  Something placed into /etc/init/ .... just follow the examples there already.  There are 3 different techniques for doing it:
* old-style init scripts
* 6 yr old "upstart scripts"
* 3 yr old "systemd stuff

Pick one. Read up on it.  Follow one of the 50 examples already on the machine.

Hi,

thanks for the quick reply! Which one would you prefer and why?

best

K.

---

