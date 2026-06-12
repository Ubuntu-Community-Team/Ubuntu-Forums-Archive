---
title: "GRUB2  Menu Entry for Bash Scripts"
date: 2014-11-21
forum: General Help
---

### Post by joe141 on 2014-11-21
Hello everyone, I am a first time thread maker, but not a first time visitor to these forums. 

I would not normally make a thread and take up your time by asking you all silly questions; usually I manage to find what I'm after by trawling around online and through various forums, but it's come to a point where I am just not sure where else to go. So here is what I am trying to do.

I am currently editing a grub.cfg on a bootable grub2 USB flash stick. it boots into a custom grub2 boot menu from the USB and displays various usernames which then each load their own custom Config files with custom menu entries. So far so good, each username has its own basic password. each custom menu entry usually points to a partition on the usb drive to load various payloads ranging from diagnostics to stress test software, requiring a total of 6 partitions so far. 

What I want however is to be able to run bash scripts from a grub menu entry, I have seen people who say they have managed this, but they fail to reproduce the menuentry coding etc etc. (Example of one that says it's done it, but then doesn't tell me exactly how [http://ubuntuforums.org/showthread.php?t=1874565](http://ubuntuforums.org/showthread.php?t=1874565))

 The end goal is to chain load various Zenity commands through a bash script to display password boxes when the user selects a specific password protected menu entry choice from the root grub.cfg menu. I realise this all might seem rather pointless, but it's a pet project, something to keep me occupied in my free time.

So the menu entry so far is as follows:

menuentry "Run Script Test" --unrestricted {
insmod linux
insmod echo
search --set=root --fs-uuid --set=root FC7A-4E5C
linux /bash/vmlinuz-3.13.0-32-generic 
echo "error 1"
initrd /bash/initrd.lz
echo "error 2"
linux16 /bash/bootinfoscript.gz
echo "error 3"

I added in the echo's just so that I could see what error messages I got, and where they came in the order sequence.

From what I understand so far (and I may be completely wrong) I need to load up a linux kernal, then make it point to bash and then load in the relevant bash script file? 

Even if I have to chainload or boot into a full linux terminal to do this, that would be fine too, I just wouldn't know where to start.


Any help is appreciated as I am curious as to how this can be done, and how far off I was before admitting defeat  :p

---

### Post by oldfred on 2014-11-21
Grub does not run bash, it has its own very limited set of commands for booting.
 [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)


And once you booted into a kernel, you cannot then boot into another system without rebooting or perhaps chroot into another system?

[https://help.ubuntu.com/community/Grub2/Passwords](https://help.ubuntu.com/community/Grub2/Passwords)
[http://ubuntuforums.org/showthread.php?t=1369019](http://ubuntuforums.org/showthread.php?t=1369019)

---

### Post by joe141 on 2014-11-24
> **oldfred said:**
> Grub does not run bash, it has its own very limited set of commands for booting.
 [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)


And once you booted into a kernel, you cannot then boot into another system without rebooting or perhaps chroot into another system?

[https://help.ubuntu.com/community/Grub2/Passwords](https://help.ubuntu.com/community/Grub2/Passwords)
[http://ubuntuforums.org/showthread.php?t=1369019](http://ubuntuforums.org/showthread.php?t=1369019)


Thank you once again for the information, the password link is excellent and I'll be taking a look at it today in detail. However I have to wonder is there not a terminal environment that can be loaded during boot that would be able to handle bash? or would bash scripts only ever be able to run once Ubuntu has loaded up? :)

---

### Post by yancek on 2014-11-24
The post you link to in your initial post is an example of loading the Linux kernel and then running a bash script as indicated in post #5 and is no longer just Grub:

> You could try making a grub entry that boots into a kernel with an init argument.

> The end goal is to chain load various Zenity commands through a bash  script to display password boxes when the user selects a specific  password protected menu entry choice from the root grub.cfg menu

I'm not sure exactly what you mean by that.

---

