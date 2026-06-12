---
title: "Power save mode vs power off"
date: 2022-05-20
forum: General Help
---

### Post by Tom_Carr on 2022-05-20
What is the difference between power save mode and power off with ubuntu?  
When should I power off and when should I just do power save mode?

---

### Post by GhX6GZMB on 2022-05-20
(x)ubuntu has four power states:
- Normal operation
- Suspend: system state is kept in RAM and the rest of the system is powered down. This still needs power, but way less than when operating
- Hibernate: system state is saved to disk and the system is powered down completely. This is disabled in (x)ubuntu as standard.
- Power down.

---

### Post by Tom_Carr on 2022-05-23
When it says "Entering power save mode" is that suspend or hibernate?

---

### Post by Tom_Carr on 2022-05-23
A better question would be - how do I know if it is in suspend or hibernate?

I have a Logitech keyboard with 8 small keys above the function keys.  One of these is a power key.  when I hit it, the system goes into some kind of suspend or hibernate state.  I can then quickly bring the system back up by hitting the return key or the moving the mouse.  The system is not fully powered down.  I am curious what is happening then.  I would also like to know if there is any reason to ever fully power down the system.

This is running Jammy.

---

### Post by #&amp;thj^% on 2022-05-23
*Suspend stops operation of all applications and puts the machine into a low-power mode. Various triggers can resume the machine, among them pressing a key or quickly pressing and releasing the power button.

*Hibernate moves the contents of memory into swap, tells the bootloader to boot directly into the appropriate kernel, and shuts the machine down. You thaw the machine by powering up, which causes the kernel to reload the contents of memory from swap.

 *Thaw brings you back to grub menu.
More here: [https://wiki.archlinux.org/title/Power_management/Suspend_and_hibernate](https://wiki.archlinux.org/title/Power_management/Suspend_and_hibernate)
> A better question would be - how do I know if it is in suspend or hibernate?

A user only, would know what state they placed the system in. ;)
> When it says "Entering power save mode" is that suspend or hibernate? 
Suspend Mode, unless the user changed the values.

---

### Post by Tom_Carr on 2022-05-23
How do I put it in suspend if I don't have the keyboard with the special power key.

---

### Post by #&amp;thj^% on 2022-05-23
Suspension is quicker but doesn&#8217;t work well when running the battery out of power, while hibernating can deal with running out of power but it is slower.

****Before you use any command**** I show here best figure out if you can first 

"systemctl suspend Command &#8211; Use systemd to suspend/hibernate"
again read the link first
**suspend: This is safe to use without reading the link**. ;)
```
systemctl suspend 
```
hibernate:
```
systemctl hibernate 
```
This link will help you determine your choice: [https://www.linuxuprising.com/2021/08/how-to-enable-hibernation-on-ubuntu.html](https://www.linuxuprising.com/2021/08/how-to-enable-hibernation-on-ubuntu.html)

---

### Post by GhX6GZMB on 2022-05-23
@1fallen: good link and exactly what I had to do myself to get hibernate to work. Main difference, I never got it to work properly, though. Using a Swap partition on the other hand turned out to be  100% reliable.
On Lubuntu you can choose whether the machine should shut down, hibernate or suspend when the battery is low. Same thing for lid close. Very nice.

---

### Post by #&amp;thj^% on 2022-05-23
> **ml9104 said:**
> @1fallen: good link and exactly what I had to do myself to get hibernate to work. Main difference, I never got it to work properly, though. Using a Swap partition on the other hand turned out to be  100% reliable.
On Lubuntu you can choose whether the machine should shut down, hibernate or suspend when the battery is low. Same thing for lid close. Very nice.

Nice, thanks for adding your findings as well. ;)
I find it a bit different on another OS, this will work on my system:
```
swapon
NAME      TYPE SIZE USED PRIO
/swapfile file 512M   0B   -2

```

---

### Post by deadflowr on 2022-05-23
> What is the difference between power save mode and power off with ubuntu?
Power Saving Mode is a gnome feature. (well, any desktop can use it, just that gnome on Ubuntu ships with it)
Power save mode cuts down resources being used.
Power off shuts down the machine.
You can read more about the power-profiles-daemon that is used here: [https://gitlab.freedesktop.org/hadess/power-profiles-daemon]("https://gitlab.freedesktop.org/hadess/power-profiles-daemon")

> When should I power off and when should I just do power save mode?


Power off when there is no need to be on.
Power save when you have to be on, but have no access to external power.

Obviously suspend and hibernate are somewhere in between those.
Allowing the system to be in a semi-shutdown state, but quickly powering on when needed bring in back to the state it was left at.
(Instead of having to go through the whole boot up process from a normal power off.)

---

