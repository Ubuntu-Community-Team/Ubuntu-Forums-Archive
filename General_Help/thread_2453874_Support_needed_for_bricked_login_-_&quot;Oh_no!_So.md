---
title: "Support needed for bricked login - &quot;Oh no! Something went wrong&quot; screen"
date: 2020-11-18
forum: General Help
---

### Post by lr55drk on 2020-11-18
Recently, I've had to flush my disks due to a Windows update bug and I had lost my Ubuntu 20.04 disk, which worked perfectly. However, after installing Windows and Linux again, and trying to set up Ubuntu 20.04, I've received multiple times the brick screen "Oh no! Something went wrong" when trying to login, after changing some settings of gnome, such as dock or desktop icons (yeah, it's unbeliavable that the brick is being caused by gnome settings, but it's true since I tested it reinstalling 20.04 and only changing gnome settings; after rebooting, the brick screen appeared.

I have tried solutions found in post like [this]("https://askubuntu.com/questions/1239025/after-upgrade-to-ubuntu-20-04-oh-no-something-went-wrong") or [this]("https://superuser.com/questions/917377/how-do-i-fix-oh-no-something-has-gone-wrong-gdm3-fails-to-start"), but none of them worked. Since I'm not an experienced Linux user, I'm feeling lost when trying to debug what is going on, such as greping `/var/log/` files, but I don't not where neither what to search. I'm still providing the content of `syslog` file with `grep error`, just in case any helpful information relies [there]("https://hastebin.com/raw/ojafazuyez").

If anybody could help me solving this problem I would be so grateful, I've been struggling with this for weeks and after asking in many forums and not getting response, I'm a little bit desperate, since I can't work in my job without my Ubuntu desktop :(

So please, if I can provide any information that could be useful, ask me and I'll do it as quickly as I can.

[UPDATE] Here you can see the content of crash file (_usr_sbin_gdm3.0.crash): [link]("https://controlc.com/914ae515").

---

### Post by tea for one on 2020-11-18
> Recently, I've had to flush my disks due to a Windows update bug and I had lost my Ubuntu 20.04 disk, which worked perfectly. 

A Windows update destroyed your Ubuntu installation - I hope I have understood that correctly?

Secondly, after you have installed Ubuntu 20.04, it all works fine until you change a setting?

Please be precise, exactly which setting? 

Which utility did you use to change the setting?

---

### Post by lr55drk on 2020-11-18
Yes, a Windows updated distroyed my Ubuntu installation, but after reinstalling everything (Windows & Ubuntu) everything was fine.
Yes, Ubuntu 20.04 fresh worked perfectly and without any errors.
When I reinstalled 20.04 fresh and tried to  test what was causing the crash I think I had only changed dock (with dconf-editor) and  .desktop icons (edited with Menulibre). In the current case, I've been  using 18.04 for late work, so multiple things had changed, and was after  updating when the brick screen appeared. However, I'm pretty sure that  the error is the same as the 20.04 reinstallation I've done before. Moreover, since I've seen the crash file is related to gdm3, I think the problem might not be caused by a gnome problem but gdm3 instead (see UPDATED line in original post if you missed it).

---

### Post by lr55drk on 2020-11-18
I've tried to change from gdm3 to lightdm and check if I could login, but the brick screen appeared again. However, a lightdm crash file didn't appear in /var/crash.

---

### Post by tea for one on 2020-11-18
> **lr55drk said:**
> Yes, a Windows updated distroyed my Ubuntu installation, but after reinstalling everything (Windows & Ubuntu) everything was fine.


That is bizarre and very unusual.......

```
I think I had only changed dock (with dconf-editor) 
```

Using dconf-editor to change the Dock doesn't sound quite right to me?
What did you want to do with the Dock?

```
.desktop icons (edited with Menulibre).
```

I'm not familiar with menu libre.

As you originally said, you were not too experienced with Ubuntu, I would suggest:-

Ignore dconf-editor for the time being.
Don't change any settings yet.
Use your virgin 20.04 installation until you feel more comfortable with the system.
When you are ready - explore [https://extensions.gnome.org/](https://extensions.gnome.org/) together with [COLOR="#0000FF"]gnome-tweaks[/COLOR] from the repository.

Gnome extensions offer easier ways to modify the desktop and, when they fail, they are simple to remove.

---

### Post by lr55drk on 2020-11-18
I just used dconf-editor to change the dock in a very small aspects (as you can see in [this]("https://linuxconfig.org/how-to-customize-dock-panel-on-ubuntu-18-04-bionic-beaver-linux") page). As with desktop icons, its just changing their display icon to another, nothing super-edgy.
However, the main problem here is that I've been using 18-04 for the past two weeks to work on delayed tasks I had to do, and after updating today, I lost access to anything due to the brick screen.
That's why I want to solve the brick screen, I know I could use virgin 20.04 to do those tasks, but I can't reinstall and lose all the data again.

Doesn't .crash file provide any helpful information? :(

---

### Post by tea for one on 2020-11-18
Post no. 1 - You are using 20.04
Post no. 6 - You refer to 18.04 with a link to editing 18.04

Your quickest option to finish your delayed tasks is to backup your files, install 20.04, restore your data and continue your work.

---

### Post by lr55drk on 2020-11-18
Providing more information, doing "sudo cat /var/log/syslog | grep -i gdm3 | grep -i error", the following line appears:

Nov 18 16:25:29 pakitoUX kernel: [   33.483023] gdm3[1152]: segfault at 1 ip 00007f19d5c5e77a sp 00007ffdb1b2f740 error 4 in libgobject-2.0.so.0.6400.3[7f19d5c30000+36000]

---

### Post by oldfred on 2020-11-18
If you have an old BIOS/MBR install of Windows, a major update rewrites partition table and "forgets" to include Linux logical partitions. This has been a "feature" since Windows 7 but applies to all BIOS Windows installs. Partition is still there & just needs partition table updated with Parted Rescue or Testdisk.

If BIOS/MBR but newer system (since 2012), much better to use UEFI/gpt.

---

