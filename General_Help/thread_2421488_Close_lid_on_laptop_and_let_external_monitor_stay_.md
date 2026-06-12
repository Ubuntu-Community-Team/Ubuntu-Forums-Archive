---
title: "Close lid on laptop and let external monitor stay on. Ubuntu 19.04"
date: 2019-06-22
forum: General Help
---

### Post by irv on 2019-06-22
I upgraded to Ubuntu 19.04 with Gnome desktop. When I use my laptop at home I just plug in an external monitor and shut off the screen on the laptop in the monitor setting. The problem is when I close the lid on the laptop the external monitor shuts off. I can find a setting anywhere that allows me to let the monitor stay on? Am I overlooking it somewhere?

EDIT: I forgot to say, I am using the external monitor plugged into the HDMI port if that makes any difference?

---

### Post by Autodave on 2019-06-22
I don't use Gnome, but there should be an icon in Settings for Power Manager.  In there you should find what you need.

---

### Post by irv on 2019-06-22
[ATTACH=CONFIG]283471[/ATTACH] I don't see one.

---

### Post by #&amp;thj^% on 2019-06-22
Be very careful if you change this setting. Some laptops can overheat if they are left running with the lid closed, especially if they are in a confined place like a backpack.
You need to have Tweaks installed 
[list]
    [*]Open the Activities overview and start typing Tweaks.

    [*]Click Tweaks to open the application.

    [*]Click the Power tab.

    [*]Switch Suspend when laptop lid is closed to OFF.

    [*]Close the Tweaks window.[/list]
**EDIT:** I'm also including some more advanced tips for this, so use on your own.
```
sudo nano /etc/UPower/UPower.conf
```
and append or add this:
```
# <snip> ...

**ignoreLid=true**

# <snip> ...

```
It in real time looks like this:
```
# Do we ignore the lid state
#
# Some laptops are broken. The lid state is either inverted, or stuck
# on or off. We can't do much to fix these problems, but this is a way
# for users to make the laptop panel vanish, a state that might be used
# by a couple of user-space daemons. On Linux systems, see also
# logind.conf(5).
#
# default=false
**[COLOR="#FF0000"]IgnoreLid=true[/COLOR]**

```
Now if you don't want to reboot to see the change made, restart upower on systemd with:
```
sudo service upower restart
##OR
systemctl restart upower.service
```
to have the new config take effect. Otherwise a reboot will be needed.

---

### Post by irv on 2019-06-22
I had Tweaks already installed. The switch Suspend when the Laptop lid is closed was on. So when I turn it off and closed the lid my mouse started jumping around and windows started opening and closing. 
I had to reboot and I tried again and the same thing happened. I tried this a few times and the same thing happened every time. There must be a bug. or it might be my hardware. I guess I will leave it part way open. I wanted it close to keep the dust off of it. You're right about the heat thing. I do render videos and the laptop does get hot.

---

### Post by #&amp;thj^% on 2019-06-22
One other thing, do you have both displays set to mirror?
If so disable that.
Also see my edit in post#4

---

### Post by crip720 on 2019-06-22
Just wondering if you are also using an external keyboard, I am using an external keyboard and find I just have to hit a key to have external monitor come back on, after closing lid.

---

### Post by irv on 2019-06-22
1fallen, I tried adding Code:
# <snip> ...

ignoreLid=true

# <snip> ...
but didn't help.
I am using a wireless mouse/keyboard and this might be some of the problems as well. 
This is not a life and death thing, I can operate with the lid partway open. Like what was said before, it will help with the heat.

---

