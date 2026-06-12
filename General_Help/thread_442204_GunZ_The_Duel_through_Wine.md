---
title: "GunZ: The Duel through Wine"
date: 2007-05-13
forum: General Help
---

### Post by kmslinux on 2007-05-13
I installed ies4linux and went to gunz.ijji.com through IE. I installed GunZ and now I want to play it. Whenever I click the 'Play Live' button, the orange dialog box opens up and then disappears and nothing happens after that. I decided to dig deeper and went to my Gunz directory.

```
root@Connubuntu:/downloads/Gunz# ls
BAReport.exe   Gunz.exe                mlog.txt       sfx.mrs
config.xml     GunzLauncher.exe        Model          Shader
CUSTOM         GunzUS.ini              model.mrs      Sound
dbghelp.dll    HanAuthForClient.dll    msvcp71.dll    system.mrs
fmod.dll       HanReportForClient.dll  msvcr71.dll    Uninstall.exe
GameGuard.des  Interface               patchlog.html  Update1.mrs
gdiplus.dll    Maps                    Quest
root@Connubuntu:/downloads/Gunz# wine GunzLauncher.exe
fixme:shdocvw:WebBrowser_QueryInterface (0x171ef0)->({bd1ae5e0-a6ae-11ce-bd37-504200c10000} 0x33d430) interface not supported
fixme:shdocvw:PersistStreamInit_Load (0x171ef0)->(0x33d3fc)
fixme:shdocvw:OleControl_FreezeEvents (0x171ef0)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x171ef0)->(0)
root@Connubuntu:/downloads/Gunz#
```

Please help! Is there a Wine patch for WebBrowser_QueryInterface?

---

### Post by Sammi on 2007-05-13
The official and right place to discuss and look for info on running apps in Wine is at [appdb.winehq.org]("http://ubuntuforums.org/appdb.winehq.org")

The direct link for GunZ: [http://appdb.winehq.org/appview.php?iAppId=3723](http://appdb.winehq.org/appview.php?iAppId=3723)

It does not look promising.

---

### Post by kmslinux on 2007-05-13
> **Sammi said:**
> The official and right place to discuss and look for info on running apps in Wine is at [appdb.winehq.org]("http://ubuntuforums.org/appdb.winehq.org")

The direct link for GunZ: [http://appdb.winehq.org/appview.php?iAppId=3723](http://appdb.winehq.org/appview.php?iAppId=3723)

It does not look promising.

Dang.

---

