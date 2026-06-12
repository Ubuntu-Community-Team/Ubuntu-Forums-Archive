---
title: "Unable to use SCIM in java programs and OpenOffice"
date: 2008-05-21
forum: General Help
---

### Post by MagiSu on 2008-05-21
Hi all!
I've met a small problem using 8.04. I installed Kubuntu and enjoyed it, but found myself unable to use SCIM under OpenOffice, Google Earth or NetBeans: it simply do not activated using hotkey or any other ways. I tried to deal it myself but failed, here is my configure file:

--/etc/X11/xinit/xinput.d$ cat scim
XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes
GTK_IM_MODULE=xim
QT_IM_MODULE=xim
XMODIFIERS=@im=SCIM
DEPENDS="scim,scim-anthy|scim-canna|scim-chewing|scim-pinyin|scim-hangle|scim-prime|scim-skk|scim-tables-additional|scim-m17n|scim-uim|scim-tables-ja|scim-tables-ko|scim-tables-zh"

--~$ locale
LANG=en_US.UTF-8
LANGUAGE=en_US.UTF8
LC_CTYPE=zh_CN.UTF8
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

Any suggestions? Thank you very much.

---

### Post by Zorael on 2008-05-21
I think this is a bug with the OpenOffice version available from the Ubuntu repos which pops up every now and then. Googling it turns up some reports saying that the initial version bundled with (Ubuntu) 7.04 worked but a shortly following update broke it again. Solution is said to be to install the version available from openoffice.org itself.

I seem to have the issue myself so I'll go ahead and try it and then post results.

---

### Post by Zorael on 2008-05-21
Not recommended, didn't work and hard to revert.

---

### Post by Zorael on 2008-05-21
It doesn't seem to obey scim.

Worked for me if I removed the [FONT="Courier New"]openoffice.org-kde[/FONT] package and installed the [FONT="Courier New"]openoffice.org-gnome[/FONT] package instead, but now it looks ugly with missing borders on some menus.

---

### Post by Zorael on 2008-05-21
[FONT="Courier New"]openoffice.org-kde seems[/FONT] to be the key, yes. Uninstall it and grab the [FONT="Courier New"]-gnome[/FONT] one instead.

I posted a bug over at launchpad; [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/232499](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/232499). Confirm it if your findings match mine.


edit: As for it not working in *other* programs, try to edit your [FONT="Courier New"]/etc/X11/xinit/xinput.d/scim[/FONT] file according to the one I posted as an attachment to that launchpad bug, changing **xim** to **scim-bridge**.

---

### Post by tacutu on 2008-05-21
what's the output of:
 ```
im-switch -l
```

---

### Post by Zorael on 2008-05-21
Mine is the following.
```
$ im-switch -l
Your input method setup under en_US locale as below.
=======================================================
No private "/home/familjen/.xinput.d/en_US or /home/familjen/.xinput.d/all_ALL" is defined.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-en_US" .
No alternatives for xinput-en_US.
=======================================================
The available input method configuration files are:
/usr/bin/find: /home/familjen/.xinput.d: No such file or directory
default default-xim none scim scim-bridge scim-immodule skim th-xim
=======================================================
```
But as mentioned, scim works in everything else, just not OO.o.

---

### Post by tacutu on 2008-05-21
i set my input method using im-switch (this being the preferred method) and I have no problems whatsoever with oo or java or any other app for that matter.

If it matters, I use gnome but I suppose it should work the same in kde.

see also: [http://ubuntuforums.org/showthread.php?t=757070](http://ubuntuforums.org/showthread.php?t=757070)
and let me know if you succeed.

---

### Post by Zorael on 2008-05-21
Do you have the [FONT="Courier New"]openoffice.org-kde[/FONT] package installed? If not, then no, it's not the same.

---

### Post by MagiSu on 2008-05-22
Your input method setup under zh_CN locale as below.
=======================================================
The configuration "/home/magi/.xinput.d/zh_CN" is defined as a link pointing to
skim
This private configuration supersedes the system wide default.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-zh_CN" .
xinput-zh_CN - status is auto.
 link currently points to scim-bridge
scim-pinyin - priority 50
scim-bridge - priority 60
scim - priority 50
scim-immodule - priority 0
skim - priority 50
Current `best' version is scim-bridge.
=======================================================
The available input method configuration files are:
default default-xim none scim scim-bridge scim-immodule scim-pinyin skim th-xim
=======================================================


Well, I have tried to switch XIM into SCIM-BRIDGE, but both not work. I just cannot figure what happened. I can switch to Deutsch keyboard, and type character like ÄÜÖ in Openoffice, but I cannot start SCIM.

---

### Post by Zorael on 2008-05-29
So I've got it working for me now. Turns out that applications that listened for input from XIM were set up to actually use XIM and not scim. These included OpenOffice and Java applications. To test it, start up [FONT="Courier New"]xterm[/FONT] and see if scim works there.

I'll make it thorough.

```
$ ls /etc/alternatives/xinput* -l
lrwxrwxrwx 1 root root 28 2008-05-28 00:50 /etc/alternatives/xinput-all_ALL -> **/etc/X11/xinit/xinput.d/skim**
lrwxrwxrwx 1 root root 35 2008-05-28 00:50 /etc/alternatives/xinput-ja_JP -> **/etc/X11/xinit/xinput.d/scim-bridge**
*(truncated)*
```
As illustrated above, in **my** system, the [FONT="Courier New"]skim[/FONT] and [FONT="Courier New"]scim-bridge[/FONT] files (in [FONT="Courier New"]/etc/X11/xinit/xinput.d/[/FONT]) are the *input alternatives* defined to be used for my relevant languages. They are configuration files regarding which input methods to use for XIM, Qt and GTK programs. A more intuitive way of displaying which alternatives are available to a given language be to enter the following in a terminal.
```
$ sudo update-alternatives --config xinput-*<language>*
```
Ascertain which alternatives are chosen on your system; if you're using Ubuntu, you probably don't have [FONT="Courier New"]skim[/FONT] picked for anything. **Likely only the [FONT="Courier New"]xinput-all_ALL[/FONT] one matters**, but if you have other ones that you actually use *as global locales* for the whole desktop, try (if possible) to set them all to the same setting. Makes things clean and consistent.

Modify the file(s) they reference towards to look like the following. Again, these are located under [FONT="Courier New"]/etc/X11/xinit/xinput.d/[/FONT]. **Backup first.**
```
[B]XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS=-d
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes[/B]

if [ -e /usr/lib/gtk-2.0/*/immodules/im-scim-bridge.so ]; then
**    GTK_IM_MODULE="scim-bridge"**
elif [ -e /usr/lib/gtk-2.0/*/immodules/im-scim.so ]; then
**    GTK_IM_MODULE=scim**
else
    GTK_IM_MODULE=xim
fi
if [ -e /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so ] || [ -e /usr/lib/qt4/plugins/inputmethods/im-scim-bridge.so ]; then
**    QT_IM_MODULE="scim-bridge"**
elif [ -e /usr/lib/qt3/plugins/inputmethods/libqscim.so ]; then
**    QT_IM_MODULE=scim**
else
    QT_IM_MODULE=xim
fi

DEPENDS=
```
No dependencies should need to be defined on the [FONT="Courier New"]DEPENDS=[/FONT] line, since it'll detect whether to use scim-bridge, scim or xim, but if you want to you could copy the line from your [FONT="Courier New"]scim[/FONT]/[FONT="Courier New"]scim-bridge[/FONT]/[FONT="Courier New"]skim[/FONT] backup file(s).

---

