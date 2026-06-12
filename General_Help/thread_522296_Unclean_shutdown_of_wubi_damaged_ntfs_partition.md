---
title: "Unclean shutdown of wubi damaged ntfs partition"
date: 2007-08-10
forum: General Help
---

### Post by eddj on 2007-08-10
Having used wubi successfully for a few days, it shut down in an incomplete manner, forcing me to hit the power button in order to turn the computer off, as the keyboard was unresponsive, and the screen blank.

It seems that this damaged the ntfs partition wubi is working from inc. all my windows installation.

Running "chkdsk c: /R" from the windows cd appears to have fixed windows inability to boot as it was quoting "invalid boot.ini, booting from c:/windows, ntdetect failed"

Having saved windows (for my files, the OS can go :p) and it boots fine, I have yet to try wubi ubuntu to see if that is borked.

If there are any log files that I could post to help future diagnostics and bug fixing if there is one, please let me know.

---

### Post by nooby on 2007-09-29
I've got a similar shut down failure. 

I used WBI maybe 2 days all went well but being nagged that it was vital I upgraded cause upgrades make Ubuntu more safe it failed to shut down. 

Like you me too had to hit the power buton but that failed too. So I pulled the pug on it. 

Lucky for me my win xp managed to start. I'm using that one now. Have not tried WUBI yet. 
And based on your experience I will not. Cause to have to repair windown I will not go into. I'm a noob.

Sad nobody answered you. Hopefully now when they know your not alone they allert someone who knows what it could be. . 

I am using an AOpen XC Cube Mini with intel 915 chipset. I'm on wqubi for Fiesty Fawn 7.04 as I remember

Could one of the upgrade have changed something? 

I could wait until WUBI for Gutsy is official and download that one? Would that solve the shutdown bug?

---

### Post by ago on 2007-10-01
The filesystem used is an external project.

You should get in touch with ntfs-3g project. But keep in mind that hard reboots do cause filesystem corruption whether you use wubi/ntfs-3g or not.

[www.ntfs-3g.org/](www.ntfs-3g.org/)

---

### Post by nooby on 2007-10-04
Then how does one avoid doing such hard reboots? 

Should I delete the wubi file. Download it again when the gutsy release arrive around November and not do the upgrade cause the problem with unclean shutdown started after the upgrade to the 120? upgrades. 

If I don't upgrade then maybe no shutdown error occur again? 

The reason I haven't used LVPM to make a regular partitioned install of Ubuntu is that as a noob I have no knowledge on how to be able to test other distros like Kubuntu or PCLinuxOS or any other if I already have a partitioned Linux going. Where could I learn such advanced stuff?

---

### Post by ago on 2007-10-04
> **nooby said:**
> Then how does one avoid doing such hard reboots?> 
In Linux is extremely unlikely that you need to hard reboot (except when there is a kernel panic). Most users do hard reboot because they _think_ they are in a deadlock. In the worst case you can use sysrq key combinations. There are several guides on the topic.

[quote]Should I delete the wubi file. Download it again when the gutsy release arrive around November and not do the upgrade cause the problem with unclean shutdown started after the upgrade to the 120? upgrades.
The hardreboot issue is a filesystem/hardware problem and things are not going to change in gutsy. 

[quote]The reason I haven't used LVPM to make a regular partitioned install of Ubuntu is that as a noob I have no knowledge on how to be able to test other distros like Kubuntu or PCLinuxOS or any other if I already have a partitioned Linux going. Where could I learn such advanced stuff?
If you want to test several ubuntu flavors just install Ubuntu allocating 20GB. Then you can install other desktop environments as packages (es kubuntu-desktop, xubuntu-desktop...). When you login you simply select the desktop environment in the options.

---

### Post by nooby on 2007-10-04
Ago, 

I used the search but failed to find how one does a "hard reboot" cause suddenly I felt unsure of how that could be avoided with using WUBI and having done the unfortunate upgrade and getting the unclean shutdown error. What exactly do you mean when you say Hard reboot? 

Is it your experience or good guess that if I uninstall WUBI and wait until WUBI 7.1 Gutsy comes out and I install that one but don't do the update then it wil lwork again? 

Under these conditions will I then not have the unclean shotdwon error? 

I feel very insecure doing  partition. Other users have lost a whole HDD doing that. Doing backup? I'm a noob have no idea how one do such. If I do it wrong then it will fail to restore.Using your advice to do google on Raising Elephants Linux but without the question marks gave a wikipedia answer. 
[http://en.wikipedia.org/wiki/Magic_SysRq_key]("http://en.wikipedia.org/wiki/Magic_SysRq_key")
> The magic SysRq key is a key combination in the Linux kernel which, if the CONFIG_MAGIC_SYSRQ option was enabled at kernel compile time, allows the user to perform various low level commands regardless of the system's state using the SysRq key. It is often used to recover from freezes, or to reboot a computer without corrupting the filesystem.


But how does one reach the command line if one has shut down already? I don't get it.

Ooops I should read further down. I had no idea what a sysrequest was, It is a button sharing with Printscreen and if one make alt it maybe only address what is need now and not the printer. 

> An alternative to issuing the REISUB/RSEIUB keystrokes is to just press Alt + SysRq + R, followed by Ctrl + Alt + Del. This is the equivalent of issuing a shutdown now command at a root console; it does take a short while for the system to shut down after the Ctrl + Alt + Del keystroke. However, not all Linux systems support this easier method.


Being a noob I have no idea which one of the REISUB I am supposed to use?

---

### Post by ago on 2007-10-04
> **nooby said:**
> I used the search but failed to find how one does a "hard reboot"
Hardreboot = Pulling the plug off the back or your computer, or keeping the power button down until the machine turns off. That does not give the OS time to terminate the processes in an orderly fashion and can result in filesystem corruption (whether you use wubi or not).

So it's quite simple to avoid a hard reboot...

---

### Post by ago on 2007-10-04
The sysrq are needed if you find yourself in a situation that seems like a dead end, where the keyboard has no effect and the screen is frozen. That's when most users unfamiliar with linux pull the plug. As mentioned it's extremely unlikely for linux to freeze solid, and even if it looks like it, there are ways around it so that pulling the plug is mostly unnecessary. Sysrq is one such option.

---

### Post by nooby on 2007-10-05
Thanks ago,

I have tried the alt+sysrq+REISUB now but that didn't help either. 

Now, I am no Command Line guy at all. 

But is it not possible to make an easy command line shutdown. 

the Gui is supposed to do that if Iget it. 

So how do I enter the command line console and what do I write here to do a clean shut down. 

I don't think wubi/ntfs-3g that makes this error happens. 

Remember that the wubi installer has managed to make several clean restarts on it's own several times already and the first time I logged in i could do a clean restart but the error started after this: 

1. I changed to another keyboard cause this one is Swedish layout. I changed to Swedish for instead US keyboard to be first. 

2. The update manager automatically looked for updates and told me in a popup that 121 was there for download. 

3. some system told me I'm not using an ordinary DSL connection and that the system I uised was not recommended. Not sure how important that one is. 

If ind it most likely that it was the update that changed something. 

Or the me changing to another keyboard 

Should I check setting such to default and see if the error disappear? 

But first is it not easy to go into command line and write something that makes a log that explains why the CPU seems to go 100% and then it never shutdown. the fan roll at max speed and stay forever. 

Using a log I could tell what went wrong? 

Remember me a noob so you have to tell if I have to go Admin and how one does that and how to find the command line and what to write. 

Nooby

---

### Post by ago on 2007-10-05
If you can get to command line there is no need to use sysrq keys. Those are used when the keyboard does not seem to respond. The command to reboot is... ...surprise, surprise... "reboot" ("sudo reboot" to be precise). To get to the console CTRL+ALT+F2

If you cannot reboot in wubi with the above command, see [http://ubuntuforums.org/showthread.php?t=446006&highlight=sendsigs](http://ubuntuforums.org/showthread.php?t=446006&highlight=sendsigs)

---

### Post by nooby on 2007-10-05
Thanks
I read the whole thread. I get it as the error remains. None reported they now have clean shutdown. 
[http://ubuntuforums.org/showthread.p...light=sendsigs]("http://ubuntuforums.org/showthread.p...light=sendsigs")

I didn't know how to tell the system I'm an admint? But after three times failing to give username and psw it allowed me to be admin nevertheless. 

I wrote sudo reboot and it worked so now I want to know how to shutdown instead. 

Sudo shutdown 

or does one need a qualifier or some sort?

Report after a failure. I fail to use the sudo it ask me to give login and password and don't accept the username and psw that the GUI login to Ubuntu accept so easily After servaral failing it took my sudo shutdown -h now but failed to power off. But the hard reboot didn't destoy my files and I was able to start window again. 

What to do next?

---

### Post by nooby on 2007-10-09
Looking around on the web I found this suggestion on an openSuse forum. 

He says that DSDT could help us. 

>  Howto Fix Your Buggy DSDT., Yes you most probably have one!
[http://www.suseforums.net/index.php?showtopic=13893&hl=dsdt]("http://www.suseforums.net/index.php?showtopic=13893&hl=dsdt")

Does we who use Ubuntu have a similar way of fixing this DSDT? Link to it please. 

How much does OpenSuse and Ubuntu differ? if it works for them it maybe works for us too?

---

### Post by ago on 2007-10-09
> **nooby said:**
> Thanks
I didn't know how to tell the system I'm an admint? But after three times failing to give username and psw it allowed me to be admin nevertheless. 
Is this during installation? If so make sure you use wubi 7.04.04. If it's after second reboot then it may be that the wrong keyboard is used. Make sure you type what you think you do. You may try to install ubuntu with a simple username/password

I wrote sudo reboot and it worked so now I want to know how to shutdown instead. 

> Sudo shutdown 

or does one need a qualifier or some sort?
sudo halt

---

### Post by ago on 2007-10-09
> **nooby said:**
> Looking around on the web I found this suggestion on an openSuse forum. 

He says that DSDT could help us. 


[http://www.suseforums.net/index.php?showtopic=13893&hl=dsdt]("http://www.suseforums.net/index.php?showtopic=13893&hl=dsdt")

Does we who use Ubuntu have a similar way of fixing this DSDT? Link to it please. 

How much does OpenSuse and Ubuntu differ? if it works for them it maybe works for us too?

Yes DSDT might be one of the reason why people have issues. But that is taken care of by ubuntu kernel devs. Best shot here is to wait for next revision.

---

### Post by nooby on 2007-10-09
> that is taken care of by ubuntu kernel devs. Best shot here is to wait for next revision. Does that mean April? 2008 or now Gutsy within ten days or so? 

Or are kernel update unrelated to the Gutsy update? Is Kernel same for all different distros? I read on Open Suse that they had same shut down problem too. so it seems unrelated to WUBI installation. 

Are there any distro that has solved it?

Is this a good place to look?
[http://www.kernel.org/]("http://www.kernel.org/")

---

### Post by ago on 2007-10-09
> **nooby said:**
> Does that mean April? 2008 or now Gutsy within ten days or so? 
Within 1-2 weeks we should hopefully have betas for Gutsy (early alphas are already out). If such beta behaves, we might ship a final by the end of the month.

> Or are kernel update unrelated to the Gutsy update?
You do have kernel updgrades within Feisty, by they are minor version upgrades, major kernel upgrades only happen with a new distro.

> Is Kernel same for all different distros?
It is the same for all flavors so kubuntu-7.10 and xubuntu-7.10 will use the same kernel

> I read on Open Suse that they had same shut down problem too. so it seems unrelated to WUBI installation.
As mentioned, ACPI is one of the reasons. Another issue is that people do tend to hard reboot. And that practice may result in a corrupted FS. Both cases are unrelated to Wubi (unless it can be proven that ntf-3g exhacerbates hard reboot issues, which is probably not the case).  

> Are there any distro that has solved it?
Hard reboots can easily cause a filesystem corruption also in plain old windows without any Linux or Wubi (just googl for "ntfs corruption"). ACPI is a slightly different story

---

### Post by nooby on 2007-10-10
> Another issue is that people do tend to hard reboot. 

But we have no choice. If one live in a small room one has to shut it down to be able to sleep. 

I've tried the command line commands and they didn't work. 

One time I managed to restart instead and that way I could let windows shut it down it still said next morning that it couldn't boot cause some file missing. 

when I did a hard reboot boot after that message then it could boot again. 

If I get what you say then before one try out linux one should check if the computer one have is hardware compatible with the way linux make their shutdown. 

But to find that info you already have to be a very good computer user. It is not easy to find out if one are compatible or not. I spent many ours but could not find my computer in the list of non-compatibles. 

AOpen XC Cube Mini MZ 915

[http://xc.aopen.com.tw/CubeProduct_01.aspx?Auno=2170&mdstyl=22]("http://xc.aopen.com.tw/CubeProduct_01.aspx?Auno=2170&mdstyl=22")

Are you able to find it mentioned as not having the hardware needed. 

It is a relatively very new computer so I am very surprised it didn't work. Bought it 2005 when it was very new. 

I have an old HP/Compac. I don't dare to test if that one work. that one was bought 2003.

---

### Post by ago on 2007-10-11
> **nooby said:**
> I've tried the command line commands and they didn't work.
If you can use the command line and "sudo halt" does not work it means that /etc/init.d/fixsendisgs is missing or the ACPI used in your machine is not compatible

> If I get what you say then before one try out linux one should check if the computer one have is hardware compatible with the way linux make their shutdown.
It's not Linux shutdown that is weird in any shape way or form, it is the ACPI shipped by some manufacturers which is completely *#!@* and those manufacturers only release the workarounds to one company...

> I have an old HP/Compac. I don't dare to test if that one work. that one was bought 2003.
As a rule of thumb linux compatibility on old machines is better than on the newest ones

---

