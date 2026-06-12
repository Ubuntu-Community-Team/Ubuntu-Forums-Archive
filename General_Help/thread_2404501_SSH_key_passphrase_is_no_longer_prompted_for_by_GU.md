---
title: "SSH key passphrase is no longer prompted for by GUI window the first time it's needed"
date: 2018-10-24
forum: General Help
---

### Post by colin-conway on 2018-10-24
Hi,

I'm using *Xubuntu 18.04 Desktop*.

Until recently the first time I did** anything** that required using my *id_rsa* key, a window would open prompting for the "passphrase" to unlock the key.

Now, when I *ssh* it prompts in the terminal for the passphrase every time, and if I try to using *Remmina* to make a VNC connection that tunnels through SSH, it fails with an error.


**NOTE**: I vaguely recall unchecking some checkboxes in the *Session and Startup*, *Application Autostart* tab a while ago (maybe around the time this started), but I have tried enabling what I think would be the ones that might affect this with no luck. That may be completely unrelated, but thought I should mention it.


**So far I've worked out:**

If I run *ssh-add* in the terminal and enter the passphrase then all the SSH connections work perfectly, ...until I reboot.

If I run [FONT=courier new]env | grep SSH[/FONT] I get this:
```

SSH_AUTH_SOCK=/home/colin/.byobu/.ssh-agent
SSH_AGENT_PID=2420
```

The file [FONT=courier new]/home/colin/.byobu/.ssh-agent[/FONT] is a symlink to: [FONT=courier new]/tmp/ssh-hC8goIZugo6A/agent.2319[/FONT]

According to [FONT=courier new]ps -ejH[/FONT] *2319* is the process id of a *lightdm* shell, and *2420* is the process id of the *ssh-agent*:
```

...
2201  1704  1704 ?        00:00:00     lightdm
2319  2319  2319 ?        00:00:00       sh
2420  2420  2420 ?        00:00:00         ssh-agent
...
```

...which all looks great, but now I'm stumped and no amount of searching has turned up any useful clues.


Any help would be greatly appreciated. =)

---

### Post by TheFu on 2018-10-26
Just a guess. 

**ssh-askpass** on the system? There are different versions for each GUI, if you prefer to have a pop-up.
I don't have 18.04, so can't check my guess.

---

### Post by colin-conway on 2018-10-27
Thanks TheFu!!

*ssh-agent* was installed, but your suggestion gave me a new direction in which to investigate and I stumbled upon this post:

      [https://ask.fedoraproject.org/en/question/116777/ssh-agent-not-running-by-default-in-xfce/?answer=116783#post-id-116783](https://ask.fedoraproject.org/en/question/116777/ssh-agent-not-running-by-default-in-xfce/?answer=116783#post-id-116783)

...in which I found that *Launch GNOME Services On Startup* wasn't checked (I think I unchecked this while "fixing" my laptop not sleeping issue.)

---

