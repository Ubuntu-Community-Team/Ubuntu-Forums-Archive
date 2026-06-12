---
title: "Outdated update information [Ubuntu][15.10]"
date: 2016-02-01
forum: General Help
---

### Post by damian19 on 2016-02-01
I posted this on stack overflow as well.


[COLOR=#222426][FONT=Arial]I am getting an "Outdated update information" warning on the top right corner of my screen.[/FONT][/COLOR]
[COLOR=#222426][FONT=Arial]I try to update using the terminal and I get the warning:[/FONT][/COLOR]
W: Failed to fetch [http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu/dists/wily/main/binary-amd64/Packages](http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu/dists/wily/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
[COLOR=#222426][FONT=Arial]Here is how it happened: I tried installing a sound recorder, which was unsuccesful(or succesdul, I do not know) for reasons I do not know. Then I proceeded to uninstall a gnome sound recorder(which seemed to be the one I installed) by using[/FONT][/COLOR]
sudo apt-get purge gnome-media
sudo apt-get autoremove
[COLOR=#222426][FONT=Arial]The warning was supressed for a little while but appeared again. Is there any easy way to fix this?[/FONT][/COLOR]
[COLOR=#222426][FONT=Arial]Thank you in advance.[/FONT][/COLOR]

---

### Post by Vladlenin5000 on 2016-02-01
Just remove those two PPA which, BTW, don't exist.

---

### Post by damian19 on 2016-02-01
I try that but it says that they don't exist
edit: i tried to update again and get the same error as above, but now the warning on the top right is gone.

---

### Post by kansasnoob on 2016-02-01
> **Vladlenin5000 said:**
> Just remove those two PPA which, BTW, don't exist.

+1!

Read that PPA page again:

[https://launchpad.net/~osmoma/+archive/ubuntu/audio-recorder](https://launchpad.net/~osmoma/+archive/ubuntu/audio-recorder)

It says:

> This PPA will not be updated after April 2015.
The ultimate version of audio-recorder in this repository is v1.6-3 for Ubuntu 15.04 (Vivid Vervet). This private PPA will be closed.

Then it refers you to a newer PPA:

[https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa](https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa)

---

### Post by damian19 on 2016-02-01
So I can't simply remove the PPA, how can I fix the error?

---

### Post by Vladlenin5000 on 2016-02-01
Why can't you remove?
An easy (and graphical) way is System Settings > Software properties. You'll find the PPAs in the "other software" tab. Just select each one and press Remove (password required).

---

### Post by monkeybrain20122 on 2016-02-01
> **damian19 said:**
> I try that but it says that they don't exist
edit: i tried to update again and get the same error as above, but now the warning on the top right is gone.


What did you try??
It is an easy procedure as Vladlenin5000 said.

---

### Post by damian19 on 2016-02-01
I simply used:

sudo rm -r [name]
and it says it does not exist.
(I am not a Unix or Ubuntu expert)

---

### Post by Vladlenin5000 on 2016-02-01
You don't need to be an expert to follow the instructions I gave in post#6.

(And if you aren't an expert - by your own admission - then please don't use "expert" commands you don't understand. FYI, that command is for files).

---

### Post by damian19 on 2016-02-01
That fixes it, thank you.

---

