---
title: "Trusty Workspace Settings Won't Stay Put"
date: 2015-08-14
forum: General Help
---

### Post by mlnease on 2015-08-14
Hello,

I keep 'Workspace Switcher' in an XFCE panel on my desktop.  The default number of workspaces is 4; when I change it to 2, it reverts to 4 with every restart.

Any ideas?

Thanks in advance.

---

### Post by pqwoerituytrueiwoq on 2015-08-14
i am unable to reproduce that, however i am using the xfce 4.12 ppa
the value is stored in [FONT=Courier New]~/.config/xfce4/xfconf/xfce-perchannel-xml/xfwm4.xml[/FONT]
search for these lines
```

    <property name="workspace_count" type="int" value="6"/>
    <property name="workspace_names" type="array">
      <value type="string" value="Workspace 1"/>
      <value type="string" value="Workspace 2"/>
      <value type="string" value="Workspace 3"/>
      <value type="string" value="Workspace 4"/>
      <value type="string" value="Workspace 5"/>
      <value type="string" value="Workspace 6"/>
    </property>

```
the number of rows is in [FONT=Courier New]~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml[/FONT]
```

    <property name="plugin-41" type="string" value="pager">
      <property name="rows" type="uint" value="2"/>
      <property name="show-names" type="bool" value="false"/>
      <property name="workspace-scrolling" type="bool" value="false"/>
      <property name="miniature-view" type="bool" value="true"/>
    </property>

```
make sure you have write permissions to those files

---

### Post by mlnease on 2015-08-14
> **pqwoerituytrueiwoq said:**
> i am unable to reproduce that, however i am using the xfce 4.12 ppa
the value is stored in [FONT=Courier New]~/.config/xfce4/xfconf/xfce-perchannel-xml/xfwm4.xml[/FONT]
search for these lines
```

    <property name="workspace_count" type="int" value="6"/>
    <property name="workspace_names" type="array">
      <value type="string" value="Workspace 1"/>
      <value type="string" value="Workspace 2"/>
      <value type="string" value="Workspace 3"/>
      <value type="string" value="Workspace 4"/>
      <value type="string" value="Workspace 5"/>
      <value type="string" value="Workspace 6"/>
    </property>

```
the number of rows is in [FONT=Courier New]~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml[/FONT]
```

    <property name="plugin-41" type="string" value="pager">
      <property name="rows" type="uint" value="2"/>
      <property name="show-names" type="bool" value="false"/>
      <property name="workspace-scrolling" type="bool" value="false"/>
      <property name="miniature-view" type="bool" value="true"/>
    </property>

```
make sure you have write permissions to those files

Thanks for this.  I have no ```
xfce-perchannel-xml/xfce4-panel.xml
``` in ```
~/.config/xfce4/xfconf
```.

---

### Post by pqwoerituytrueiwoq on 2015-08-14
[IMG]http://i.imgur.com/F4rl2Gt.png[/IMG]
Did I make a typo or are you as blind as me?

---

### Post by mlnease on 2015-08-15
Got it now, thanks for your patience.  My problem isn't with the number of rows but the number of workplaces;  this continually reverts to the default 4.  Here's what I have in xfwm4.xml: ```
<property name="workspace_count" type="int" value="2"/>
```--and I do currently have 2 workspaces.  When I log out or shut down and restart though, it will revert to 4.

---

### Post by mlnease on 2015-08-15
I seem to be particularly senile this week.  The problem occurs only if I shut down altogether and start Xubuntu fresh--it does *not* occur if I log out or suspend.  Thanks for your patience.

---

### Post by pqwoerituytrueiwoq on 2015-08-15
are you on a guest account or something?
reboot and check if the file exist when you login vis a tty

---

### Post by mlnease on 2015-08-15
> **pqwoerituytrueiwoq said:**
> are you on a guest account or something?
reboot and check if the file exist when you login vis a tty

Thanks again for your time and attention.  No, not a guest account--and  when I reboot and log in via a TTY, it boots me into the system default, Unity(I think--I don't use it),  without the option (at least apparently to me)--since Unity has no  panel, the problem doesn't exist there.  Am I missing something obvious?

---

### Post by pqwoerituytrueiwoq on 2015-08-15
when i mean tty i mean when it boots to the login screen press ctrl+alt+f2 and login there and check if the file has been altered since shutdown

---

### Post by mlnease on 2015-08-15
> **pqwoerituytrueiwoq said:**
> when i mean tty i mean when it boots to the login screen press ctrl+alt+f2 and login there and check if the file has been altered since shutdown
Of course--got it.  Will do but probably not till tomorrow--thanks again.

---

### Post by mlnease on 2015-08-16
> **pqwoerituytrueiwoq said:**
> when i mean tty i mean when it boots to the login screen press ctrl+alt+f2 and login there and check if the file has been altered since shutdownWell, it's interesting.  If I shut down, then start fresh via TTY (into system default Unity), the value is 
```
<property name="workspace_count" type="int" value="2"/>
``` (of course there's no panel in Unity).  But then if I restart normally (into Xubuntu desktop), the value changes to "4".  If I then edit the value in 
```
xfce4-panel.xml
``` to read "2" and save it, the xml file does read "2" but the panel still shows 4 workspaces.

Thanks again for your time and attention.

---

### Post by pqwoerituytrueiwoq on 2015-08-16
i wonder if unity is changing something, try changing it in [ccsm](apt:compizconfig-settings-manager)
i don't have unity installed

---

### Post by mlnease on 2015-08-16
> **pqwoerituytrueiwoq said:**
> i wonder if unity is changing something, try changing it in [ccsm]("apt:compizconfig-settings-manager")
i don't have unity installed
As it turns out, the 'System Default' I took for Unity is actually GNOME 3, which is horribly Unity-like.  I wouldn't touch either of them with a dung fork.

Thanks for the CCSM suggestion.  I've tried it and can't seem to find anything pertinent (filtering by 'panel', 'xfce', 'workspace', etc.) there.

But I really think I've taken up too much of your time already. This is a minor annoyance and doesn't seem to be bugging enough users to make it a significant problem.

Thanks again.

p.s.  It isn't GNOME that seems to be changing this value; it remains as set until I start Xubuntu Desktop.

---

### Post by pqwoerituytrueiwoq on 2015-08-16
i think it is under desktop settings
i wonder if unity is changing something, as in xfce is looking at a unity config and using that that unity keeps changing back

---

### Post by mlnease on 2015-08-16
> **pqwoerituytrueiwoq said:**
> i think it is under desktop settings
i wonder if unity is changing something, as in xfce is looking at a unity config and using that that unity keeps changing backI get it now, thanks.  There's a 'Viewport Switcher' setting under Desktop in CCSM, but nothing there about number of workspaces.

---

### Post by pqwoerituytrueiwoq on 2015-08-16
il just boot my flash drive on my laptop and find the thing
general options -> desktop size
set rows by columns
[http://imgur.com/a/i3rRm](http://imgur.com/a/i3rRm)

---

### Post by mlnease on 2015-08-16
> **pqwoerituytrueiwoq said:**
> il just boot my flash drive on my laptop and find the thing
general options -> desktop size
set rows by columns
[http://imgur.com/a/i3rRm](http://imgur.com/a/i3rRm)Thanks for taking the trouble, I appreciate it.  I changed Horizontal Virtual Size from the default '1' to '2' and left the Vertical Virtual Size at the default '1'.  I then shut down completely and restarted

CCSM still reads '2' and '1'; xfce4-panel.xml has reverted to '4' as usual and my bottom panel has reverted again to four workspaces.

---

### Post by pqwoerituytrueiwoq on 2015-08-16
have you tried the xfce 4.12 ppa? maybe that will fix it
```
sudo apt-add-repository ppa:xubuntu-dev/xfce-4.12 -y && sudo apt-get update && sudo apt-get dist-upgrade -y
```
does it happen without a reboot if you restart the X server
switch to a tty and run ```
sudo service lightdm restart
```
* save all work before running that
*if you don't do it in a tty it will not start back up

---

### Post by mlnease on 2015-08-16
[QUOTE=pqwoerituytrueiwoq;13339609]have you tried the xfce 4.12 ppa? maybe that will fix it
```
sudo apt-add-repository ppa:xubuntu-dev/xfce-4.12 -y && sudo apt-get update && sudo apt-get dist-upgrade -y
```I have now--and Hey Presto, it worked.  I edited  xfce4-panel.xml, rebooted and my bottom panel showed two workspaces.  Shut down completely, restarted with the same result.  So case closed!  And thanks a million for all your help.

---

### Post by mlnease on 2015-08-22
It's back--the Workspace Switcher icon in my xfce panel has again reverted to the default '4'.  So apparently switching to the xfce 4.12 ppa didn't do the trick.

Thanks anyway!

---

