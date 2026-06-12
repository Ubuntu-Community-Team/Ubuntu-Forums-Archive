---
title: "Annoying Error"
date: 2007-05-13
forum: General Help
---

### Post by z0phi3l on 2007-05-13
Been using UBUNTU since just after Feisty came out. I have just about everything figured out but I get this annoying error every time I install or update an app be it through the command line or through Synaptic:


```
E: emifreq-applet: subprocess post-installation script returned error exit status 2
```

What do I need to do to get rid of the error?

---

### Post by phidia on 2007-05-13
See this thread  [http://ubuntuforums.org/showthread.php?page=2&t=296174](http://ubuntuforums.org/showthread.php?page=2&t=296174)

---

### Post by jimbob on 2007-05-13
It looks like emifreq-applet is an installable program used to indicate CPU frequency scaling.

Check Synaptic to see if you somehow have it installed.

Also check System->Preferences->Sessions to see if it is being started up for some reason.

Also enter ps aux | grep emi on a terminal to see if it is running.

You could also try entering acpi=off and noapic on the kernel boot line in grub to see if that fixes it.

That's all I can think of right now.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

