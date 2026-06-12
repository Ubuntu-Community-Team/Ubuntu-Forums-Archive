---
title: "Ubuntu 13 change drm_kms_helper poll param"
date: 2013-05-11
forum: General Help
---

### Post by skgskg on 2013-05-11
[COLOR=#333333][FONT=Ubuntu Beta]I had ubuntu for 3 years( since version 11). Every version I had, had the Intel Graphics bug in it's kernel - randomly freezing mouse. I fixed this problem using "echo N> /sys/module/drm_kms_helper/parameters/poll" (changing it from Y to N), as described in[http://souriguha.wordpress.com/2011/03/08/how-to-solve-problem-with-thinkpadkslowd-kworker-on-linux-kernel-2-35-2-36/](http://souriguha.wordpress.com/2011/03/08/how-to-solve-problem-with-thinkpadkslowd-kworker-on-linux-kernel-2-35-2-36/) .[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]I upgraded to version 13, and unfortunately this doesn't work (there is no /etc/modprobe.d/local.conf), I searched the web and tried adding the command above to /etc/rc.local, when I check the param it seem to be set to N, but still didn't solve the problem, so tried setting it to 0, and checked it, it turns back to Y somehow. The freezes still occurs :([/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]My kernel version is: Linux *****-ThinkPad-T400 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:35:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]What should I do? And on what version this bug will be fixed (It's really annoying since v11)?[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Btw: If someone could explain to me what is the relation between polling and the mouse (I think it's the whole screen)?![/FONT][/COLOR]

---

### Post by rod40cool on 2013-05-11
Same here. I too would like to know how to fix this. T400 also but with proposed kernel (although made no difference). Linux rods-T400ssd 3.8.0-20-generic #31-Ubuntu SMP Mon May 6 17:03:32 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux.

---

### Post by rod40cool on 2013-05-12
skgskg,

I think I've found a way to make the drm_kms_helper poll parameter stick. After doing a little reading and experimenting with different conf files in /etc/modprob.d/ I found I couldn't get the parameter to stick using a conf file, BUT I was able to get it to work using a kernel boot option.

Try this, it worked for me.

```
 sudo gedit /etc/default/grub 
```

Edit the line
```
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Add the option "drm_kms_helper.poll=N" inside the double quotes after "splash" so that it looks like mine.
```
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash drm_kms_helper.poll=N"
```

Save and close.

Then run
```
sudo update-grub
```

Then reboot and check the parameter afterwards using this command
```
sudo cat /sys/module/drm_kms_helper/parameters/poll
```

---

### Post by skgskg on 2013-05-13
Wow! :D it really works!
Thanx mate!!

I hope it sticks this time, I test my mouse these few days :)

---

