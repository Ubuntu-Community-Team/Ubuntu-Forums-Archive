---
title: "Command to show screenlets"
date: 2008-05-24
forum: General Help
---

### Post by m3alnemer on 2008-05-24
Hey! :)

I Needed to make an icon to show my screen let,in other words i want to make an icon like the one on leopard to set it on my AWN(Avant Window Navigator)

[IMG]http://upload.wikimedia.org/wikipedia/en/e/ed/Dashboard_Widget_icon.png[/IMG]

So **I just need the command to create icon to set back on sofa and enjoy showing screenlet** using my new wireless mouse. :)

Is there a way to figure out commands ?!
EX. turn on computer, lunch screenlets

Thanks in advance

---

### Post by atomkind on 2008-05-25
Not sure this is what you're asking for... but here's a way to figure out a program's command assuming you can access it through your main menu.

1) Right click on your main menu (the one on panel)
2)Select Edit Menus
3)On the left select the submenu where your application is (for example: Accessories)
4)On the right you will see a list "Items": find and select the application you want and right-click on it
5)Select 'Properties'

You should see a new dialog come up called "Launcher Properties" there is a command line box with the command for the app you need.

---

### Post by m3alnemer on 2008-05-25
> **atomkind said:**
> Not sure this is what you're asking for... but here's a way to figure out a program's command assuming you can access it through your main menu.

1) Right click on your main menu (the one on panel)
2)Select Edit Menus
3)On the left select the submenu where your application is (for example: Accessories)
4)On the right you will see a list "Items": find and select the application you want and right-click on it
5)Select 'Properties'

You should see a new dialog come up called "Launcher Properties" there is a command line box with the command for the app you need.


It is good to know that, but i couldn't do it to show screenlets.
I assigned the key F9 in Compiz to show the widget layer, but i wanted to make an icon instead of pressing F9.

Thanks anyway :)

---

### Post by kawaji on 2008-05-26
This is a command to toggle widget layer.
Compiz-fusion Dbus plugin needs to be enabled.
```
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/widget/allscreens/toggle_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'`
```
Replace toggle_key with toggle if you are using Compiz ver.0.5.x or 0.6.x on Gutsy.

Here is a python script written by **crdlb** to make it easy to run dbus commands like the above.
[http://forum.compiz-fusion.org/showthread.php?t=7359]("http://forum.compiz-fusion.org/showthread.php?t=7359")
Save the script as compiz-dbus-send.py in /usr/local/bin and run
```
sudo chmod +x /usr/local/bin/compiz-dbus-send.py
```

Now, You can make a AWN launcher icon to toggle widget layer.
Entry a command : **compiz-dbus-send.py widget toggle_key**

Or you can use another dock applications which have a function to launch keyboard shortcuts.(e.g. Cairo-Dock ver.1.5.6) Then, No scripts are required and Dbus plugin doesnt need to be enabled.

---

