---
title: "Novell Groupwise Messenger"
date: 2008-04-30
forum: General Help
---

### Post by pricetech on 2008-04-30
Trying to install Groupwise Messenger.
Downloaded nvlmsgr.bin from both the server that runs messenger, per Novell's instructions, and directly from Novell's website.
Tried Novell's instructions, which are to install using the command
sh ./nvlmsgr.bin
I get the same error each time.
Extracting files, please wait...tail: cannot open `+36' for reading: No such file or directory

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
Failed to extract the client files.

Novell only supports this under their own flavor of Linux, so no help from them.

Any ideas ??
Thanks

P.S. Pidgin works OK, but GW Messenger has some features I miss.

---

### Post by deezer on 2011-04-20
I am having this issue as well, did you ever figure it out?

---

### Post by deezer on 2011-04-21
Ok, I figured out how to get GroupWise Messenger 2.0.4 working in Ubuntu 10.10

1 First, download the tar.gz (I downloaded gvm204_client_linux_multi.tar.gz)

2 Unpack the file within (nvlmsgr.bin).  Open the file with vi (or some other editor that can open it)

3 Change the line with a "tail" to have a -n in front of the +
```
21c22
< tail +$SKIP $0 | tar xz -C $TMP_DIR
---
> tail -n +$SKIP $0 | tar xz -C $TMP_DIR
```

4 Run the binary as root.  It will create some files in your tmp  directory and fail - this is fine.

5 Look in a folder in your tmp directory that is newly created and called "novell_messenger_client_install_18606" (or similar).  In that folder you will find novell-messenger-client-2.0.4-20080930.i586.rpm (or similar)

6 On that rpm, run "sudo alien -t –veryverbose novell-messenger-client-2.0.4-20080930.i586.rpm"  This will unpack the files for messenger in opt/ and usr/ directories relative to your current location

7 Run "sudo mv /opt/novell/messenger /opt/novell/" (create the novell dir if needed)

8 You can copy the desktop icon in the "usr" folder that was created if you desire - just sudo copy it to the same location under usr/share

9 Run "cd /opt/novell/messenger/client/"

10 Run "mv jre jre_old"

11 install 32bit jre –> sudo apt-get install ia32-sun-java6-bin

12 Run "sudo ln -s /usr/lib/jvm/ia32-java-6-sun/jre /opt/novell/messenger/client/jre"
(or just put a 32 bit JRE in here for GW)      

13 start "run-messenger" to start the app

---

### Post by cdinz on 2011-04-21
Hi deezer... Followed the steps above but it gives me an error:
```
read: 23: Illegal option -e
``` which goes into an infinite loop... I am using Novell messenger 2.2 on Ubuntu 11.04

---

### Post by deezer on 2011-07-12
> **cdinz said:**
> Hi deezer... Followed the steps above but it gives me an error:
```
read: 23: Illegal option -e
``` which goes into an infinite loop... I am using Novell messenger 2.2 on Ubuntu 11.04

Just saw your reply.  Did you ever figure this out?

---

