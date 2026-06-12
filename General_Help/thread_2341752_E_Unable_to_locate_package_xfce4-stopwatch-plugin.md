---
title: "E: Unable to locate package xfce4-stopwatch-plugin"
date: 2016-10-31
forum: General Help
---

### Post by Pablo_San_Martn on 2016-10-31
I get that error in xenial. Any idea as to how this plugin can be installed? I am unable to locate the ppa.

For reference: [http://goodies.xfce.org/projects/panel-plugins/xfce4-stopwatch-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-stopwatch-plugin)

---

### Post by CantankRus on 2016-10-31
Hello, is it me you're looking for.... **xfce4-timer-plugin**.
Regards Lionel R.

---

### Post by slickymaster on 2016-10-31
The xfce4-stopwatch-plugin is part of the xfce4-goodies meta-package. To install it just open a terminal window and run```
sudo apt-get update && sudo apt-get install xfce4-goodies
```

---

### Post by Pablo_San_Martn on 2016-11-02
> **CantankRus said:**
> Hello, is it me you're looking for.... **xfce4-timer-plugin**.
Regards Lionel R.

Thanks Lionel. I already have that one - they're different packages and do different things: one measures time elapsed, the other runs backwards from a given time to zero.

---

### Post by Pablo_San_Martn on 2016-11-02
> **slickymaster said:**
> The xfce4-stopwatch-plugin is part of the xfce4-goodies meta-package. To install it just open a terminal window and run```
sudo apt-get update && sudo apt-get install xfce4-goodies
```

Thanks slickymaster. I've already installed the goodies - it contains the timer but not the stopwatch.

For reference: [https://launchpad.net/ubuntu/xenial/+package/xfce4-goodies](https://launchpad.net/ubuntu/xenial/+package/xfce4-goodies)

---

### Post by CantankRus on 2016-11-02
I think it hasn't worked for some time.
[https://bugzilla.xfce.org/show_bug.cgi?id=6789](https://bugzilla.xfce.org/show_bug.cgi?id=6789)

---

### Post by Pablo_San_Martn on 2016-11-02
> **CantankRus said:**
> I think it hasn't worked for some time.
[https://bugzilla.xfce.org/show_bug.cgi?id=6789](https://bugzilla.xfce.org/show_bug.cgi?id=6789)

Oh, you're right, good to know that. Any good stopwatch for Xfce you know of?

---

### Post by CantankRus on 2016-11-02
No sorry, the only thing I'm aware of is the application called stopwatch.

---

### Post by Pablo_San_Martn on 2016-11-02
> **CantankRus said:**
> No sorry, the only thing I'm aware of is the application called stopwatch.

Thanks, I'll try that one, add transparency and keep the window always on top, let's see how it works.

---

