---
title: "Getting Groupwise 7 client to run on Hoary"
date: 2005-09-14
forum: General Help
---

### Post by iMerlin on 2005-09-14
I tried the Groupwise 7 suite and so far everything is working fine.

My windows users are happy with their Outlook and/or Groupwise client but I on my Ubuntu workstation want to be able to run the client.

I do not want to use Evolution for this due to it being slow, crashing and giving me authentication errors with Groupwise.

* I downloaded the "crossplatform client" from Novell's website
* Exctracted it into a rpm file
* Used Alien on the rpm file
* Installed the Groupwise Client with the deb package

Then the JRE (preinstalled with the client refused to run, even with ./java -version).

I decided to trick the GWclient to use my own Java installation and I am getting really close to make it run... However I get this when running the client.

> 
 Exception in thread "main" java.lang.UnsatisfiedLinkError: /opt/novell/groupwise/client/lib/libgwapijni.so.1: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.3.4' not found (required by /opt/novell/groupwise/client/lib/libinetpack.so)


Then when running ldd on the library in question.

> 
user@ubuntu:/opt/novell/groupwise/client$ ldd /opt/novell/groupwise/client/lib/libgwapijni.so.1
/opt/novell/groupwise/client/lib/libgwapijni.so.1: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.3.4' not found (required by /opt/novell/groupwise/client/lib/libinetpack.so)
/opt/novell/groupwise/client/lib/libgwapijni.so.1: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.3.4' not found (required by /opt/novell/groupwise/client/lib/libtoolkit.so)
/opt/novell/groupwise/client/lib/libgwapijni.so.1: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.3.4' not found (required by /opt/novell/groupwise/client/lib/libXis10.so)


Is there any way of tricking this version requirement? 

Why do they call it "crossplatform" when it ships with platform specific binaries?  ](*,)

---

### Post by sdide on 2005-11-08
[QUOTE=iMerlin]
* I downloaded the "crossplatform client" from Novell's website
* Exctracted it into a rpm file
* Used Alien on the rpm file
* Installed the Groupwise Client with the deb package

Then the JRE (preinstalled with the client refused to run, even with ./java -version).

I decided to trick the GWclient to use my own Java installation and I am getting really close to make it run... However I get this when running the client.

Then when running ldd on the library in question.

Is there any way of tricking this version requirement? 

Why do they call it "crossplatform" when it ships with platform specific binaries?  ](*,)[/QUOTE]

How do you "trick" it to use your own java?

when I run it , I get:

Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object

It sets

LD_LIBRARY_PATH=/opt/novell/groupwise/client/jre/lib/i386

If I change that to eg /opt/java/jre1.5.0_04/lib/i386

I get the same error.

Any ideas?

Søren Dideriksen.

---

### Post by iMerlin on 2005-11-08
The client searches for Java inside '/opt/novell/groupwise/client/jre'

I simply made a symbolic link from the 'jre' java directory from /usr/lib to the jre folder the client was looking for.

Still didn't solve my problem but I don't get no Java errors anymore. Now it simply says that my libc is invalid.

> 
/opt/novell/groupwise/client/bin/groupwise: relocation error: /opt/novell/groupwise/client/lib/libc.so.6: symbol _dl_starting_up, version GLIBC_PRIVATE not defined in file ld-linux.so.2 with link time reference


So I may be one closer but this still isn't working...

---

### Post by iMerlin on 2005-11-08
I'd like to thank Sdide for reminding me of the LD_LIBRARY_PATH variable.

I've gotten the Groupwise 7 Linux client to work on Breezy with the Blackdown J2RE package.

First you 'alienate' the rpm packages and install them.

Then under /opt/novell/groupwise/client/
> lrwxrwxrwx  1 root root   22 Nov  8 13:31 jre -> /usr/lib/j2se/1.4/jre/

The groupwise.sh script that runs the client also needs to be changed a bit. Comment out the both LD_LIBRARY_PATH lines and put instead:
> LD_LIBRARY_PATH=/lib

I think that's it. I'll keep monitoring this thread if anyone else has problems.

---

### Post by sdide on 2005-11-09
[QUOTE=iMerlin]
I've gotten the Groupwise 7 Linux client to work on Breezy with the Blackdown J2RE package.
<CUT>
 I'll keep monitoring this thread if anyone else has problems.[/QUOTE]

Now I start having the same problem you had earlier: the "GLIBC_2.3.4' not found" issue.

I installed blackdown j2re 1.4.2, from the binary (couldn't find it on any of the repositories.) 

it installs under /opt/j2re1.4.2/

In /opt/novell/groupwise/client i make the link: 

ln -s /op/j2re1.4.2/ jre

and in /opt/novell/groupwise/client/bin/groupwise.sh i change the 
 LD_LIBRARY_PATH to various different values (eg : /lib, /opt/novell/groupwise/client/jre/lib/i386, with no effect.

I do run Hoary and not Breezy, but still ... 

Regards Søren Dideriksen

---

### Post by iMerlin on 2005-11-09
I don't remember what glibc hoary had but consider upgrading your machine to breezy. I've upgraded two so far without any problems. Blackdown is in the multiverse repo in Breezy.

It's possible that the new glibc in breezy makes this possible. Also make sure your jre link links to the 'jre' directory under the j2re not the main directory itself.

> jre -> /usr/lib/j2se/1.4/jre/

Hope this helps.

---

