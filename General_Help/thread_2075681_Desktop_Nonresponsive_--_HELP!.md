---
title: "Desktop Nonresponsive -- HELP!"
date: 2012-10-24
forum: General Help
---

### Post by Rebelli0us on 2012-10-24
System is ubuntu 12.10 with optional Mate desktop.

I changed the command in "Users & Groups" (under Administration) by simply adding "gksudo" at the beginning. I thought this way I won't have to login every time. I've done this for Synaptic, Software-Center and a couple of others and it works fine.

Running the command "Users and Groups" with gksudo  brought up an undresponsive window,I couldn't get rid of it so I rebooted.  Now, system boots up fine, but it's non-responsive. **Main menu is frozen**. Help, how do I get out of this??

---

### Post by danielbauwens on 2012-10-24
Try booting again by typing:
```
ALT-F1
```
Then log in.

Type:
```
sudo reboot
```

This should help it from being unresponsive.
Daniel

---

### Post by Rebelli0us on 2012-10-24
> **danielbauwens said:**
> Try booting again by typing:
```
ALT-F1
```
Then log in.

Type:
```
sudo reboot
```

This should help it from being unresponsive.
Daniel


Thank you, I can reboot fine, I can login, but once there the menu is frozen. I can login a Guest session, or Unity, or anything, just **my** profile is frozen.

---

### Post by danielbauwens on 2012-10-24
Ah, okay.

Then try this:

```
CTRL-ALT-F2
```
Then type:
```
sudo stop lightdm
```
you will get a notification: lightdm stop/wait then enter the following:

```
sudo start lightdm
```
This should restart your Xserver and send you back to your login screen.

***All of the above is by TrailRider, so thanks alot to him***

---

### Post by Rebelli0us on 2012-10-24
Thank you, I did Ctrl+Alt F1 or F2 > command prompt > Ctrl+Alt+Del > reboot >  then can I login fine, just nothing works. Looks like some "security" feature causing system to self-destruct.

---

### Post by danielbauwens on 2012-10-24
Sorry, I don't know how to fix this anymore.
What I do know I once had something similar and there was this killall command (It wasn't killall, something that quit everything and then restarted) and that worked, but I don't remember command for it.

Good Luck,
Daniel

---

### Post by Paddy Landau on 2012-10-24
You might have caused some of your home files or folders to be owned by root, which would certainly spoil your day!

If the other suggestions do not work, boot into Recovery Mode and try the following.


[LIST=1]
[*]Enter the commands:
```
mount --options remount,rw /
mount --all
```
[*]Enter the following command, substituting [COLOR=Navy]Rebelli0us[/COLOR] with your actual user name.
```
find /home/[COLOR=Navy]Rebelli0us[/COLOR]/ -xdev -user root -print 2>/dev/null
```
[*]The find command should not display anything.
[/LIST]
 
If the find command does find something, you would have to change it back to yourself. The command would be as follows (again replacing instances of [COLOR=Navy]Rebelli0us[/COLOR] with your actual user name).
```
find /home/[COLOR=Navy]Rebelli0us[/COLOR]/ -xdev -user root -exec chown --recursive [COLOR=Navy]Rebelli0us[/COLOR]:[COLOR=Navy]Rebelli0us[/COLOR] {} ';' 2>/dev/null
```To reboot, enter the command:
```
reboot now
```Once you are running again, please undo the changes you described in your [post=12315166]first post[/post]. The programs come with the permissions-requests built in.

---

### Post by Rebelli0us on 2012-10-24
Thanks Paddy. After several reboots it "unlocked", I worked for several minutes, then it locked again. Rebooted, worked some more, locked again. Then I noticed that on a fresh reboot main menu has a couple of minutes delay before it becomes available, so it wasn't frozen... just **very** late. Based on that is your diagnosis still possible?

---

### Post by Paddy Landau on 2012-10-24
> **Rebelli0us said:**
> Based on that is your diagnosis still possible?
I do not know. I wonder if it is anything to do with the mix of Ubuntu and Mate on your hardware. I have never used Mate, so I cannot comment on that.

At this point, you may just have to wait two minutes before using your system when logging in.

---

### Post by Rebelli0us on 2012-10-24
> **Paddy Landau said:**
> I do not know. I wonder if it is anything to do with the mix of Ubuntu and Mate on your hardware. I have never used Mate, so I cannot comment on that.

At this point, you may just have to wait two minutes before using your system when logging in.

I discovered it by chance. I browsed Ubuntu in [distrowatch]("http://distrowatch.com/table.php?distribution=ubuntu")

On the left column under "Package" I noticed it says "[mate-desktop (1.4.1)]("http://mate-desktop.org/")" and if you follow the links it takes you to [the installation instructions]("http://wiki.mate-desktop.org/download?&#ubuntu_quantal_quetzal_1210_repository"). It looks like you can have Ubuntu 12.10  with the latest kernel **but without Unity**, and perhaps you're right that MATE is not fully *baked* yet or not well-integated with 12.10...

---

### Post by Paddy Landau on 2012-10-24
I would not know if Mate is fully baked. However, it is not an official part of Ubuntu and as such I wonder if this thread might have been better in the [Other OS/Distro Talk forum]("http://ubuntuforums.org/forumdisplay.php?f=401").

As you have installed Mate within Ubuntu, you should still have Unity available. Try booting into normal Ubuntu (the option should be at the login screen). Does it still give you problems?

---

### Post by Rebelli0us on 2012-10-24
It's genuine Ubuntu 12.10, I assume you can install any UI shell you want on top of it, just like xfce.

I'm suspecting that my gksudo command may have been coincidence,  and now leaning towards blaming 2 Firefox Unity addons installed automatically (which I have disabled).

---

