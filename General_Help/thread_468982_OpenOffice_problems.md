---
title: "OpenOffice problems"
date: 2007-06-09
forum: General Help
---

### Post by dpsguard on 2007-06-09
Hi All,

I have Ubuntu 7.04 with Gnome office on it. I have just installed openoffice 2.2. On starting, openoffice program, all I see is first splash screen and after few minutes that goes away as well without starting the program. During the time of display of splash screen, harddisk light is continuously lit and CPU / memory seems to be almost 100% in use (I can not verify the utilization as during this time, even terminal does not start ).

Please advise as to what could be the problem and how should I fix it.

Thanks

---

### Post by loathsome on 2007-06-09
You could try reinstalling OpenOffice.

Other than that, I can't help you very much.

---

### Post by dpsguard on 2007-06-09
Thanks. I had tried it twice already and that did not help. Rather, after uninstallaling openoffice, everytime, rebooting computer causes it to forced disk error check and it is not able to recover, requiring me to start computer from live CD and then do a fsck, fix some inodes  and other issues and then computer recovers. Installing openoffice does the same thing, just an opening flash screen. Uninstalled again, again have to do fsck and it is the same cycle then.

To me it looked like some bug, but I have not been able to identify.

Appreciate again your help.

---

### Post by loathsome on 2007-06-09
Do you use KDE? If so, try grabbing the 'openoffice.org-kde' package.

OO is unusable without that under KDE :)

---

### Post by Mohammed Abbas on 2007-06-10
I also have this problem , splash screen shows for a few seconds then nothing happens !
any suggestions ?

---

### Post by loathsome on 2007-06-11
> **Mohammed Abbas said:**
> I also have this problem , splash screen shows for a few seconds then nothing happens !
any suggestions ?

Did you try my suggestion?

---

### Post by Rui Pais on 2007-06-11
Hi, 
sometimes Oo borke they own configuration files.

Get fresh config with:
```
mv .openoffice.org2 .openoffice.org2_BACKUP
```

and restart OO



Edit:
You can too start from command line and check for any warning/errors output. The coomand line is:
ooffice 
or
oowrite

---

### Post by loathsome on 2007-06-11
> **Rui Pais said:**
> Hi, 
sometimes Oo borke they own configuration files.

Get fresh config with:
```
mv .openoffice.org2 .openoffice.org2_BACKUP
```

and restart OO



Edit:
You can too start from command line and check for any warning/errors output. The coomand line is:
ooffice 
or
oowrite

Remember to do this from your home folder, or else it wont work!

**[COLOR="DarkSlateGray"]$ mv ~/.openoffice.org2 openoffice.org2_backup[/COLOR]**

---

### Post by Rui Pais on 2007-06-11
> **loathsome said:**
> Remember to do this from your home folder, or else it wont work!

**[COLOR="DarkSlateGray"]$ mv ~/.openoffice.org2 openoffice.org2_backup[/COLOR]**

:)
as long as it don't have sudo ... it's "almost" implicit that you need do it as user and inevitably at home.

Thanks for the note. 

(btw, then your command should be:
mv ~/.openoffice.org2 **~/**openoffice.org2_backup 
or if user is not at his/her home folder it will fail with incorrect permissions.)

---

### Post by Mohammed Abbas on 2007-06-11
I get this message in terminal :

[B]*** glibc detected *** /usr/lib/openoffice/program/soffice.bin: free(): invalid pointer: 0x080d1600 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6c8d7cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb6c90e30]
/usr/lib/openoffice/program/libuno_sal.so.3(rtl_freeMemory+0x1d)[0xb72e60bd]
/usr/lib/openoffice/program/soffice.bin[0x809192e]
/usr/lib/openoffice/program/soffice.bin(_ZdlPv+0x26)[0x8091966]
/usr/lib/libscim-1.0.so.8[0xa9772156]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xa9772f77]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xa976df05]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so[0xa9814f7b]
/usr/lib/libgobject-2.0.so.0(g_type_class_ref+0x381)[0xb5c96b41]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0xa2f)[0xb5c7d1cf]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x21f)[0xb5c7d5ef]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb5c7d7a0]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(_Z23gtk_im_context_scim_newv+0x67)[0xa9809b57]
/usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so(im_module_create+0x3c)[0xa981927c]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_im_module_create+0xb9)[0xb5772d29]
/usr/lib/libgtk-x11-2.0.so.0[0xb577393b]
/usr/lib/libgtk-x11-2.0.so.0[0xb5773b39]
/usr/lib/libgtk-x11-2.0.so.0(gtk_im_context_set_client_window+0x4e)[0xb5770f0e]
/usr/lib/libgtk-x11-2.0.so.0[0xb571a71f]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49)[0xb5c849d9]
/usr/lib/libgobject-2.0.so.0[0xb5c75e49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb5c7762b]
/usr/lib/libgobject-2.0.so.0[0xb5c8859a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb5c89627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb5c897e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0xba)[0xb58aebea]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_set_parent+0x1de)[0xb58af1ce]
/usr/lib/libgtk-x11-2.0.so.0(gtk_fixed_put+0xd3)[0xb5747ec3]
/usr/lib/libgtk-x11-2.0.so.0[0xb5747f08]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__OBJECT+0x59)[0xb5c83ee9]
/usr/lib/libgobject-2.0.so.0[0xb5c75e49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb5c7762b]
/usr/lib/libgobject-2.0.so.0[0xb5c8859a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb5c89627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb5c897e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_add+0x12c)[0xb56fe1bc]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb59e22bd]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb59e4043]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb59eeabd]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e41ff5]
/usr/lib/openoffice/program/libvcl680li.so[0xb7dcf09b]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11ModalDialogC2EP6WindowRK5ResId+0x67)[0xb7dcfac7]
/usr/lib/openoffice/program/libsvt680li.so(_ZN12WizardDialogC2EP6WindowRK5ResIdhs+0x3e)[0xb789c99e]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt14OWizardMachineC2EP6WindowRK5ResIdmhhs+0x4a)[0xb786e1da]
/usr/lib/openoffice/program/libsvt680li.so(_ZN3svt13RoadmapWizardC2EP6WindowRK5ResIdmS5_h+0x4f)[0xb786b55f]
/usr/lib/openoffice/program/libspl680li.so[0xa991d926]
/usr/lib/openoffice/program/libspl680li.so[0xa9914024]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop4MainEv+0xd59)[0x806bc39]
/usr/lib/openoffice/program/libvcl680li.so[0xb7c4fc3c]
/usr/lib/openoffice/program/libvcl680li.so(_Z6SVMainv+0x35)[0xb7c4fd45]
/usr/lib/openoffice/program/soffice.bin(main+0x65)[0x805ff85]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb6c3bebc]
/usr/lib/openoffice/program/soffice.bin(__gxx_personality_v0+0x249)[0x805fe11]
======= Memory map: ========
08048000-0809c000 r-xp 00000000 03:08 864035     /usr/lib/openoffice/program/soffice.bin
0809c000-0809e000 rw-p 00053000 03:08 864035     /usr/lib/openoffice/program/soffice.bin
0809e000-08378000 rw-p 0809e000 00:00 0          [heap]
a9600000-a9621000 rw-p a9600000 00:00 0 
a9621000-a9700000 ---p a9621000 00:00 0 
a9707000-a9709000 r-xp 00000000 03:08 767462     /usr/lib/libscim-x11utils-1.0.so.8.1.0
a9709000-a970a000 rw-p 00001000 03:08 767462     /usr/lib/libscim-x11utils-1.0.so.8.1.0
a970a000-a97de000 r-xp 00000000 03:08 767458     /usr/lib/libscim-1.0.so.8.1.0
a97de000-a97ec000 rw-p 000d4000 03:08 767458     /usr/lib/libscim-1.0.so.8.1.0
a97fd000-a981e000 r-xp 00000000 03:08 830762     /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so
a981e000-a981f000 rw-p 00021000 03:08 830762     /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so
a981f000-a987f000 rw-s 00000000 00:08 1081374    /SYSV00000000 (deleted)
a987f000-a988f000 r-xp 00000000 03:08 863828     /usr/lib/openoffice/program/libfileacc.so
a988f000-a9890000 rw-p 00010000 03:08 863828     /usr/lib/openoffice/program/libfileacc.so
a9890000-a98ed000 r-xp 00000000 03:08 863885     /usr/lib/openoffice/program/libpackage2.so
a98ed000-a98f0000 rw-p 0005d000 03:08 863885     /usr/lib/openoffice/program/libpackage2.so
a98f0000-a9902000 r-xp 00000000 03:08 440348     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
a9902000-a9903000 rw-p 00012000 03:08 440348     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
a9903000-a9935000 r-xp 00000000 03:08 86392
** (process:5821): WARNING **: Unknown error forking main binary / abnormal early exit ...
[/B]

---

### Post by loathsome on 2007-06-11
Try reinstalling gtk and X11 utilities and report back.

---

### Post by dpsguard on 2007-06-11
Loathsome, sorry for responding back late. I have been out of town. I do not use KDE, just the GNOME. I have tried your other suggestions and I still have the same issue. If I start from terminal, atleast I can kill this sooner by pressing Ctrl-C. 

Please advise anything else you want me to try.

Thanks

---

### Post by loathsome on 2007-06-12
I'm sorry, I'm (currently) out of ideas :p

Somebody else will have to help you from here.

---

### Post by Macchi on 2007-06-12
I believe that when you reinstall things it is a good idea to first remove them with "sudo apt-get remove --purge PACKAGE_NAME" in order to clean any previous configuration files that may be creating problems at a system level. Locally you can also clean the specific configuration files such as in .openoffice.org2 etc

OpenOffice is integrated with Gnome and messing around with them may break so many things that I can't imagine how easy or hard it will be to fix it. After wild experiments I think that a good backup and reinstalation is a safe way to get back a stable system. That's why it is good to have /home on a separate partition and have a different username for installation  and administration. Sorry, but I have no other suggestions right now.

PS: By the way I am trying to find a solution for a mysterious OOffice Base bug in a wizard that does not terminate.

---

### Post by swisscow on 2007-06-12
> **loathsome said:**
> Do you use KDE? If so, try grabbing the 'openoffice.org-kde' package.

OO is unusable without that under KDE :)

Out of interest, why do you say this? I have no problems without it. I installed directly from open-office.org, making the debs myself

---

### Post by dpsguard on 2007-06-12
Macchi, 

I have always uninstalled openoffice complete by using purge option. So I did this once again. Howover I noticed that I still had (after rebooting my machine as well) .openoffice.org2 directory in my home directory. I deleted that, restarted my machine and then installed just the spreadsheet program. This time, splash screen showed faster progress war of loading the program and it got to the end and then splash screen disappeared.  To me it appears to be some timing issue and that after waiting for some time, it simply times out.  If I launch it from terminal, I do not see any thing appearing on terminal window. During the time of display of splash screen, hard disk light is continuous lit and I can not do anything else (other than moving the mouse curser around, can not even open a new terminal window as if all CPU and memory is consumed by this hung openoffice process.

Thanks

---

### Post by dpsguard on 2007-06-12
Folks,

Since I had this time installed only the spreadsheet, I started it from terminal via oocalc ( I have been earlier trying to start it from GUI or as ooffice from terminal) and now I could see some message pop up. As per this it is a java issue, however I have latest JRE installed:

dpsguard@dpsguard-laptop:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
dpsguard@dpsguard-laptop:~$ oocalc
javaldx: Could not find a Java Runtime Environment! 
Bus error (core dumped)

Please advise.

Thanks

---

### Post by dpsguard on 2007-06-12
Missed some last lines of exception dump info that appeared on the terminal window:

Bus error (core dumped)

(process:7475): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:7475): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:7475): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:7475): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

** (process:7395): WARNING **: Unknown error forking main binary / abnormal early exit ...

---

### Post by Rui Pais on 2007-06-13
> **dpsguard said:**
> Folks,

Since I had this time installed only the spreadsheet, I started it from terminal via oocalc ( I have been earlier trying to start it from GUI or as ooffice from terminal) and now I could see some message pop up. As per this it is a java issue, however I have latest JRE installed:

dpsguard@dpsguard-laptop:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
dpsguard@dpsguard-laptop:~$ oocalc
javaldx: Could not find a Java Runtime Environment! 
Bus error (core dumped)

Please advise.

Thanks

i have read a lot of times around the advise to not use the 1.6 version of java that seems to have serious instabilities on Linux.
Maybe purging that version and install the 1.5 to see if it goes better. You can always return to 1.6 if that don't solve your problem.
(personally i have 1.5. It works... or at least i don't note nothing wrong. I never update java stuff, unless something specifically need it. I had serious troubles with it before.)

I have read a lot of posts when people have insoluble problems with OO that only go way when they use direct packages from [www.openoffice.org](www.openoffice.org) (either using debian versions or alien rpm converted).

There are too some experimental packages, [here]("http://people.ubuntu.com/~doko/ubuntu/"). You may want to give them a try, if _any else fails_.

Good luck.

---

### Post by dpsguard on 2007-06-15
I have tried completely uninstallaing Java 1.6 and installaing Java 1.5 but problem still remains. I am not sure if this has anything to do with my problem, please review below:

root@dpsguard-laptop:~# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  openoffice.org-common
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 35.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 112637 files and directories currently installed.)
Removing openoffice.org-common ...
dpkg: error processing openoffice.org-common (--remove):
 cannot remove file `/usr/share/icons/locolor/32x32/mimetypes/ooffice-extension.png': Not a directory
Errors were encountered while processing:
 openoffice.org-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@dpsguard-laptop:~# 
root@dpsguard-laptop:~# apt-get update

Fetched 5B in 0s (6B/s)  
Reading package lists... Done

root@dpsguard-laptop:~# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  openoffice.org-common
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 35.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 112637 files and directories currently installed.)
Removing openoffice.org-common ...
dpkg: error processing openoffice.org-common (--remove):
 cannot remove file `/usr/share/icons/locolor/32x32/mimetypes/ooffice-extension.png': Not a directory
Errors were encountered while processing:
 openoffice.org-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@dpsguard-laptop:~# 


Please advise.

Thanks

---

### Post by Rui Pais on 2007-06-15
hi have you tried remove the file fist and then purge the package?:
```
sudo mv /usr/share/icons/locolor/32x32/mimetypes/ooffice-extension.png .
```
and then:
```
sudo aptitude purge openoffice.org-common
```
?

---

### Post by dpsguard on 2007-06-15
I get this error message:

mv: cannot stat `/usr/share/icons/locolor/32x32/mimetypes/ooffice-extension.png': Not a directory

Thanks

---

### Post by Rui Pais on 2007-06-15
> **dpsguard said:**
> I get this error message:

mv: cannot stat `/usr/share/icons/locolor/32x32/mimetypes/ooffice-extension.png': Not a directory

Thanks

weird... can you delete it?
```
sudo rm /usr/share/icons/locolor/32x32/mimetypes/ooffice-extension.png
```
or do a deep clean of the folder:
```
sudo rm -rf /usr/share/icons/locolor/32x32/mimetypes/*
```?

---

### Post by dpsguard on 2007-06-15
Here are the results:

dpsguard@dpsguard-laptop:~$ sudo rm /usr/share/icons/locolor/32x32/mimetypes/ooffice-extension.png
Password:
rm: cannot remove `/usr/share/icons/locolor/32x32/mimetypes/ooffice-extension.png': Not a directory
dpsguard@dpsguard-laptop:~$ sudo rm -rf /usr/share/icons/locolor/32x32/mimetypes/*
rm: cannot remove `/usr/share/icons/locolor/32x32/mimetypes/*': Not a directory
dpsguard@dpsguard-laptop:~$

---

### Post by Rui Pais on 2007-06-15
Something is very strange...

did 
```
ls -l /usr/share/icons/locolor/32x32/mimetypes/
```
list a bunch of png with diffrent sizes and permitions:
> -rw-r--r-- 1 root root

if you type:
```
eog /usr/share/icons/locolor/32x32/mimetypes/ooffice-extension.png
```
it shows an icon? Did it outputs any error?



Can you boot from a livecd (or another version of Linux you have installed) and do:
```
sudo e2fsck -f
```
and then redo the apt-get remove (or apt-get install -f)

---

### Post by dpsguard on 2007-06-15
I logged in as root and then removed the file as you had suggested and  it is all good now. No more errors. I will now try reinstallaing the OpenOffice from the binaries direct from openoffice and hopefully that will fix my problems.

Appreciate excellent support and I will report back on OpenOffice installation.

Thanks

---

### Post by Rui Pais on 2007-06-15
No prob. 
That was really strange... 
since it disappear  (seems) try to purge the package and redo a conventional ubuntu install first, to see if that was a failure due to the corrupted files.


But at first opportunity, reboot from a five cd and check your filesystem with e2fsck -f (to avoid bad surprises in the  future)

good luck (please  let us know how it gone)

---

