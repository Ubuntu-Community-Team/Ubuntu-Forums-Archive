---
title: "Grub menu screen has changed; want to revert"
date: 2017-10-01
forum: General Help
---

### Post by vaskark2 on 2017-10-01
Hi. I used to have a grub screen with white text over purple coloured background. Now I have a Debian wallpaper as a background and the menu entry says GNU/Linux where it just said Ubuntu before. How can I return it to its previous state? Running 'sudo update-grub' produces:

Generating grub configuration file ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-4.10.0-35-generic
Found initrd image: /boot/initrd.img-4.10.0-35-generic
Found linux image: /boot/vmlinuz-4.10.0-33-generic
Found initrd image: /boot/initrd.img-4.10.0-33-generic
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done

I also have no /etc/default/grub file to edit so I'm not sure where I can make the changes necessary (or if I have to reconfigure / reinstall something).

Any help is appreciated. Thanks.

---

### Post by yancek on 2017-10-02
> I also have no /etc/default/grub file to edit

The various options for getting a background image for Grub on Ubuntu are explained at the link below.  If you don't have an /etc/default/grub file (??) take a look in the /etc/grub.d/05_debian_theme file discussed in this link.  Doesn't seem likely that something like this would change on it's own so if you made some changes, undoing whatever you originally did would probably solve the problem.

 [https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by Kirboosy on 2017-10-02
Hi Vaskark2,

Few questions for you.

1. What version of Ubuntu are you running?
2. Are you sure that **/etc/default/grub.cfg** doesn't exist?
3. Does this command find anything on your system?

```
locate grub.cfg
```




Hope that helps!
~Caboose

P.S. to make your code easier to read please use the CODE tags

---

### Post by vaskark2 on 2017-10-02
Hi guys. Thanks for the responses.

I did a little more research and got myself part of the way. So sorry for the late reply.

I'm using Ubuntu 17.04.

I did not have /etc/default/grub ... so I copied /usr/share/grub/default/grub to that location so that's ok.

Looking at that file and what I can configure myself did help me some. I was able to change the resolution there and things like that. And running 'sudo update-grub' to write the changes. Although, configuring a background picture is proving difficult. Are there any limits imposed as to size or resolution? Not sure. I installed grub-customizer but that isn't helping as much. The correct config line is being added ... but the picture doesnt show up.

I think this problem started when I installed the Ubuntu Budgie Desktop. It installed a bunch of stuff that I probably didn't need. I'm rolling that stuff back as we speak. One thing it did was change the plymouth ubuntu animation screen. Still haven't gotten that back.

Anyhoo, that's it for now.
Thanks again.

---

### Post by yancek on 2017-10-02
The limitations on the images you may use are listed in the link I posted earlier.

---

### Post by vaskark2 on 2017-10-02
Ah. Many thanks.

---

