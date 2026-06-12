---
title: "&quot;lsmod | grep amdgpu&quot; return nothing"
date: 2023-08-30
forum: General Help
---

### Post by habernir on 2023-08-30
after i uninstall ROCm from amd ppa
 i see that amdgpu not loaded and when i do 
[RIGHT][COLOR=#4D5156][FONT=arial]
lsmod | [/FONT][/COLOR][COLOR=#5F6368][FONT=arial][B]grep amdgpu

it return nothing
anyone know how do i fix it?

[/B][/FONT][/COLOR][/RIGHT]

---

### Post by MAFoElffen on 2023-08-30
<Here is my updated guide for using amdgpu opensourced drivers>
Guide to let Ubuntu use Opensource amdgpu driver
(Updated as of: 2023.08.30)

I add some options to the Grub2 boot parameters to clear the way for the amdgpu module to load, with no conflicts, then set the KMS mode to a resolution. This helps it get the splash and graphical login set, and adds a helper before the graphics drivers are loaded in the desktop.

At the Grub2 Boot Menu... Press the <E> key. <Arrow-Down to the line that starts with the word "linux". <Arrow-Right> until you get to the words "quiet splash" Delete the word "quiet" and replace with "--" (2 dashes). <Arrow-Right until after "splash"...

Add a <Space> after the word "splash, then type in the text "radeon.modeset=0 amdgpu.noretry=0 amdgpu.dc=1 video=uvesafb:1920x1080-32@60,mtrr:3,ywrap,noblank " (without the quotes). Then press <Cntrl><X>. See if it boots and test.

If that works, then edit (with privileges) file /etc/default/grub, line that starts with "GRUB_CMDLINE_LINUX_DEFAULT" with the same edits. Like this:
```

GRUB_CMDLINE_LINUX_DEFAULT="-- splash radeon.modeset=0 amdgpu.noretry=0 amdgpu.dc=1 video=uvesafb:1920x1080-32@60,mtrr:3,ywrap,noblank"

```
Then go down more in that file to where "GRUB_GFXMODE" is located and change it to this"
```

GRUB_GFXMODE=1920x1080x32

```
Then save it, and do
```

sudo update-grub

```
Then see if the amdgpu module is loaded to the kernel
```

lsmod | grep amdgpu

```
If not ouput, then the amdgpu module needs to be loaded to the kernel...

If is is not being loaded, then to load it do
```

sudo modprobe amdgpu
sudo echo "amdgpu" >> /etc/module-load.d/modules.conf
sudo update-initramfs -c -k all

```
Next thing I do, is to check if the firmware exists for the GPU
```

ls /lib/firmware/amdgpu
apt list linux-firmware --installed

```
If no output, then install it via
```

sudo apt install linux-firmware

```
If you search the syslogs, their are firmware load issues, 
```

sudo cat /var/log/syslog | grep 'amdgpu'

```
If one of the filtered messages says:
```

Failed to enable requested dpm features!

```
Then add this boot parameter: ""
```

amdgpu.ppfeaturemask=0xffffb

```
For some reason the hardware is "very new", and it errored on loading one of the firmware files or is missing one, then go to kernel.org and install the latest firmware blob from there...
```

## Go to the kernel.org git 
## -- https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/
## and get the latest firmware tarfile link. Adjust the DL link and filename 'here' accordingly.

DL_LINK="https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/snapshot/linux-firmware-20230804.tar.gz"
FILNAME="linux-firmware-20230804.tar.gz"

mkdir $HOME/Downloads/linux-firmware
mkdir $HOME/Downloads/linux-firmware/amdgpu
cd $HOME/Downloads/Linux-firmware

wget -n -t 5 -T 10 $DL_LINK

# Look in tar...
tar -tvf $FILENAME | grep -m1 'amdgpu'

# Extract just folder 'amdgpu' into the target folder
tar -xvf $FILENAME amdgpu/ -C ./amdgpu

sudo cp ./amdgpu/* /usr/lib/firmware/amdgpu/

```

---

### Post by habernir on 2023-08-30
thanks a lot i will try it

---

