---
title: "Custom icons for Burg theme"
date: 2013-01-31
forum: General Help
---

### Post by guari on 2013-01-31
Hi all, 
when using Burg as default bootloader I found that many themes available on the web display only the icons for any operative system but no name for the selected entry so it's difficult to distinguish between one and another entry at boot time when they have the same icon and nothing else.

In case it can be usefull to someone else I write here the little changes I did to have a more usable burg theme, the common target here is who would like to use a theme with only icons (like sora-clean and derivated) and have multiple ubuntu, windows or other distributions installed on the hard drive:

First you have to add your new icons (eg. the one for ubuntu recovery or windows 7 or vista etc.) in */boot/burg/themes/YOURSELECTEDTHEME/icons/* (here you'll find the default icons of the selected theme)
eg. assume we'll add here normal_ubunturecovery.png, hover_ubunturecovery.png, normal_windows7.png, hover_windows7.png

Then open the file */boot/burg/themes/YOURSELECTEDTHEME/icons/icons *and add the correct lines for the icons inserted:
```

+class
{
  -windows { image = "$$/normal_windows.png:$$/hover_windows.png" }
  -windows7 { image = "$$/normal_windows7.png:$$/hover_windows7.png" }
...
  -ubuntu { image = "$$/normal_ubuntu.png:$$/hover_ubuntu.png" }
  -ubunturecovery { image = "$$/normal_ubunturecovery.png:$$/hover_ubunturecovery.png" }
...
}
```

Ok, now we have to change burg configuration scripts in order to recognize the correct icons:
for windows or mac open */etc/burg.d/30_os-prober* with a text editor and add the corresponding lines:
eg. to link windows 7 icon
```

...
  s=`echo :${GRUB_CLASS_OVERRIDE}: | sed "s,.*:${DEVICE}=\([^:]*\):.*,\1,"`
  if test "x$s" != "x:${GRUB_CLASS_OVERRIDE}:" ; then
    OSLABEL="$s"
  fi

[B]  #MODIFY OSLABEL FOR WINDOWS 7
  case ${LONGNAME} in
  Windows?7*)	
	OSLABEL=windows7            
	;;
  esac
  get_auth_option ${OSLABEL}[/B]

  echo "Found ${LONGNAME} on ${DEVICE}" >&2
...

```

then for linux entry we need to modify the file */etc/burg.d/10_linux*:
eg. to link ubuntu recovery mode icon
```

...
  if ${recovery} ; then
    title="$(gettext_quoted "%s, with Linux %s (recovery mode)")"
    auth_option=${AUTH_RESCUE}
    [B]#MODIFY OSCLASS FOR UBUNTU RECOVERY 
    CLASS="--class ${OSLABEL}recovery"[/B]
  else
...
```

Finally save all, give a 'sudo update-burg' command into a terminal (and, if you have installed burg manager emulate burg to verify that everything works as it should), then reboot to see your new different icons for all your systems/entries ;)

ADVICE: if you change $oslabel in burg configuration and then you switch to another theme you have to add the missing icons also to that theme.

---

