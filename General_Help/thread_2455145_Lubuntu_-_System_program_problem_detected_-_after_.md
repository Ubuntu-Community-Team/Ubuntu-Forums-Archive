---
title: "Lubuntu - System program problem detected - after creating sddm.config"
date: 2020-12-13
forum: General Help
---

### Post by hybris2 on 2020-12-13
I have Lubuntu 18.04

I tried via command line to set the autologin at startup (currently I was able to set only to enter without password but I still have to confirm with ok)

I entered the command "sudo nano /etc/sddm.config" and placed it in the file:

 [Autologin]
 User = my_user
 Session = Lubuntu

 I have saved (and created, this file did not exist before), but the autologin does not work.

Now, however, I get an error at startup "System program problem detected.
Do you want to report the problem now?"  but it doesn't appear what kind of problem it is.

I tried to delete the sddm.config file but it is not possible, I also deleted the commands inside but nothing changes.

How can I fix this problem and remove this error message?

Thanks in advance for your help

---

### Post by deadflowr on 2020-12-13
Not an Ubuntu Development Release.
[I]Thread moved to **General Help**
[/I]

The file has the wrong name.
It should be sddm.conf

I would think you'd already have one.

---

### Post by hybris2 on 2020-12-14
> **deadflowr said:**
> Not an Ubuntu Development Release.
[I]Thread moved to **General Help**
[/I]

The file has the wrong name.
It should be sddm.conf

I would think you'd already have one.

Sorry, I misspelled. The file is sddm.conf and not .config

---

### Post by guiverc on 2020-12-14
Lubuntu 18.04 LTS does not use `sddm` as it's greeter (`lightdm` is the default for releases up to and including 18.04)

 The first Lubuntu to use `sddm` was 18.10.

On an unchanged 18.04 system I'd not expect a modification of `sddm.conf` to make any difference, as I gather occurred in your case, or did you add `sddm` to your system, thus the reason for that modication?

The error message (*System problem detected*) will be the result of a program having a problem, and a .crash file existing in /var/crash/.  You can submit the crash report with 

`ubuntu-bug /var/crash/[name_of_crash_file.crash]`

which should make the "*System problem detected*" no longer occur (*the file will be renamed to have a .uploaded at the end of it's name, meaning you won't be told about it again*), or you can just delete that file (you won't be asked about it again as it won't exist; you'll need to use `sudo` to delete the file as your user doesn't have write access to /var/crash without it).

*Please Note:* You'll need to change my "[name_of_crash_file.crash]" to be the actual filename, you can use <TAB> to expand it out, or use <TAB><TAB> to list the files in that directory (*should have have more than one*). The name of the file will tell you what program crashed & left the crash report (the file date/time will tell you when the error occurred etc).

---

### Post by hybris2 on 2020-12-14
> **guiverc said:**
> Lubuntu 18.04 LTS does not use `sddm` as it's greeter (`lightdm` is the default for releases up to and including 18.04)

 The first Lubuntu to use `sddm` was 18.10.

On an unchanged 18.04 system I'd not expect a modification of `sddm.conf` to make any difference, as I gather occurred in your case, or did you add `sddm` to your system, thus the reason for that modication?

Not being very experienced I thought that by modifying the sddm.conf file I would be able to get the autologin.



> **guiverc said:**
> The error message (*System problem detected*) will be the result of a program having a problem, and a .crash file existing in /var/crash/. You can submit the crash report with 

`ubuntu-bug /var/crash/[name_of_crash_file.crash]`

which should make the "*System problem detected*" no longer occur (*the file will be renamed to have a .uploaded at the end of it's name, meaning you won't be told about it again*), or you can just delete that file (you won't be asked about it again as it won't exist; you'll need to use `sudo` to delete the file as your user doesn't have write access to /var/crash without it).


in the / var / crash / folder there are 2 files:
_usr_bin_pcmanfm.1000.crash
is
_usr_lib_xorg_Xorg.0.crash


I tried to upload the report for both files, for the first file with
'ubuntu-bug /var/crash/_usr_bin_pcmanfm.1000.crash'


and this message appears


(apport-gtk: 3978): dbind-WARNING **: 15: 25: 28.729: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
ERROR: gdb does not exist in the sandbox nor on the host


if I try with the second file with
'ubuntu-bug /var/crash/_usr_lib_xorg_Xorg.0.crash'


(apport-gtk: 4057): dbind-WARNING **: 15: 27: 06.675: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
Gtk-Message: 15: 27: 08.531: GtkDialog mapped without a transient parent. This is discouraged.


In both cases the procedure is not successful.



> **guiverc said:**
> *Please Note:* You'll need to change my "[name_of_crash_file.crash]" to be the actual filename, you can use <TAB> to expand it out, or use <TAB><TAB> to list the files in that directory (*should have have more than one*). The name of the file will tell you what program crashed & left the crash report (the file date/time will tell you when the error occurred etc).


here i didn't understand what exactly i should do..


I thank you infinitely for the help you are giving me!!

---

