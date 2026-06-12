---
title: "Changing the Background Color of GRUB"
date: 2021-10-19
forum: General Help
---

### Post by tb75252 on 2021-10-19
I am using Ubuntu 21.10, 64-bit.

The current background of GRUB is black.  I would like to change it to Ubuntu's default color which I believe they call it "aubergine" (sort of a fuchsia color).

I found the following instructions online (which obviously do not work or else I would not post this!!):
```
sudo -H gedit /usr/share/plymouth/themes/default.grub
```
followed by
```

if background_color 44,0,30 ; then
  clear
fi 
```
followed by
```
sudo update-grub
```

After all this, the background color is still black...  So, how do I change the background color of GRUB?

---

### Post by tea for one on 2021-10-19
For grub 2.04, you can simply put an image in /boot/grub.
You will have to use [COLOR="#0000FF"]sudo[/COLOR] to move the image to the grub folder.

```
edited@edited:/boot/grub$ ls
fonts  grub.cfg  grubenv  [COLOR="#0000FF"]hummingbird02.png[/COLOR]  unicode.pf2  x86_64-efi
```
Followed by
```
sudo update-grub
```
You could create a suitable solid colour image in the correct resolution for your PC using GIMP or similar.

---

### Post by grahammechanical on 2021-10-19
You are following instructions that you found online. We do not know what those instructions are. It would help if you provided a link to those instructions.

When we run update-grub we are running a script that calls a program called grub-mkconfig that build the grub.cfg file from text files in /etc/grub.d. It is grub.cfg that prints the grub menu to the screen. I give you a quote from one of those files - 05_debian-theme

> set_default_theme(){
    case $GRUB_DISTRIBUTOR in
        Tanglu|Ubuntu|Kubuntu)
            # Set a monochromatic theme for Tanglu/Ubuntu.
            echo "${1}set menu_color_normal=white/black"
            echo "${1}set menu_color_highlight=black/light-gray"

            if [ -e /usr/share/plymouth/themes/default.grub ]; then
                sed "s/^/${1}/" /usr/share/plymouth/themes/default.grub
            fi
            # For plymouth backward compatiblity. Can be removed
            # after xenial.
            if [ -e /lib/plymouth/themes/default.grub ]; then
                sed "s/^/${1}/" /lib/plymouth/themes/default.grub
            fi
            ;;
        *)
            # Set the traditional Debian blue theme.
            echo "${1}set menu_color_normal=cyan/blue"
            echo "${1}set menu_color_highlight=white/blue"
            ;;
    esac
}



It is the set menu_color = lines that have to be changed. You are doing by creating a default.grub file in /usr/share/plymouth/themes/. Note these lines:

> if [ -e /usr/share/plymouth/themes/default.grub ]; then
                **sed **"s/^/${1}/" /usr/share/plymouth/themes/default.grub

That is an **if** statement. I have no idea what the **sed** instruction is doing. It is that that is not working. It seems grub-mkconfig is not finding the text file that you have created. You could try editing 05_debian_theme directly. 

Here is the Grub 2.06 manual

[https://www.gnu.org/software/grub/manual/grub/grub.html#Introduction-1](https://www.gnu.org/software/grub/manual/grub/grub.html#Introduction-1)

Regards

---

