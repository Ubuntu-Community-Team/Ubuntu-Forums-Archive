---
title: "error occured when installing exfat"
date: 2014-08-05
forum: General Help
---

### Post by kousuke.ariga on 2014-08-05
Hello, I'm a new user of ubuntu 12.04.
I was trying to read photo data from a 128GB SD memory card (Lexar), but I got this message.
[FONT=Verdana]    Error mounting: mount: unknown filesystem type 'exfat'
[/FONT]After some search ([http://superuser.com/questions/436368/how-to-open-exfat-ssd-in-ubuntu-12-04](http://superuser.com/questions/436368/how-to-open-exfat-ssd-in-ubuntu-12-04)), it turned out that I needed to add a PPA and install some packages like below.
    1. sudo add-apt-repository ppa:relan/exfat
    2. sudo apt-get update && sudo apt-get install fuse-exfat exfat-utils
The problem is, after I ran the first line, I got this message. 
[FONT=Verdana]    gpg: keyring `/tmp/tmpsUFDSG/secring.gpg' created[/FONT]
[FONT=Verdana]    gpg: keyring `/tmp/tmpsUFDSG/pubring.gpg' created[/FONT]
[FONT=Verdana]    gpg: "tag:launchpad.net:2008:redacted" not a key ID: skipping recv failed[/FONT]

Sicne I didn't understand the message, I ignored and proceeded to the second line. Then I got this message.
[FONT=Verdana]    ~~~ long line ~~~
    Reading package lists... Done
    W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not[/FONT][FONT=Verdana] [/FONT][FONT=Verdana]available: NO_PUBKEY 4DF9B28CA252A784
[/FONT][FONT=Verdana]    [/FONT][FONT=Verdana]Reading package lists... Done
[/FONT][FONT=Verdana]    [/FONT][FONT=Verdana]Building dependency tree       
[/FONT][FONT=Verdana]    [/FONT][FONT=Verdana]Reading state information... Done
[/FONT][FONT=Verdana]    [/FONT][FONT=Verdana]E: Unable to locate package fuse-exfat-utils
[/FONT]
I know something is wrong, but I can't figure out what I can do for it. Could anyone help me to read the SD card? Thank you very much for any help.

---

### Post by crobicha on 2014-09-13
I had the same issue using a Lexar sdcard (from a gopro camera), also using Ubuntu 12.04.

This thread ended up being helpful: [http://askubuntu.com/questions/370398/how-to-get-a-drive-formatted-with-exfat-working](http://askubuntu.com/questions/370398/how-to-get-a-drive-formatted-with-exfat-working)

I was also installing and updating packages as I attempted to upgrade, so that may have helped as well.

---

