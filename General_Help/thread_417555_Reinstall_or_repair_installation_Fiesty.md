---
title: "Reinstall or repair installation Fiesty"
date: 2007-04-21
forum: General Help
---

### Post by dta116 on 2007-04-21
I belive I am missing some files or configuration info. Is there a way to reinstall or repair a new install of 7.04? (Fiesty)

Thanks.

---

### Post by mhansen on 2007-04-21
What leads you to believe that?  And of course you're "missing" files.  There are over 21000 packages available, and one of Ubuntu's objectives is to keep the install CD to just that, one CD, so you're going to have to add stuff yourself, if you decide you need/want it.

What in particular do you think you're missing?



Regards,
Mike

---

### Post by dta116 on 2007-04-21
Well Mike,

I realize there are things to install, but I am trying to install a driver for my Intel PRO\Wireless 2195ABG adapter. (this one should have installed).

The docs for the driver says to insure the kernal is configured by: 
/lib/modules/'uname -r'/build/include/linux/autoconf.h

Well mike, autoconf cannot be found anywhere by me..

I typed "autoconf" and found it to be in packages
* autoconf
* autoconf2.13

if i type the command "autoconf" ,  it cannot be found.

that in turn leads me to believe something did not get installed properly.

Do you agree?

Thanks.

---

### Post by smartboyathome on 2007-04-21
Will you tell me when you get this solved? I am trying to repair/reinstall mine so that my wireless card works...

---

### Post by mhansen on 2007-04-21
autoconf isn't installed by default, so you'll have to install it yourself.  There are some other packages you have to install on a fresh Ubuntu system in order to compile a lot of the most common stuff.  Some of them off the top of my head are build-essentials, automake, autoconf, libc6-dev, linux-headers-<version>...there will be more, but u can always check the error log when u try to compile to see what's missing..



Regards,
Mike

---

### Post by dta116 on 2007-04-21
Where can I find this "List"

Thanks

---

### Post by mhansen on 2007-04-21
Well, due to the various library requirements of each software package, there is no "one size fits all" list of required libraries, unless you were to install every library known to man.  :)


The best you can do for a failed ./configure is to look thru config.log to see why it failed, and install the missing libraries/packages accordingly.



Regards,
Mike

---

