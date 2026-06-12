---
title: "verify iso image before burn"
date: 2013-05-10
forum: General Help
---

### Post by Kojak Peg on 2013-05-10
Hi Everyone
I've downloaded two distros and want to check them before I burn them. I'm new to linux and don't really understand the terminal. So please explain it to me like a kids, and don't assume I know what you're talking about

So, I looked online and found three ways to verify the image:

1)SH1SUM
2)MD5SUM
3)manually mount
su -c 'mount -o loop -t iso9660 <isofilename> <mountpoint>

Neither of the iso images have a SH1SUM, or a MD5SUM file, and I don't really understand how to use the manual mount. For that matter, I'm not a 100% sure how to use the other two either, if I had them.

Here are the two file from one of the downloads 
Pinguy_OS_12.04-shell-i686.iso.torrentPinguy_OS_12.04-shell-i686.iso


When I tried the manual mount I typed in [COLOR=#63565F]su -c 'mount -o loop -t iso9660 <[/COLOR]Pinguy_OS_12.04-shell-i686.iso[COLOR=#63565F]> <mountpoint>[/COLOR]

And this is what happened
kojak@kojak-OptiPlex-760:~/Downloads$ su -c 'mount -o loop -t iso9660 <Pinguy_OS_12.04-shell-i686.iso> <mountpoint>
> 

Obviously I've done something wrong, and I'm sure it is laughably simple, but I have no clue what it is. So can you give me a step by step explanation of how I can verify my iso image. Starting at the beginning

Thanks

---

### Post by oldos2er on 2013-05-10
The Pinguy_OS_12.04-shell-i686.iso md5sum is here: [http://sourceforge.net/projects/pinguy-os/files/Pinguy_OS_12.04_LTS/Pinguy_OS_12.04-shell-i686.iso.md5/download](http://sourceforge.net/projects/pinguy-os/files/Pinguy_OS_12.04_LTS/Pinguy_OS_12.04-shell-i686.iso.md5/download)
The md5sum "hash" itself is a long alphanumeric string; once you've downloaded it you can open it in a text editor.

To actually check the md5sum of the iso, you need to run ```
md5sum Pinguy_OS_12.04-shell-i686.iso
``` 

More info here: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Kojak Peg on 2013-05-10
Thanks oldos2er
It worked, hurray. Feel like a linux pro now, lol. Well, maybe now, but getting there...slowly. One command line at a time

Cheers

---

### Post by oldos2er on 2013-05-10
You're welcome!

---

