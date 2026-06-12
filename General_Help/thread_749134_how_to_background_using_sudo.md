---
title: "how to background using sudo?"
date: 2008-04-08
forum: General Help
---

### Post by roots on 2008-04-08
hi there,

is there any trick to use the combination of sudo and "&" to send the command/app... to the background, *if sudo has not been used before or the time interval to remember the password has passed*?

for example, if i do - after system startup

```

roots@machineone:~$ sudo fancontrol &
[6] 6168
roots@machineone:~$ 

```

*nothing* happens, but upon the next "return" or ctrl sequence i do get 

```

roots@machineone:~$ 

[6]+  Stopped                 sudo fancontrol

```

the only way to sudo-start the desired app/command (fancontrol or any other stuff) and send it to background is to first do ```
sudo command
```, then stop the running process using ctrl-c and then do ```
sudo command &
```.

is there any way around this?!



cheers,
.roots

---

### Post by matts@yoyo.org on 2008-04-08
Yes, this is basic job control.

Run ```
sudo fancontrol
``` as normal.

Then press Ctrl-Z - this will suspend the process.

Then type ```
bg
``` to tell the shell to run your program in the background.

See [http://www.faqs.org/docs/bashman/bashref_78.html](http://www.faqs.org/docs/bashman/bashref_78.html) for more information.


HTH,
Matt.

---

### Post by roots on 2008-04-08
hmmmm alright... but in the end this leaves you with exactly the same number of keystrokes - ctrl-z instead of ctrl-c, and then "bg" instead of history-up and adding a "&", followed by a final return.

no other way to do that?

thanks anyway!


.roots

---

### Post by Gen2ly on 2008-04-08
I wonder if fancontrol is a bash script.  Sudo doesn't work really with echo'd pipes, cd and such.  I'm not sure if it's a security risk but you might be able to put fancontrol in visudo.

---

### Post by roots on 2008-04-08
> **Dirk.R.Gently said:**
> ....you might be able to put fancontrol in visudo.

um, sudoers...this is unknown territory for me --- would you briefly let me know how to do that?!


thx in advance,
cheers
.roots

---

### Post by Gen2ly on 2008-04-08
It may be different in Ubuntu but as I know Ubuntu does sudo permission a bit differently.  In Gentoo I'm part of the users group and I define the group and permissions as such.  I use put my computer to sleep without using sudo.

```
%users  ALL=/usr/libexec/hal-system-power-pmu
```

---

