---
title: "can I boot win11, ubuntu 20.04 and ubuntu 22.04"
date: 2023-09-26
forum: General Help
---

### Post by tkhobby on 2023-09-26
I have dual boot set up for win11 and Ubuntu 20.04. I now need to also be able to boot Ubuntu 22.04.
When I use the bootable Ubuntu 20.04 usb I don't get the option of booting alongside .... the only option is to erase 20.04 and re-install it. I am using a Ubuntu 22.04 usb with yelly fish screen and all.
I have tried to disc partition free space but had same results.

Can I boot win11 or Ubuntu 20.04 or 22.04?

---

### Post by guiverc on 2023-09-26
The system I'm using now has 3 OSes windows 11, Ubuntu *development* and Ubuntu *jammy* (LTS). I have 6 systems with like setups (*different OSes/releases*).

It's likely your system has an issue such as windows *fastboot*, *hibernate* enabled (*thus that disk maybe ignored, and you may only allowed to install to a different drive if you have one, or part of that disk cannot be changed*).

You weren't specific as to which Ubuntu products you're asking about, as Server & Desktop have different installers; I've assumed Desktop here, but it's best if you're specific.

Also if you're using Secure-EFI, check you're using an upgraded system to install (*and not an older ISO with revoked keys*), as again you weren't specific (ie. 22.04.3 and/or 20.04.6); though if not using Secure-Boot this shouldn't be an issue. Usually when *revoked* keys are used, systems won't boot, but some machine *firmware* can give *deceptive *error messages/behavior.

---

### Post by Rubi1200 on 2023-09-26
It's not 100% clear to me how you are going about this, but here is something to think about.

Step 1. always, always backup everything before changing partitions, adding new installs etc. etc.

Step 2. boot the laptop using a liveUSB, does not matter which version, and use GParted to set up your partitions as you want them. 

When installing multiple OSes to the same drive I always first map it out on paper. May seem old-fashioned, but I have never, ever run into problems during partitioning and installing. Why? Because everything was planned out. I knew how many partitions to create, their sizes, filesystems etc. etc.

Step 3. boot the laptop again but this time with the version you want to install. When it comes to the partition screen, choose manual partitioning (may be also called Something else) and select the partition you want to install to. 

Use the Change option and set it to use the / root partition unless you plan on separate root and home (which can be done but makes things slightly more complicated). You can also choose to format the partition. Once done, click Next and read the warnings before continuing.

Step 4. you should now be on the way to your new install of whatever version you have chosen

If you run into any problems, ask here first.

---

### Post by dragonfly41 on 2023-09-26
[COLOR=#000000]> When I use the bootable Ubuntu 20.04 usb I don't get the option of booting alongside .... the only option is to erase 20.04 and re-install it. 

Are you sure you don't see the LiveUSB option "Try something else". From my memory.[/COLOR]

---

### Post by MAFoElffen on 2023-09-26
Run the [UbuntuForums 'system-info' Script]("https://github.com/UbuntuForums/system-info") from your Ubuntu 22.04 system. Post the URL of where it uploads to. That will tell us what the hardware is, and how the storage is presently allocated...

If not, then stop here, and wait for instructions on what to do based on us reading that 'system-info' report...

If you already have a plan, and have prepped the storage by making run for the Installation (important), then boot the 20.04 Desktop installer media. When you get to the Grub2 menu, select Ubuntu. When it boots and gets to the first Panel, select "Try". When the desktop starts, press <Cntrl><L> to open a graphical terminal session. 

Do
```

sudo ubiquity -b

```
That will open the installer in a mode that will skip the installation of Grub2. This has to by done from a terminal session to work this way. 

Why skip installing Grub2? Because it already has the newest version of it installed on your Ubuntu 22.04 install, and you can maintain it in one place (your 22.04 install) to avoid problems caused by conflicting updates between the two. That sometimes happens.

Right before the installer gets to the partitioner, there is a screen that is for configuring the installation type. Select the box that says "Something else", the select Continue.

(If you plan includes creating a separate home, adjust the following directions and create it second... that way you can set the size for the OS partition, and leave what is left over for your home partition...)

Once inside the partitioner, select the "free space" you created for the installation. Select the "+" control. In the window that appears, set If you are doing a separate home, set the size of the root partition to greater than 30GB. Select the dropdown box beside "Use as:" and set it to "/"

If you are creating a separate home, then press the "+" control again, leave the size at what it say (full), the set the "Use as" to /home

If you are through now, press "Continue"... Continue the install.

When through, reboot to your 22.04 system.

Edit /etc/default/grub with elevated permissions. Uncoment the GRUB_OSPROBER_DISABLE=false line, save and exit.

Do 
```

update-grub

```
Wtach the output to ensure it finds the new 20.04 installation and adds it to the Grub2 menu... Done.

---

