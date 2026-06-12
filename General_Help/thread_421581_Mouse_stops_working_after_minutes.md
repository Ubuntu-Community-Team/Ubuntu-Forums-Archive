---
title: "Mouse stops working after minutes"
date: 2007-04-24
forum: General Help
---

### Post by timelord726 on 2007-04-24
I have a somewhat strange problem on my desktop Ubuntu install.  Consistently, with every install I've done on this computer (of both 6.10 and 7.04), my mouse randomly stops working after a few minutes of using the computer.  There's no way to get it to come back, either -- I've tried unplugging it and plugging it back in, restarting the graphical environment, etc.  The only thing that works is a full restart, but then it will just stop again after another few minutes.  I'm not sure what could be causing this.  I have a Logitech S510 wireless keyboard and mouse combination, and the keyboard and mouse both use the same receiver and USB connection.  However the keyboard continues working after the mouse has stopped.

Does anyone have any ideas about this?  Thank you very much!  :)

---

### Post by beeman69 on 2007-04-25
I have a similar issue with the mouse AND keyboard stopping to work after I click on one thing.  I have done some research but have not found any suitable solutions,  One suggestion was to check the BIOS settings and de-activate and then re-activate USB, but I dont have that option.  Another idea was that this is an issue with feisty, and edgy didn't have any probs, so I re-installed from the Live CD again, with no upgrade, same thing.  Another suggestion was to check the Braille settings, but I cant do that since the mouse will die after the first click, and I can't SSH into it yet.  The weird thing is, when I don't touch anything, just mouse over menu items, I get the tool-tips, and that will work for hours, but when I click on anything, it stops working immediatly, and requires a full restart.  I don't know my hardware setup, it is an old box I got from a friend that I decided to go from RH8 to ubuntu, but the mouse and keyboard are just Dell serial devices, nothing special.  One thing I should mention though, is that during the installation, everything is fine, but after the reboot, no luck.  Any ideas would be great...

---

### Post by timelord726 on 2007-06-29
Well, after simply giving up on Ubuntu for a while on my desktop, I decided to try it again a few days ago.  I was impressed at how well the whole thing ran (haven't had much of a chance to play with 7.04 since it doesn't work properly) but the mouse problem is still a major issue for me.  I can't use Ubuntu on my computer at all because of it.  :(

Does anyone have any possible suggestions?  Please?

---

### Post by Crafty Kisses on 2007-06-29
> **timelord726 said:**
> I have a somewhat strange problem on my desktop Ubuntu install.  Consistently, with every install I've done on this computer (of both 6.10 and 7.04), my mouse randomly stops working after a few minutes of using the computer.  There's no way to get it to come back, either -- I've tried unplugging it and plugging it back in, restarting the graphical environment, etc.  The only thing that works is a full restart, but then it will just stop again after another few minutes.  I'm not sure what could be causing this.  I have a Logitech S510 wireless keyboard and mouse combination, and the keyboard and mouse both use the same receiver and USB connection.  However the keyboard continues working after the mouse has stopped.

Does anyone have any ideas about this?  Thank you very much!  :)

It could be a possible driver issue.

---

### Post by timelord726 on 2007-06-29
Are there any other drivers that might work better that I could try replacing it with?  If so, how would I go about doing that?

---

### Post by Crafty Kisses on 2007-06-29
> **timelord726 said:**
> Are there any other drivers that might work better that I could try replacing it with?  If so, how would I go about doing that?

What kind of mouse do you have?

---

### Post by timelord726 on 2007-06-29
> **Codename said:**
> What kind of mouse do you have?
Posted above:
> **timelord726 said:**
> I have a Logitech S510 wireless keyboard and mouse combination, and the keyboard and mouse both use the same receiver and USB connection.  However the keyboard continues working after the mouse has stopped.

---

### Post by timothy.crosley on 2007-07-01
I had the same problem(with the same keyboard/mouse) when using a non-powered usb hub, switching to a powered one fixed it for me.

---

### Post by lisati on 2007-07-02
I had a similar problem on my laptop, using a usb mouse. I can't remember the exact thread, but there are a couple which involve a solution that worked for me.

IThe procedure is something like this:

In a terminal, type:
```

sudo gedit /boot/grub/menu.lst

```

Then scroll down to the line that begins "# defoptions=quiet splash "

add the following to the end of the line:
```

acpi=force irqpoll

```
Save and exit the editor, then type in the terminal,
```

sudo update-grub

```
Reboot, and things should be fine.

Note: This solution seems to work better for some people than others....

---

### Post by Mike_RM on 2007-07-10
I had the same mouse problem and the solution suggested by Lisati works just fine on my IBM thinkpad with MS USB mouse - looks like the answer to a lot of people's problems. Many thanks.

---

### Post by shedokan on 2008-03-13
do you mean the menu.lst file should look like this:
```
# defoptions=quiet splash acpi=force irqpoll
```
or like this:
```
# defoptions=quiet splash
acpi=force irqpoll
```

---

### Post by russellnation on 2008-04-05
I had this problem too, where my mouse would suddenly stop working while the computer stayed alive (not frozen).

The Fix. use ps/2 : I have s510 logitech cordless desktop. It came with the option to use USB or PS/2. Since I started using the PS/2 adapter that came with it, it has worked great.
worth a try. If you don't have a ps/2 mouse get an adapter. If you don't have a ps/2 port ???

---

### Post by L8erG8er on 2008-04-15
I have the S510 combo also, and using the PS2 connections only worked for me as well.  I use the Logitech Cordless Desktop LX-300 in the keyboard preferences, and most of the keyboard buttons are usable (except the Mode keys).  Haven't figured that one out yet.  Think I'll have to wait for the next kernel version to fix that.

---

