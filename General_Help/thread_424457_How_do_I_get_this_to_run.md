---
title: "How do I get this to run?"
date: 2007-04-26
forum: General Help
---

### Post by ardchoille42 on 2007-04-26
I am using Kubuntu Feisty. I installed gkrellm with "sudo apt-get install gkrellm", but when I launch it from a term, all I get is this:

```

[~ @ 15:26:36] gkrellm
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

That stuff is output for almost every app I run from konsole. But, gkrellm never shows up on the desktop and there is no other error output either. How do I get gkrellm running?

---

### Post by vigleik on 2007-04-26
The only solution I know of is to edit your /etc/X11/xorg.conf file. Remove every instance of things having to do with wacom. This happens with every computer I install ubuntu on too. It's very annoying. This won't help you run gkrellm, but it'll get rid of that particular error message.

---

### Post by ardchoille42 on 2007-04-26
> **vigleik said:**
> The only solution I know of is to edit your /etc/X11/xorg.conf file. Remove every instance of things having to do with wacom. This happens with every computer I install ubuntu on too. It's very annoying. This won't help you run gkrellm, but it'll get rid of that particular error message.

Ah, thank you very much. That does help for the errors.

Anyone have any idea to get gkrellm to show up on the desktop after launching it?

---

### Post by ardchoille42 on 2007-04-26
Now, this is very interesting. I can launch gkrellm and it runs, but doesn't popup on the desktop like it should. Then, exactly three minutes later, it pops up on the dekstop.

Anyone know how to fix this?

---

### Post by ardchoille42 on 2007-04-28
* bump *

---

### Post by ardchoille42 on 2007-04-28
Ok, new information about this problem. I got some info from /var/log/messages that hinted toward the firewall being misconfigured. So, I uninstalled the firewall and uninstalled KMyFirewall. Then I rebooted, ran gkrellm and it immediately popped up on the desktop.

Seems the whole problem was caused by a misconfigured firewall.

---

