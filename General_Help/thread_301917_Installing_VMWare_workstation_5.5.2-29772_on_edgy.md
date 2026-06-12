---
title: "Installing VMWare workstation 5.5.2-29772 on edgy"
date: 2006-11-17
forum: General Help
---

### Post by suicidal6 on 2006-11-17
hi guys, i'm trying to install VMware-workstation-5.5.2-29772.tar.gz on Ubuntu 6.10 edgy, it's kind of a fresh Ubuntu install...
the first step of running the installer is going ok, but then i get to the section where i need to run /usr/bin/vmware-config.pl
it gets to a part where it needs to recompile vmmon for my kernel (i have downloaded the headers and all).
at this stage i'm getting some really weird compile errors, i'll post the last parts of it since it's really long....

```
/tmp/vmware-config5/vmmon-only/linux/driver.c: In function ‘Log’:
/tmp/vmware-config5/vmmon-only/linux/driver.c:2132: error: ‘va_list’ undeclared (first use in this function)
/tmp/vmware-config5/vmmon-only/linux/driver.c:2132: error: expected ‘;’ before ‘args’
/tmp/vmware-config5/vmmon-only/linux/driver.c:2139: error: ‘args’ undeclared (first use in this function)
/tmp/vmware-config5/vmmon-only/linux/driver.c:2140: error: ‘KERN_DEBUG’ undeclared (first use in this function)
/tmp/vmware-config5/vmmon-only/linux/driver.c:2140: error: too many arguments to function ‘LinuxDriverError’
/tmp/vmware-config5/vmmon-only/linux/driver.c: In function ‘Panic’:
/tmp/vmware-config5/vmmon-only/linux/driver.c:2163: error: ‘va_list’ undeclared (first use in this function)
/tmp/vmware-config5/vmmon-only/linux/driver.c:2163: error: expected ‘;’ before ‘args’
/tmp/vmware-config5/vmmon-only/linux/driver.c:2165: error: ‘args’ undeclared (first use in this function)
/tmp/vmware-config5/vmmon-only/linux/driver.c:2166: error: ‘KERN_EMERG’ undeclared (first use in this function)
/tmp/vmware-config5/vmmon-only/linux/driver.c:2166: error: too many arguments to function ‘LinuxDriverError’
/tmp/vmware-config5/vmmon-only/linux/driver.c: At top level:
/tmp/vmware-config5/vmmon-only/linux/driver.c:2312: error: expected declaration specifiers or ‘...’ before string constant
/tmp/vmware-config5/vmmon-only/linux/driver.c:2312: warning: data definition has no type or storage class
/tmp/vmware-config5/vmmon-only/linux/driver.c:2312: warning: type defaults to ‘int’ in declaration of ‘MODULE_AUTHOR’
/tmp/vmware-config5/vmmon-only/linux/driver.c:2312: warning: function declaration isn’t a prototype
/tmp/vmware-config5/vmmon-only/linux/driver.c:2313: error: expected declaration specifiers or ‘...’ before string constant
/tmp/vmware-config5/vmmon-only/linux/driver.c:2313: warning: data definition has no type or storage class
/tmp/vmware-config5/vmmon-only/linux/driver.c:2313: warning: type defaults to ‘int’ in declaration of ‘MODULE_DESCRIPTION’
/tmp/vmware-config5/vmmon-only/linux/driver.c:2313: warning: function declaration isn’t a prototype
make[2]: *** [/tmp/vmware-config5/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config5/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-386'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config5/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

i've been looking all day to find a fix or a solution to no avail, anyone hhelp please?

](*,) 


PS: my /proc/version:
Linux version 2.6.17-10-386 (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Fri Oct 13 18:41:40 UTC 2006 (Ubuntu 2.6.17-10.33-386)

---

### Post by K.Mandla on 2006-11-18
(Bumped as a courtesy. ;) )

---

### Post by suicidal6 on 2006-11-18
thx for bump :)

---

### Post by jallain on 2006-11-18
What I can contribute is this: I installed vmware on a fresh install of edgy with no problems. I did not have to install any headers or packages ahead of time. My install was the stock install (using alternate method disk). The modules conpiled just fine and vmware runs like it should. Have you considered trying to apply the vmware any-any update?

---

### Post by jimbob on 2006-11-18
Why don't you just install VMware via Automatix, it is a lot easier or is there some reason you want to do it your way?
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by suicidal6 on 2006-11-19
well thanks guys, installing the vmware-player works, but what i was trying to install is the Workstation which doesn't come pre-packeged as a deb file like the player, and that's what's giving me the errors compiling, anyway for now the player is good enough for me.

---

### Post by rbmorse on 2006-11-19
I just installed Workstation 5.5.3 onto Kubuntu Edgy from the tar package with no problems. 

I first did workstation about 5.5.1 and had a lot of difficulty until I bit the bullet and downloaded the manual. I know some think it's a bit rude to tell people seeking assistance to RTFM, and I largely agree, but in this case going through the install section of VMware's well-written documentation helped me a lot.

---

### Post by suicidal6 on 2006-11-19
yes indeed. 5.5.3 works out of the box :)
thanks everyone for the help.

---

### Post by acascianelli on 2006-11-21
I got 5.5.3 to work out of the box also, but I cannot install Windows XP.  I keep getting read errors on the disc.  I tried different discs and different drives too.

---

