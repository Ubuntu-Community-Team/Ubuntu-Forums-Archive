---
title: "Rebooting Via 'REISUB' Doesn't Work"
date: 2021-11-29
forum: General Help
---

### Post by scribner on 2021-11-29
I was previously able to use the magic SysRq key (see <[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)>) to do a graceful reboot of my Ubuntu computer by pressing Alt-PrtScr and then, in order, R, E, I, S, U, and B. That was with a Lenovo X270. When I tried it today with a Dell Latitude 3590, however, it did not work. Same version of Ubuntu (20.04 LTS), same instructions followed, but the computer just continued to hang until I held down the power button.

According to a blog post (see <[https://www.binarytides.com/linux-command-shutdown-reboot-restart-system/](https://www.binarytides.com/linux-command-shutdown-reboot-restart-system/)>), I can check if sysrq is enabled on the system by running 
```
$ cat /proc/sys/kernel/sysrq
```. I did that, and it returned 176 (nonzero), so I take it that means sysrq is enabled.

Does anyone have any idea why "REISUB" doesn't work on this computer? I have also tried it when the computer is running normally, and it still doesn't work. Also, does anyone know any other method of doing a graceful reboot when the computer hangs?

---

### Post by The Cog on 2021-11-29
According to the article you link, any value greater than 1 is a bit-mask of which functions are enabled. The article doesn't say what the different bits enable. Try writing a "1" to /proc/sys/kernel/sysrq first, to enable all functions. This should help: [https://linuxconfig.org/how-to-enable-all-sysrq-functions-on-linux](https://linuxconfig.org/how-to-enable-all-sysrq-functions-on-linux)

---

### Post by KBar on 2021-11-29
As The Cog said, you need to set it to 1. Open */etc/sysctl.d/10-magic-sysrq.conf *(with **sudoedit**) and change this value from 176 to 1:
```
kernel.sysrq = 1
```

---

### Post by scribner on 2021-11-29
[FONT=arial]Thanks for the replies. But 176 was the value returned in the example I linked to in my OP. When I used "REISUB" on my Lenovo, I did not have to change any of the configurations for it to work. Are you sure "REISUB" doesn't work when the value is 176?

> **The Cog said:**
> According to the article you link, any value  greater than 1 is a bit-mask of which functions are enabled. The article  doesn't say what the different bits enable. Try writing a "1" to  /proc/sys/kernel/sysrq first, to enable all functions. This should help:  [https://linuxconfig.org/how-to-enable-all-sysrq-functions-on-linux](https://linuxconfig.org/how-to-enable-all-sysrq-functions-on-linux)
Except, according to that link you provided, I would want to write "1" to */etc/sysctl.d/99-sysctl.conf*, not */proc/sys/kernel/sysrq*, right? It sounds like this way the configuration will survive a reboot.

So how do I make this change? According to the link you provided, I should run: ```
# echo "kernel.sysrq = 1" >> /etc/sysctl.d/99-sysctl.conf
```. Does this look right? What if my command prompt is $, not #? Aren't I supposed to type "sudo" or something?

> **kbar said:**
> As The Cog said, you need to set it to 1. Open */etc/sysctl.d/10-magic-sysrq.conf *(with **sudoedit**) and change this value from 176 to 1:
```
kernel.sysrq = 1
```
It looks like you are editing a different file than the one mentioned above. Do you think I should instead edit the one above? Regarding sudoedit, according to this blog post <[http://www.wingtiplabs.com/blog/posts/2013/03/13/sudoedit/](http://www.wingtiplabs.com/blog/posts/2013/03/13/sudoedit/)>: "If you&#8217;re not using a least privilege model for your users, or if you don&#8217;t customize your editor, sudoedit is probably not right for you. But if you&#8217;re like me, this is gonna make your day." I'm not sure if I'm using a "least privilege model for [my] users," as I am the only user, and I didn't customize my editor. Therefore, do you think, if following these instructions, it would be better for me to run: ```
sudo vi /etc/sysctl.d/10-magic-sysrq.conf
```?



[/FONT]

---

### Post by oldfred on 2021-11-29
They changed the default. 
I believe only R & B work with default.

[https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/](https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/)
Here is a method to enable the process by editing a file:-
sudo nano /etc/sysctl.d/10-magic-sysrq.conf
Then change the number in line 26 from 176 to 244 i.e. kernel.sysrq = 244

---

### Post by The Cog on 2021-11-29
Interesting. My installer script writes kernel.sysrq=1 to /etc/sysctl.conf, not /etc/sysctl.d/10-magic-sysrq.conf (which still contains kernel.sysrq = 176). /proc/sys/kernel/sysrq shows 1, so I guess sysctl.conf has priority.

---

### Post by KBar on 2021-11-30
> **scribner said:**
> [FONT=arial]It looks like you are editing a different file than the one mentioned above. Do you think I should instead edit the one above? Regarding sudoedit, according to this blog post <[http://www.wingtiplabs.com/blog/posts/2013/03/13/sudoedit/](http://www.wingtiplabs.com/blog/posts/2013/03/13/sudoedit/)>: "If you’re not using a least privilege model for your users, or if you don’t customize your editor, sudoedit is probably not right for you. But if you’re like me, this is gonna make your day." I'm not sure if I'm using a "least privilege model for [my] users," as I am the only user, and I didn't customize my editor. Therefore, do you think, if following these instructions, it would be better for me to run: ```
sudo vi /etc/sysctl.d/10-magic-sysrq.conf
```?[/FONT]

[FONT=arial]You're just changing one line, you don't have to customize your editor, which is by default *nano* for sudoers. You can do whatever you want provided that you know about consequences, but it's a good practice to always use **sudoedit** (or **sudo -e**). It's also a good practice to read manuals installed on your system or at least refer to official documentation online, instead of resorting to some questionable guides and how-tos.

**sudoedit**(8)
[/FONT]
> **The Cog said:**
> Interesting. My installer script writes kernel.sysrq=1 to /etc/sysctl.conf, not /etc/sysctl.d/10-magic-sysrq.conf (which still contains kernel.sysrq = 176). /proc/sys/kernel/sysrq shows 1, so I guess sysctl.conf has priority.

The *procps* utility installs binaries like **ps** and **kill**, the **sysctl** tool, and configuration files in */etc/sysctl.d*. Here's the order of precedence of configuration files that **sysctl** reads:
 
[LIST=|INDENT=1]
[*]/run/sysctl.d/*.conf
[*]/etc/sysctl.d/*.conf
[*]/usr/local/lib/sysctl.d/*.conf
[*]/usr/lib/sysctl.d/*.conf
[*]/lib/sysctl.d/*.conf
[*]/etc/sysctl.conf
[/LIST]

You probably set the **--load**=*/etc/sysctl.conf* option to **sysctl**, or left it empty, which will also load */etc/sysctl.conf*.

**sysctl**(8), **sysctl.conf**(5), **sysctl.d**(5)

---

### Post by The Cog on 2021-11-30
> The procps utility installs binaries like ps and kill, the sysctl tool, and configuration files in /etc/sysctl.d. Here's the order of precedence of configuration files that sysctl reads:

/run/sysctl.d/*.conf
/etc/sysctl.d/*.conf
/usr/local/lib/sysctl.d/*.conf
/usr/lib/sysctl.d/*.conf
/lib/sysctl.d/*.conf
/etc/sysctl.conf


You probably set the --load=/etc/sysctl.conf option to sysctl, or left it empty, which will also load /etc/sysctl.conf.

sysctl(8), sysctl.conf(5), sysctl.d(5)
Good references, thanks. My "installer" script is a playbook that I run post-install, a collection of tweaks I have accumulated over time. That one line in /etc/sysctl.conf is the only change I make in that area, found it with an internet search after Ubuntu changes its settings.

---

### Post by Impavidus on 2021-11-30
You can edit /etc/sysctl.d/10-magic-sysrq.conf or /etc/sysctl.conf or add an extra file to /etc/sysctl.d/. It all works.

My /etc/sysctl.d/10-magic-sysrq.conf tells how it works:```
# Here is the list of possible values:
#   0 - disable sysrq completely
#   1 - enable all functions of sysrq
#  >1 - enable certain functions by adding up the following values:
#          2 - enable control of console logging level
#          4 - enable control of keyboard (SAK, unraw)
#          8 - enable debugging dumps of processes etc.
#         16 - enable sync command
#         32 - enable remount read-only
#         64 - enable signalling of processes (term, kill, oom-kill)
#        128 - allow reboot/poweroff
#        256 - allow nicing of all RT tasks
#

```So, the default of 176 = 128+32+16 allows rebooting.

If set to 176 and you still can't reboot, it may be that you have to hold fn too or your SysRq key is somewhere else. It isn't always the same as the PrintScreen key. On my HP laptop, it's the delete key, so I have to hit fn+alt+delete+{REISUB}.

---

### Post by scribner on 2021-11-30
> **Impavidus said:**
> If set to 176 and you still can't reboot, it may be that you have to hold fn too or your SysRq key is somewhere else. It isn't always the same as the PrintScreen key. On my HP laptop, it's the delete key, so I have to hit fn+alt+delete+{REISUB}.

This.

I tried a few methods online, but none worked. Then I found [a method posted at Ask Ubuntu]("https://askubuntu.com/questions/1192496/how-does-altsysrq-work-on-a-dellxps13") that says to press Fn-R-Alt, then release Fn while holding the others to trigger a command key. This worked, but I'm not sure I'm doing it right. I pressed Fn-R-Alt, released Fn while holding the other two keys, then pressed E, I, S, U, and B. So R was pressed down the entire time and I counted that as the R in "REISUB." Does this sound right? Also, I didn't wait a full second between pressing each of the letters in EISUB -- could this have done any damage?

---

### Post by Impavidus on 2021-12-01
That sounds weird, as none of those keys is the SysRq key. But if it works ...

Another issue that may happen with this SysRq use is with non-qwerty keyboards. If you use a non-qwerty keyboard, use the keys where REISUB would have been if it were a qwerty-keyboard.

The short delay between the keys is to give the software time to respond. If you're too fast, you may get damaged files. The functions of the keys are:
R - Switch the keyboard from raw mode to XLATE mode. I'm not sure what that means exactly.
E - Send the terminate signal to all processes except init. This is a kind request for those processes to terminate, giving them opportunity to save files. They may need some time for this.
I - Send the kill signal to all processes except init. This terminates all remaining processes (except init) immediately.
S - Sync, flushes all file changes to permanent storage. This may take some time.
U - Remount filesystems in read-only mode. This blocks further writes to the filesystem.
B - Reboot.

---

### Post by KBar on 2021-12-01
> **Impavidus said:**
> R - Switch the keyboard from raw mode to XLATE mode. I'm not sure what that means exactly.

*XLATE* stands for translate and is an ASCII mode. 

**kbd_mode**(1)

---

