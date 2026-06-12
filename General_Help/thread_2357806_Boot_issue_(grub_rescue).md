---
title: "Boot issue (grub rescue)"
date: 2017-04-06
forum: General Help
---

### Post by epharion on 2017-04-06
[COLOR=#000000][FONT=Arial]Hello,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I have ubuntu (server) in a virtual machine (vSphere). It worked well since today :([/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]My application didn't work this morning. When I tried to do something on it, ubuntu said me something like the hard drive is in read only mode.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]So I tried to reboot, and now ubuntu won't launch : filesystem unrecognized, grub rescue....
I installed boot repair but it didn't fix my issue.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Here, is the boot info
[http://paste.ubuntu.com/24326648/](http://paste.ubuntu.com/24326648/)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Do you have any idea about my issue ?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Thanks for help[/FONT][/COLOR]

---

### Post by oldfred on 2017-04-06
Does not show sda1.
And Boot-Repair's suggested fix is fix file system. If you ran it, it would run fsck.

This does it in two steps and has a few more of the parameters than the simple fsck that Boot-Repair does.
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

---

