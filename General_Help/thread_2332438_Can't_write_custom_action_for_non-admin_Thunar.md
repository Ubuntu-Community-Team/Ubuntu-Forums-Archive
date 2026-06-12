---
title: "Can't write custom action for non-admin Thunar"
date: 2016-07-31
forum: General Help
---

### Post by 4kh3RAm on 2016-07-31
I can write custom actions for root access Thunar but not for regular thunar.

Why is that and is there a work around ?

Why can't I edit uca.xml ?

---

### Post by 4kh3RAm on 2016-08-01
Anyone want to take a stab ?

Ubuntu has a uca.xml file,  but it contains no custom actions.

Since I have custom actions with Thunar when run as root, it has to be stored somewhere ?

Maybe a P.M ?

---

### Post by dragonfly41 on 2016-08-01
Although I don't often use Thunar I ran this command ..

```
sudo locate uca.xml

```
and saw this returned ..

```
/etc/xdg/Thunar/uca.xml
/home/<myusrname>/.config/Thunar/uca.xml
/root/.config/Thunar/uca.xml
```

...

First time you use the locate command you might have to index all your filesystem ...

```
sudo updatedb 
```
.. then wait several minutes for the update to complete.

...

Incidentally, I'm currently using Actionaz to automate various workflows for other GUI's and an action script can be to run command .. thunar.

Then navigate the Thunar GUI.

---

### Post by 4kh3RAm on 2016-08-01
This is what both Catfish and Search for Files found:

```
/etc/xdg/Thunar/uca.xml
/etc/xdg/Thunar/uca.xml.zip
```

This is what locate found:
Strange that it found more.

```
/etc/xdg/Thunar/uca.xml
/etc/xdg/Thunar/uca.xml.zip
/home/andy/.config/Thunar/uca.xml
/root/.config/Thunar/uca.xml
```

I copied the uca.xml that had the custom actions over the other locations.


I use this to invoke Thunar as a superuser.

```
echo password | sudo -S thunar 
```

and this as regular thunar.

```
thunar
```

No change. Time to give up.

These are my current custom actions and they all work.

Thunar saves a lot of typing. :-)

```
<?xml encoding="UTF-8" version="1.0"?>
<actions>
<action>
    <icon></icon>
    <name>Delete Movies</name>
    <unique-id>1470092428421234-5</unique-id>
    <command>rm *.mp4  *.mov *.mpg</command>
    <description>Delete Movies</description>
    <patterns>*</patterns>
    <audio-files/>
    <image-files/>
    <other-files/>
    <text-files/>
    <video-files/>
</action>
<action>
    <icon></icon>
    <name>COPY FILES TO BACKUP DRIVE</name>
    <unique-id>1470093255515550-5</unique-id>
    <command>cp %f /media/andy/MAXTOR_SDB1/Linux_Files/</command>
    <description>COPY FILES TO BACKUP DRIVE</description>
    <patterns>*</patterns>
    <audio-files/>
    <image-files/>
    <other-files/>
    <text-files/>
    <video-files/>
</action>
<action>
    <icon></icon>
    <name>MAKE SCRIPTS EXECUTABLE</name>
    <unique-id>1470092406557559-4</unique-id>
    <command>chmod -x %f</command>
    <description>MAKE SCRIPTS EXECUTABLE</description>
    <patterns>*</patterns>
    <text-files/>
</action>
<action>
    <icon></icon>
    <name>7_ZIP UP FILES</name>
    <unique-id>1470092501612542-6</unique-id>
    <command>7za a -t7z %n.7z %F</command>
    <description>7_ZIP UP FILES</description>
    <patterns>*</patterns>
    <text-files/>
</action>
</actions>
```

---

### Post by vasa1 on 2016-08-01
> **4kh3RAm said:**
> ...
Maybe a P.M ?
Do you mean *Private Message*? As far as support issues go, the preference is that all communication is via the forums and visible to all. Thanks.

---

### Post by vasa1 on 2016-08-01
> **4kh3RAm said:**
> I can write custom actions for root access Thunar but not for regular thunar.
...
Could you please change directory to your home folder and then run```
find . -user root
```and post the output here?

---

### Post by 4kh3RAm on 2016-08-02
Here it is.

   ```
./.thumbnails
./Music/MUSIC.zip
./Icons/Scripts.png
./Icons/Maxtor_SDB1.png
./Icons/Thermometer.png
./Icons/Icons.png
./Icons/hardware.png
./Icons/Reboot.png
./Icons/thermometer2.png
./Icons/Console.png
./Icons/Search.png
./Icons/Webcam-icon.png
./Icons/calculator.png
./Icons/Thunar-logo.png
./Icons/Journal.png
./Icons/Shutdown.png
./Icons/alarm-clock-icon.png
./Icons/Ubuntu_Icons.zip
./Icons/Music.png
./Icons/Documents.png
./Icons/IrfanView-icon.png
./Icons/Backup_Files.png
./Icons/Mazda_CX-7.png
./Icons/Fax-icon.png
./Icons/POWER_OFF.png
./Icons/Puppy_6.3.0_Linux_Icons.zip
./Icons/****.png
./Icons/BLANK_ODT.png
./Icons/LogOff.png
./Icons/Downloads.png
./Icons/Timer.png
./.cache/gvfs-burn
./.cache/mozilla/firefox/f5kf937w.default/cache2/entries/F95C8F0FBC3C9853D8DA49C7A3D5CBC7B1003494
./.cache/mozilla/firefox/f5kf937w.default/cache2/entries/ED435D317DDF6011C4E77BBE98E492B8E1DC5C09
./.cache/mozilla/firefox/f5kf937w.default/cache2/entries/76EF1292F45B28008B0E37EDAF898359BDA69EF7
./.cache/mozilla/firefox/f5kf937w.default/cache2/entries/BA5B00FE10C66B51AE0A363E2D5F1B4E065442C6
./.cache/mozilla/firefox/f5kf937w.default/cache2/entries/BD5DB8CE4929C1712F5574692E6212EDA82ECAB7
./.cache/mozilla/firefox/f5kf937w.default/cache2/entries/DD05E790120E585B1C257C3CC0E3E5525BF5FC2F
./.cache/mozilla/firefox/f5kf937w.default/cache2/entries/D18F4EF5FC84632FD5ED8C637B828A6C7F6EE03B
./.cache/mozilla/firefox/f5kf937w.default/cache2/entries/71DFBAAACE3BD1BEE046A44CB507CE69B57936F1
./.cache/mozilla/firefox/f5kf937w.default/cache2/entries/E9BCF22B1A6686E3F1225F2654502667B514C9AA
./.cache/mozilla/firefox/f5kf937w.default/cache2/entries/4CDE31880A631335F789FC6D73660CD945C147B9
./.cache/mozilla/firefox/f5kf937w.default/cache2/entries/81891801FEAAB03CA623D8EA33A96214385BBE6D
./.cache/mozilla/firefox/f5kf937w.default/cache2/entries/9067225723E8BEB7D067C473D8D686A9CB64BD72
./.cache/mozilla/firefox/f5kf937w.default/cache2/entries/108573E2B07FF25FFCAFE37F58D375561A47424D
./.cache/mozilla/firefox/f5kf937w.default/cache2/entries/197C06D2B4D851808F7B725C0A8AAD7085808F2D
./.cache/mozilla/firefox/f5kf937w.default/cache2/entries/4B4C98FE6DAD465F6E25ADAF795AFB170E6AB706
./.cache/mozilla/firefox/f5kf937w.default/cache2/entries/F1B5C3EDE100D4A38A0A28F1CEF6FAEFB619EC1B
./.cache/mozilla/firefox/f5kf937w.default/directoryLinks.json
./.cache/mozilla/firefox/f5kf937w.default/frequencyCap.json
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/test-malware-simple.sbstore
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/test-trackwhite-simple.pset
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/goog-phish-shavar.pset
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/test-phish-simple.cache
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/goog-badbinurl-shavar.sbstore
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/test-block-simple.sbstore
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/test-unwanted-simple.sbstore
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/goog-malware-shavar.pset
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/test-unwanted-simple.pset
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/test-track-simple.pset
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/goog-phish-shavar.cache
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/test-phish-simple.pset
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/test-block-simple.pset
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/test-forbid-simple.sbstore
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/test-unwanted-simple.cache
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/test-phish-simple.sbstore
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/mozstd-track-digest256.cache
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/test-track-simple.sbstore
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/goog-unwanted-shavar.pset
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/test-forbid-simple.pset
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/test-track-simple.cache
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/test-malware-simple.pset
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/test-malware-simple.cache
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/goog-phish-shavar.sbstore
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/mozstd-track-digest256.sbstore
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/mozstd-trackwhite-digest256.sbstore
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/test-trackwhite-simple.cache
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/goog-malware-shavar.cache
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/goog-malware-shavar.sbstore
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/test-trackwhite-simple.sbstore
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/test-block-simple.cache
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/goog-unwanted-shavar.cache
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/mozstd-trackwhite-digest256.pset
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/mozstd-trackwhite-digest256.cache
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/goog-badbinurl-shavar.pset
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/test-forbid-simple.cache
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/goog-unwanted-shavar.sbstore
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/goog-badbinurl-shavar.cache
./.cache/mozilla/firefox/f5kf937w.default/safebrowsing/mozstd-track-digest256.pset
./.cache/mozilla/firefox/f5kf937w.default/startupCache
./.cache/mozilla/firefox/f5kf937w.default/startupCache/startupCache.8.little
./.cache/dconf
./.cache/thumbnails/normal/7506e32a97f5f6b328ae62bab071faa9.png
./.cache/thumbnails/normal/28388851dac539d5720a71bd89dcf267.png
./.cache/thumbnails/normal/804bb0615140583a968e8ec0d750135d.png
./.cache/thumbnails/normal/d0f7160c87760818ca88aaaaf724b6d0.png
./.cache/thumbnails/normal/ae2a32d6d0a20c0a1fb7d642855f5e6b.png
./.cache/thumbnails/normal/618617fe026d136f4168314577fda82d.png
./.cache/thumbnails/normal/2354fd234851d242826baa2ffc15a0ee.png
./.cache/thumbnails/normal/316b19979e0dd144be4fd964f5a5204f.png
./.cache/thumbnails/normal/b144f08ddbe0dd2d0b0ceaa2d90740be.png
./.cache/thumbnails/normal/677553021ff4477ec7b8ae1ef22c2369.png
./.cache/thumbnails/normal/6be3dd31aadaad48975485f9a380a0dd.png
./.cache/thumbnails/normal/89c414ae6d6e7217c1b380fda980f799.png
./.cache/thumbnails/normal/362c93e6be329a803cf6942e441881c4.png
./.cache/thumbnails/normal/cc1f50c04d5b19178cd81e33ba2768e1.png
./.cache/thumbnails/normal/8d9ac9bf6adcc79153497c0de7a39515.png
./.cache/thumbnails/normal/665551ffee4334fb770c94d52d431c03.png
./.cache/thumbnails/normal/f3d56d2731ccfafb74d1699fcc15634c.png
./.cache/thumbnails/normal/ae59271346825c20c1398f8df09df7a2.png
./.cache/thumbnails/normal/ec841e4687564db415b9accada15d426.png
./.cache/thumbnails/normal/30087eeadaa23994b0dd2e8e02f85557.png
./.cache/thumbnails/normal/927ca83d68b463fc4b6ddc2857da1f43.png
./.cache/thumbnails/normal/3f69b9af6f6f8a31d6230f56b79d89d2.png
./.cache/thumbnails/normal/0b692e152bcb0f157a4c8f72cff30ee9.png
./.cache/thumbnails/normal/a95a7d23c4dd8c5b6eee7ab2c66287ee.png
./.cache/thumbnails/normal/32889aae6c60c0a40d79c29299f4aa3d.png
./.cache/thumbnails/normal/404fbb74500fb52fb014465dd5bb3efd.png
./.cache/thumbnails/normal/f99824a6e949a0e0135784fdd342ebf5.png
./.cache/thumbnails/normal/41151b974dff10bc73d05aa4733b3219.png
./.cache/thumbnails/normal/bcb3e23eeb5ffe399c2eab601766a3cf.png
./.cache/thumbnails/normal/fad2af326e1d06ab561f3791502842e9.png
./.cache/thumbnails/normal/ceea7ffdca15c6a7238c440cad52d8b5.png
./.cache/thumbnails/normal/01907f6053554a77b3dea106307936f2.png
./.cache/thumbnails/normal/8d789ffe8037b71da00d37355622b9db.png
./.cache/thumbnails/normal/c77e258d7340e8dcd7b88084d9c2bdfc.png
./.cache/thumbnails/normal/d27f06c3940dcbc96547eac8e293b037.png
./.cache/thumbnails/normal/dc4736e7baca58eee54b8bfe66ecb5d9.png
./.cache/thumbnails/normal/17120505524a03b3a2f04a64a94464f1.png
./.cache/thumbnails/normal/897fd57076e5f2411959062494eaa174.png
./.cache/thumbnails/normal/2fcf437af6372c52e827e6ad7f313f6f.png
./.cache/thumbnails/normal/d53a8a72f93ffc087ce45e8492153298.png
./.cache/thumbnails/normal/efa87d2f7647a1a9d5724e817cc2ce91.png
./.cache/thumbnails/normal/a42d576d64a3e4a2d966d76655145340.png
./.cache/thumbnails/normal/6dc2c170492eb6b205d417fbe1a880a4.png
./.cache/thumbnails/normal/8977ab36fe84f7956944fcfa737aa750.png
./.cache/thumbnails/normal/584ad25c8f8911e3a8fecf5593d50ae0.png
./.cache/thumbnails/normal/59529bd904a19fedd61695bb68c4a3a7.png
./.cache/thumbnails/normal/747de5b6d047d6a04d61e387ed0d7f59.png
./.cache/.fr-24IRBz
./Ubuntu_Scripts.zip
./.config/xfce4
./.config/xfce4/xfconf
./.config/xfce4/xfconf/xfce-perchannel-xml
./.config/Thunar
./.config/xarchiver/xarchiverrc
./.config/enchant
./.config/libreoffice/4/user/extensions
./.config/libreoffice/4/user/extensions/tmp
./.config/libreoffice/4/user/extensions/tmp/extensions
./.config/libreoffice/4/user/extensions/tmp/registry
./.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend
./.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend
./.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend
./.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/backenddb.xml
./.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend
./.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend
./.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/backenddb.xml
./.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend
./.config/libreoffice/4/user/extensions/tmp/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend
./.config/libreoffice/4/user/extensions/buildid
./.config/libreoffice/4/user/extensions/bundled
./.config/libreoffice/4/user/extensions/bundled/lastsynchronized
./.config/libreoffice/4/user/extensions/bundled/registry
./.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend
./.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend
./.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend
./.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/backenddb.xml
./.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend
./.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend
./.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/backenddb.xml
./.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend
./.config/libreoffice/4/user/extensions/bundled/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend
./.config/libreoffice/4/user/extensions/shared
./.config/libreoffice/4/user/extensions/shared/lastsynchronized
./.config/libreoffice/4/user/extensions/shared/registry
./.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend
./.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend
./.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend
./.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/backenddb.xml
./.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend
./.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend
./.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/backenddb.xml
./.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend
./.config/libreoffice/4/user/extensions/shared/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend
./.config/libreoffice/4/user/extensions/shared/log.txt
./.config/libreoffice/4/user/uno_packages
./.config/libreoffice/4/user/uno_packages/cache
./.config/libreoffice/4/user/uno_packages/cache/uno_packages
./.config/libreoffice/4/user/uno_packages/cache/registry
./.config/libreoffice/4/user/uno_packages/cache/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend
./.config/libreoffice/4/user/uno_packages/cache/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend
./.config/libreoffice/4/user/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend
./.config/libreoffice/4/user/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/backenddb.xml
./.config/libreoffice/4/user/uno_packages/cache/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend
./.config/libreoffice/4/user/uno_packages/cache/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend
./.config/libreoffice/4/user/uno_packages/cache/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/backenddb.xml
./.config/libreoffice/4/user/uno_packages/cache/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend
./.config/libreoffice/4/user/uno_packages/cache/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend
./.config/libreoffice/4/user/uno_packages/cache/log.txt
./.config/libreoffice/4/user/basic
./.config/libreoffice/4/user/basic/script.xlc
./.config/libreoffice/4/user/basic/Standard
./.config/libreoffice/4/user/basic/Standard/Module1.xba
./.config/libreoffice/4/user/basic/Standard/script.xlb
./.config/libreoffice/4/user/basic/Standard/dialog.xlb
./.config/libreoffice/4/user/basic/dialog.xlc
./.config/libreoffice/4/user/autocorr
./.config/libreoffice/4/user/database
./.config/libreoffice/4/user/database/evolocal.odb
./.config/libreoffice/4/user/database/biblio.odb
./.config/libreoffice/4/user/database/biblio
./.config/libreoffice/4/user/database/biblio/biblio.dbt
./.config/libreoffice/4/user/database/biblio/biblio.dbf
./.config/libreoffice/4/user/autotext
./.config/libreoffice/4/user/autotext/mytexts.bau
./.config/libreoffice/4/user/temp
./.config/libreoffice/4/user/temp/document_io_logring.txt
./.config/libreoffice/4/user/config
./.config/libreoffice/4/user/config/soffice.cfg
./.config/libreoffice/4/user/config/soffice.cfg/modules
./.config/libreoffice/4/user/config/soffice.cfg/modules/swriter
./.config/libreoffice/4/user/config/soffice.cfg/modules/swriter/statusbar
./.config/libreoffice/4/user/config/soffice.cfg/modules/swriter/images
./.config/libreoffice/4/user/config/soffice.cfg/modules/swriter/images/Bitmaps
./.config/libreoffice/4/user/config/soffice.cfg/modules/swriter/popupmenu
./.config/libreoffice/4/user/config/soffice.cfg/modules/swriter/menubar
./.config/libreoffice/4/user/config/soffice.cfg/modules/swriter/toolbar
./.config/libreoffice/4/user/config/soffice.cfg/modules/sdraw
./.config/libreoffice/4/user/config/soffice.cfg/modules/sdraw/statusbar
./.config/libreoffice/4/user/config/soffice.cfg/modules/sdraw/images
./.config/libreoffice/4/user/config/soffice.cfg/modules/sdraw/images/Bitmaps
./.config/libreoffice/4/user/config/soffice.cfg/modules/sdraw/popupmenu
./.config/libreoffice/4/user/config/soffice.cfg/modules/sdraw/menubar
./.config/libreoffice/4/user/config/soffice.cfg/modules/sdraw/toolbar
./.config/libreoffice/4/user/config/soffice.cfg/modules/scalc
./.config/libreoffice/4/user/config/soffice.cfg/modules/scalc/statusbar
./.config/libreoffice/4/user/config/soffice.cfg/modules/scalc/images
./.config/libreoffice/4/user/config/soffice.cfg/modules/scalc/images/Bitmaps
./.config/libreoffice/4/user/config/soffice.cfg/modules/scalc/popupmenu
./.config/libreoffice/4/user/config/soffice.cfg/modules/scalc/menubar
./.config/libreoffice/4/user/config/soffice.cfg/modules/scalc/toolbar
./.config/libreoffice/4/user/config/autotbl.fmt
./.config/libreoffice/4/user/config/javasettings_Linux_X86_64.xml
./.config/libreoffice/4/user/psprint
./.config/libreoffice/4/user/psprint/pspfontcache
./.config/libreoffice/4/user/gallery
./.config/libreoffice/4/user/gallery/sg30.thm
./.config/libreoffice/4/user/gallery/sg30.sdv
./.config/menus/applications-merged/xdg-desktop-menu-dummy.menu
./Ubuntu_Documents.zip
./.gvfs
./.wine/drive_c/windows/ml.exe
./Documents/Hope_Journal.odt
./Documents/MomsPhoneList.rtf
./Documents/Ubuntu_Documents.zip
./Documents/JSC_Check_Register.odt
./Documents/CrockPotRecipesWeb.pdf
./Documents/Blank.odt
./Documents/CX7_Maintenance_Log.odt
./Documents/Beacon_Check_Register.odt
./Documents/TEMP_Deleteme.txt
./Documents/5160_LABEL_2_And_5_eights_X_1_inch.doc
./Documents/files.7z
./Documents/temp.txt.7z
./Documents/wrdbckup.zip
./Documents/CrockPotRecipesWeb.odg
./.local/share/gvfs-metadata/home-f598ad89.log
./.local/share/gvfs-metadata/home
./.mozilla/seamonkey/v23gi2p8.default/Ubuntu_Scripts.zip
./.mozilla/seamonkey/v23gi2p8.default/Ubuntu_Documents.zip
./.mozilla/firefox/f5kf937w.default/mimeTypes.rdf
./.mozilla/firefox/f5kf937w.default/revocations.txt
./.mozilla/firefox/f5kf937w.default/prefs.js
./.mozilla/firefox/f5kf937w.default/sessionCheckpoints.json
./.mozilla/firefox/f5kf937w.default/sessionstore.js
./.mozilla/firefox/f5kf937w.default/webapps/webapps.json
./.mozilla/firefox/f5kf937w.default/xulstore.json
./.mozilla/firefox/f5kf937w.default/datareporting/archived/2016-07/1469473464313.e9a54e5e-8c7a-4c8c-8fa2-abf59822c5b6.main.jsonlz4
./.mozilla/firefox/f5kf937w.default/datareporting/archived/2016-07/1468636776820.95b256b5-f86d-492a-8ed8-91830380b5c4.main.jsonlz4
./.mozilla/firefox/f5kf937w.default/datareporting/archived/2016-07/1468593573048.4b4ae19e-d68c-44eb-875c-ca24f9c8ff4c.main.jsonlz4
./.mozilla/firefox/f5kf937w.default/datareporting/archived/2016-07/1469998678355.d5eac893-ce05-4949-962f-afafdca172a8.main.jsonlz4
./.mozilla/firefox/f5kf937w.default/datareporting/archived/2016-07/1469998669337.8fef6431-bcd4-4d09-b265-df2cf5df5e23.main.jsonlz4
./.mozilla/firefox/f5kf937w.default/datareporting/archived/2016-08
./.mozilla/firefox/f5kf937w.default/datareporting/session-state.json
./.mozilla/firefox/f5kf937w.default/sessionstore-backups/previous.js
./.mozilla/firefox/f5kf937w.default/bookmarks.html
./.mozilla/firefox/f5kf937w.default/saved-telemetry-pings/089cae66-dac9-4f87-8688-3ea53cfa88fe
./.mozilla/firefox/f5kf937w.default/saved-telemetry-pings/b2f0949f-c04f-4052-97e9-f2244b3e2850
./.mozilla/firefox/f5kf937w.default/saved-telemetry-pings/6589a043-9771-4240-adb5-1a55f3536f69
./.mozilla/firefox/f5kf937w.default/saved-telemetry-pings/cd7af0b4-56d1-4411-843f-4f1bde81e4fd
./.mozilla/firefox/f5kf937w.default/saved-telemetry-pings/8d722b48-eab9-4b71-93ec-0354c3bd0d88
./.mozilla/firefox/f5kf937w.default/saved-telemetry-pings/774ee7fd-fe7b-4375-aef7-313690ba7029
./.mozilla/firefox/f5kf937w.default/saved-telemetry-pings/f8b561f8-3e76-49f6-adfc-fe18db0b16cb
./.mozilla/firefox/f5kf937w.default/gmp/Linux_x86_64-gcc3
./Scripts/50_VOL.sh
./Scripts/Locate_File.sh
./Scripts/Puppy_6.3.0_Bash_Scripts.zip
./Scripts/Documents.sh
./Scripts/Alarm1.sh
./Scripts/MAKE_SCRIPTS_EXE.sh
./Scripts/Find_File.sh
./Scripts/Ubuntu_Scripts.zip
./Scripts/Music.sh
./Scripts/30_VOL.sh
./Scripts/Battery_State.sh
./Scripts/Icons_Dir.sh
./Scripts/SDB1_LF.sh
./Scripts/Shutdown.sh
./Scripts/CleanUp.sh
./Scripts/HD_Temp.sh
./Scripts/Blank.sh
./Scripts/CPU_Temp.sh
./Scripts/Reboot.sh
./Scripts/HD_AND_Cpu_Temps.sh
./Scripts/HardInfo.sh
./Scripts/50_Percent_VOL.sh
./Desktop/Blank.sh
```

---

### Post by ajgreeny on 2016-08-02
There's the reason for your problem!

It looks as if many of your home folders and files are owned by root for some reason, including ~/.config/Thunar which is why you can not write a new uca.xml file for you as user.

I think the first action to take is to make sure everything in your home is owned by you so run command ```
sudo chown *user*:*user* /home/*user*
``` changing *user* where I show it to your username, and everything should now belong to you as it should.

---

### Post by 4kh3RAm on 2016-08-02
I did so.

Getting permission denied.

---

### Post by ajgreeny on 2016-08-02
> **4kh3RAm said:**
> I did so.

Getting permission denied.
Are you logged in as your username to run that command?
Permission denied for what; to run that **sudo chown** command?  

If so, there is something very strange going on here and I, for one, can not put my finger on what it might be.

Have you been using **sudo** to run GUI apps as root at some time? That can cause the type of problem we are seeing here by changing ownership of some of your home files and folders to root, thereby occasionally even locking users out of their system.

---

### Post by dragonfly41 on 2016-08-02
Shouldn't that command include -R  arg?

```

sudo chown -R *user*:*user* /home/[I]user

```[/I]

---

### Post by ajgreeny on 2016-08-02
Well spotted dragonfly41, yes it should be recursive; my whoopsie as I was thinking too quickly to get it right.

Yes, sorry 4kh3RAm, it should indeed be ```
sudo chown -R *user*:*user* /home/*user*
```
See if that makes any difference; my original command changed ownership of the root of your home folder only, not everything in it as well, so my sincere apologies for the mistake.

---

### Post by 4kh3RAm on 2016-08-02
I got the message when I tried to create a custom action.

Yes, I frequently use scripts to avoid having to type password all the time.

```
echo xxxxxxx | sudo -S  cp -u -f bookmarks.html /media/andy/MAXTOR_SDB1/Linux_Files

```
If there is a better alternative, I am game.

```
sudo chown -R andy:andy /home/andy
chown: changing ownership of '/home/andy/.gvfs': Function not implemented
```

Things are getting worse.
```

sudo wine telephone.exe
wine: /home/andy/.wine is not owned by you
```

How do I undo the chown command that I ran ?

---

### Post by vasa1 on 2016-08-02
> **ajgreeny said:**
> There's the reason for your problem!

It looks as if many of your home folders and files are owned by root for some reason, including ~/.config/Thunar which is why you can not write a new uca.xml file for you as user. ...
That's why I asked OP to run that command ;) I was worried when I read that OP had set up custom actions for Thunar when running as root (in the first post).

---

### Post by dragonfly41 on 2016-08-03
Researching your problem here ... after google search phrase ...
chown: changing ownership of : Function not implemented

[https://ubuntuforums.org/showthread.php?t=1165553](https://ubuntuforums.org/showthread.php?t=1165553)

one conclusion seems to be ...

> 
You are probably trying to change the ownership of a non-linux file system. Chown will work on ext2/3/4 formats but if you are trying to do this on fat16/32 or ntfs it will give you the message you are getting.

Ownership is set at the time of mounting and can't be changed once mounted. What you are describing is normal for an ntfs partition: owned by root (but you should still have read/write access).

                                                                       source: post #5 @drs305


To find what partition filesystem you have installed, read further here ...

[http://askubuntu.com/questions/309047/how-do-i-find-out-what-filesystem-my-partitions-are-using](http://askubuntu.com/questions/309047/how-do-i-find-out-what-filesystem-my-partitions-are-using)

```

df -T

```

Since you are using wine is it reasonable to deduce that you have come from the land of Windows and perhaps incorrectly installed Ubuntu on ntfs?

Now trying to answer your question on wine ...
> 
sudo wine telephone.exe
wine: /home/andy/.wine is not owned by you

You can find who owns a file by change directory to the location of telephone.exe
and run in terminal ...

```

ls -l telephone.exe

```

Now check ownership of wine executable (to find it use sudo locate wine).


[COLOR=#b22222]**[Later edit]**[/COLOR]

Reading a related thread here started by you ...

[https://ubuntuforums.org/showthread.php?t=2332351&page=2](https://ubuntuforums.org/showthread.php?t=2332351&page=2)

@howfield suggests ...
> Or the old chestnut, a Windows VM.

Have you considered running Windows in VirtualBox for your use in Ubuntu?
Or even dual boot Ubuntu/Windows?

---

### Post by 4kh3RAm on 2016-08-03
> **dragonfly41 said:**
> Researching your problem here ... after google search phrase ...
chown: changing ownership of : Function not implemented

[https://ubuntuforums.org/showthread.php?t=1165553](https://ubuntuforums.org/showthread.php?t=1165553)

one conclusion seems to be ...



To find what partition filesystem you have installed, read further here ...

[http://askubuntu.com/questions/309047/how-do-i-find-out-what-filesystem-my-partitions-are-using](http://askubuntu.com/questions/309047/how-do-i-find-out-what-filesystem-my-partitions-are-using)

```

df -T

```

Since you are using wine is it reasonable to deduce that you have come from the land of Windows and perhaps incorrectly installed Ubuntu on ntfs?

Now trying to answer your question on wine ...

You can find who owns a file by change directory to the location of telephone.exe
and run in terminal ...

```

ls -l telephone.exe

```

Now check ownership of wine executable (to find it use sudo locate wine).


[COLOR=#b22222]**[Later edit]**[/COLOR]

Reading a related thread here started by you ...

[https://ubuntuforums.org/showthread.php?t=2332351&page=2](https://ubuntuforums.org/showthread.php?t=2332351&page=2)

@howfield suggests ...


Have you considered running Windows in VirtualBox for your use in Ubuntu?
Or even dual boot Ubuntu/Windows?

I have not incorrectly installed Ubuntu on ntfs.

It is installed on a ext3 partition.

I have been using Linux for over 2 years.
Quite familiar with it.

I am not running Windows at all and have no plans to do so.
How someone has the impression I was running Windows, is a mystery.

> df -T
Filesystem     Type     1K-blocks     Used Available Use% Mounted on
udev           devtmpfs   3523980        0   3523980   0% /dev
tmpfs          tmpfs       708652     9688    698964   2% /run
/dev/sda3      ext3     619166160 11724528 575983088   2% /
tmpfs          tmpfs      3543248      444   3542804   1% /dev/shm
tmpfs          tmpfs         5120        4      5116   1% /run/lock
tmpfs          tmpfs      3543248        0   3543248   0% /sys/fs/cgroup
/dev/sdb1      ext3     101397896  3944988  92295532   5% /media/andy/MAXTOR_SDB1
/dev/sdb5      ext3     101760368 19732716  76851844  21% /media/andy/MAXTOR_SDB5
/dev/sdb2      ext3     104112352    61164  98755932   1% /media/andy/MAXTOR_SDB2
tmpfs          tmpfs       708652       32    708620   1% /run/user/1000


ls -l telephone.exe
-rwxrwxr-x 1 andy andy 1536 Aug  1 22:48 telephone.exe

The info that you gave me has no bearing on my question.

> I would still like to **_undo_** those 2 chown "experiments" that I ran.

Those chown commands I was asked to run have made me unable to use a program I installed in Wine.

So, I have too options.

Live with NOT being able to use that program OR re-install Ubuntu and lose all my customizations etc.

---

### Post by &amp;KyT$0P# on 2016-08-03
Or just don't run Wine as root (drop the sudo)?

---

### Post by dragonfly41 on 2016-08-03
o.k. .. gleaned some more clues.  Now do you have your partition defined as ext3 in /etc/fstab ?

> 
[COLOR=#000000]I am not running Windows at all and have no plans to do so.[/COLOR]
[COLOR=#000000]How someone has the impression I was running Windows, is a mystery.[/COLOR]


I usually associate a .exe file with Windows.

---

### Post by vasa1 on 2016-08-03
Please use **code** tags to enclose material you copy from the terminal.

Please use **quote** tags for quoting material from other posts or sources other than the terminal.

Thanks in anticipation of your cooperation :)

---

### Post by 4kh3RAm on 2016-08-03
> **dragonfly41 said:**
> o.k. .. gleaned some more clues.  Now do you have your partition defined as ext3 in /etc/fstab ?



I usually associate a .exe file with Windows.[/COLOR]

I understand you.

Of course an .exe is designed for Windows, but if I had a problem running it with Windows, I would not be posting about in a Linux forum.

---

### Post by dragonfly41 on 2016-08-03
You should not assume that we can read your mind.  
Is this the first time you have attempted to execute telephone.exe in wine?
Or did it work *before* the chown hiccup?

---

### Post by 4kh3RAm on 2016-08-03
> **halogen2 said:**
> Or just don't run Wine as root (drop the sudo)?

It does not work.

I can open my editor for compiling programs, but it produces no programs like it use to.

> **dragonfly41 said:**
> You should not assume that we can read your mind.  
Is this the first time you have attempted to execute telephone.exe in wine?
Or did it work *before* the chown hiccup?

Executing the .exe is not the issue.

It ran before the chown hiccup even if it produced no sound.

I have been told that Linux has no sound APIs like Windows, so Windows source code that produce sound will not generally work. :-(

I posted a reply to a request to run my editor without sudo.

---

### Post by dragonfly41 on 2016-08-03
One more idea ...
From memory in using wine (which I dropped a long time ago) ...

[COLOR=#000000]Go to the Applications menu -> Wine -> Browse C:\ Drive. 

Then copy your telephone.exe to this location. 

Right click the file, and select Open with Wine.[/COLOR]

---

### Post by 4kh3RAm on 2016-08-03
Dragonfly,

Thanks.

I need to fix the issue of NOT being able to compile programs that I USED to be able to do before running those chown commands.

I have an Ubuntu file for tips etc.

I may have to add this statement.

NEVER run any chown statements !! :-)

Hope you have  great day.

---

### Post by 4kh3RAm on 2016-08-03
Gentlemen and scholars,

I re-installed wine.

Everything is working now. :-)

I am running wine without sudo.

---

### Post by dragonfly41 on 2016-08-03
Reading discussion here ...

[https://ubuntuforums.org/archive/index.php/t-634075.html](https://ubuntuforums.org/archive/index.php/t-634075.html)

Try ...
```

sudo chown -R andy:andy ~/.wine

```

and also try ...
```

sudo wincfg

```

more tips here ...

[https://bbs.archlinux.org/viewtopic.php?id=158318](https://bbs.archlinux.org/viewtopic.php?id=158318)

...

I can't offer any more tips.   Beyond my ken.

[Later edit]

You beat me by a few seconds.

---

### Post by 4kh3RAm on 2016-08-03
Before I try those, I need to know exactly what they will do.

Everything is working now....I do not want to risk undoing anything. :-)

I know to not run wine as root.

I may see if I can write a script that would prevent me from accidentally using sudo.

All my source code is written by me or by others whom I trust and have known a long time.

While Linux is quite resistant to malware, I know there are some that work at creating havoc.

---

### Post by dragonfly41 on 2016-08-03
Ignore my last suggestion which was overtaken by your installation.
I was typing while you were reinstalling.
I didn't delete my post.   Left it there for the record.

I suggest that you mark this thread as solved.

---

### Post by lisati on 2016-08-03
> **4kh3RAm said:**
> I understand you.

Of course an .exe is designed for Windows,<snip>

Not necessarily. Somewhere I have some floppy disks gathering dust with some .EXE files on them which weren't designed for Windows, but for MS-DOS/PC-DOS. Some of them might be usable with some versions of Windows, but we digress.

---

### Post by 4kh3RAm on 2016-08-03
> 
IBM again approached Bill Gates. Gates in turn approached [Seattle Computer Products]("https://en.wikipedia.org/wiki/Seattle_Computer_Products"). There, programmer [Tim Paterson]("https://en.wikipedia.org/wiki/Tim_Paterson") had developed a variant of [CP/M-80]("https://en.wikipedia.org/wiki/CP/M-80"), intended as an internal product for testing SCP's new [16-bit]("https://en.wikipedia.org/wiki/16-bit") [Intel 8086]("https://en.wikipedia.org/wiki/Intel_8086") [CPU]("https://en.wikipedia.org/wiki/Central_processing_unit") card for the [S-100 bus]("https://en.wikipedia.org/wiki/S-100_bus"). The system was initially named QDOS (Quick and Dirty Operating System), before being made commercially available as [86-DOS]("https://en.wikipedia.org/wiki/86-DOS"). Microsoft purchased 86-DOS, allegedly for $50,000. This became Microsoft Disk Operating System, MS-DOS, introduced in 1981.[SUP][[4]]("https://en.wikipedia.org/wiki/DOS#cite_note-mshist-4")[/SUP]

16 bit programs can not be run from any Windows version past XP.


I still have the source code for a lot of 16 bit programs.

They probably would not run on my 64 bit system.

---

