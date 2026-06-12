---
title: "Easy Ubuntu error"
date: 2006-10-18
forum: General Help
---

### Post by mo79 on 2006-10-18
Newbie, don't shoot! ;) 

Tried running Easy Ubuntu, got this message?

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

Any ideas?

---

### Post by dagnabit dang doohickey on 2006-10-18
This key worked for me:

```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 0x12B83718 ;  gpg --export -a 0x12B83718 | sudo apt-key add -
```

---

### Post by mo79 on 2006-10-18
No luck, getting a dialogue about having to 'fix packages' first.

---

### Post by mo79 on 2006-10-19
...Still no luck. Getting the message 'Could not apply packages! Fix broken packages first.'
Followed by another dialogue box saying:
/bin/sh: update-flashplugin: command not found
fc-cache: "/usr/share/fonts": caching, 0 fonts, 2 dirs
fc-cache: "/usr/share/fonts/truetype": caching, 0 fonts, 21 dirs
fc-cache: "/usr/share/fonts/truetype/arphic": caching, 2 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/baekmuk": caching, 4 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/freefont": caching, 12 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/kochi": caching, 4 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/openoffice": caching, 1 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/thai": caching, 23 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-arabeyes": caching, 39 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-bengali-fonts": caching, 7 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-bitstream-vera": caching, 10 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-dejavu": caching, 21 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-devanagari-fonts": caching, 5 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-gentium": caching, 4 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-gujarati-fonts": caching, 5 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-kannada-fonts": caching, 8 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-lao": caching, 1 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-malayalam-fonts": caching, 1 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-mgopen": caching, 16 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-oriya-fonts": caching, 1 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-punjabi-fonts": caching, 2 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-tamil-fonts": caching, 9 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-telugu-fonts": caching, 2 fonts, 0 dirs
fc-cache: "/usr/share/fonts/type1": caching, 0 fonts, 1 dirs
fc-cache: "/usr/share/fonts/type1/gsfonts": caching, 35 fonts, 0 dirs
fc-cache: "/usr/share/X11/fonts": caching, 0 fonts, 5 dirs
fc-cache: "/usr/share/X11/fonts/100dpi": caching, 397 fonts, 0 dirs
fc-cache: "/usr/share/X11/fonts/75dpi": caching, 397 fonts, 0 dirs
fc-cache: "/usr/share/X11/fonts/Type1": caching, 9 fonts, 0 dirs
fc-cache: "/usr/share/X11/fonts/encodings": caching, 0 fonts, 1 dirs
fc-cache: "/usr/share/X11/fonts/encodings/large": caching, 0 fonts, 0 dirs
fc-cache: "/usr/share/X11/fonts/misc": caching, 55 fonts, 1 dirs
fc-cache: "/usr/share/X11/fonts/misc/misc": caching, 0 fonts, 0 dirs
fc-cache: "/usr/local/share/fonts": caching, 0 fonts, 0 dirs
fc-cache: "/root/.fonts": skipping, no such directory
fc-cache: succeeded

---

### Post by dagnabit dang doohickey on 2006-10-19
Open Synaptic Package Manager and in the Edit menu you'll find *Fix Broken Packages*. You may need to edit your sources.list for this to work, if EasyUbuntu hasn't already done it for you.

Also you may not want to use EasyUbuntu to install FlashPlayer, since the beta of FlashPlayer9 became available yesterday and it seems to work well.
It's a piece of cake to install manually. If you need, you can follow this:
[http://ubuntuforums.org/showthread.php?t=279990](http://ubuntuforums.org/showthread.php?t=279990)

BTW: You don't have to use EasyUbuntu to install msttcorefonts either. It's easy to install using the Ubuntu Add/Remove Applications tool.

---

### Post by mo79 on 2006-10-19
Hmm, the fix broken packages options didn't do anything. When I unchecked Web/Video everything installed...So, how can I get Web/Video to work? Cheers for the FlashPlayer tip tho ;)

> **dagnabit dang doohickey said:**
> Open Synaptic Package Manager and in the Edit menu you'll find *Fix Broken Packages*. You may need to edit your sources.list for this to work, if EasyUbuntu hasn't already done it for you.

Also you may not want to use EasyUbuntu to install FlashPlayer, since the beta of FlashPlayer9 became available yesterday and it seems to work well.
It's a piece of cake to install manually. If you need, you can follow this:
[http://ubuntuforums.org/showthread.php?t=279990](http://ubuntuforums.org/showthread.php?t=279990)

BTW: You don't have to use EasyUbuntu to install msttcorefonts either. It's easy to install using the Ubuntu Add/Remove Applications tool.

---

### Post by dagnabit dang doohickey on 2006-10-19
I don't know exactly what packages you tried to install, but you can take a look at this thread, as they discuss a similar problem.
[http://ubuntuforums.org/showthread.php?t=240439](http://ubuntuforums.org/showthread.php?t=240439)

Also, you can use synaptic to check what may and may not have been installed compared to the following.

EasyUbuntu multimedia packages:
```
<category id="multimedia">
    <!-- http://packages.ubuntu.com/dapper/libs/gstreamer0.10-pitfdll
    <subcat id="totem" arch="x86-powerpc-amd64" de="gnome">
        <label>Enhance video player: Install the xine backend to totem</label>
        <alert>free</alert>
        <pkg>totem-xine</pkg>
    </subcat>
    -->
    <subcat id="freecodecs" arch="x86-powerpc-amd64" de="gnome-kde">
        <label>Codecs: Add Support for playing restricted formats</label>
        <alert>free</alert>
        x<pkg>gstreamer0.10-plugins-ugly</pkg>
        x<pkg>gstreamer0.10-plugins-ugly-multiverse</pkg>
        x<pkg>gstreamer0.10-plugins-bad-multiverse</pkg>
        x<pkg>gstreamer0.10-ffmpeg</pkg>
        x<pkg>gstreamer0.10-plugins-bad</pkg>
        x<pkg>libxine-extracodecs</pkg> 
        x<pkg>libxine-main1</pkg>
        x<pkg>faad</pkg> 
        x<pkg>sox</pkg> 
        x<pkg>lame</pkg>
        x<pkg>ffmpeg</pkg>
        x<pkg>mjpegtools</pkg> 
        x<pkg>vorbis-tools</pkg>
        x<pkg>libxvidcore4</pkg>
    </subcat>
    <subcat id="bincodecs" arch="x86" de="gnome-kde">
        <label>Binary Codecs: Add support for proprietary video and audio formats</label>
        <alert>illegal</alert>
        x<pkg>gstreamer0.10-pitfdll</pkg>
        x<pkg>w32codecs</pkg>
    </subcat>
    <subcat id="libdvdcss" arch="x86-powerpc-amd64" de="gnome-kde">
        <label>libdvdcss: Read commercial and encrypted DVDs</label>
        <alert>illegal</alert>
        x<pkg>libdvdcss2</pkg>
    </subcat>
    <!--
    <subcat id="realplay" arch="x86" de="gnome-kde">
        <label>RealPlayer: A proprietary software to read Real audio and video streams</label>
        <alert>nonfree</alert>
        <pkg>realplayer</pkg>
    </subcat>
    -->
    <subcat id="midi" arch="x86-powerpc-amd64" de="gnome-kde">
        <label>MIDI: Add support for playing midi files</label>
        <alert>free</alert>
        <pkg>timidity</pkg>
        <pkg>timidity-interfaces-extra</pkg>
        <pkg>freepats</pkg>
    </subcat>
</category>

```

EasyUbuntu Web pagkages:
```
<category id="web">
    <subcat id="flash" arch="x86" de="gnome-kde">
        <label>Flash: Enable the Macromedia Flash plugin</label>
        <alert>nonfree</alert>
        <pkg>flashplugin-nonfree</pkg>
        <config>update-flashplugin</config>
    </subcat>
    <subcat id="java" arch="x86-amd64" de="gnome-kde">
        <label>Java: Enable the Sun Java plugin</label>
        <alert>nonfree</alert>
        <pkg>sun-java5-bin</pkg>
        <pkg>sun-java5-plugin</pkg>
    </subcat>
    <subcat id="ibm-java" arch="powerpc" de="gnome-kde">
        <label>Java: Enable the IBM Java plugin</label>
        <alert>nonfree</alert>
        <pkg>ibm-j2re1.5</pkg>
    </subcat>
    <subcat id="video-totem" arch="x86-powerpc-amd64" de="gnome">
        <label>Videos: Enable viewing videos embedded in webpages with totem</label>
        <alert>free</alert>
        <pkg>totem-gstreamer-firefox-plugin</pkg>
    </subcat>
    <subcat id="video-kaffeine" arch="x86-powerpc-amd64" de="kde">
        <label>Videos: Enable viewing videos embedded in webpages with kaffeine</label>
        <alert>free</alert>
        <pkg>kaffeine-mozilla</pkg>
    </subcat>
    <subcat id = "skype" arch="x86" de="gnome-kde">
        <label>Skype: the most popular VoIP software</label>
        <alert>nonfree</alert>
        <pkg>skype</pkg>
    </subcat>
    <subcat id = "openwengo" arch="x86-powerpc-amd64" de="gnome-kde">
        <label>OpenWengo: Free alternative to Skype</label>
        <alert>free</alert>
        <pkg>wengophone</pkg>
    </subcat>
</category>

```

Key:
"arch=" tells you what processor the package may be applicable.
"de=" tell you what desktop environment the package may be applicable.
"<pkg>" is the package name. (if you see an "x" before <pkg>, that's just a mark I put there when I was making a list of packages I wanted to install.)

This is the package list from when I installed a couple of months ago, so the version numbers on some of your packages may differ.

---

