---
title: "liblzma.so no version information available (required by dpkg-deb)"
date: 2012-10-20
forum: General Help
---

### Post by masuch on 2012-10-20
Hi,

I have within (ubuntu 12.10 quantal)
> apt-get upgrade 
many error messages:
> dpkg-deb: /usr/local/lib/liblzma.so.5: no version information available (required by dpkg-deb)

Tried to 
> apt-get purge lzma, lzma-dev 
and install it again but did not help.

Is there any workaround about it ?

thank you,
kind regards,
M.

---

### Post by ibjsb4 on 2012-10-20
Looks like a bug.

[https://bugs.launchpad.net/ubuntu/+source/xz-utils/+bug/1065604](https://bugs.launchpad.net/ubuntu/+source/xz-utils/+bug/1065604)

---

### Post by masuch on 2012-10-21
> **ibjsb4 said:**
> Looks like a bug.

[https://bugs.launchpad.net/ubuntu/+source/xz-utils/+bug/1065604](https://bugs.launchpad.net/ubuntu/+source/xz-utils/+bug/1065604)

Yes,bug. 
It was reported by me. 
I went through many forums and did not find any workaround.

---

### Post by trollsroyce on 2012-10-21
Same error after upgrade on my pc.

---

### Post by masuch on 2012-10-21
> **trollsroyce said:**
> Same error after upgrade on my pc.

if you can support this "bug report" please click on it on launchpad web site.

---

### Post by trollsroyce on 2012-10-22
already done

---

### Post by trollsroyce on 2012-10-22
Not a bug for me.

I fix the problem on my pc.

1. Locate liblzma.so.5
Discover that i have 2 versions (/usr/local/lib and /lib/x86_64-linux-gnu/liblzma.so.5). Cant remember why.

2. remove the one in /usr/local/lib and any symbolic link.

3. sudo ldconfig

Problem solved (for me)

---

### Post by masuch on 2012-10-22
> **trollsroyce said:**
> Not a bug for me.

I fix the problem on my pc.

1. Locate liblzma.so.5
Discover that i have 2 versions (/usr/local/lib and /lib/x86_64-linux-gnu/liblzma.so.5). Cant remember why.

2. remove the one in /usr/local/lib and any symbolic link.

3. sudo ldconfig

Problem solved (for me)

Hi,
You are lucky. But does not work for me.
Even if I have found:
> -rwxr-xr-x. 1 root root 626051 2012-02-08 21:19:29.000000000 +0000 /usr/local/lib/liblzma.so.5.0.3
-rwxr-xr-x  1 root root 712623 2012-10-10 01:18:42.761336414 +0100 /usr/local/lib/liblzma.so.5.0.4

and remove and ldconfig 

did not helped.

---

### Post by masuch on 2012-10-22
> **trollsroyce said:**
> Not a bug for me.

I fix the problem on my pc.

1. Locate liblzma.so.5
Discover that i have 2 versions (/usr/local/lib and /lib/x86_64-linux-gnu/liblzma.so.5). Cant remember why.

2. remove the one in /usr/local/lib and any symbolic link.

3. sudo ldconfig

Problem solved (for me)


If you marked this thread as solved Could you please change it back ? From my side I could not change.

---

### Post by trollsroyce on 2012-10-22
I don't change subject on this thread. Certainly a admin task.

---

### Post by masuch on 2012-10-22
> **trollsroyce said:**
> I don't change subject on this thread. Certainly a admin task.
(I did not change it as well, ... )

Could you please post result of:
> sudo dpkg -l|grep lzma

thank you

---

### Post by trollsroyce on 2012-10-23
Here's the result of lzma packages

ii  liblzma-dev:amd64                           5.1.1alpha+20120614-1                     amd64        XZ-format compression library - development files
rc  liblzma2                                    5.0.0-2                                   amd64        XZ-format compression library
ii  liblzma5:amd64                              5.1.1alpha+20120614-1                     amd64        XZ-format compression library
ii  liblzma5:i386                               5.1.1alpha+20120614-1                     i386         XZ-format compression library

---

### Post by masuch on 2012-10-23
> **trollsroyce said:**
> Here's the result of lzma packages

ii  liblzma-dev:amd64                           5.1.1alpha+20120614-1                     amd64        XZ-format compression library - development files
rc  liblzma2                                    5.0.0-2                                   amd64        XZ-format compression library
ii  liblzma5:amd64                              5.1.1alpha+20120614-1                     amd64        XZ-format compression library
ii  liblzma5:i386                               5.1.1alpha+20120614-1                     i386         XZ-format compression library

Thanks for info. I have the same installed. Don't you know what library exactly you had or any information can help me ?

> I had 
/lib/x86_64-linux-gnu/liblzma.so.3 # have not been in use anyway
/lib/x86_64-linux-gnu/liblzma.so.5
now
/lib/x86_64-linux-gnu/liblzma.so.5


run out of ideas.

Funny is that on another Ubuntu instance it is not appeared this problem but on another Ubuntu instance it is there. so it is 2:1 course (lzma error:correct).

---

### Post by trollsroyce on 2012-10-24
Just got

/lib/x86_64-linux-gnu/liblzma.so.5 -> liblzma.so.5.0.0
/lib/x86_64-linux-gnu/liblzma.so.5.0.0

I check the repository version of xz-util and the liblzma version in it is liblzma.so.5.0.0. So perhaps you should download the deb and try to install it manually.

Good luck

---

### Post by masuch on 2012-10-24
> **trollsroyce said:**
> Just got

/lib/x86_64-linux-gnu/liblzma.so.5 -> liblzma.so.5.0.0
/lib/x86_64-linux-gnu/liblzma.so.5.0.0

I check the repository version of xz-util and the liblzma version in it is liblzma.so.5.0.0. So perhaps you should download the deb and try to install it manually.

Good luck

Thanks for tip but I have already did it before twice.
Could you please post result of following:
> sudo updatedb
ls -lA --time-style=full-iso `sudo locate liblzma.so`

I believe I have the same just for sure that problem will be probably somewhere else. thank you.
M.

---

### Post by trollsroyce on 2012-10-24
Result :

lrwxrwxrwx 1 root root     16 2012-06-19 23:57:37.000000000 +0200 /lib/i386-linux-gnu/liblzma.so.5 -> liblzma.so.5.0.0
-rw-r--r-- 1 root root 153008 2012-06-19 23:57:42.000000000 +0200 /lib/i386-linux-gnu/liblzma.so.5.0.0
lrwxrwxrwx 1 root root     16 2012-06-19 23:57:31.000000000 +0200 /lib/x86_64-linux-gnu/liblzma.so.5 -> liblzma.so.5.0.0
-rw-r--r-- 1 root root 137344 2012-06-19 23:57:34.000000000 +0200 /lib/x86_64-linux-gnu/liblzma.so.5.0.0
-rwxr-xr-x 1 root root 137456 2009-12-24 17:10:57.000000000 +0100 /opt/calibre/lib/liblzma.so.0
lrwxrwxrwx 1 root root     38 2012-06-19 23:57:31.000000000 +0200 /usr/lib/x86_64-linux-gnu/liblzma.so -> /lib/x86_64-linux-gnu/liblzma.so.5.0.0

---

### Post by masuch on 2012-10-25
> **trollsroyce said:**
> Result :

lrwxrwxrwx 1 root root     16 2012-06-19 23:57:37.000000000 +0200 /lib/i386-linux-gnu/liblzma.so.5 -> liblzma.so.5.0.0
-rw-r--r-- 1 root root 153008 2012-06-19 23:57:42.000000000 +0200 /lib/i386-linux-gnu/liblzma.so.5.0.0
lrwxrwxrwx 1 root root     16 2012-06-19 23:57:31.000000000 +0200 /lib/x86_64-linux-gnu/liblzma.so.5 -> liblzma.so.5.0.0
-rw-r--r-- 1 root root 137344 2012-06-19 23:57:34.000000000 +0200 /lib/x86_64-linux-gnu/liblzma.so.5.0.0
-rwxr-xr-x 1 root root 137456 2009-12-24 17:10:57.000000000 +0100 /opt/calibre/lib/liblzma.so.0
lrwxrwxrwx 1 root root     38 2012-06-19 23:57:31.000000000 +0200 /usr/lib/x86_64-linux-gnu/liblzma.so -> /lib/x86_64-linux-gnu/liblzma.so.5.0.0


thanks a lot for help - problem solved. I had to manually redirect some links and remove some files because even links have been redirected it somehow have been redirected back to original libraries after some moment. Do not understand why was/is it happening.

---

