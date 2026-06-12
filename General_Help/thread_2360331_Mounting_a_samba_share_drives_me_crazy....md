---
title: "Mounting a samba share drives me crazy..."
date: 2017-05-03
forum: General Help
---

### Post by misterfriday on 2017-05-03
Hello and thanks for reading this. I'm getting to the edge of desperation right now.

I have the newest ubuntu 17.4.
Now I want to permanently mount a samba share from a windows machine in the network.

I'm a user with root privileges,
I've edited /etc/fstab and added this line:

//10.142.1.1/z /home/fridayvfx/z cifs credentials=/home/fridayvfx/.smbcredentials,iocharset=utf8,sec=ntlm,uid=1000 0 0

The credentials file is there and accessable. Now I've rebooted and as soon as I try a "sudo mount -a" I'm getting the error:

mount error(79): Can not access a needed shared library
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

Now, of course I've googled this error and tried a bunch of stuff I found online, yet nothing helped. 
I've tried different char sets, I've tried setting the sec parameters to a bunch of different modes, 
testing around with different user name parameters, nothing worked.

The really weird thing is though, as soon as I try:

sudo mount -t cifs //10.142.1.1/z -o username=MYUSERNAME,password='MYPASSWORD' /home/fridayvfx/z 

This works! Of course with the correct credentials... Does anyone have any hint about whats going on?
It all worked in Ubuntu 16!
Thanks for reading!

---

### Post by Morbius1 on 2017-05-03
The obvious difference is there is no **iocharset=utf8 **in your terminal mount.

Add it to your terminal mount and see if it fails. If it does the not so obvious is why.

---

### Post by HermanAB on 2017-05-03
Chances are about 99 to 1 that the system tries to mount the share before the network is up.

---

### Post by misterfriday on 2017-05-04
You are absolutely right. Without the isocharset=utf8 it's working fine in the fstab... the big question now is.. why.. :X

Thanks for the hint anyways! Much appreciated.

---

### Post by Morbius1 on 2017-05-04
First off, this is way over my comfort level but .....

There's an Ask Ubuntu topic ( for an older version of Ubuntu ) that goes into this: [https://askubuntu.com/questions/519796/unable-to-mount-cifs-with-iocharset-utf8-in-trusty](https://askubuntu.com/questions/519796/unable-to-mount-cifs-with-iocharset-utf8-in-trusty)

If I run Xubuntu 17.04 I don't have your problem but if I do the check offered in the answer I have the missing module:
> tester@vxub1704:~$ [COLOR=#0000cd]**ls /lib/modules/$(uname -r)/kernel/fs/nls/nls_utf8.ko**[/COLOR]
/lib/modules/4.10.0-20-generic/kernel/fs/nls/[COLOR=#0000cd]nls_utf8.ko[/COLOR]
Maybe yours is missing?

---

