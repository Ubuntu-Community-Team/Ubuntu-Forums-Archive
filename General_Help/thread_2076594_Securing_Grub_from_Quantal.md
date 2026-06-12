---
title: "Securing Grub from Quantal"
date: 2012-10-26
forum: General Help
---

### Post by twipley on 2012-10-26
The goal that is to be achieved is the securing of Grub, that is, preventing standard users to fiddle with its terminal, edit its command lines, or enter the much-powerful recovery mode.

A fresh Quantal install was performed, which is the only operating system to be installed, and BIOS and the boot order and been taken care of, in addition to limiting users to "standard" accounts. (Physical machine intrusions are in this case not to be worried about, for it to be noted.)

[https://help.ubuntu.com/community/Grub2/Passwords](https://help.ubuntu.com/community/Grub2/Passwords)
[http://www.gnu.org/software/grub/manual/html_node/Security.html](http://www.gnu.org/software/grub/manual/html_node/Security.html)

Beside the information contained in the above resources, it is to be noted password encryption in such a case seems unjustified, as whenever "sudo update-grub" is ran while a plaintext password is present in the "/etc/grub.d/40_custom" file, the "grub.cfg" file is rendered unreadable to standard users, which of course are lacking administrative passwords.

The objective is to design a future-proof-enough method to make it so that, even after release upgrades, and various system updates, the users are able to boot in Ubuntu without problem, although the single-user, or other such modes, are locked to them.

I have fiddled for quite a time, although I am resorting to your help to continue progressing, as progress is tedious over here.

I have edited the "40_custom file," so that official Ubuntu Grub and kernel updates would not be breaking anything, or in other words so that the system continues both to be bootable and to be protected against the most curious minds, to that effect. Ideally the system would boot straight to Ubuntu, without even prompting for a password at the Grub level, all the while password-protecting related entries and settings, although I am having difficulty at doing so.

What I have tried is gksudo-editing the "/etc/grub.d/40_custom" file through gedit, adding the following lines:

```
set superusers="admin_username"
password admin_username admin_password
```

although it seems a standard username and a corresponding password also has to be set up, then associated to the default "Ubuntu" entry only, so as for standard users to be able to enter the default "Ubuntu" entry.

I am having problems. I am hoping some of you would be able to guide me in such a way to shed light on some of these issues. What would be the simplest and most-future-proof method to be used in this case? Any help would be *greatly* appreciated.

Thanks in advance,
twipley

---

### Post by dino99 on 2012-10-26
its not so easy to elaborate on grub as grub 2.0 is very different now compared to the previous 1.99.
You should send a message to the maintainer/developer Colin Watson to request about adding the appropriate missing features.

[https://launchpad.net/~cjwatson](https://launchpad.net/~cjwatson)

---

### Post by twipley on 2012-10-26
Okay. But are the features really missing? Basically I need to *apply* what is being talked about in the two pages, and determine if the protection would remain, even after Grub and kernel updates.

Since they seem to be talking about those features, I am assuming they are there, although on the Internet one is mostly talking about pre-2.0 versions, and on top of that it seems Quantal scripts need to differ from the Precise-and-earlier ones.

---

### Post by dino99 on 2012-10-26
> **twipley said:**
> Okay. But are the features really missing? Basically I need to *apply* what is being talked about in the two pages, and determine if the protection would remain, even after Grub and kernel updates.

generally speaking, all the custom settings are not changed , and with major upgrades the installer show a popup asking if we agree to install the change made by the coder or if we still want to continue with our own settings (even if they are mostly non compatibles)

so im still thinking than grub is missing the admin part (its a pure client oriented object, not client/server)

---

### Post by twipley on 2012-10-26
> **dino99 said:**
> generally speaking, all the custom settings are not changed, and with major upgrades the installer show a popup asking if we agree to install the change made by the coder or if we still want to continue with our own settings (even if they are mostly non compatibles)
It seems to be stressed in some pages that if the changes are only made to the "/etc/grub.d/40_custom" file, then that file will never be overwritten by Grub updates. What I wanted to assess was more concerning whether or not the system automatically runs "update-grub" after related updates have been performed in order to merge custom settings with the main configuration file.

> **dino99 said:**
> so im still thinking than grub is missing the admin part (its a pure client oriented object, not client/server)
Okay. Although, as long as it is administerable from the custom files, it is well enough for the current needs.

I am trying, in more precise terms, to make a script ressembling the following one:

```
set superusers="admin_username"
password admin_username admin_password
password standard_user public_password

menuentry "Ubuntu" --unrestricted {
     	set root=(hd0,1)
     	linux /vmlinuz
     }
```

Although I am not fluent enough to determine what the second set (paragraph) of code means, and how to apply it so that anybody can enter the default "Ubuntu" menu entry without problems, even without passwords. Furthermore, I am not getting, even after having read the documentation twice, what hd0 and /vmlinuz, for example, really mean. I have spent quite a good amount of time on that, and now I cannot afford to spend more time fiddling around without being fluent enough in the terminology at hand (this is not my field).

EDIT: in short, layman needs expert advice.

---

### Post by grahammechanical on 2012-10-26
Expert advice on this subject is in short supply, in my opinion. :)

I wonder if you are going about this the wrong way.

1) With only Ubuntu on the machine the Grub menu will not be displayed unless the shift or Esc keys are pressed just as Grub is doing it stuff.

2) you can set a password on a boot entry but you want that entry to boot for any user. So, if you set a 'superuser' password then only the 'superuser' can boot that kernel. What does the 'anyuser' do? If 'anyuser' is allowed to boot the kernel, then what is the point of setting a 'superuser' password.

3) it seems to me that you want to prevent anyone but you from getting access to the Grub menu and its editing features at boot time.

You must

a) find some way of disabling the keys (shift/Esc) to bring up the Grub menu.

b) reduce the countdown to 1 second or zero using the GRUB_TIMEOUT command

Option (b) might be enough. Also look at the GRUB_HIDDEN_TIMEOUT command.

> Wait this many seconds for a key to be pressed before displaying the menu.
If no key is pressed during that time, display the menu for the number of
seconds specified in GRUB TIMEOUT before booting the default entry. We
expect that most people who use GRUB HIDDEN TIMEOUT will want to
have GRUB TIMEOUT set to &#8216;0&#8217; so that the menu is not displayed at all
unless a key is pressed. Unset by default.

By the way, update-grub is a Ubuntu script that runs grub-mkconfig, which does the actual updating of grub.cfg. If you disable update-grub then grub.cfg will not be updated.

Regards.

---

### Post by twipley on 2012-10-26
> **grahammechanical said:**
> it seems to me that you want to prevent anyone but you from getting access to the Grub menu and its editing features at boot time.
Exactly.

Although if I am right the methods you described are not sound enough from a security standpoint, at least for Ubuntu 12.10 (Quantal). Thanks for the try, though, although it seems I have read the method is not fool-proof enough.

---

### Post by twipley on 2012-10-26
to have an idea of the entries:
```
grep menuentry /boot/grub/grub.cfg
```

```
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os --unrestricted {
```

I think the latest code, coupled with:
```
set superusers="admin_username"
password admin_username admin_password
```
would produce the desired result. If I am not replying back to confirm that means I am stuck somewhere bad. ... :)

EDIT: this did not work, even after having added the following lines:
```
     	set root=(hd0,1)
     	linux /vmlinuz
     }
```

---

### Post by twipley on 2012-10-27
> **grahammechanical said:**
> Expert advice on this subject is in short supply, in my opinion. :)
Indeed.

This is probably my last reply here until someone finds something else, because I could not. There is "GRUB_DISABLE_RECOVERY" which may help, although one holding the SHIFT key could bypass that without trouble.

Furthermore, in retrospective, GRUB_HIDDEN_TIMEOUT and GRUB_TIMEOUT, as grahammechanical pointed out, may, if used correctly, be of some value (not *sure* about that, though).

I remain confident I was close with what I have tried in the just-above post. That is, telling Grub to boot default menu entry with latest kernel without any problems for anyone, but to ask for superuser password input whenever one attempts to do anything else.

---

### Post by cariboo on 2012-10-27
This may be one of those cases, where enabling the root account may be a good idea, so that if an unprivileged user boots into recovery mode, he/she needs to enter root's password, in order to do anything. It is against forum policy to tell you how to do this, but if you read the [RootSudo]("https://help.ubuntu.com/community/RootSudo") howto, it will point you in the right direction.

---

### Post by twipley on 2012-10-28
Thanks, cariboo907. That indeed seems to be pointing to an adequate direction.

I really hope in the future, one reads such a thread back, while being guided towards both a unobtrusive and future-proof method of doing what was tried here.

[SIZE="1"]tags: custom-menu grub 12.10 password protection preventing root-shell privileges.[/SIZE]

---

