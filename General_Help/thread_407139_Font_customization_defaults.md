---
title: "Font customization defaults"
date: 2007-04-11
forum: General Help
---

### Post by Cody8417 on 2007-04-11
I'm using Ubuntu Edgy 6.10.  Using the ubuntu guide,
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Extra_Fonts](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Extra_Fonts)

I installed the MS fonts, however I also did the last bit about making the fonts look better.  However, everything is now pixelated and very distracting.  Is there anyway to revert back to the defaults?

Thanks
-Chris

---

### Post by rai4shu2 on 2007-04-11
Where did you observe this problem? You could try removing one or more of the MS fonts from your ~/.fonts folder and see what happens when you restart whatever program gives you problems.

You could add the following to "~/.fonts.conf" and see if this helps:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<!-- /etc/fonts/conf.d/no-bitmaps.conf -->
<fontconfig>
<!-- Reject bitmap fonts -->
 <selectfont>
  <rejectfont>
   <pattern>
     <patelt name="scalable"><bool>false</bool></patelt>
   </pattern>
  </rejectfont>
 </selectfont>
</fontconfig>
```

---

### Post by Cody8417 on 2007-04-11
```
wget http://www.osresources.com/files/centos-windows-fonts/fontconfig.tbz
sudo tar xvjpf fontconfig.tbz -C /etc/fonts/
```

That was the command that caused the pixelation of fonts.  It occurs in OpenOffice and in the title bars of all programs.

---

