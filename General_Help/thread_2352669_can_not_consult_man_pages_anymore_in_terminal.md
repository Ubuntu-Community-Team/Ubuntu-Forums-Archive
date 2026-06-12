---
title: "can not consult man pages anymore in terminal"
date: 2017-02-14
forum: General Help
---

### Post by Hankbonk on 2017-02-14
[IMG]file:///home/henk/Pictures/does_not_display_manual_pages.png[/IMG]

---

### Post by howefield on 2017-02-14
Do the pages exist on your system ?

For instance, for the "ls" man page..

```
man --where --all ls
/usr/share/man/man1/ls.1.gz
```

PS. Terminal input and output is best pasted here between [noparse]```

```[/noparse] tags rather than loading a hard to read image. Of course, there are other reasons such as you found out.. :)

---

### Post by sisco311 on 2017-02-14
What is the output of:
```
update-alternatives --display pager
```
```
echo $PAGER
echo $MANPAGER
```
and
```
whereis pager
```
oh, and
```
alias man
```

There is no manual entry for the `cd' command because it's a shell builtin ;). You have to check out the man page of your shell (bash, dash, zsh...) for its documentation.

---

### Post by Hankbonk on 2017-02-14
```
[COLOR=#000000][FONT=&amp]update-alternatives --display pager[/FONT][/COLOR]
```

gives 
```
pager - auto mode  link best version is /bin/less
  link currently points to /bin/less
  link pager is /usr/bin/pager
  slave pager.1.gz is /usr/share/man/man1/pager.1.gz
/bin/less - priority 77
  slave pager.1.gz: /usr/share/man/man1/less.1.gz
/bin/more - priority 50
  slave pager.1.gz: /usr/share/man/man1/more.1.gz
/usr/bin/pg - priority 10
  slave pager.1.gz: /usr/share/man/man1/pg.1.gz
```

```
man --where --all ls
/usr/share/man/man1/ls.1.gz
```

```
 whereis pager
pager: /usr/bin/pager /usr/share/man/man1/pager.1.gz
```

```
echo $PAGER


```

which is just a blank line

and finally 

```
echo $MANPAGER


```
which is just a blank line too

---

### Post by sisco311 on 2017-02-14
Everything looks good. Unless I miss something. The output pager (the program which should output the man pages) is less.

Can you use it?
```
less path/to/text.file
```

If not, try to reinstall it:
```
sudo apt --reinstall install less
```

---

### Post by Hankbonk on 2017-02-14
"less" of an existing file gives nothing !
Then I tried "more" of the same file, and that was printed

then I did the following :

```
henk@~$ sudo apt --reinstall install less[sudo] password for henk: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of less is not possible, it cannot be downloaded.
```

---

### Post by sisco311 on 2017-02-14
We are getting closer. :)

Try to do a
```
sudo apt update
```then reinstall less.

---

### Post by Hankbonk on 2017-02-14
I did the ```
sudo apt update
```

and then :

```
henk@~$ sudo apt --reinstall install less[sudo] password for henk: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of less is not possible, it cannot be downloaded.
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-59 linux-headers-4.4.0-59-generic
  linux-image-4.4.0-59-generic linux-image-extra-4.4.0-59-generic
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
henk@~$ 
```

---

### Post by vasa1 on 2017-02-14
> **Hankbonk said:**
> ...
and finally 
```
echo $MANPAGER
```
which is just a blank line too
Here, the response for me is```
/usr/bin/less -r -X -is
```
BTW, does```
info ls
```
work for you?
[hr][/hr]
Try to rebuild the man database:```
sudo mandb
```which seems to be what worked according to [https://bbs.archlinux.org/viewtopic.php?pid=1268028#p1268028](https://bbs.archlinux.org/viewtopic.php?pid=1268028#p1268028). In any case, do go through that thread for other suggestions.

---

### Post by Hankbonk on 2017-02-14
@ vasa1

what I did and get is
```
henk@~$ echo $MANPAGER

henk@~$ /usr/bin/less -r -X -is
henk@~$ 

```
and
```
[FONT=Ubuntu Mono][COLOR=#000000]sudo mandb[/COLOR][/FONT]
```
gives a lot of lines, with on the end :
```
0 man subdirectories contained newer manual pages.0 manual pages were added.
0 stray cats were added.
228 old database entries were purged.
```

in answer to your BTW :
```
henk@~$ info ls
henk@~$ 
```

According to me, it is the "less"-command that does not work anymore

---

### Post by vasa1 on 2017-02-14
Do you use the terminal for most of your work? Since, from your title, less worked before, can you look at your ~/.bash_history for clues?

And what do```
apt list --installed | grep -E '^less'
```
and```
less -V
```show?

---

### Post by Hankbonk on 2017-02-15
last entries (a lot) in ~/bash_history are :
```
mkdir --helpman ls
man cd
man man
cd
cd ..
man ls
exit
man ls
exit
man ls
sudo bash
man man
man
man cd
man ls
man
man cd
man ls
man --where --all ls
update-alternatives --display pager
whereis pager
echo $PAGER
echo $MANPAGER
alias man
man man
ls -l
less cnt.txt 
sudo apt --reinstall install less
less cnt.txt 
more cnt.txt 
sudo apt update
less cnt.txt 
sudo apt --reinstall install less
sudo apt autoremove
less
more
exit



```


```
henk@/usr/bin$ apt list --installed | grep -E '^less'

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


less/now 481-2.1ubuntu0.1 i386 [installed,local]
henk@/usr/bin$
```

```
henk@~$ less -V
henk@~$ less -v
henk@~$
```

---

### Post by vasa1 on 2017-02-15
> **Hankbonk said:**
> ...


```
henk@/usr/bin$ apt list --installed | grep -E '^less'

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


less/now 481-2.1ubuntu0.1 i386 [installed,local]
henk@/usr/bin$
```

...
I don't see "[installed,_local_]"; I see just ```
less/xenial-updates,now 481-2.1ubuntu0.1 amd64 [installed]
```
So there seems to be something out of the way there :(

Let us see the output of```
apt list --installed | grep -E ',local\]$'
```
and, in case, you haven't already provided this:```
which less
```

Also, post the output of```
echo -e "Version $(lsb_release -a)
Session: $DESKTOP_SESSION
Desktop: $XDG_CURRENT_DESKTOP
Window Manager: $(wmctrl -m | awk '/Name:/{print $2}')
Kernel info: $(uname -a)"
```

---

### Post by Hankbonk on 2017-02-20
@ vasa

I did the things you asked
```
henk@~$ apt list --installed | grep -E ',local\]$'

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


abiword/now 3.0.1-6ubuntu0.16.04.1 i386 [installed,local]
abiword-common/now 3.0.1-6ubuntu0.16.04.1 all [installed,local]
accountsservice/now 0.6.40-2ubuntu11.2 i386 [installed,local]
adwaita-icon-theme/now 3.18.0-2ubuntu3.1 all [installed,local]
adwaita-icon-theme-full/now 3.18.0-2ubuntu3.1 all [installed,local]
apparmor/now 2.10.95-0ubuntu2.2 i386 [installed,local]
audacious-plugins/now 3.6.2-2ubuntu1 i386 [installed,local]
audacious-plugins-data/now 3.6.2-2ubuntu1 all [installed,local]
base-files/now 9.4ubuntu4.2 i386 [installed,local]
bash/now 4.3-14ubuntu1.1 i386 [installed,local]
bash-completion/now 1:2.1-4.2ubuntu1.1 all [installed,local]
bsdutils/now 1:2.27.1-6ubuntu3.1 i386 [installed,local]
command-not-found/now 0.3ubuntu16.04.2 all [installed,local]
command-not-found-data/now 0.3ubuntu16.04.2 i386 [installed,local]
console-setup/now 1.108ubuntu15.2 all [installed,local]
console-setup-linux/now 1.108ubuntu15.2 all [installed,local]
dh-python/now 2.20151103ubuntu1.1 all [installed,local]
dmidecode/now 3.0-2ubuntu0.1 i386 [installed,local]
dpkg/now 1.18.4ubuntu1.1 i386 [installed,local]
fonts-noto-cjk/now 1:1.004+repack2-1~ubuntu1 all [installed,local]
fuse/now 2.9.4-1ubuntu3.1 i386 [installed,local]
gir1.2-gtk-3.0/now 3.18.9-1ubuntu3.1 i386 [installed,local]
gir1.2-packagekitglib-1.0/now 0.8.17-4ubuntu6~gcc5.4ubuntu1.1 i386 [installed,local]
gir1.2-unity-5.0/now 7.1.4+16.04.20160701-0ubuntu1 i386 [installed,local]
glib-networking/now 2.48.2-1~ubuntu16.04.1 i386 [installed,local]
glib-networking-common/now 2.48.2-1~ubuntu16.04.1 all [installed,local]
glib-networking-services/now 2.48.2-1~ubuntu16.04.1 i386 [installed,local]
grep/now 2.25-1~16.04.1 i386 [installed,local]
grub-common/now 2.02~beta2-36ubuntu3.2 i386 [installed,local]
grub-pc/now 2.02~beta2-36ubuntu3.2 i386 [installed,local]
grub-pc-bin/now 2.02~beta2-36ubuntu3.2 i386 [installed,local]
grub2-common/now 2.02~beta2-36ubuntu3.2 i386 [installed,local]
gstreamer1.0-libav/now 1.8.2-1~ubuntu1 i386 [installed,local]
gstreamer1.0-plugins-ugly/now 1.8.2-1ubuntu0.1 i386 [installed,local]
gstreamer1.0-plugins-ugly-amr/now 1.8.2-1ubuntu0.1 i386 [installed,local]
gtk2-engines-murrine/now 0.98.2-0ubuntu2.2 i386 [installed,local]
gvfs/now 1.28.2-1ubuntu1~16.04.1 i386 [installed,local]
gvfs-backends/now 1.28.2-1ubuntu1~16.04.1 i386 [installed,local]
gvfs-common/now 1.28.2-1ubuntu1~16.04.1 all [installed,local]
gvfs-daemons/now 1.28.2-1ubuntu1~16.04.1 i386 [installed,local]
gvfs-fuse/now 1.28.2-1ubuntu1~16.04.1 i386 [installed,local]
gvfs-libs/now 1.28.2-1ubuntu1~16.04.1 i386 [installed,local]
hunspell-en-au/now 1:5.1.0-1ubuntu2.2 all [installed,local]
hunspell-en-ca/now 1:5.1.0-1ubuntu2.2 all [installed,local]
hunspell-en-gb/now 1:5.1.0-1ubuntu2.2 all [installed,local]
hunspell-en-za/now 1:5.1.0-1ubuntu2.2 all [installed,local]
hunspell-nl/now 1:5.1.0-1ubuntu2.2 all [installed,local]
init/now 1.29ubuntu2 i386 [installed,local]
init-system-helpers/now 1.29ubuntu2 all [installed,local]
initramfs-tools/now 0.122ubuntu8.1 all [installed,local]
initramfs-tools-bin/now 0.122ubuntu8.1 i386 [installed,local]
initramfs-tools-core/now 0.122ubuntu8.1 all [installed,local]
isc-dhcp-client/now 4.3.3-5ubuntu12.1 i386 [installed,local]
isc-dhcp-common/now 4.3.3-5ubuntu12.1 i386 [installed,local]
keyboard-configuration/now 1.108ubuntu15.2 all [installed,local]
klibc-utils/now 2.0.4-8ubuntu1.16.04.1 i386 [installed,local]
language-pack-de/now 1:16.04+20160627 all [installed,local]
language-pack-de-base/now 1:16.04+20160627 all [installed,local]
language-pack-en/now 1:16.04+20160627 all [installed,local]
language-pack-en-base/now 1:16.04+20160627 all [installed,local]
language-pack-fr/now 1:16.04+20160627 all [installed,local]
language-pack-fr-base/now 1:16.04+20160627 all [installed,local]
language-pack-gnome-de/now 1:16.04+20160627 all [installed,local]
language-pack-gnome-de-base/now 1:16.04+20160627 all [installed,local]
language-pack-gnome-en/now 1:16.04+20160627 all [installed,local]
language-pack-gnome-en-base/now 1:16.04+20160627 all [installed,local]
language-pack-gnome-fr/now 1:16.04+20160627 all [installed,local]
language-pack-gnome-fr-base/now 1:16.04+20160627 all [installed,local]
language-pack-gnome-nl/now 1:16.04+20160627 all [installed,local]
language-pack-gnome-nl-base/now 1:16.04+20160627 all [installed,local]
language-pack-nl/now 1:16.04+20160627 all [installed,local]
language-pack-nl-base/now 1:16.04+20160627 all [installed,local]
language-selector-common/now 0.165.4 all [installed,local]
language-selector-gnome/now 0.165.4 all [installed,local]
less/now 481-2.1ubuntu0.1 i386 [installed,local]
libabiword-3.0/now 3.0.1-6ubuntu0.16.04.1 i386 [installed,local]
libaccountsservice0/now 0.6.40-2ubuntu11.2 i386 [installed,local]
libapparmor-perl/now 2.10.95-0ubuntu2.2 i386 [installed,local]
libapparmor1/now 2.10.95-0ubuntu2.2 i386 [installed,local]
libblkid1/now 2.27.1-6ubuntu3.1 i386 [installed,local]
libboost-filesystem1.58.0/now 1.58.0+dfsg-5ubuntu3.1 i386 [installed,local]
libboost-system1.58.0/now 1.58.0+dfsg-5ubuntu3.1 i386 [installed,local]
libcupsfilters1/now 1.8.3-2ubuntu3.1 i386 [installed,local]
libdrm-amdgpu1/now 2.4.67-1ubuntu0.16.04.2 i386 [installed,local]
libdrm-intel1/now 2.4.67-1ubuntu0.16.04.2 i386 [installed,local]
libdrm-nouveau2/now 2.4.67-1ubuntu0.16.04.2 i386 [installed,local]
libdrm-radeon1/now 2.4.67-1ubuntu0.16.04.2 i386 [installed,local]
libdrm2/now 2.4.67-1ubuntu0.16.04.2 i386 [installed,local]
libdvdcss-dev/now 1.4.0-1~local i386 [installed,local]
libdvdcss2/now 1.4.0-1~local i386 [installed,local]
libegl1-mesa/now 11.2.0-1ubuntu2.2 i386 [installed,local]
libfdisk1/now 2.27.1-6ubuntu3.1 i386 [installed,local]
libfm-data/now 1.2.4-1ubuntu1.1 all [installed,local]
libfm-extra4/now 1.2.4-1ubuntu1.1 i386 [installed,local]
libfm-gtk-data/now 1.2.4-1ubuntu1.1 all [installed,local]
libfm-gtk4/now 1.2.4-1ubuntu1.1 i386 [installed,local]
libfm-modules/now 1.2.4-1ubuntu1.1 i386 [installed,local]
libfm4/now 1.2.4-1ubuntu1.1 i386 [installed,local]
libfuse2/now 2.9.4-1ubuntu3.1 i386 [installed,local]
libgbm1/now 11.2.0-1ubuntu2.2 i386 [installed,local]
libgif7/now 5.1.4-0.3~16.04 i386 [installed,local]
libgl1-mesa-dri/now 11.2.0-1ubuntu2.2 i386 [installed,local]
libgl1-mesa-glx/now 11.2.0-1ubuntu2.2 i386 [installed,local]
libglapi-mesa/now 11.2.0-1ubuntu2.2 i386 [installed,local]
libglib2.0-0/now 2.48.1-1~ubuntu16.04.1 i386 [installed,local]
libglib2.0-bin/now 2.48.1-1~ubuntu16.04.1 i386 [installed,local]
libglib2.0-data/now 2.48.1-1~ubuntu16.04.1 all [installed,local]
libgstreamer1.0-0/now 1.8.2-1~ubuntu1 i386 [installed,local]
libgtk-3-0/now 3.18.9-1ubuntu3.1 i386 [installed,local]
libgtk-3-bin/now 3.18.9-1ubuntu3.1 i386 [installed,local]
libgtk-3-common/now 3.18.9-1ubuntu3.1 all [installed,local]
libklibc/now 2.0.4-8ubuntu1.16.04.1 i386 [installed,local]
libldap-2.4-2/now 2.4.42+dfsg-2ubuntu3.1 i386 [installed,local]
liblightdm-gobject-1-0/now 1.18.2-0ubuntu2 i386 [installed,local]
libllvm3.8/now 1:3.8-2ubuntu4 i386 [installed,local]
libmount1/now 2.27.1-6ubuntu3.1 i386 [installed,local]
libnautilus-extension1a/now 1:3.18.4.is.3.14.3-0ubuntu5 i386 [installed,local]
libnm0/now 1.2.0-0ubuntu0.16.04.3 i386 [installed,local]
libnma-common/now 1.2.0-0ubuntu0.16.04.4 all [installed,local]
libnma0/now 1.2.0-0ubuntu0.16.04.4 i386 [installed,local]
libosmesa6/now 11.2.0-1ubuntu2.2 i386 [installed,local]
libp11-kit0/now 0.23.2-5~ubuntu16.04.1 i386 [installed,local]
libpackagekit-glib2-16/now 0.8.17-4ubuntu6~gcc5.4ubuntu1.1 i386 [installed,local]
libplymouth4/now 0.9.2-3ubuntu13.1 i386 [installed,local]
libpoppler-glib8/now 0.41.0-0ubuntu1.1 i386 [installed,local]
libpoppler58/now 0.41.0-0ubuntu1.1 i386 [installed,local]
libsmartcols1/now 2.27.1-6ubuntu3.1 i386 [installed,local]
libunity-protocol-private0/now 7.1.4+16.04.20160701-0ubuntu1 i386 [installed,local]
libunity-scopes-json-def-desktop/now 7.1.4+16.04.20160701-0ubuntu1 all [installed,local]
libunity9/now 7.1.4+16.04.20160701-0ubuntu1 i386 [installed,local]
libupower-glib3/now 0.99.4-2ubuntu0.3 i386 [installed,local]
libuuid1/now 2.27.1-6ubuntu3.1 i386 [installed,local]
libwayland-egl1-mesa/now 11.2.0-1ubuntu2.2 i386 [installed,local]
libwhoopsie0/now 0.2.52.1 i386 [installed,local]
libwnck-common/now 1:2.30.7-5ubuntu1.1 all [installed,local]
libwnck22/now 1:2.30.7-5ubuntu1.1 i386 [installed,local]
libxatracker2/now 11.2.0-1ubuntu2.2 i386 [installed,local]
lightdm/now 1.18.2-0ubuntu2 i386 [installed,local]
lsb-base/now 9.20160110ubuntu0.2 all [installed,local]
lsb-release/now 9.20160110ubuntu0.2 all [installed,local]
lshw/now 02.17-1.1ubuntu3.2 i386 [installed,local]
lubuntu-artwork/now 0.61.1 all [installed,local]
lubuntu-artwork-16-04/now 0.61.1 all [installed,local]
lubuntu-core/now 0.65.1 i386 [installed,local]
lubuntu-icon-theme/now 0.61.1 all [installed,local]
lubuntu-lxpanel-icons/now 0.61.1 all [installed,local]
lxshortcut/now 1.2.4-1ubuntu1.1 i386 [installed,local]
mount/now 2.27.1-6ubuntu3.1 i386 [installed,local]
mplayer/now 2:1.2.1-1ubuntu1 i386 [installed,local]
mtools/now 4.0.18-2ubuntu0.16.04 i386 [installed,local]
mtr-tiny/now 0.86-1ubuntu0.1 i386 [installed,local]
network-manager/now 1.2.0-0ubuntu0.16.04.3 i386 [installed,local]
network-manager-gnome/now 1.2.0-0ubuntu0.16.04.4 i386 [installed,local]
p11-kit/now 0.23.2-5~ubuntu16.04.1 i386 [installed,local]
p11-kit-modules/now 0.23.2-5~ubuntu16.04.1 i386 [installed,local]
plymouth/now 0.9.2-3ubuntu13.1 i386 [installed,local]
plymouth-label/now 0.9.2-3ubuntu13.1 i386 [installed,local]
plymouth-theme-lubuntu-logo/now 0.61.1 all [installed,local]
plymouth-theme-lubuntu-text/now 0.61.1 all [installed,local]
plymouth-theme-ubuntu-text/now 0.9.2-3ubuntu13.1 i386 [installed,local]
python3-commandnotfound/now 0.3ubuntu16.04.2 all [installed,local]
python3-distupgrade/now 1:16.04.16 all [installed,local]
python3-software-properties/now 0.96.20.4 all [installed,local]
python3-urllib3/now 1.13.1-2ubuntu0.16.04.1 all [installed,local]
shared-mime-info/now 1.5-2ubuntu0.1 i386 [installed,local]
software-properties-common/now 0.96.20.4 all [installed,local]
software-properties-gtk/now 0.96.20.4 all [installed,local]
sudo/now 1.8.16-0ubuntu1.2 i386 [installed,local]
ubuntu-drivers-common/now 1:0.4.17.1 i386 [installed,local]
ubuntu-mono/now 14.04+16.04.20160804-0ubuntu1 all [installed,local]
ubuntu-release-upgrader-core/now 1:16.04.16 all [installed,local]
ubuntu-release-upgrader-gtk/now 1:16.04.16 all [installed,local]
update-notifier/now 3.168.1 i386 [installed,local]
update-notifier-common/now 3.168.1 all [installed,local]
upower/now 0.99.4-2ubuntu0.3 i386 [installed,local]
util-linux/now 2.27.1-6ubuntu3.1 i386 [installed,local]
uuid-runtime/now 2.27.1-6ubuntu3.1 i386 [installed,local]
whoopsie/now 0.2.52.1 i386 [installed,local]
xinit/now 1.3.4-3ubuntu0.1 i386 [installed,local]
xserver-common/now 2:1.18.3-1ubuntu2.3 all [installed,local]
xserver-xorg-core/now 2:1.18.3-1ubuntu2.3 i386 [installed,local]
xserver-xorg-video-intel/now 2:2.99.917+git20160325-1ubuntu1.1 i386 [installed,l
```

which less gives```
/usr/bin/less
```

and```
[COLOR=#000000][FONT=&quot]echo -e "Version $(lsb_release -a)[/FONT][/COLOR]Session: $DESKTOP_SESSION
Desktop: $XDG_CURRENT_DESKTOP
Window Manager: $(wmctrl -m | awk '/Name:/{print $2}') [COLOR=#000000][FONT=&quot]Kernel info: $(uname -a)"[/FONT][/COLOR]
```
gives 

```
No LSB modules are available.The program 'wmctrl' is currently not installed. You can install it by typing:
sudo apt install wmctrl
Version Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial
Session: Lubuntu
Desktop: LXDE
Window Manager: 
Kernel info: Linux henk-HP-Compaq-dc7700-Small-Form-Factor 4.4.0-62-generic #83-Ubuntu SMP Wed Jan 18 14:09:55 UTC 2017 i686 i686 i686 GNU/Linux



```

---

### Post by vasa1 on 2017-02-20
I don't understand why so many packages are shown as "installed, local" as seen by the output of```
henk@~$ apt list --installed | grep -E ',local\]$'
```
I can't find anything amiss in the other information.

---

### Post by Hankbonk on 2017-07-15
I just checked this thread only now, months after the last post : I don't have anymore problems with less nor man pages .
I mark will mark the thread as solved now, thanks for your help .

---

