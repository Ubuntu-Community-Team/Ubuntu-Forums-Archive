---
title: "USB requiring authentication now"
date: 2015-10-17
forum: General Help
---

### Post by JKyleOKC on 2015-10-17
In just the last couple of days, my Xubuntu 14.04.3 system has begun requiring authentication to mount, unmount, or eject USB flash drives. I suspect that this is a consequence of some recent update, since I've not modified any of the configuration settings recently. While I'm able to work around the annoyance by using sudo, it's definitely unwanted behavior.

Is anyone else seeing this? And does anyone have ideas as to the cause, or a cure?

---

### Post by slickymaster on 2015-10-17
Hummm..., I'm also on 14.04.03 fully updated, on this laptop, and not getting that.

---

### Post by QDR06VV9 on 2015-10-17
> **slickymaster said:**
> Hummm..., I'm also on 14.04.03 fully updated, on this laptop, and not getting that.

+1 Not Here also.

---

### Post by JKyleOKC on 2015-10-17
Interesting -- so it has to be something that I've done here, not an artifact of some system update (which have been appearing almost daily for the past week).

The searching I've done so far indicates that it's related to "polkit" and "udisks2" but I don't see anything like that in the recent logs...

---

### Post by slickymaster on 2015-10-17
Check in your **/usr/share/polkit-1/actions/org.freedesktop.udisks2.policy** file if the permissions are correct. It's just a xml file, so if there's aforw need to edit it's pretty straightforward.

---

### Post by JKyleOKC on 2015-10-17
So I hit Google searching for "polkit udisks" and the very first hit provided the answer. I created the file  /etc/polkit-1/10-udisks2.rules with this content:```
// See the polkit(8) man page for more information
// about configuring polkit.

// Allow udisks2 to mount devices without authentication
// for users in the "wheel" group.
polkit.addRule(function(action, subject) {
    if ((action.id == "org.freedesktop.udisks2.filesystem-mount-system" ||
         action.id == "org.freedesktop.udisks2.filesystem-mount") &&
        subject.isInGroup("sudo")) {
        return polkit.Result.YES;
    }
});

```
Then I restarted the system (and discovered that restarting also now requires authentication despite being escaped in /etc/sudoers), and the annoyance has disappeared.

Must be something associated with the switch to systemd; I did note that it had an update within the past week. The funny thing is that the post I found via Google dates from 2013!

Looks as if I may have to add several more rules in /etc/polkit-1, as other annoyances spring to life...

---

### Post by slickymaster on 2015-10-17
Great you've got it solved. Don't forget to mark the thread as such.

---

### Post by JKyleOKC on 2015-10-17
> **slickymaster said:**
> Check in your **/usr/share/polkit-1/actions/org.freedesktop.udisks2.policy** file if the permissions are correct. It's just a xml file, so if there's aforw need to edit it's pretty straightforward.Where can I find the definition of "auth-admin" as used in this file? Seems to me the simplest solution would be to either add my personal id/group to that, or perhaps the "sudo" group, and kill all the annoyances with a single edit...

The man page, like so many of them, isn't much help for someone new to the specific program!

---

### Post by slickymaster on 2015-10-17
> **JKyleOKC said:**
> Where can I find the definition of "auth-admin" as used in this file? Seems to me the simplest solution would be to either add my personal id/group to that, or perhaps the "sudo" group, and kill all the annoyances with a single edit...

The man page, like so many of them, isn't much help for someone new to the specific program!

Not sure you'll find it [here]("https://wiki.archlinux.org/index.php/Polkit"), but it's the most thorough asset I found.

---

### Post by JKyleOKC on 2015-10-17
Many thanks. There's some sample code way down the page that ought to do it nicely, to make the "sudo" group "auth-admin" for all systemd processes! Haven't tested it yet but I'm confident it will work -- at least until the next update comes out!

---

