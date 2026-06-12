---
title: "Problems with Ubuntu partition and maybe HDD"
date: 2017-02-06
forum: General Help
---

### Post by hernandeza on 2017-02-06
Hello to everyone,

I have an ASUS laptop. It is exactly this one: [https://www.cnet.com/products/asus-k55vm-sx090v-15-6-core-i7-3610qm-8-gb-ram-500-gb-hdd/specs/](https://www.cnet.com/products/asus-k55vm-sx090v-15-6-core-i7-3610qm-8-gb-ram-500-gb-hdd/specs/) (ASUS K55 VM). Since a couple of years, I have had Ubuntu 14.04 and Windows 7 in the same HDD and it all worked really well and fast. A couple of weeks ago, the laptop started to work really slow and, after that, Ubuntu (where all my personal information is stored) would not login anymore. However, Windows still runs perfect. I think I the HDD is damaged (below I say why). All the information I have gathered is the following:

I have an aprox 300GB partition with Ubuntu installed and another one with Windows 7 (aprox 80GB). GRUB works as it allows me choose the desired SO. However, if I choose Windows, everything works but, if I choose Ubuntu, apart from loading the SO really slow, when I get to the login screen, I write my username and password and then nothing happens. If I press CTRL+ALT+F1 to run the terminal, this shows up:

[[IMG]https://s27.postimg.org/8o25fxpdf/6_DGQwt_P.jpg[/IMG]]("https://postimg.org/image/nws2tpj1r/")[


It clearly says that there are some error in some sectors of the HDD and it does not allow me to execute commands. If I boot my computer and go into advanced options for Ubuntu and choose recovery mode, the following screen appears:

[IMG][[IMG]https://s27.postimg.org/4ir8u0rlf/i9_E5v_Np.jpg[/IMG]]("https://postimg.org/image/nnui3s69b/")[/IMG]

I have both executed dpkg and fsck. Dpkg ends up with:

[IMG][[IMG]https://s27.postimg.org/4u8p6s81f/G4e_Fbl2.jpg[/IMG]]("https://postimg.org/image/r66i0675b/")[/IMG]

So, in the end, no packages are installed, right?

On the other hand, executing fsck ends up in:

[IMG][[IMG]https://s27.postimg.org/ehc7gi10z/IY1j_T6s.jpg[/IMG]]("https://postimg.org/image/oen89k8mn/")[/IMG]

I have also tried to use an Ubuntu LiveCD to try to rescue files from the Ubuntu system, and also use the Windows (with ext2 readers) to try to rescue files. 

The case regarding the live CD gives me this error:

[IMG][[IMG]https://s27.postimg.org/4syrdd67n/c_BLDwj_M.jpg[/IMG]]("https://postimg.org/image/h7ljdoxpr/")[/IMG]

Which is the same error as trying to carry out the extraction graphically:

[IMG][[IMG]https://s27.postimg.org/ra0bgfcmr/SOC29r_P.jpg[/IMG]]("https://postimg.org/image/84x26nxyn/")[/IMG]

From windows, with Ext2/4 readers... some files can be retrieved but not all of them (I supossed the damaged ones). The question is, I need to retrieve as much information from Ubuntu as possible, does anyone know how?

Sorry for my English, I have tried to describe the situation as accurate as possible, but if you need anything else to know about to help me, just say it.

Thank you very much

---

### Post by oldfred on 2017-02-06
Please post screen shots & photos as attachments, not in line. 
Not everyone has high speed Internet.
You can easily attach with the Forum's advanced editor and paperclip icon.

Post this:
sudo parted -l

And  run full e2fsck on all ext4 partitions.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdXY to your partition(s) like sda5
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdXY
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdXY

---

### Post by Bashing-om on 2017-02-06
hernandeza; Hello; My Welcome to the forum .

Hard drive file system issues are certainly indicated.
How about we take the system's advise to run the file system check manually ?
Boot a liveDVD(USB) and from terminal run:

[color=red]swap off if necessary[/color], change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
Identify the target !
```

sudo parted -l

```
run a simple check:
```

sudo e2fsck -C0 -p -f -v /dev/sda1

```
#if errors: -y auto answers yes for fixes needing response see: man e2fsck
```

sudo e2fsck -f -y -v /dev/sda1

```
fsck [http://www.thegeekstuff.com/2012/08/fsck-command-examples/](http://www.thegeekstuff.com/2012/08/fsck-command-examples/)

Now if there are continued problems we need to see these outputs as text - posted between code tags. 
 code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

As it will be real tough to work from images .

[INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT]

---

