---
title: "Debugging output from root process"
date: 2013-03-13
forum: General Help
---

### Post by fromberg100 on 2013-03-13
Hi,

I have a simple question.  I have a process that starts at startup as root.  The command is basically the following:

samba -i -M single -d3


When that process starts, it outputs a lot of debugging information.

I would like to see that output when I log in as another user, let say administrator.  Is this possible? to capture debugging output from a process running on the background?

Thanks in advance and regards,
Fabian

---

### Post by Slim Odds on 2013-03-13
sudo is what you need to use.

---

### Post by fromberg100 on 2013-03-14
Hi,

thanks for your reply.

If my process runs on the background, how can I capture the output on terminal if I log in as root?

Thanks and regards,
Fabian

---

### Post by Slim Odds on 2013-03-14
> **fromberg100 said:**
> Hi,

thanks for your reply.

If my process runs on the background, how can I capture the output on terminal if I log in as root?

Thanks and regards,
Fabian

Where is it sending its output?

If it's a file, you can use "tail -f" to follow the output.
```
sudo tail -f filename
```

---

### Post by fromberg100 on 2013-03-15
Hi, the process is run from the terminal and the debugging info is output in the same terminal.  I want to capture that output on another terminal.

Thanks in advance and regards,
Fabian

---

### Post by schragge on 2013-03-15
Try something like this.
In the root terminal running samba ```
samba -i -M single | sudo -u [COLOR=blue]yourusername[/COLOR] tee /tmp/samba.log
```
In the second terminal ```
tail -f /tmp/samba.log
```
TBH, I don't see why you would start the first terminal as root. If both terminals are running with regular user's privileges then the first command should be changed to ```
sudo samba -i -M single >/tmp/samba.log
```

---

### Post by fromberg100 on 2013-03-16
HI schragge,

thank you very much for your help.

That was exactly what I wanted.

Thanks again and regards,
Fabian

---

