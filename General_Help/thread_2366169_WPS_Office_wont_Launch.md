---
title: "WPS Office wont Launch"
date: 2017-07-14
forum: General Help
---

### Post by jaren2004 on 2017-07-14
I tried i opening wps office after the alpha 21 update but it wont update anymore so i tried opening it through the terminal but it just gave me this
 /usr/bin/wps: line 38:   920 Segmentation fault      (core dumped) ${gInstallPath}/office6/${gApp} ${gOptExt} ${gOpt} "$@"

Please help i really neeed wps office for business reasons

---

### Post by #&amp;thj^% on 2017-07-14
Can you use the stable branch?  [https://www.wps.com/download](https://www.wps.com/download)
 alpha 21 I would think to be less stable.
It states you first need to uninstall the older version before installing the a21_amd64.deb.
Give that a try, then install the newer version.

---

### Post by jaren2004 on 2017-07-14
ok well i tried tried that but i still got an error code when i launched it from the terminal heres the error code
/usr/bin/wps: line 38: 29533 Segmentation fault      (core dumped) ${gInstallPath}/office6/${gApp} ${gOptExt} ${gOpt} "$@"

---

### Post by #&amp;thj^% on 2017-07-14
Seems they are having a few errors being reported here: [http://wps-community.org/forum/viewtopic.php?f=4&t=313](http://wps-community.org/forum/viewtopic.php?f=4&t=313)
I would direct your questions there for a possible quicker reply.
You also could try installing the older version to get your work done in the meantime.

---

### Post by jaren2004 on 2017-07-14
Alright thanks for the tips

---

### Post by #&amp;thj^% on 2017-07-14
Hmm? BTW I see no problems on my end here:
```
apt policy wps-office
wps-office:
  Installed: 10.1.0.5707~a21
  Candidate: 10.1.0.5707~a21
  Version table:
 *** 10.1.0.5707~a21 100
        100 /var/lib/dpkg/status

```
If it helps line#38 in "/usr/bin/wps" on mine only Reads like
```
{
```
In fact here is the complete file as it reads on mine:
```
#!/bin/bash

gOpt=
#gOptExt=-multiply
gTemplateExt=("wpt" "dot" "dotx")
gBinPath=$(dirname "$0")
if [ -d "${gBinPath}/office6" ]; then
	gInstallPath=${gBinPath}
else
	gInstallPath=/opt/kingsoft/wps-office
fi
gApp=wps
gDaemon=0

function parse_arg()
{
	if [ "$1" == "-quickstart" ]; then
		gOpt=-quickstart
		gDaemon=1
		return 0
	fi
	if [ $# -eq 1 ] ; then
		ext="${1##*.}"
		if [ "" = "${ext}" ] ; then
			return 0
		fi

		for i in ${gTemplateExt}
		do
			if [ "${ext}" = "${i}" ] ; then
				gOpt=-t
			fi
		done
	fi
}

function run()
{  [COLOR="#FF0000"] <'---INFORMATION ONLY This is line 38[/COLOR]
	oldPwd="${PWD}"
	if [ -e "${gInstallPath}/office6/${gApp}" ] ; then
		if [ 1 -eq ${gDaemon} ]; then
			nohup ${gInstallPath}/office6/${gApp} ${gOpt} > /dev/null 2>&1 &
		else
			${gInstallPath}/office6/${gApp}  ${gOptExt} ${gOpt} "$@"
		fi
	else
		echo "${gApp} does not exist!"
	fi
}

function main()
{
	parse_arg "$@"
	run "$@"
	exit 0
}

main "$@"
```

---

### Post by jaren2004 on 2017-07-20
well i tried uninstalling everything and re installing but nothing worked so i guess ill just stick with the old version

but thanks for trying to help anyway.

---

### Post by speartip on 2017-07-20
> **jaren2004 said:**
> well i tried uninstalling everything and re installing but nothing worked so i guess ill just stick with the old version

but thanks for trying to help anyway.
Did you delete the old profile in your Home folder?
If not, after uninstalling, delete the 2 kingsoft folders in your /Home/.config folder, then reinstall.

---

### Post by joyjeetchowdhury-gmail on 2018-04-09
Dear All,

finally i found the problem. 

I was using Ubuntu 18.04, Once i tried WPS office it was working find but since i installed KDE then the problem begin, kindly follow the following steps

first download and install libpng12 from the following link:  [https://packages.ubuntu.com/xenial/amd64/libpng12-0/download](https://packages.ubuntu.com/xenial/amd64/libpng12-0/download)

it will help you run WPS office in the default version of the Ubuntu that is GTK+

Segmentation fault is appearing due to the theme of design which may not have sufficient styles for some elements of WPS Office interface.

so try doing as following in the command prompt

GTK2_RC_FILES=/usr/share/themes/Adwaita/gtk-2.0/gtkrc et -style GTK+   //Spreadsheet
GTK2_RC_FILES=/usr/share/themes/Adwaita/gtk-2.0/gtkrc wps -style GTK+  //Writer
GTK2_RC_FILES=/usr/share/themes/Adwaita/gtk-2.0/gtkrc wpp -style GTK+  //Presentation


if the above works, then you can add them in the menu command to work. 

Kindly pardon me. i'm not sure if you like to do it on the global environment or not, if you like to do so then you can try the following

in the file   ~ / .config / Trolltech.conf

please find and edit under [Qt]
Style=adwaita

which is by the way blank in case of desktop default settings.

Best Regards,

Joy

---

### Post by mslx on 2018-04-28
> **joyjeetchowdhury-gmail said:**
> Dear All,

finally i found the problem. 

I was using Ubuntu 18.04, Once i tried WPS office it was working find but since i installed KDE then the problem begin, kindly follow the following steps

first download and install libpng12 from the following link:  [https://packages.ubuntu.com/xenial/amd64/libpng12-0/download](https://packages.ubuntu.com/xenial/amd64/libpng12-0/download)

it will help you run WPS office in the default version of the Ubuntu that is GTK+

Segmentation fault is appearing due to the theme of design which may not have sufficient styles for some elements of WPS Office interface.

so try doing as following in the command prompt

GTK2_RC_FILES=/usr/share/themes/Adwaita/gtk-2.0/gtkrc et -style GTK+   //Spreadsheet
GTK2_RC_FILES=/usr/share/themes/Adwaita/gtk-2.0/gtkrc wps -style GTK+  //Writer
GTK2_RC_FILES=/usr/share/themes/Adwaita/gtk-2.0/gtkrc wpp -style GTK+  //Presentation


if the above works, then you can add them in the menu command to work. 

Kindly pardon me. i'm not sure if you like to do it on the global environment or not, if you like to do so then you can try the following

in the file   ~ / .config / Trolltech.conf

please find and edit under [Qt]
Style=adwaita

which is by the way blank in case of desktop default settings.

Best Regards,

Joy

Thanks! The library file works like charm :guitar:

---

