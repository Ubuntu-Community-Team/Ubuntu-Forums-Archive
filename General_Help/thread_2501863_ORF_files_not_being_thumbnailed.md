---
title: "ORF files not being thumbnailed"
date: 2024-10-23
forum: General Help
---

### Post by asherax on 2024-10-23
Firstly, thank you to the Ubuntu team and community for your incredible contributions and work you continue to do in making Ubuntu the great distro it is.

That out of the way, I have had INORDINATE issues trying to get Olympus .ORF files, the RAW files thumb-nailed. I have installed multiple programs, cleared caches, uninstalled, and rewritten files, but still I cannot get a thumb-nailer program of any description to recognize and thumbnail RAW files, let alone ORF files which are native to Olympus and OM Systems.

Has anyone had any luck or progress in this department?

There used to be a fix back in 20.04 days, but sadly this work around no longer works, and neither Debian, Flatpak, applmage, or Snap have a thumbnailer that can do this either out of the box or as a reconfigured file. 

Ive also used Nemo, and Thunar alongside Nautilus as my file managers, to no avail. 

That said, ORF files, as a species of RAW files can be processed and viewed effortlessly in Darktable, Rawtherapee and GIMP, even Gthumb handles them, so it is beyond me as to why I cannot generate a thumbnail.

Any assistance would be greatly appreciated.

<3

---

### Post by Norm24 on 2024-10-23
Since you're using Thunar do you have tumbler and tumbler-plugins-extra installed?

---

### Post by Holger_Gehrke on 2024-10-23
In addition to Norm24's hint: tumbler is configured through the file /etc/xdg/tumbler/tumbler.rc. This look just like an .ini file with sections starting with headings in brackets. Check that the RawThumbnailer(section '[RawThumbnailer]') isn't disabled ('Disabled=true'). There's also a line 'MaxFileSize=xxxxxxxxx' (set this to a size in bytes larger than the largest .orf file you want thumbnails for; set it to 0 to disable the file size check). The RawThumbnailer isn't installed by default, it's in the package tumbler-plugins-extra. The file is quite extensively commented, so it shouldn't be hard to understand.

Holger

---

### Post by asherax on 2024-10-26
Thank you both for your excellent and prompt advice. I had tumbler installed, but used synaptic to discover that tumbler plugins had indeed not been installed, so an easy fix. Thankyou Norm24! 

Holger your advice was very helpful also, although once configured, I utilized shotwell in EXT4 to run through the RAW files, not an issue!, once tumbler-plugins-extra was installed through synaptic, and configuration checked with Thunar file manager to ensure Raw Thumbnailer was enabled (Disabled=False) and 'Maxfilesize' set to 0 to allow large enough RAWS in HD to image without issue, RAW thumbnails worked a treat, and you can utilize any image photo-manager you like to process RAWS. 

Thank you both for your excellent advice, BUT!........ and this is going to sound peculiar, after going through the process, I find that the fix is temporary. This is of course probably down to the fact that I have kept Nautilus EX4 as my main file system. I installed Thunar alongside it to see whether I liked it as an alternative, and whilst it has many advantages, I am willing to give Nautilus the benefit of the doubt and see if we cant get this thing functioning as it should. 

Whilst the aforementioned fix with Thunar and the Raw-thumbnailer, alongside the addition of tumbler-plugin-extra and tumbler installed through synaptic did in fact solve the issue, when the ORF (RAW) files are initially opened in Thunar file manager by default, converting all the ORFs in that file into workable thumbnails, this only works if each file folder opened also has Thunar file manager utilized as the default file option, which of course is great for converting the ORFs (RAWS) in each file into workable thumbnail images, but is of course absolutely useless when wanting to open those ORF's or view them within a regular Photographic or image viewer or editor, like GThumb, XnView, Rawtherepee, Darktable, shotwell, Eye of Gnome.... etc etc, without individually selecting each thumbnail ORF and selectively opening them in the program of your desire. 

The second issue may well come when the Thumb cache is cleared when cleaning the drives with something like Bleachbit, for regular system maintenance, which will of course wipe the cache files and you are back to square one. 

So although it is possible to reinstall the system using Thunar or perhaps Nemo, instead of Nautilus, and avoid this issue entirely, the issue will remain until Nautilus allows tumbler and tumbler plugins extra to become part of the depository, either Debian or snap as far as I can see. 

Unless of course better minds than mine can figure out a solution. 

Thanks guys for your great responses though, it is a work around, only, it's kind of a partial fix at this stage.

---

### Post by asherax on 2024-10-26
THIS might be the issue. In Home/.Cache/Thumbnails/ Tumbler.rc Nautilus.

# RAW image files using libopenraw (the libopenraw pixbuf loader is kind of
# broken, hence the priority)
[RawThumbnailer]
Disabled=false
Priority=1
Locations=
Excludes=
MaxFileSize=0


[https://github.com/xfce-mirror/tumbler/blob/master/tumblerd/tumbler.rc](https://github.com/xfce-mirror/tumbler/blob/master/tumblerd/tumbler.rc)

---

