---
title: "Changing the boot order"
date: 2013-06-02
forum: General Help
---

### Post by alfirdaous on 2013-06-02
Hello everybody,

I am using both system (windows vista and ubuntu), the computer is booting from windows first, I would like to change it to Ubuntu system:

```

# cat /boot/grub/grub.cfg | grep menuentry
if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
  menuentry_id_option=""
export menuentry_id_option
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-a6eece84-8179-4998-be7d-08085c5290d4' {
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-a6eece84-8179-4998-be7d-08085c5290d4' {
    menuentry 'Ubuntu, with Linux 3.8.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-23-generic-advanced-a6eece84-8179-4998-be7d-08085c5290d4' {
    menuentry 'Ubuntu, with Linux 3.8.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-23-generic-recovery-a6eece84-8179-4998-be7d-08085c5290d4' {
    menuentry 'Ubuntu, with Linux 3.8.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-22-generic-advanced-a6eece84-8179-4998-be7d-08085c5290d4' {
    menuentry 'Ubuntu, with Linux 3.8.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-22-generic-recovery-a6eece84-8179-4998-be7d-08085c5290d4' {
    menuentry 'Ubuntu, with Linux 3.8.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-21-generic-advanced-a6eece84-8179-4998-be7d-08085c5290d4' {
    menuentry 'Ubuntu, with Linux 3.8.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-21-generic-recovery-a6eece84-8179-4998-be7d-08085c5290d4' {
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-advanced-a6eece84-8179-4998-be7d-08085c5290d4' {
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-recovery-a6eece84-8179-4998-be7d-08085c5290d4' {
    menuentry 'Ubuntu, with Linux 3.5.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-25-generic-advanced-a6eece84-8179-4998-be7d-08085c5290d4' {
    menuentry 'Ubuntu, with Linux 3.5.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-25-generic-recovery-a6eece84-8179-4998-be7d-08085c5290d4' {

```

this was the result of the command "cat /boot/grub/grub.cfg | grep menuentry", how can I get the boot order from this command??

Thx in advance

---

### Post by Bashing-om on 2013-06-02
[COLOR=#000000]alfirdaous; Hi !

The general control of system booting is from the /etc/default/grub file  -->
IF
a) ubuntu's grub menu is displayed (or displayable with the use of the shift key)
b) the system you desire to boot is on this initial boot menu
c) all operating systems are installed on individual partitions (not WUBI install)
THEN
a) count down in the menu to the entry you want to boot - count starts at 0 (zero) for first entry
  let's say ubuntu is the third entry (latest kernel) so the count is "2"
b) Make a backup of the file to-be-edited; ->
```
sudo cp /etc/default/grub /etc/defaultgrub-orig
```
c) open your favorite text editor with admin authority
```
gksudo gedit /etc/default/grub
```
d) see the enrty "GRUB_DEFAULT=0  in the editor ? -> change the 0 to a 2
e) save the file and exit
F) IMPORTANT if not done, changes will not "stick"
```
sudo update-grub
```
g) reboot to see effect
else
a)install grub as the system's boot loader 

For full grub details please consult:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[/COLOR][INDENT=3][COLOR=#000000]
workie great, last long time

[/COLOR][/INDENT]

---

### Post by alfirdaous on 2013-06-03
I have Vista as first and Ubuntu as second, so the number is 1, I did these changes before, BUT no effect, that's why I am wondering, may be the number is not correct

---

### Post by Bashing-om on 2013-06-03
[COLOR=#000000]alfirdaous;

The number is correct,,,, did you do:
```
sudo update-grub
``` after the edit to /etc/default/grub ?
and
the hard drive that has ubuntu installed on it, is set as the first boot priority in bios.

If that bios needs to be reset, do so, then boot into ubuntu and update grub again to generate a new device.map file.[/COLOR]

---

### Post by alfirdaous on 2013-06-05
> **Bashing-om said:**
> [COLOR=#000000]alfirdaous;

The number is correct,,,, did you do:
```
sudo update-grub
``` after the edit to /etc/default/grub ?

Yes

and

> the hard drive that has ubuntu installed on it, is set as the first boot priority in bios.

How to check that?

> 
If that bios needs to be reset, do so, then boot into ubuntu and update grub again to generate a new device.map file.[/COLOR]

How to do that??

Thx

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]alfirdaous;
Now we are treading on dangerous waters, if you have never been there !

Every computer manufacturer has differing ways to access the bios set-up routines.... many times one may access bios when you are booting and as soon as the bios screen appears, press the "escape" key, or maybe f12 key or some other key ... many many times on the bios screen is an advisory as to which key will access bios.. and again each bios set-up is different, one will just have to look at all the options until the boot priority function is found. DO NOT CHANGE WHAT YOU DO NOT KNOW !!

Your version and maker of bios should appear on the boot-up screen... the manuals are available on-line with a bit of searching... it is strongly advised to obtain this manual for comprehension.

That said, if you can provide the name of your computers manufacturer and what vendor provided the bios and the version of bios, some one on this forum may have experience with that set up, may see this thread, and if so will advise you from their pool of knowledge.

Not meant to be difficult in response, just do not want to break your system.[INDENT=3]
if you insist we will !

[/INDENT]


[/COLOR]

---

### Post by alfirdaous on 2013-06-05
The BIOS boot order is Hard Drive first, the CD-DVD, then others

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]alfirdaous;

You do good work...as it is not working -> the only other thing I can think of is that another grub configuration file has been edited, the files in /etc/grub.d/ are part of that chain of events,
show us the output of :
```
ls -la /etc/grub.d/
cat /etc/grub.d/40_custom

```[/COLOR][INDENT=2][COLOR=#000000]
we mov'n on now

[/COLOR][/INDENT]

---

### Post by alfirdaous on 2013-06-05
```

# ls -la /etc/grub.d/
total 76
drwxr-xr-x   2 root root  1024 Apr 29 05:34 .
drwxr-xr-x 155 root root  9216 Jun  6 02:09 ..
-rwxr-xr-x   1 root root  7541 Oct 14  2012 00_header
-rwxr-xr-x   1 root root  5974 Apr  9 08:53 05_debian_theme
-rwxr-xr-x   1 root root 11381 Apr  9 09:29 10_linux
-rwxr-xr-x   1 root root 10634 Oct  1  2012 10_lupin
-rwxr-xr-x   1 root root 10258 Oct 14  2012 20_linux_xen
-rwxr-xr-x   1 root root  1688 Oct 11  2012 20_memtest86+
-rwxr-xr-x   1 root root 10976 Oct 14  2012 30_os-prober
-rwxr-xr-x   1 root root  1426 Oct 14  2012 30_uefi-firmware
-rwxr-xr-x   1 root root   214 Oct 14  2012 40_custom
-rwxr-xr-x   1 root root   216 Oct 14  2012 41_custom
-rw-r--r--   1 root root   483 Oct 14  2012 README


# cat /etc/grub.d/40_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

```

thanks

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]alfirdaous;
Oh Shoot, you got two files in there that are not standard and are marked as executable:
10_lupin
20_linux_xen
What are they and where did they come from ?

in addition the file 10_linux has been heavily edited....(can tell by the size of the file)

You can bet that one of these files contains the boot menu order. Those files are too large to place in the post directly; perhaps they can be posted by use of the "attachments" tool (paper clip icon) at the top  of the post. When the file is identified, one may edit it and re-arrange the items to appear on the grub boot selection screen.[INDENT=2]
with that we know more

[/INDENT]

[/COLOR]

---

### Post by alfirdaous on 2013-06-06
> **Bashing-om said:**
> [COLOR=#000000]alfirdaous;
Oh Shoot, you got two files in there that are not standard and are marked as executable:
10_lupin
20_linux_xen
What are they and where did they come from ?
[/COLOR][COLOR=#000000]

I really don't know

> 
in addition the file 10_linux has been heavily edited....(can tell by the size of the file)


[/COLOR][http://www.speedyshare.com/2FRHY/10-linux](http://www.speedyshare.com/2FRHY/10-linux)[COLOR=#000000]


Thx[/COLOR]

---

### Post by Bashing-om on 2013-06-07
[COLOR=#000000]alfirdaous; My thoughts gathered;
As there appears no problems with the outside application 'speedyshare' that it integrated well into ubunt's operating system and does not affect the booting process, thus -> we look at other files.

All we need to do is identify the file that contains the boot "menu entry" items, and edit that sequence.
To that end, let us look at the file 10_linux, please post that file using the "attachment" tool (paperclip icon).
[/COLOR][INDENT=2][COLOR=#000000]
I am a one-thing-at-a-time kinda guy

[/COLOR][/INDENT]

---

### Post by alfirdaous on 2013-06-07
I posted it here [http://www.speedyshare.com/2FRHY/10-linux](http://www.speedyshare.com/2FRHY/10-linux) it seems not to be accepted while attaching the item, it says: Invalid file

---

### Post by Bashing-om on 2013-06-07
[COLOR=#000000]alfirdaous; 

Speedy share file share works !
I did not find in the 10_linux file what I am I looking to find.
How bout the next one ?
10_lupin
Will see what is there.
[/COLOR][INDENT][COLOR=#000000]
keep'n on keep'n on

[/COLOR][/INDENT]

---

### Post by oldfred on 2013-06-08
I was not familiar with lupin either, but it seems to be wubi related. Is this a wubi install inside the NTFS partition?
If so you have to modify boot order with Windows, not grub.

---

### Post by alfirdaous on 2013-06-09
this is the 10_lupin file
[COLOR=#000000]
[http://www.speedyshare.com/T859R/10-lupin](http://www.speedyshare.com/T859R/10-lupin)

@[**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711"): it is a wubi installation[/COLOR]

---

### Post by oldfred on 2013-06-09
bcdEdit - bcbc
[http://ubuntuforums.org/showpost.php?p=11927905&postcount=5](http://ubuntuforums.org/showpost.php?p=11927905&postcount=5)
[http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu](http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu)

   Change boot order
[http://www.psychocats.net/ubuntu/wubi#bootorder](http://www.psychocats.net/ubuntu/wubi#bootorder)
BCDedit to remove
[http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu/145605#145605](http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu/145605#145605)

---

### Post by Bashing-om on 2013-06-10
[COLOR=#000000]alfirdaous;

See oldfred's last.... I have never encountered "wubi" so at this point I am out of my depth and must bow out ...will continue to monitor your thread .
[/COLOR][INDENT=3][COLOR=#000000]
it is all a learning experience

[/COLOR][/INDENT]

---

### Post by alfirdaous on 2013-06-10
I changed throw Windows, Thanks everybody

---

### Post by Bashing-om on 2013-06-10
[COLOR=#000000]alfirdaous; Great;

Good you have resolution. Sorry if my dissknowledge of the "wubi" install caused such a delay.
Please mark this thread as "solved" as that helps keep the forum tidy.

[/COLOR]Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.
[INDENT=2]
all's well that ends well

[/INDENT]

---

### Post by alfirdaous on 2013-06-11
it's fine [**[COLOR=#000000]Bashing-om[/COLOR]**]("http://ubuntuforums.org/member.php?u=1111508"), I learned a lot from your side :)

sorry for the resolve issue, I did not find in where it was "Thread Tools"

---

### Post by Bashing-om on 2013-06-11
[COLOR=#000000]alfirdaous;
One thing for sure there is always something more to learn in this operating system, keeps me engrossed !

Mods continue to work on the "thread tools" ->solved issue since the upgrade to the present forum version.
Like ubuntu, this forum is a work in progress and gets better all the time.
[/COLOR][INDENT][COLOR=#000000]
I look forward to our next adventure[/COLOR][/INDENT]

---

