---
title: "ACPI madness..."
date: 2018-03-31
forum: General Help
---

### Post by kawalec-kkc on 2018-03-31
Ok 
I dont even know what to write here
I have been playing with the options for a while and dont remember all the changes that Ive made.

One thing Im sure is that my Laptop (MSI GL62QD) starts with ACPI=off all the time but...
1. LiveCD Ubuntu goes without it - live Xubuntu no
2. After Installing pure Ubuntu I need the option on again (same goes for Xub - both ACPI=off)
3. Nvidia:
  a. after installing Nvidia Ubu is ok without 
  b. Xub with Nvidia is black all the time - no login at all
  c. changing gdm3 to lightdm (or any other) in Ubu - with Nvidia - and it is black again (dont remember if without Nvidia other dm's work)
3. Tried some changes with Xub recently - dont remember exactly what - there was a lot of it and IIRC I turned off light-locker or smthng and logged in without acpi=off but only once! (no Nvidia this time)
then in another login it goes black again...
so I switched few parameters, restarted/reinstalled lockers and it is ok again - one fockken time only... and I just dont understand it anymore

made so many changes, tried so many thing... acpi, pci etc etc ... some times this works, sometimes that - mostly for one damn login
I just dont get it anymore - is that some screensaver problem as I read somewhere? 


The thing is - I know that this ACPI parameter isnt neccessary, but can live with ACPI=OFF as long as someone tells me how to enable FnKeys, Battery, Touchpad and other controls...
Im just tired off playing with this...
and gdm + pure ubuntu isnt the answer for me, even though I know that it works flawlessly with Nvidia installed - I use XFCE (not Xubuntu defaults) for 10 years now and dont want to chenge that
plsss - can someone tell me WTF is wrong before I go mad?

oh and Its 18.04 - but I had same problem with previous ones (and its the same thing in Debian)

---

### Post by Bashing-om on 2018-03-31
kawalec-kkc; Hello - Welcome to the forum .

< TJ-> "ACPI == Advanced Configuration and Power Interface. It provides a way for the PC firmware (UEFI/BIOS) to declare to an Operating System how to control its platform-specific hardware.  ACPI provides several in-firmware 'tables'. One such is the Differentiated Services Description Table (DSDT). This actually contains executable code in a special ACPI 'language' which the OS has to execute. Rather like Java and its Virtual Machine.  when the OS boots it calls a 'method' in the DSDT reporting its name _OSI("Linux") and the code in _OSI() should configure the hardware correctly... in your case the PC doesn't recognise it so it will adopt fail-safe minimal defaults.  HOWEVER... in almost 100% of cases the DSDT will declare various "Windows XXXX" versions for _OSI() so we can have Linux pretend to be the latest Windows versions ...... "
To change this table see:
[http://iam.tj/prototype/enhancements/Windows-acpi_osi.html](http://iam.tj/prototype/enhancements/Windows-acpi_osi.html)
Where he has a script to make the changes .. or you may choose to do so manually and know what the changes are .

[INDENT][INDENT]workie great
[INDENT][INDENT]last long time[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kawalec-kkc on 2018-03-31
> **Bashing-om said:**
> kawalec-kkc; Hello - Welcome to the forum .

< TJ-> "ACPI == Advanced Configuration and Power Interface. It provides a way for the PC firmware (UEFI/BIOS) to declare to an Operating System how to control its platform-specific hardware.  ACPI provides several in-firmware 'tables'. One such is the Differentiated Services Description Table (DSDT). This actually contains executable code in a special ACPI 'language' which the OS has to execute. Rather like Java and its Virtual Machine.  when the OS boots it calls a 'method' in the DSDT reporting its name _OSI("Linux") and the code in _OSI() should configure the hardware correctly... in your case the PC doesn't recognise it so it will adopt fail-safe minimal defaults.  HOWEVER... in almost 100% of cases the DSDT will declare various "Windows XXXX" versions for _OSI() so we can have Linux pretend to be the latest Windows versions ...... "
To change this table see:
[http://iam.tj/prototype/enhancements/Windows-acpi_osi.html](http://iam.tj/prototype/enhancements/Windows-acpi_osi.html)
Where he has a script to make the changes .. or you may choose to do so manually and know what the changes are .
[INDENT][INDENT]workie great[INDENT][INDENT]last long time[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


ok
but in my /sys/firmware/ 
theres no acpi

quick workaround?

---

### Post by Bashing-om on 2018-03-31
kawalec-kkc; Ouch !!

> 
but in my /sys/firmware/ 
theres no acpi


Are you for certain ?
my result:
> 
sysop@x1604:~$ ls -al /sys/firmware/acpi/
total 0
drwxr-xr-x 5 root root    0 Mar 31 11:56 .
drwxr-xr-x 5 root root    0 Mar 31 11:56 ..
drwxr-xr-x 5 root root    0 Mar 31 11:57 hotplug
drwxr-xr-x 2 root root    0 Mar 31 11:57 interrupts
-r--r--r-- 1 root root 4096 Mar 31 10:37 pm_profile
drwxr-xr-x 3 root root    0 Mar 31 10:37 tables
sysop@x1604:~$


I do think that the directory is required of the system . with out it .. well ... there is a problem .

[INDENT][INDENT]can not make something from
[INDENT][INDENT][INDENT]nothing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kawalec-kkc on 2018-03-31
> **Bashing-om said:**
> kawalec-kkc; Ouch !!



Are you for certain ?
my result:


I do think that the directory is required of the system . with out it .. well ... there is a problem .[INDENT][INDENT]can not make something from[INDENT][INDENT][INDENT]nothing
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


as you see:
[QUOTE=]
main@HAL9000msi:~$  ls -al /sys/firmware/acpi/
ls: cannot access '/sys/firmware/acpi/': No such file or directory
main@HAL9000msi:~$
[/QUOTE]

any other suggestions?

---

### Post by kawalec-kkc on 2018-03-31
As you see it must be something else since it worked before...
right now I have no touchpad, battery stats or Fn Keys and thats all I want/need

---

### Post by Bashing-om on 2018-03-31
kawalec-kkc; Yuk -

Regrets but this is above my skill set to advise on a procedure here .

[INDENT]a know it all, I am not
[/INDENT]

---

