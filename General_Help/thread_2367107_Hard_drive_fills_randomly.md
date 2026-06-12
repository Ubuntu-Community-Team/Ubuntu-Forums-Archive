---
title: "Hard drive fills randomly"
date: 2017-07-26
forum: General Help
---

### Post by zerobytez on 2017-07-26
My curent 119GB linux pc's hard drive keeps filling up no matter what Ubuntu distro or version I use. It eventually just derps out and runs out of space. As an experiment, I installed fresh and just left it running, and it still did it. I have no idea what's causing it, as I've confirmed it is the ONLY linux that causes it (Tested with Debian 9 and 8, Kali linux, Arch, Parrot, Black Arch, Tinycore and core). I estimate I only have a single boot left before it fills up and the x-server is unstable to start, so please be careful with your answers as I then be unable to use GUI applications, and possibly have to reinstall and might not be able to provide correct information pass that.

Edit: There are no files Bigger then 2GB, and /var is 60kb in total.

---

### Post by mastablasta on 2017-07-26
boot with live session and check the logs in /var/log

what file system are you using? ext4? any particular setup or just default settings (overwrite everything) on install?

---

### Post by zerobytez on 2017-07-26
ext3 and 4 do it (but im using 4 right now), and I do default install every time

Logs are now 8.2MB, should i be looking for something in them?

---

### Post by zerobytez on 2017-07-26
Okay, using the Live CD i dug around, and I found something weird.
```
ubuntu@ubuntu:/media/ubuntu/03b10f71-a8bd-42d7-875c-1cc31f564122$ sudo du -sx * 2>/dev/null | sort -n
0    initrd.img
0    initrd.img.old
0    vmlinuz
0    vmlinuz.old
4    cdrom
4    lib64
4    media
4    mnt
4    opt
4    proc
4    snap
4    srv
4    sys
16    dev
48    root
52    tmp
88    run
3952    lib32
12656    sbin
12980    bin
13700    etc
161288    boot
467108    var
914580    lib
4490272    usr
98516484    home
ubuntu@ubuntu:/media/ubuntu/03b10f71-a8bd-42d7-875c-1cc31f564122$ cd home/
ubuntu@ubuntu:/media/ubuntu/03b10f71-a8bd-42d7-875c-1cc31f564122/home$ sudo du -sx * 2>/dev/null | sort -n
98516480    prof1
ubuntu@ubuntu:/media/ubuntu/03b10f71-a8bd-42d7-875c-1cc31f564122/home$ cd prof1/
ubuntu@ubuntu:/media/ubuntu/03b10f71-a8bd-42d7-875c-1cc31f564122/home/prof1$ sudo du -sx * 2>/dev/null | sort -n
0    PlayOnLinux's virtual drives
4    Desktop
4    Documents
4    Music
4    Pictures
4    Public
4    Templates
4    Videos
12    examples.desktop
60    0B19qro3VGFYwQi1kU1ZkaFkyN28?e=download
120    open?id=0B19qro3VGFYwQi1kU1ZkaFkyN28
136    Steam
245340    Pokémon+Uranium.exe
443388    Downloads
ubuntu@ubuntu:/media/ubuntu/03b10f71-a8bd-42d7-875c-1cc31f564122/home/prof1$ 


```

A lot of bytes seem to be hidden in hidden folders.

```
ubuntu@ubuntu:/media/ubuntu/03b10f71-a8bd-42d7-875c-1cc31f564122/home/prof1$ ls .* -a
.bash_history  .bashrc  .ICEauthority  .pulse-cookie  .steampid                  .wget-hsts   .xsession-errors
.bash_logout   .dmrc    .profile       .steampath     .sudo_as_admin_successful  .Xauthority  .xsession-errors.old

.:
.                                        Documents         .nv                                   .steampath
..                                       Downloads         open?id=0B19qro3VGFYwQi1kU1ZkaFkyN28  .steampid
0B19qro3VGFYwQi1kU1ZkaFkyN28?e=download  examples.desktop  Pictures                              .sudo_as_admin_successful
.adobe                                   .gconf            .pki                                  Templates
.bash_history                            .gnupg            .PlayOnLinux                          Videos
.bash_logout                             .ICEauthority     PlayOnLinux's virtual drives          .wget-hsts
.bashrc                                  .java             Pokémon+Uranium.exe                   .wine
.cache                                   .local            .profile                              .Xauthority
.compiz                                  .macromedia       Public                                .xsession-errors
.config                                  .minecraft        .pulse-cookie                         .xsession-errors.old
Desktop                                  .mozilla          .steam
.dmrc                                    Music             Steam

..:
.  ..  prof1
ls: cannot open directory '.adobe': Permission denied
ls: cannot open directory '.cache': Permission denied
ls: cannot open directory '.compiz': Permission denied
ls: cannot open directory '.config': Permission denied
ls: cannot open directory '.gconf': Permission denied
ls: cannot open directory '.gnupg': Permission denied

.java:
.  ..  fonts
ls: cannot open directory '.local': Permission denied
ls: cannot open directory '.macromedia': Permission denied
ls: cannot open directory '.minecraft': Permission denied
ls: cannot open directory '.mozilla': Permission denied
ls: cannot open directory '.nv': Permission denied
ls: cannot open directory '.pki': Permission denied

.PlayOnLinux:
.  ..  configurations  extensions.cfg  icones  logs  playonlinux.cfg  plugins  ressources  shortcuts  tmp  wine  wineprefix

.steam:
.                 bin_steam.sh     graphics  registry.vdf  skins                        steam.pipe                   ubuntu12_32
..                config           html5app  resource      steam                        steam.sh                     ubuntu12_64
bin               controller_base  linux32   root          steamdeps.txt                tenfoot
bin32             error.log        linux64   sdk32         steam_install_agreement.txt  ThirdPartyLegalNotices.css
bin64             fontconfig       package   sdk64         steam_msg.sh                 ThirdPartyLegalNotices.doc
bin_steamdeps.py  friends          public    servers       steam.pid                    ThirdPartyLegalNotices.html

.wine:
.  ..  dosdevices  drive_c  system.reg  .update-timestamp  userdef.reg  user.reg
```

---

### Post by mastablasta on 2017-07-26
you can search logs for any errors. 

what does df -h say abotu the disk??

---

### Post by rsteinmetz70112 on 2017-07-26
Try running du to see where the space is being used.

Looks like home has the most stuff int it. 
When you do a reinstall are you restoring your home directory? 
If so you may be reintroducing whatever problem you are having.

---

### Post by zerobytez on 2017-07-27
So, I don't know what happened, but in frustration I accidently ran sudo rm -r / when i meant to select a folder called . i made. I reset grub, no random filling? Im marking this as solved cause it's fied, but I don't know what the **** was going on.

---

