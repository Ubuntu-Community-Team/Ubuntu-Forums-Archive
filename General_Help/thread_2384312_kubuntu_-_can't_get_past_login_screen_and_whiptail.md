---
title: "kubuntu - can't get past login screen and whiptail error in recovery"
date: 2018-02-05
forum: General Help
---

### Post by oother on 2018-02-05
I was working fine earlier today in kubuntu zesty 17.04. I tried to do a restart and then couldn't get past the login screen. It accepted the password but just brought the login screen up again.

I tried them to go into recovery mode and see if any errors appeared. The shell loaded but the filesystem was read  only. First it appeared there was an error with mounting the encrypted swap partition. so I disabled mounting that temporarily but it didn't fix the issue. I loaded up a live CD and ran fsck too. No joy.

There is another error in the recovery shell, "/usr/bin/env: 'node': no such file or directory". Then on the next line "couldn't find whiptail, starting root shell instead of recovery menu'.

When I try sudo apt-get install whiptail it says it's already installed.

Thanks - now I've also got to post about a phone problem which seemed to happen strange simultaneously... Hopefully not related, certainly there's no reason for me to think there's something connecting them!

---

### Post by oother on 2018-02-06
Managed to solve it: 


1) I'd forgotten that I can enter command line from the login screen with CTRL +  ALT + F2.


2) I didn't understand the support for zesty had expired, I did a dist upgrade and everything worked fine after that. I must have accidentally turned off notifications that zesty had run out as I didn't see a message about it...

---

