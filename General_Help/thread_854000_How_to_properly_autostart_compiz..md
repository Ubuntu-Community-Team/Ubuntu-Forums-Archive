---
title: "How to properly autostart compiz."
date: 2008-07-09
forum: General Help
---

### Post by Rafal07BC on 2008-07-09
Hello.

I have installed compiz-fusion. Everything is working fine but I have problem with autostarting compiz.
If I just save session with working compiz it wont auto start after reebot. It is the same with fusion-icon.

My solution was to add compiz --replace to autostart. But this has problems:
1. I think it extends loading time
2. If I have windows placed on many desktops after compiz start windows are bunched up together in single desktop.

When I autostart fusion-icon no decorator is started, plus the problem of windows bunched up in single desktop remains.

So my question is how to configure compiz startup so it loads as default window manager (without loading xfwm or any other window manager ) and so it preserves windows desktop positions.

Thanks in advance.

---

### Post by iaculallad on 2008-07-09
Try to follow-up with this [thread]("http://ubuntuforums.org/showthread.php?t=849091&highlight=compiz") we had solved some weeks ago.

---

### Post by Rafal07BC on 2008-07-09
I have seen it, I am using autostart to start compiz right now. I look for alternatives.

The problem is that this doesnt preserve windows desktop positions.

So if I have window on desktop 2 after reebot it will be placed on destkop 1. I would like it to stay where I left it.

Thanks.

---

### Post by GanShun on 2010-10-03
You're using xubuntu right? if you're using the up to date version, you can try doing this

[B]sudo gedit /etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml

[/B]change the following in the file:

```

      <property name="Client0_Command" type="array">
        <value type="string" value="xfwm4"/>
      </property>
```

to

```

      <property name="Client0_Command" type="array">
        <value type="string" value="compiz"/>
        <value type="string" value="ccp"/>
      </property>
```

---

