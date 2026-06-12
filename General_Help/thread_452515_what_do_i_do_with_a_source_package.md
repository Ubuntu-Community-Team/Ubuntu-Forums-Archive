---
title: "what do i do with a source package?"
date: 2007-05-23
forum: General Help
---

### Post by nephish on 2007-05-23
hello there all,

i need a package on 7.04 that is called zaptel-source, i need it so i can make the kernel modules necessary for my telephony card for asterisk.
i was able to apt-get install the zaptel modules package, now what do i do with it ?

thanks

---

### Post by fragos on 2007-05-23
Open up the folder created and check for "readme" text files.  This will have directions.  In most instances there will be a shell file called configure.  The normal process would be to open a terminal window and "cd" to the folder that has the configure file.  Next run "./configure".  When complete run "make" and lastly run "sudo make install".  You will be prompted for a password by sudo.  Enter your user password.  There may be more extensive instructions in the folder but this usually does the trick.

---

### Post by nephish on 2007-05-23
ok , well i went through that and it wound up just being a symlink that i had to create and then the usual 
./configure
make
make install.

i was just nervous i suppose,

thanks

---

### Post by fragos on 2007-05-23
The first compile can be a scary thing.  The next one will be easier.  Before resorting to a compile you should always check to see if the Ubuntu repositories have what you need.  I have a lot of unusual hardware and I still rarely have to resort to a compile.  Every kernel release the hardware supports gets better.  Having Dell sell PCs preinstalled with Ubuntu will greatly encourage the creation of more vender supported open source drivers.  Nvidia is a good example of a hardware vender that supports open source.  HP printers and scanners are another.

---

