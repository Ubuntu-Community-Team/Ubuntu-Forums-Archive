---
title: "Customized grub problem on 12.04 13.04"
date: 2013-09-23
forum: General Help
---

### Post by ubume2 on 2013-09-23
I have been using a custom grub menu in /etc/grub.d called 06_custom.

It has been working fine until late last week. I have Ubuntu 12.04 32 and 64 bit, Ubuntu 13.04 64 bit, Windows 7, and two Arch Linux installs all on separate partitions.

Now, in both 12.04 installs and the 13.04 install  when I use 06_custom I get this message:
> 
Found Ubuntu
error: $.
error: syntax error.
error: Incorrect command.
error: syntax error.
error: line no: 91
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done

When I boot this all I get is a grub prompt

After booting into Ubuntu I chmod -x /etc/grub.d/06_custom
and then update grub.

Then I get a standard grub boot based on os-prober.

The only difference between 12.04 and 13.04 is that 13.04 recognizes the Arch Linux installs.

I also tried grub-customizer on 12.04 64 bit and 13.04, but I deleted it.  It really made a mess of things.

After that I removed and completely reinstalled the grub components from synaptic.

Now I am back to an uncustomized grub menu.

Is there a new way to customize grub? I followed drs305 how to and followed this:
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

but am unable to get it customized.  I now use grub in 13.04 to control the grub menu.

Anybody else have this problem?  Any suggestions for fixes?

Edit: I have reinstalled grub-customizer on the 13.04 64 bit install. I am trying to tame the menu.  I really don't like to use ppa stuff.   Would really like to customize the grub manually.

---

### Post by Kirboosy on 2013-09-23
I would recommend deleting 06_custom and instead use the 40_custom or 41_custom file. What I do to make custom splash screens is take a working copy from /boot/grub/grub.cfg and write it to 40_custom. Then I edit and tweak everything till its what I want.

[Custom Grub2 Menus]("https://help.ubuntu.com/community/Grub2/CustomMenus")

Hope that helps!
~Caboose

---

### Post by deadflowr on 2013-09-23
Unfortunately, without knowing what the syntax error in line 91 is, it would be hard to help understand what the problem has been.
The error would be in /boot/grub/grub.cfg.new.

---

### Post by ubume2 on 2013-09-23
I couldn' find any syntax problems.

However, I went back into my 12.04 64 bit made a new 06_custom from from 40_custom, following the url 
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen), shut off 30_os-prober,

and grub works again!

I don't think custom grub likes those complicated lines in grub. A simple
> menuentry "Ubuntu 12.04" {
set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro quiet splash
        initrd /initrd.img
}
took care of it

Thanks.

---

### Post by oldfred on 2013-09-23
I had a typo in my 40_custom from almost the beginning of grub2. It was a missing end } and only that boot stanza did not show. Since it was an old install I never noticed it missing. But then new version of grub2 1.99 must have an improved checker as it would not update my 40_custom at all. Took me a while to realize I was missing something.

---

### Post by grahammechanical on 2013-09-23
This is the clue

> [COLOR=#000000]*error: line no: 91*[/COLOR]
[COLOR=#000000]*Syntax errors are detected in generated GRUB config file*[/COLOR]

If you examined /boot/grub.cfg and looked at line 91 you would have seen an error that was causing Grub to fail to load an OS. The file grub.cfg is generated from scripts in /etc/default/grub and /etc/grub.d/ One of these scripts will be your 06_custom file. It is my guess that something in 06_custom was wrong. Perhaps it is the spelling or the references to other operating system that are incorrect.

Of course, everything has since been changed. But it might help you an others the next time it happens. We can use 40_custom as a template but renaming it to something like 06_custom is acceptable. I use 15_custom and that will leave the Ubuntu that controls the MBR at the top of the Grub menu and put the other operating systems in 15_custom after it but before the memtest options.

The order for which these scripts are read and by which entries are listed in the Grub menu is

00; 05; 10; 20; 30; 40; 41. I am not sure it is wise to use 06. Better to use something between 10 and 20.

Graham

---

### Post by Dennis N on 2013-09-23
> **ubume2 said:**
> Would really like to customize the grub manually.

An easy way to make a custom menu:

Start with the working uncustomized **grub.cfg** and use the cut and paste method described here (same guide as recommended in post #2 above):

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

Personally, I make a separate file in **/etc/grub.d** for each OS I want on the custom menu. Just cut the menuentry section for an OS in its entirety from the working **grub.cfg** and paste into the **40_custom** template and use "save as" to save with a file name starting with 06_, 07_, 08_, or 09_. You don't have to name your files with the word "custom". **08_Ubuntu1304** is fine. All these files end up in **/etc/grub.d**. If you have more than four OS, double up - two files can start with the same number:

[B]07_a-Ubuntu-1204
07_b-Ubuntu-1210
08_Lubuntu-1304[/B]
are all good file names.

Note: Copy and paste will not get you maintainance free. Follow the suggestions at the end of the article to make it maintainance free.

---

### Post by deadflowr on 2013-09-23
> **oldfred said:**
> I had a typo in my 40_custom from almost the beginning of grub2. It was a missing end } and only that boot stanza did not show. Since it was an old install I never noticed it missing. But then new version of grub2 1.99 must have an improved checker as it would not update my 40_custom at all. Took me a while to realize I was missing something.

Sometimes all it takes is an extra space between characters or lines.
I had that problem once.

---

### Post by ubume2 on 2013-09-23
> **deadflowr said:**
> Sometimes all it takes is an extra space between characters or lines.
I had that problem once.

I might have had that problem in my custom script. Completely redoing the 06_custom from scratch apparently took care of the problem.   I wonder if the error on line 91 of grub.cfg.new (which appeared to be an empty line) was actually an error in my custom file.

I also chmod -x the /etc/grub.d/30_os-prober, so my menu items don't keep growing when I have a new kernel installed.  I try to keep the two latest kernels for each os. The way I have the menu set up, it always uses the latest kernel.

Thanks to all who contributed. All of you had good ideas. I will refer back to this thread if I have any more problems with grub. :)

---

