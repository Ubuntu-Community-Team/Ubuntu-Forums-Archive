---
title: "dpkg-reconfigure Syntax Question . . ."
date: 2013-08-20
forum: General Help
---

### Post by BuntuSeriously on 2013-08-20
Good day.

Had a quick question about what seems to be an undocumented option for dpkg-reconfigure.  Here's the line in question:

```
sudo dpkg-reconfigure -plow unattended-upgrades
```

Now, having read the [manpage]("http://manpages.ubuntu.com/manpages/lucid/man8/dpkg-reconfigure.8.html") about dpkg-reconfigure, there doesn't seem to be an option called "plow" which would apply to this commandline.  The context for this cited operation can be found [here]("https://help.ubuntu.com/community/AutomaticSecurityUpdates"); just scroll down the page to the 'Using the "unattended-upgrades" package' section.

Is the above usage of "-plow" currently valid syntax for dpkg-reconfigure, or an artifact from an earlier version of the tool in question?  If valid, where could I look to find the official source for such things in the future?


Thanks again --

---

### Post by steeldriver on 2013-08-20
The **option** is *-p*, the **value** is *low*  i.e. present the user with even low-priority questions

```

       -pvalue, --priority=value
           Specify the minimum priority of question that will be displayed.
           dpkg-reconfigure normally shows low priority questions no matter
           what your default priority is. See debconf(7) for a list.

```

Hope this helps

---

### Post by VMC on 2013-08-20
> -pvalue, --priority=value           Specify the minimum priority of question that will be displayed.  dpkg-reconfigure normally shows low priority questions no matter what your default priority is. See debconf(7) for a list.

The -plow is "-p low" as above states

---

### Post by BuntuSeriously on 2013-08-21
Thanks folks.

Kinda funny when you think aout the syntax implications ("plow" sounds like a valid command to use on a Windows box before peacefully installing Linux :twisted: )

Have a great day ;)

---

