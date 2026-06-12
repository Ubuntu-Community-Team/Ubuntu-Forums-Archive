---
title: "Window Manager Problem"
date: 2008-04-02
forum: General Help
---

### Post by ububaba on 2008-04-02
Somehow I have messed up with the result that I cannot access desktop. Besides Evolution is restricted
to a quarter of the screen. 

[COLOR="Blue"]Have reinstalled xserver-xorg
In the Terminal typed xfwm4  no help[/COLOR]

When I go to preferences>windows I get this message [HTML] "Cannot start preferences application for your 
Window Manager. [/HTML]

Another message I get is [HTML]Window Manager "uknown" has not registered a configuration tool[/HTML]
Any idea how does one come out of this? Thanks.

---

### Post by dstew on 2008-04-02
> Have reinstalled xserver-xorgDo you mean that you *reconfigured* xserver-xorg?

---

### Post by ububaba on 2008-04-02
> **dstew said:**
> Do you mean that you *reconfigured* xserver-xorg?


I entered the following in the Terminal
[HTML]sudo apt-get install xserver-xorg[/HTML]

---

### Post by mali2297 on 2008-04-02
> **ububaba said:**
> 
In the Terminal typed xfwm4 no help

What did it say when you ran this?

Have you installed another window manager like Compiz or Openbox?

---

### Post by ububaba on 2008-04-02
> **mali2297 said:**
> What did it say when you ran this?

Have you installed another window manager like Compiz or Openbox?
Thanks I will try to do that. 

xfwm4 was accepted without any protest.

---

### Post by mali2297 on 2008-04-02
> **ububaba said:**
> Thanks I will try to do that. 

It wasn't a suggestion.:-) 
Rather, if you had installed another window manager, it would have explained why you couldn't use the settings tool.

Try
```

pkill xfwm4
xfwm4 &

```

---

### Post by ububaba on 2008-04-02
> **mali2297 said:**
> It wasn't a suggestion.:-) 
Rather, if you had installed another window manager, it would have explained why you couldn't use the settings tool.

Try
```

pkill xfwm4
xfwm4 &

```

This did the trick. Thanks.

---

