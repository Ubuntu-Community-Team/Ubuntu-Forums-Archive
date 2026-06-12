---
title: "Reuse login password to run script to decrypt and mount home"
date: 2018-07-22
forum: General Help
---

### Post by brunoais on 2018-07-22
**[SIZE=5]Current situation[/SIZE]**

I have a PC which also doubles as a server. I may need to restart it remotely through internet.
Currently, I have the **/etc/crypttab** with (UUID replaced):
```
encryptedhome  UUID=something none  luks,noauto
```
Additionally, I have set **/etc/fstab** with(home directory replaced):
```
/dev/mapper/encryptedHome   /home/myhome/crypt    btrfs    user,noauto,x-systemd.automount
```
I already tried **crypttab** with the same content and then using fstab with:
```
/dev/mapper/encryptedHome   /home/myhome/crypt    btrfs    user,_netdev
```

Unfortunately, by the time fstab requests crypttab to mount and crypttab tries to request the password to the user, Xorg is starting and the request is suppressed in Xorg's tty (tty7) leading to no prompt and so I login to the user with the "fake" home that is there just to "jumpstart" the encrypted home.

**Note:** If I connect using ssh, when the shell starts, I coded so that I get the prompt and the mount on top of the "fake" home. So, I login and the file system is mounted as expected.

[SIZE=5]**Objective**[/SIZE]

I want, when I do a login using Xorg, a script is ran with the password used to login in the greeter, which then is used to decrypt the encrypted volume, runs the mount of the home directory and finally, finishes the login process by showing the desktop, ready to start working.


[SIZE=5]**Alternative objective**[/SIZE]

If the above doesn't work, then:
I want, when I do a login using Xorg or I am viewing the greeter, a script is ran, so a window appears requesting for the password, which then leads to the decryption (may not be through crypttab) and mounting of the encrypted home, then show the login so I can fill the login form.

[SIZE=5]**What I tried so far**[/SIZE]

Create an ./.xsession file with the prompt (this should have created a prompt right after login). For the prompt, I was using zenity. ```
zenity --password --title="Password for that drive" --display=:0
``` but nothing was displaying and Xorg would start.

Create a script that calls "cryptdisks_start encryptedhome" which is called either in ./.xsession or any other boot called files. It would cause the login to hang or it would be ignored (depending on the situation)


Thanks in advance....

---

