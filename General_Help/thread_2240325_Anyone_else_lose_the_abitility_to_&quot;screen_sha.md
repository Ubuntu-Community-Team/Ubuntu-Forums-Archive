---
title: "Anyone else lose the abitility to &quot;screen share&quot; in Skype 4.3.0.37?"
date: 2014-08-19
forum: General Help
---

### Post by Habitual on 2014-08-19
Share screen has been disabled since I installed it from Software Manager in Linux MInt 17 -Qiana
My boss also does not have this ability in Ubuntu 14.x (pretty certain he runs latest LTS).

Skype "support" is useless saying wait for the next release but doesn't specify when that is.

I've tried everything, literally.
New user, "new" .config, "new" .Skype, additional groups, Disabling Skype Video (I have no webcam).

Not sure it''ll help you help me but here's an ldd on the binary:
```
ldd /usr/bin/skype
    linux-gate.so.1 =>  (0xf76fa000)
    libXv.so.1 => /usr/lib/i386-linux-gnu/libXv.so.1 (0xf5458000)
    libXss.so.1 => /usr/lib/i386-linux-gnu/libXss.so.1 (0xf5454000)
    librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xf544a000)
    libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf5445000)
    libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf5311000)
    libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf52fe000)
    libQtDBus.so.4 => /usr/lib/i386-linux-gnu/libQtDBus.so.4 (0xf5281000)
    libQtWebKit.so.4 => /usr/lib/i386-linux-gnu/libQtWebKit.so.4 (0xf317b000)
    libQtXml.so.4 => /usr/lib/i386-linux-gnu/libQtXml.so.4 (0xf3138000)
    libQtGui.so.4 => /usr/lib/i386-linux-gnu/libQtGui.so.4 (0xf2684000)
    libQtNetwork.so.4 => /usr/lib/i386-linux-gnu/libQtNetwork.so.4 (0xf253d000)
    libQtCore.so.4 => /usr/lib/i386-linux-gnu/libQtCore.so.4 (0xf2255000)
    libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf2238000)
    libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xf214f000)
    libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf2109000)
    libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf20ec000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf1f3c000)
    /lib/ld-linux.so.2 (0xf76fb000)
    libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf1f19000)
    libdbus-1.so.3 => /lib/i386-linux-gnu/libdbus-1.so.3 (0xf1ece000)
    libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xf1eb4000)
    libXrender.so.1 => /usr/lib/i386-linux-gnu/libXrender.so.1 (0xf1ea9000)
    libjpeg.so.8 => /usr/lib/i386-linux-gnu/libjpeg.so.8 (0xf1e4e000)
    libpng12.so.0 => /lib/i386-linux-gnu/libpng12.so.0 (0xf1e25000)
    libxslt.so.1 => /usr/lib/i386-linux-gnu/libxslt.so.1 (0xf1de7000)
    libxml2.so.2 => /usr/lib/i386-linux-gnu/libxml2.so.2 (0xf1c8d000)
    libgstapp-1.0.so.0 => /usr/lib/i386-linux-gnu/libgstapp-1.0.so.0 (0xf1c7f000)
    libgstpbutils-1.0.so.0 => /usr/lib/i386-linux-gnu/libgstpbutils-1.0.so.0 (0xf1c5a000)
    libgstvideo-1.0.so.0 => /usr/lib/i386-linux-gnu/libgstvideo-1.0.so.0 (0xf1c11000)
    libgstaudio-1.0.so.0 => /usr/lib/i386-linux-gnu/libgstaudio-1.0.so.0 (0xf1bbf000)
    libgstbase-1.0.so.0 => /usr/lib/i386-linux-gnu/libgstbase-1.0.so.0 (0xf1b5b000)
    libgstreamer-1.0.so.0 => /usr/lib/i386-linux-gnu/libgstreamer-1.0.so.0 (0xf1a58000)
    libgobject-2.0.so.0 => /usr/lib/i386-linux-gnu/libgobject-2.0.so.0 (0xf1a06000)
    libglib-2.0.so.0 => /lib/i386-linux-gnu/libglib-2.0.so.0 (0xf18f9000)
    libsqlite3.so.0 => /usr/lib/i386-linux-gnu/libsqlite3.so.0 (0xf183c000)
    libfontconfig.so.1 => /usr/lib/i386-linux-gnu/libfontconfig.so.1 (0xf1801000)
    libQtOpenGL.so.4 => /usr/lib/i386-linux-gnu/libQtOpenGL.so.4 (0xf1705000)
    libGL.so.1 => /usr/lib32/nvidia-331/libGL.so.1 (0xf1601000)
    libaudio.so.2 => /usr/lib/i386-linux-gnu/libaudio.so.2 (0xf15e6000)
    libfreetype.so.6 => /usr/lib/i386-linux-gnu/libfreetype.so.6 (0xf1546000)
    libSM.so.6 => /usr/lib/i386-linux-gnu/libSM.so.6 (0xf153d000)
    libICE.so.6 => /usr/lib/i386-linux-gnu/libICE.so.6 (0xf1523000)
    libXi.so.6 => /usr/lib/i386-linux-gnu/libXi.so.6 (0xf1512000)
    libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf150d000)
    libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf1506000)
    liblzma.so.5 => /lib/i386-linux-gnu/liblzma.so.5 (0xf14e0000)
    liborc-0.4.so.0 => /usr/lib/i386-linux-gnu/liborc-0.4.so.0 (0xf1450000)
    libgsttag-1.0.so.0 => /usr/lib/i386-linux-gnu/libgsttag-1.0.so.0 (0xf1418000)
    libgmodule-2.0.so.0 => /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0 (0xf1412000)
    libffi.so.6 => /usr/lib/i386-linux-gnu/libffi.so.6 (0xf140b000)
    libpcre.so.3 => /lib/i386-linux-gnu/libpcre.so.3 (0xf13cd000)
    libexpat.so.1 => /lib/i386-linux-gnu/libexpat.so.1 (0xf13a4000)
    libnvidia-tls.so.331.38 => /usr/lib32/nvidia-331/tls/libnvidia-tls.so.331.38 (0xf139f000)
    libnvidia-glcore.so.331.38 => /usr/lib32/nvidia-331/libnvidia-glcore.so.331.38 (0xef15b000)
    libXt.so.6 => /usr/lib/i386-linux-gnu/libXt.so.6 (0xef0ff000)
    libuuid.so.1 => /lib/i386-linux-gnu/libuuid.so.1 (0xef0f9000)
```

Downloaded skype-ubuntu-precise_4.3.0.37-1_i386.deb from their website.

apt-cache show...
```
Package: skype
Priority: extra
Section: net
Installed-Size: 61
Maintainer: Steve Langasek <steve.langasek@canonical.com>
Architecture: amd64
Version: 4.3.0.37-0ubuntu0.12.04.1
Depends: skype-bin
Filename: pool/partner/s/skype/skype_4.3.0.37-0ubuntu0.12.04.1_amd64.deb
Size: 16054
MD5sum: 61d508cabddd6d9ef7bc9967eb4bb2ed
SHA1: 590099bbcc9c486cf92b035d534fab0b062edd4e
SHA256: 590e13cf75d75cd94ddc33af179588654b5c7c0933b585e5e118e07143c96748
Description: client for Skype VOIP and instant messaging service
 Skype is software that enables the world's conversations.  Millions of
 individuals and businesses use Skype to make free video and voice calls,
 send instant messages and share files with other Skype users.  Every day,
 people also use Skype to make low-cost calls to landlines and mobiles.
 .
 * Make free Skype-to-Skype calls to anyone else, anywhere in the world.
 * Call to landlines and mobiles at great rates.
 * Group chat with up to 200 people or conference call with up to 25 others.
 * Free to download.
Description-md5: a398bc8cee97c4027d64bae3fa223f58
```

Thanks.

---

### Post by kostkon on 2014-08-20
You mean it isn't working or isn't available at all?

I have it as an option (I didn't test it to see if it works though) 
[ATTACH=CONFIG]255672[/ATTACH]

Same version as yours, the 32bit multiarch from Skype website (downloaded the same day it came out), hmmm, alhtough I see that mine has different hash values:
```
MD5sum: a81bc08ab068e7dfc9419b2927a0fc5c
SHA1: 0a1918955096b5c7bcdba3d252b0174886c8a1a2
SHA256: 0681e35e59c2f784b12e162ab87146b06d1be2849cfac4f67c49c9e0ea2e7b3e
```

---

### Post by Habitual on 2014-08-20
> **kostkon said:**
> You mean it isn't working or isn't available at all?

I have it as an option (I didn't test it to see if it works though) 
[ATTACH=CONFIG]255672[/ATTACH]
 I have that _option_ and it is shown,  but it doesn't work. Simply, it makes the call but the screen never is seen at the other end.
Additionally during  a call I have an option from one of the lower icons displayed in the call, and one of those icons drops
down and *says "*Share screen" but it is greyed out.

Different hashes here too:
for i in md5sum sha1sum sha256sum ; do $i skype-ubuntu-precise_4.3.0.37-1_i386.deb ; done
```
d274ab94a7772766417b18e66d1864df  skype-ubuntu-precise_4.3.0.37-1_i386.deb
f8fe4185c03939c707f348c1b641811921e4f237  skype-ubuntu-precise_4.3.0.37-1_i386.deb
d19769135c014f7bdcb0c71410fd27698081c1aa4c6bbe53ccdd38576f17febc  skype-ubuntu-precise_4.3.0.37-1_i386.deb
```

fresh download of [http://download.skype.com/linux/skype-ubuntu-precise_4.3.0.37-1_i386.deb](http://download.skype.com/linux/skype-ubuntu-precise_4.3.0.37-1_i386.deb) = same hashes.

Thanks for the feedback.

Edit: [Screen shot of the non-functioning Share Screen options]("http://susepaste.org/84607255")
I used test test service merely to capture the flyout "Share screen" options.
I do not expect to share my screen with the testing service.

---

### Post by Habitual on 2014-09-02
I guess I'm a slave to Microsoft's next release then.

---

### Post by Habitual on 2014-10-08
I created a new system user, and logged in as that user, logged into Skype using my usual ID = Success.

I don't know why, I must have removed ~/.config ~/.gconf and ~/.Skype a half a dozen times (but probably not all at once, together)

Meh, live and learn.

---

