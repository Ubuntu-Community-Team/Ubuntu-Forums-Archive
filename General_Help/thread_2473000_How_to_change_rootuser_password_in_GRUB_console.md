---
title: "How to change root/user password in GRUB console?"
date: 2022-03-20
forum: General Help
---

### Post by smith73 on 2022-03-20
[COLOR=#222222][FONT=Verdana]Initially there was Ubuntu Mate 16.04 in dual boot with Windows installed on an ASUS laptop.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]I upgraded Ubuntu [COLOR=#222222][FONT=Verdana]Mate [/FONT][/COLOR]to 18.04, then entered the user password incorrectly several (10<) times,[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]and it got locked by some "tripwire", requiring passphrase. Passphrases I wrote down[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]didn't match. I booted Ubuntu from an installation disk, so it locked all user programs and desktop[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]in a file requiring this passphrase, so I could use only 20gb of storage in general "Try Ubuntu" GUI.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]I didn't use Ubuntu 18.04 since then maybe for several months or more, then I used only booting to Windows[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]for ~4-5 days. After yet several months after trying to login into locked Ubuntu desktop, the user password[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]doesn't match, though this same password was ok since my last usage if Ubuntu.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]Upon booting into Advanced Option for Ubuntu, there are [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]options to choose kernels and[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]same kernels in recovery mode: Linux 4.15.0-99-generic, [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]4.13.0-45-generic[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]Upon getting into Ubuntu recovery mode on Linux 4.15.0-99-generic kernel and getting into GRUB menu,[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]there is a fleeting "Failed" message reporting that ~"Failed Load Module service. Check your systemctl status[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]systemd-modules-load-service" . [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]So while in GRUB console I tried:[/FONT][/COLOR]
```
[COLOR=#222222][FONT=Verdana]password USER PASSWORD[/FONT][/COLOR]
```
[COLOR=#222222][FONT=Verdana]for both root and username of the laptop user, and it didn't change the password[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana](the password still doesn't allow to login).[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]I can get into full-screen console by ctrl+alt+F1-4 upon full bootup into Ubuntu, but it requires user's[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]credentials first, which no longer seem matching.

[/FONT][/COLOR]And after exiting the GRUB console Ubuntu recovery mode to resume normal Ubuntu boot,
it boots into Windows. Maybe I can try updating GRUB or Ubuntu in recovery mode?

[COLOR=#222222][FONT=Verdana]How is it possible to change user/root password in GRUB console?[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]What are other ways to change the password to login into Ubuntu?[/FONT][/COLOR]

---

### Post by MAFoElffen on 2022-03-20
In Grub CLI, you are running the grub environment, which at that level has no connection to any OS... (It is used as a boot manager to boot other OS'es.) There is no Linux kernel running yet, so you have no access or ability from there to change any user passwords for an OS (yet).

If you went into Advanced > Recovery ... Then it would boot a Linux Kernel in recovery mode. Which then you would use mount filesystem with networking... The Use drop to Root prompt... whic from there, you would be root, in that Linux OS, where you can issue that command to change a user password.

---

### Post by westie457 on 2022-03-20
This old page is still relevant for a forgotten password. [https://www.psychocats.net/ubuntu/resetpassword](https://www.psychocats.net/ubuntu/resetpassword)

---

