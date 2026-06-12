---
title: "Installing custom 18.04 distro fails at setting regional defaults"
date: 2018-05-03
forum: General Help
---

### Post by lieven-debels on 2018-05-03
I'm trying to make my own distro. An important feature of it is that it can be installed if desired.
To make my own distro, I use the scripts under this post. (Running newdist1.sh is enough, newdist2.sh is required, you may need to make both files executable)

The created distro works fine as a live distro. However, when installing to harddrive the installer crashes at 'Setting regional defaults'.
For a good understanding, this is the case with 18.04. When making a 17.10 distro, the installer continues till the end and i have a working system afterwards (although I still have to run sudo update-grub once after installation)

Now here comes my question: What makes the installer of 18.04 behaving differently than the installer of 17.10? Should I make modifications to the first or the second script to make it work?

Before using the scripts included with this post, keep in mind the following:

[LIST]
[*]If you have a folder named 'work' in your home folder, you should make a full backup of it before using my scripts, because the work folder will be deleted and used to hold the distro. 
[*]If you make changes to the scripts, you're assumed you know what you're doing and of course you're responsible if anything goes wrong after the changes, not me! 
[*]On my system, using the scripts in their current state is safe, and they produce a working live system afterwards. 
[*]You may want to use a virtual machine or a free partition on your hard drive (10 GB should be plenty) to test if the resulting distro can be installed. 
[*]The installer of any distro other than 17.10 may (and probably will) crash. 
[/LIST]
Below is also a sample packages.txt file, which can be used to create a fairly minimal GUI distro (based on the jwm window manager), and a sample .jwmrc file. It is advised to copy those two files to your home folder before using the scripts.
If you're already using jwm, please make a backup of your own .jwmrc file first, so it don't gets overwritten!

newdist1.sh:
```
#!/bin/bash

# Some information for the user of this script

clear
echo
echo "With a few bash scripts, you can easily create your own distro."
echo "You will need at least:"
echo
echo "   - This script and the script newdist2.sh"
echo "   - A computer running Ubuntu with the"
echo "     following recommended specifications:"
echo "        - A dual-core processor"
echo "        - 2 GB of RAM"
echo "        - 20 GB free disk space"
echo "   - Some elementary command-line knowledge"
echo
echo "In addition, you may want to use the following files:"
echo
echo "   - packages.txt (to install packages)"
echo "   - ppa.txt (to add software from a ppa)"
echo
echo "Press 'q' to quit or any other key to continue"
echo
read -n1 CONT
clear

# if q is pressed: abort, else start script

if [[ $CONT != "q" ]]
then

    # check if we're in the user's home folder, otherwise abort

    if [[ $(pwd) == $HOME ]]
    then

        # check if the script newdist2.sh is available, else abort

        if [[ -f "newdist2.sh" ]]
        then

            # set some variables about your distro

            BEGINARCH=$(uname -m | cut -b 1)
            DISTRIBUTION=$(cat /etc/lsb-release | grep "_ID" | cut -b 12-)

            # change the following two lines to match the distro you wanna build.            

            ADJECTIVE="Bionic"
            ANIMAL="Beaver"

            # If you're building the same release as the one you're currently running,
            # please change the next two lines to match the release you're building.
            # Alternatively, uncomment the lines thereafter to autodetect the release.

            RELEASE="18.04"
            CODENAME="bionic"
            #RELEASE=$(cat /etc/lsb-release | grep "_RELEASE" | cut -b 17-)
            #CODENAME=$(cat /etc/lsb-release | grep "_CODENAME" | cut -b 18-)

            # set the right architecture (i386 or amd64)

            if [[ $BEGINARCH == "x" ]]
            then
                ARCH="amd64"
            else
                ARCH="i386"
            fi

            # ask the user if he wants the distro to be installable

            while [[ $INSTALLER != "yes" ]] && [[ $INSTALLER != "no" ]]
            do
                echo
                echo "Do you want to be able to install your distro to a hard drive?"
                echo "Answer 'yes' or 'no'."
                echo
                read INSTALLER
                echo
            done

            # if he answers yes, ask which installer frontend he prefers

            if [[ $INSTALLER != "no" ]]
            then
                while [[ $FRONTEND != "gtk" ]] && [[ $FRONTEND != "qt" ]]
                do
                    echo
                    echo "Which installer frontend do you prefer?"
                    echo "Answer 'gtk' or 'qt'."
                    echo
                    echo "If you intend to use KDE or LXQT,"
                    echo "choose 'qt'. Otherwise, choose 'gtk'."
                    echo
                    read FRONTEND
                    echo
                done
            fi

            # ask which locale he wants to use on the live image

            echo
            echo "Which locale do you want to use on the live cd?"
            echo "Note: You will need to add the required language packs"
            echo "      supporting the locale to the file packages.txt"
            echo
            echo "Please respond by typing the language code"
            echo "(2 letters), followed by an underscore and"
            echo "the country code (2 capital letters)."
            echo "Example: for american english use en_US"
            echo
            read LOCALE
            clear
            echo
            echo "Starting build ..."
            echo

            # Check if the work folder already exists
            # If true, remove it

            if [[ -d $HOME/work ]]
            then
                sudo rm -r work
            fi

            # update package sources and install debootstrap

            sudo apt-get update --yes
            sudo apt-get install --yes debootstrap

            # make a chroot directory and change to the work folder

            mkdir -p work/chroot
            cd work

            # install a minimal system in the chroot folder

            sudo debootstrap --arch=$ARCH $CODENAME chroot

            # if the user wants an installer, create a temporary file indicating the frontend to use

            if [[ $INSTALLER != "no" ]]
            then
                if [[ $FRONTEND == "gtk" ]]
                then
                    sudo touch chroot/gtk.txt
                else
                    sudo touch chroot/qt.txt
                fi
            fi

            # copy the second script to the chroot folder

            sudo cp $HOME/newdist2.sh chroot

            # if they exist, copy the optional files to the chroot folder

            if [[ -f $HOME/packages.txt ]]
            then
                sudo cp $HOME/packages.txt chroot
            fi
            
            if [[ -f $HOME/ppa.txt ]]
            then
                sudo cp $HOME/ppa.txt chroot
            fi

            # bind run to the chroot and copy sources.list

            sudo mount -o bind /run/ chroot/run

            #If you're building another release than the one you're currently running
            #you should copy your sources.list to your home folder and change every occurrence
            #of the codename to match the codename of the release you're building.
            #In that case, comment out the next line and uncomment the line after.

            sudo cp /etc/apt/sources.list chroot/etc/apt/sources.list
            #sudo cp $HOME/sources.list chroot/etc/apt/sources.list

            # chroot into the minimal system
            # inside chroot, continue with the second script

            sudo chroot chroot /bin/bash -c "./newdist2.sh"

            # after exiting chroot, unmount /run /sys en /dev/pts

            sudo umount chroot/run
            sudo umount chroot/sys
            sudo umount chroot/dev/pts

            # remove the second script from chroot, as it is no longer needed

            sudo rm chroot/newdist2.sh
            cd ..

            # copy some settings from the host system to the chroot system

            # keyboard layout

            sudo cp /etc/default/keyboard work/chroot/etc/default

            # lightdm settings, to skip asking login credentials on the live cd

            echo "[SeatDefaults]" > work/chroot/usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
            echo "user-session=jwm" >> work/chroot/usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
            echo "autologin-user=ubuntu" >> work/chroot/usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
            echo "autologin-user-timeout=0" >> work/chroot/usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf

            # a folder and some icons on the host system, that I also want to use on the live cd
            # (Commented out for online use)

            #sudo cp -r $HOME/system-monitor work/chroot/etc/skel/
            #sudo cp -r /usr/share/icons/Other work/chroot/usr/share/icons/

            # some layout (and other) settings

            sudo cp -r /usr/share/themes work/chroot/usr/share/
            sudo cp -r /usr/share/backgrounds work/chroot/usr/share/
            sudo cp -r $HOME/.icons work/chroot/etc/skel/
            sudo cp -r $HOME/.config work/chroot/etc/skel/
            sudo cp -r $HOME/.gtkrc-2.0 work/chroot/etc/skel/
            sudo cp -r $HOME/.jwmrc work/chroot/etc/skel/
            sudo cp -r $HOME/Desktop work/chroot/etc/skel/
            sudo cp /usr/share/polkit-1/actions/org.freedesktop.UDisks2.policy work/chroot/usr/share/polkit-1/actions/
            sudo chmod -R 755 work/chroot/etc/skel/

            # if network-manager is installed, create a file in chroot

            if [[ -d work/chroot/etc/NetworkManager ]]
            then
                sudo touch work/chroot/etc/NetworkManager/conf.d/10-globally-managed-devices.conf
               fi

            # install some packages on the host system

            sudo apt-get install --yes xorriso syslinux isolinux squashfs-tools genisoimage

            # make an image folder

            mkdir -p work/image/{casper,isolinux,install}

            # export kernel version

            export kversion=`cd work/chroot/boot && ls -1 vmlinuz-* | tail -1 | sed 's@vmlinuz-@@'`

            # copy vmlinuz and initrd from the chroot to the casper folder

            sudo cp -p work/chroot/boot/vmlinuz-${kversion} work/image/casper/vmlinuz
            sudo cp -p work/chroot/boot/initrd.img-${kversion} work/image/casper/initrd.gz

            # copy some files from the host system to the isolinux folder

            sudo cp /usr/lib/syslinux/modules/bios/menu.c32 work/image/isolinux/
            sudo cp /usr/lib/ISOLINUX/isolinux.bin work/image/isolinux/
            sudo cp /usr/lib/syslinux/modules/bios/ldlinux.c32 work/image/isolinux/
            sudo cp /usr/lib/syslinux/modules/bios/libcom32.c32 work/image/isolinux/
            sudo cp /usr/lib/syslinux/modules/bios/libutil.c32 work/image/isolinux/

            # change to the isolinux folder and create an isolinux.cfg file
            # this file will be used to show a simple boot menu on the live cd

            cd work/image/isolinux
            echo "ui menu.c32" > isolinux.cfg
            echo "prompt 0" >> isolinux.cfg
            echo "menu title Ubuntu $RELEASE '$ADJECTIVE $ANIMAL'" >> isolinux.cfg
            echo "timeout 30" >> isolinux.cfg
            echo "DEFAULT Start" >> isolinux.cfg
            echo "LABEL Start" >> isolinux.cfg
              echo "  linux /casper/vmlinuz" >> isolinux.cfg
            echo -n "  append file=/cdrom/preseed/ubuntu.seed boot=casper locale=" >> isolinux.cfg && echo -n $LOCALE >> isolinux.cfg && echo " initrd=/casper/initrd.gz quiet splash --" >> isolinux.cfg
            cd ../..

            # in the case of an installer, create the files filesystem.manifest and filesystem.manifest-desktop

            if [[ $INSTALLER != "no" ]]
            then
                sudo chroot chroot dpkg-query -W --showformat='${Package} ${Version}\n' | sudo tee image/casper/filesystem.manifest
                sudo cp image/casper/filesystem.manifest image/casper/filesystem.manifest-desktop
                REMOVE='ubiquity ubiquity-frontend-gtk ubiquity-frontend-kde casper lupin-casper live-initramfs user-setup discover xresprobe os-prober libdebian-installer4'
                for i in $REMOVE
                do
                    sudo sed -i "/${i}/d" image/casper/filesystem.manifest-desktop
                done
            fi

            # compress the chroot filesystem to a squashfs

            sudo mksquashfs chroot image/casper/filesystem.squashfs

            # write the filesystem.size, needed by the installer

            printf $(sudo du -sx --block-size=1 chroot | cut -f1) > image/casper/filesystem.size

            # create README.diskdefines

            echo "#define DISKNAME  "$DISTRIBUTION $RELEASE \'$ADJECTIVE $ANIMAL\'" - Release "$ARCH > image/README.diskdefines
            echo "#define TYPE  binary" >> image/README.diskdefines
            echo "#define TYPEbinary  1" >> image/README.diskdefines
            echo "#define ARCH  "$ARCH >> image/README.diskdefines
            echo "#define ARCH"$ARCH"  1" >> image/README.diskdefines
            echo "#define DISKNUM  1" >> image/README.diskdefines
            echo "#define DISKNUM1  1" >> image/README.diskdefines
            echo "#define TOTALNUM  0" >> image/README.diskdefines
            echo "#define TOTALNUM0  1" >> image/README.diskdefines

            # create some other files, needed by the live image

            touch image/ubuntu
            mkdir image/.disk
            touch image/.disk/base_installable
            echo "full_cd/single" > image/.disk/cd_type
            echo $DISTRIBUTION $RELEASE \'$ADJECTIVE $ANIMAL\'" - Release "$ARCH > image/.disk/info
            echo "https://wiki.ubuntu.com/"$ADJECTIVE$ANIMAL"/ReleaseNotes" > image/.disk/release_notes_url
            sudo /bin/bash -c "cd image && find . -type f -print0 | xargs -0 md5sum | grep -v "\./md5sum.txt" > md5sum.txt"
            cd image

            # finally, create the live image

            xorriso -as genisoimage -r -J -joliet-long -l \
            -isohybrid-mbr /usr/lib/ISOLINUX/isohdpfx.bin -partition_offset 16 \
            -A "$DISTRIBUTION" -b isolinux/isolinux.bin -c \
            isolinux/boot.cat -no-emul-boot -boot-load-size 4 \
            -boot-info-table -o $HOME/my1804_test.iso .
            echo
            echo "----- SCRIPT COMPLETED SUCCESSFULLY -----"
            echo
            echo "The iso is available in your home folder."
            echo "You can burn it to an optical medium or"
            echo "write it to an usb flash drive using dd."
            echo
        else
            echo
            echo "------------ SCRIPT ABORTED ------------"
            echo
            echo "The script newdist2.sh is required."
            echo "Please make sure it's present in your home folder."
            echo "Then run this script again."
            echo
        fi
    else
        echo
        echo "------------ SCRIPT ABORTED ------------"
        echo
        echo "You should run this script from your home folder."
        echo
    fi
else
    echo
    echo "------------ SCRIPT ABORTED ------------"
    echo
fi
```
 
newdist2.sh:
```
#!/bin/bash

# this script is run entirely in chroot
# mount some folders

mount none -t proc /proc
mount none -t sysfs /sys
mount none -t devpts /dev/pts

# export some variables

export HOME=/root
export LC_ALL=C

# add additional ppa's

if [[ -f ppa.txt ]]
then
    for p in $(cat ppa.txt)
    do
        apt-key adv --keyserver keyserver.ubuntu.com --recv-keys $p
    done

    # remove ppa.txt when done

    rm ppa.txt
fi

# update /etc/apt/sources.list

apt-get update --yes

# install dbus and make some tricks

apt-get install --yes dbus
dbus-uuidgen > /var/lib/dbus/machine-id
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

# upgrade packages and install essential packages for the live image

apt-get --yes upgrade
apt-get install --yes --no-install-recommends ubuntu-standard casper lupin-casper
apt-get install --yes --no-install-recommends discover laptop-detect os-prober
apt-get install --yes --no-install-recommends linux-generic

# make another trick

rm /etc/resolv.conf
ln -s /run/systemd/resolve/resolv.conf /etc/resolv.conf

# add user-defined packages to the image
# of course the --no-install-recommends is optional, but can save some space

for p in $(cat packages.txt); do apt-get install --no-install-recommends --yes $p; done

# when done, remove packages.txt

rm packages.txt

# install the appropriate installer frontend

if [[ -f gtk.txt ]]
then
    apt-get install --yes ubiquity-frontend-gtk
    rm gtk.txt
elif [[ -f qt.txt ]]
then
    apt-get install --yes ubiquity-frontend-kde
    rm qt.txt
fi

# prevent the installer from crashing while installing packages

UBIQUITY=$(dpkg -l | grep ubiquity | wc -l)
if [[ $UBIQUITY > 0 ]]
then
    rm /usr/share/ubiquity/apt-setup
    touch /usr/share/ubiquity/apt-setup
    echo "#do nothing" > /usr/share/ubiquity/apt-setup
    chmod 755 /usr/share/ubiquity/apt-setup
fi

# the next bit is optional but handy if you want to make additional changes to the live image

echo
echo "Pausing build ..."
echo
echo "You can now make advanced customizations. To do so,"
echo "you should open a separate terminal window. From"
echo "there, you can chroot into your distro using the"
echo "following command: 'sudo chroot work/chroot'"
echo
echo "If you are done customizing, enter 'exit'."
echo "Then you may also copy certain files from your"
echo "build system to your distro. If you enter 'exit'"
echo "a second time, the terminal will close."
echo
echo "If you are ready to continue building, press enter"
read N
echo "Continuing build ..."
echo

# remove packages that are no longer useful and prepare to exit chroot

apt-get autoremove --purge --yes
rm /var/lib/dbus/machine-id
apt-get clean
rm -rf /tmp/*
umount -lf /proc

```

packages.txt:
```
alsa-utils
arandr
bc
dmz-cursor-theme
faenza-icon-theme
firefox
gtk2-engines
gvfs
jwm
leafpad
libfm-modules
lightdm
lightdm-gtk-greeter
lxappearance
lxterminal
nano
network-manager-gnome
numlockx
pcmanfm
plymouth-theme-ubuntu-logo
policykit-1
pulseaudio
python-alsaaudio
sysstat
upower
volumeicon-alsa
xserver-xorg
xserver-xorg-video-all
xserver-xorg-input-all
xterm
```

.jwmrc:
```
<?xml version="1.0"?>
<JWM>

    <StartupCommand>nm-applet</StartupCommand>
    <StartupCommand>/usr/bin/pulseaudio -D</StartupCommand>
    <StartupCommand>volumeicon</StartupCommand>

    <!-- The root menu. -->
    <RootMenu onroot="12" height="46">
        <!-- <Include>/etc/jwm/debian-menu</Include> -->
        <Program icon="terminal.svg" label="Terminal">lxterminal</Program>
        <Separator/>
        <Program icon="folder.svg" label="Files">pcmanfm</Program>
        <Program icon="firefox.svg" label="Webbrowser">firefox</Program>
        <Program icon="leafpad.svg" label="Texteditor">leafpad</Program>
        <Menu icon="applications-system.svg" label="Settings">
        <Program icon="display.svg" label="Display">arandr</Program>
        <Program icon="preferences-desktop-theme.svg" label="Appearance">lxappearance</Program>
        </Menu>
    <Separator/>
    <Program icon="view-refresh.svg" label="Reboot">systemctl reboot</Program>
    <Program icon="system-shutdown.svg" label="Shutdown">systemctl poweroff</Program>
    </RootMenu>

    <!-- Options for program groups. -->
    
    <Group>
    <Option>tiled</Option>
        <Option>aerosnap</Option>
    </Group>

    <!-- Tray at the bottom. -->
    <Tray x="0" y="-1" height="54" autohide="off">

        <TrayButton icon="distributor-logo-ubuntu.svg" popup="Menu">root:1</TrayButton>
        <Spacer width="2"/>
        <TrayButton icon="folder.svg" popup="Files">exec:pcmanfm</TrayButton>
        <TrayButton icon="firefox.svg" popup="Webbrowser">exec:firefox</TrayButton>
        <Spacer width="2"/>
        <Pager labeled="true"/>
        <Spacer width="2"/>
        <TaskList maxwidth="242"/>
        <Spacer width="2"/>
        <Spacer width="2"/>
        <Dock/>
        <Clock format="%H:%M">showdesktop</Clock>
        <Spacer width="8"/>
   </Tray>

   <!-- Visual Styles -->
   <WindowStyle>
        <Font>Monospace-11</Font>
        <Width>4</Width>
        <Height>28</Height>
        <Corner>3</Corner>
        <Foreground>#000000</Foreground>
        <Background>#EEEEEE</Background>
        <Outline>#EEEEEE</Outline>
        <Opacity>0.5</Opacity>
        <Active>
            <Foreground>#FFFFFF</Foreground>
            <Background>#373737</Background>
            <Outline>#373737</Outline>
            <Opacity>1.0</Opacity>
        </Active>
    </WindowStyle>
    <TrayStyle group="false" list="all">
        <Font>Monospace-11</Font>
        <Background>#373737</Background>
        <Foreground>#FFFFFF</Foreground>
        <Outline>#373737</Outline>
        <Active>
            <Foreground>#FFFFFF</Foreground>
            <Background>#F78800</Background>
        </Active>
        <Opacity>0.75</Opacity>
    </TrayStyle>
    <PagerStyle>
        <Font>Monospace-11</Font>
        <Outline>#F78800</Outline>
        <Foreground>#666666</Foreground>
        <Background>#373737</Background>
        <Text>#FFFFFF</Text>
        <Active>
            <Foreground>#FFFFA0</Foreground>
            <Background>#F78800</Background>
        </Active>
    </PagerStyle>
    <MenuStyle>
        <Font>Monospace-11</Font>
        <Foreground>#FFFFFF</Foreground>
        <Background>#373737</Background>
        <Outline>#373737</Outline>
        <Active>
            <Foreground>#FFFFFF</Foreground>
            <Background>#F78800</Background>
        </Active>
        <Opacity>0.85</Opacity>
    </MenuStyle>
    <PopupStyle>
        <Font>Monospace-11</Font>
        <Foreground>#000000</Foreground>
        <Background>#FFFFC0</Background>
    </PopupStyle>

    <!-- Path where icons can be found.
         IconPath can be listed multiple times to allow searching
         for icons in multiple paths.
      -->
    <IconPath>/usr/share/icons/Faenza/actions/scalable</IconPath>
    <IconPath>/usr/share/icons/Faenza/apps/scalable</IconPath>
    <IconPath>/usr/share/icons/Faenza/categories/scalable</IconPath>
    <IconPath>/usr/share/icons/Faenza/devices/scalable</IconPath>
    <IconPath>/usr/share/icons/Faenza/emblems/scalable</IconPath>
    <IconPath>/usr/share/icons/Faenza/mimetypes/scalable</IconPath>
    <IconPath>/usr/share/icons/Faenza/places/scalable</IconPath>
    <IconPath>/usr/share/icons/Faenza/status/scalable</IconPath>   
    <IconPath>/usr/share/pixmaps</IconPath>

    <!-- Virtual Desktops -->
    <!-- Desktop tags can be contained within Desktops for desktop names. -->
    <Desktops width="2" height="2">
        <!-- Default background. Note that a Background tag can be
              contained within a Desktop tag to give a specific background
              for that desktop.
         -->
        <Background type="image">/usr/share/backgrounds/warty-final-ubuntu.png</Background>
    </Desktops>

    <!-- Double click speed (in milliseconds) -->
    <DoubleClickSpeed>400</DoubleClickSpeed>

    <!-- Double click delta (in pixels) -->
    <DoubleClickDelta>2</DoubleClickDelta>

    <!-- The focus model (sloppy or click) -->
    <FocusModel>sloppy</FocusModel>

    <!-- The snap mode (none, screen, or border) -->
    <SnapMode distance="10">screen</SnapMode>

    <!-- The move mode (outline or opaque) -->
    <MoveMode>opaque</MoveMode>

    <!-- The resize mode (outline or opaque) -->
    <ResizeMode>opaque</ResizeMode>

    <!-- Key bindings -->
    <Key key="Up">up</Key>
    <Key key="Down">down</Key>
    <Key key="Right">right</Key>
    <Key key="Left">left</Key>
    <Key key="h">left</Key>
    <Key key="j">down</Key>
    <Key key="k">up</Key>
    <Key key="l">right</Key>
    <Key key="Return">select</Key>
    <Key key="Escape">escape</Key>

    <Key mask="A" key="Tab">nextstacked</Key>
    <Key mask="A" key="F4">close</Key>
    <Key mask="A" key="#">desktop#</Key>
    <Key mask="A" key="F1">root:1</Key>
    <Key mask="A" key="F2">window</Key>
    <Key mask="A" key="F10">maximize</Key>
    <Key mask="A" key="Right">rdesktop</Key>
    <Key mask="A" key="Left">ldesktop</Key>
    <Key mask="A" key="Up">udesktop</Key>
    <Key mask="A" key="Down">ddesktop</Key>
    
    <Key mask="4" key="e">exec:pcmanfm</Key>
    <Key mask="4" key="f">exec:firefox</Key>
    <Key mask="4" key="space">exec:lxterminal</Key>
    
</JWM>
```

---

### Post by lieven-debels on 2018-05-06
Ok, found the solution myself, but please read on, i have two more questions at the end of this post.

The following command is behind the file /usr/share/applications/ubiquity.desktop:
```
sudo --preserve-env=DBUS_SESSION_BUS_ADDRESS,XDG_RUNTIME_DIR sh -c 'ubiquity gtk_ui'
```
Double-clicking this file makes the installer crash at setting regional defaults, because the command above is totally wrong.

If I execute the following command from terminal:
```
sudo pkexec ubiquity gtk_ui
``` the installer doesn't crash, but continues until the end of the installation.
I don't know what the following bit of code should do and even less why it was added, because it seems to make things worse than before.
```
--preserve-env=DBUS_SESSION_BUS_ADDRESS,XDG_RUNTIME_DIR
```
Can someone explain this to me?
And secondly, how can I change the ubiquity.desktop file so its command reads  "sudo pkexec ubiquity gtk_ui" when booting my distro?

---

