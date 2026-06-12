---
title: "install java"
date: 2007-01-19
forum: General Help
---

### Post by Coop on 2007-01-19
Hello

I copied the Java debs from my previous Ubuntu installation into my current installation's /var/cache/apt/archives/ directory.

But when I go to install Java from Synaptic,Synaptic tries to download Java debs all over again.

How do I force Synaptic to install Java from the debs in the /var/cache/apt/archives/ directory instead of downloading the debs all over again?

Please answer me.
Ahmed

---

### Post by Ragazzo on 2007-01-19
Can you use ```
dpkg -i java.deb
```

---

### Post by Coop on 2007-01-19
Hello
There's more than one Java deb,there are three java debs:java bin,java jre and java plugin.
Each of these debs depend on each other,so I can't install them with the dpkg -i command.
Is there some way I can force Synaptic to install java from the debs already in the /var/cache/apt/archives directory,instead of downloading the debs again?
Please answer me.
Ahmed

---

### Post by yopnono on 2007-01-19
> **Coop said:**
> Hello
There's more than one Java deb,there are three java debs:java bin,java jre and java plugin.
Each of these debs depend on each other,so I can't install them with the dpkg -i command.
Is there some way I can force Synaptic to install java from the debs already in the /var/cache/apt/archives directory,instead of downloading the debs again?
Please answer me.
Ahmed

Is it the same version, then it should be used by synaptic. You have done a refresh/update

---

