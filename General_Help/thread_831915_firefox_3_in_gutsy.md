---
title: "firefox 3 in gutsy"
date: 2008-06-17
forum: General Help
---

### Post by williumbillium on 2008-06-17
Simple question:

Is there a recommended way to install Firefox 3 in Gutsy?

(I can't upgrade to Hardy because of a bug)

---

### Post by ibuclaw on 2008-06-17
There is a technique called apt-pinning that can let you install updates from newer repositories without upgrading your entire system.

You can find out a bit about pinning [here]("http://wiki.debian.org/AptPinning").

But the way you'd set it up would be:

1) Create your preferences files
```

sudo touch /var/lib/synaptic/preferences
sudo ln -s /var/lib/synaptic/preferences /etc/apt/preferences

```
2) Open the file and pin the Gutsy repositories to have full priority over everything else.
```
sudo gedit /etc/apt/preferences
```
Then paste this into the file
```

Package: *
Pin: release a=gutsy-security
Pin-Priority: 1000

Package: *
Pin: release a=gutsy-updates
Pin-Priority: 900

Package: *
Pin: release a=gutsy
Pin-Priority: 800

```
And save/quit.

3) Create an isolated Hardy Sources File in your /etc/apt/sources.list.d folder.
```
echo "deb http://archive.ubuntu.com/ubuntu/ hardy main
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main
deb http://archive.ubuntu.com/ubuntu/ hardy-proposed main" | sudo tee -a /etc/apt/sources.list.d/hardy.list
```

Then run
```
sudo apt-get update
```
And when you type in **apt-get upgrade** it should ask you for no upgrades whatsoever!

4) Finally, to install Firefox 3, run this command.
```
sudo apt-get install -t hardy-proposed firefox-3.0
```
If all goes well, that should work pretty fine.

To remove the repository and preferences file, run this command
```
sudo rm /etc/apt/preferences /etc/apt/sources.list.d/hardy.list /var/lib/synaptic/preferences
```
Followed by **sudo apt-get update** again.

Regards
Iain

---

