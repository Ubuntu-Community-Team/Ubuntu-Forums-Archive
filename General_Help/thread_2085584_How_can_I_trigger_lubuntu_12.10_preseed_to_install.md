---
title: "How can I trigger lubuntu 12.10 preseed to install the desktop?"
date: 2012-11-18
forum: General Help
---

### Post by Zack Perry on 2012-11-18
I have tried to install lubuntu 12.10 on an Acer Aspire One D257 netbook via CD, and I liked the result.  Since I have a few of such netbooks, so I created a preseed file to automate the installation.  The installation server that I use is cobbler 2.4.0 running also on a netbook which runs Scientific Linux 6.3.


The following are relevant d-i lines in my preseed file:


[FONT="Courier New"]# Setup the installation source
d-i mirror/country string manual
d-i mirror/http/hostname string $http_server:$http_port
d-i mirror/http/directory string $install_source_directory
d-i mirror/http/proxy string
# Components to use for loading installer components (optional).
d-i mirror/udeb/components multiselect main, restricted
[...]
# You can choose to install restricted and universe software, or to install
# software from the backports repository.
d-i apt-setup/restricted boolean true
d-i apt-setup/universe boolean true
d-i apt-setup/backports boolean true
[...]
# Select which update services to use; define the mirrors to be used.
# Values shown below are the normal defaults.
d-i apt-setup/services-select multiselect security
d-i apt-setup/security_host string security.ubuntu.com
d-i apt-setup/security_path string /ubuntu[/FONT]


The first time, I tried to PXE boot the test netbook, it came up with just a text login window. No graphical UI. So, I added in the following lines:


[FONT="Courier New"]d-i pkgsel/include string openssh-server \
    lubuntu-artwork \
    lubuntu-artwork-12-10 \
    lubuntu-default-settings \
    lubuntu-icon-theme \
    lubuntu-lxpanel-icons \
    lxmenu-data lxpanel \
    lxsession \
    lxsession-data
d-i pkgsel/language-pack-patterns string[/FONT]


into the preseed file, but now the debian-installer complains (Alt-F4):


[FONT="Courier New"][...] in-target: Package lubuntu-default-settings is not available, but is referred to by another package.
[...] in-target: This may mean that the package is missing, has been obsolted, or
[...] in-target: is only available from another source
[...] in-target: 
[...] in-target: E
[...] in-target: unable to locate package lubuntu-artwork
[...] in-target: E: Unable to locate package lubuntu-artwork-12-10
[...] in-target: E: Package 'lubuntu-default-settings' has no installation candidate
[...] in-target: E: Unable to locate package lubuntu-icon-theme
[...] in-target: E: Unable to locate package lubuntu-lxpanel-icons
[...] in-target: E: Unable to locate package lxmenu-data
[...] in-target: E: Unable to locate package lxpanel
[...] in-target: E: Unable to locate package lxsession
[...] in-target: E: Unable to locate package lxsession-data
[...] main-menu[417]: WARNING **: Configurating 'pkgsel' failed with error code 100
[...] main-menu[417]: WARNING **: Menu item 'pkgsel' failed.[/FONT]


But, when I double checked the loop mounted lubuntu-12.10-alternate-amd64.iso, all of them are available!

[FONT="Courier New"][root@cobbler l]# pwd
/mnt/pool/universe/l
[root@cobbler l]# ls
lame                 lubuntu-artwork           lxinput      lxsession
ldm-ubuntu-themes    lubuntu-default-settings  lxkeymap     lxshortcut
leafpad              lubuntu-meta              lxlauncher   lxtask
lightdm-gtk-greeter  lubuntu-software-center   lxmenu-data  lxterminal
linux-wlan-ng        lxappearance              lxpanel
loudmouth            lxappearance-obconf       lxrandr[/FONT]


I also enabled the universe in my preseed, IMHO.  So, why the debian-installer was complaining?  Is there a way that I can trigger the installation of the lubuntu desktop?  

Regards,

-- Zack

---

### Post by Zack Perry on 2012-11-30
I guess what I asked is a very unusual question :)

In the past couple of days, during my "spare time", I studied both Debian and Ubuntu documentation on repository structures, and learned about the significance of [FONT="Courier New"]Release[/FONT] and [FONT="Courier New"]Packages.gz[/FONT] files.  

But, the funny thing is, even after I made a copy of the loop mounted [FONT="Courier New"]lubuntu-12.10-alternate-x86_64.iso[/FONT] to the local HD, and then copied the [FONT="Courier New"]Release[/FONT] and [FONT="Courier New"]Packages.gz[/FONT] from [FONT="Courier New"]universe/binary-amd64[/FONT] to [FONT="Courier New"]universe/debian-installer/binary-amd64[/FONT], the [FONT="Courier New"]lubuntu-desktop[/FONT] meta package still failed to install.  The installation file didn't give me a clue either.  e.g. [FONT="Courier New"]grep[/FONT]ping through the [FONT="Courier New"]/var/log/installer/syslog[/FONT] for [FONT="Courier New"]lubuntu-desktop[/FONT] didn't return a hit.

I do know that the iso file contains enough files for a desktop graphical login UI. With the iso file burned to a CD, I tried it without even using a network (Ethernet cable pulled). The desktop UI came up fine after the installation.

So, at least for now, the mystery continues. 

Regards,

-- Zack

---

