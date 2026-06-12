---
title: "Install Teamviewer on lubuntu"
date: 2015-05-16
forum: General Help
---

### Post by David_Isler on 2015-05-16
Hi There

I'm a big new newbie on linux :). In a project, we try to set up a new monitoring software. We set up a server with PRTG. Now, we try to get information from a foreign network. For that, we set up a "probe" with lubuntu. We are causing some problems with the "probe". On the probe, there is lubuntu installed. To make it more Easy for me, we also put LXDE(lxde.org) on it. The "probe" is installed in the server room, we had the Idea, to install "Teamviewer" on it. I read several list, how to installed it, but i always get the same error message.

"Dependency is not statisfiable: libc6 (>=2.4)"

Lintian-Output
```
W: teamviewer: hardening-no-relro opt/teamviewer/tv_bin/RTlib/libQtCore.so.4W: teamviewer: hardening-no-relro opt/teamviewer/tv_bin/RTlib/libQtGui.so.4
E: teamviewer: embedded-library opt/teamviewer/tv_bin/RTlib/libQtNetwork.so.4: openssl
W: teamviewer: hardening-no-relro opt/teamviewer/tv_bin/RTlib/libQtNetwork.so.4
E: teamviewer: embedded-library opt/teamviewer/tv_bin/RTlib/libQtWebKit.so.4: sqlite
W: teamviewer: hardening-no-relro opt/teamviewer/tv_bin/RTlib/libQtWebKit.so.4
E: teamviewer: embedded-library opt/teamviewer/tv_bin/TVGuiDelegate: zlib
E: teamviewer: embedded-library opt/teamviewer/tv_bin/TVGuiDelegate: libjsoncpp
E: teamviewer: embedded-library opt/teamviewer/tv_bin/TVGuiSlave.32: zlib
E: teamviewer: embedded-library opt/teamviewer/tv_bin/TVGuiSlave.32: libjsoncpp
E: teamviewer: binary-from-other-architecture opt/teamviewer/tv_bin/TVGuiSlave.64
E: teamviewer: embedded-library opt/teamviewer/tv_bin/TVGuiSlave.64: zlib
E: teamviewer: embedded-library opt/teamviewer/tv_bin/TVGuiSlave.64: libjsoncpp
E: teamviewer: embedded-library opt/teamviewer/tv_bin/TeamViewer_Desktop: libjpeg
E: teamviewer: embedded-library opt/teamviewer/tv_bin/TeamViewer_Desktop: zlib
E: teamviewer: embedded-library opt/teamviewer/tv_bin/TeamViewer_Desktop: libjsoncpp
E: teamviewer: embedded-library opt/teamviewer/tv_bin/teamviewerd: zlib
E: teamviewer: embedded-library opt/teamviewer/tv_bin/teamviewerd: curl
E: teamviewer: embedded-library opt/teamviewer/tv_bin/teamviewerd: libjsoncpp
E: teamviewer: statically-linked-binary opt/teamviewer/tv_bin/wine/bin/wine-preloader
E: teamviewer: changelog-file-missing-in-native-package
E: teamviewer: no-copyright-file
E: teamviewer: description-starts-with-package-name
W: teamviewer: extended-description-line-too-long
W: teamviewer: extended-description-line-too-long
W: teamviewer: unknown-section non-free/internet
E: teamviewer: dir-or-file-in-opt opt/teamviewer/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/config/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/doc/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/doc/CopyRights_DE.txt
E: teamviewer: dir-or-file-in-opt opt/teamviewer/doc/CopyRights_EN.txt
E: teamviewer: dir-or-file-in-opt opt/teamviewer/doc/License.txt
W: teamviewer: extra-license-file opt/teamviewer/doc/License.txt
E: teamviewer: dir-or-file-in-opt opt/teamviewer/doc/License_Full.txt
E: teamviewer: dir-or-file-in-opt opt/teamviewer/doc/Lizenz.txt
E: teamviewer: dir-or-file-in-opt opt/teamviewer/doc/Lizenz_Full.txt
E: teamviewer: dir-or-file-in-opt opt/teamviewer/doc/license_foss.txt
E: teamviewer: dir-or-file-in-opt opt/teamviewer/logfiles/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/RTlib/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/RTlib/README
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/RTlib/doc/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/RTlib/doc/Qt4/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/RTlib/doc/Qt4/TeamViewerNote.txt
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/RTlib/doc/Qt4/WEBKIT-LICENSE.LGPL
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/RTlib/libQtCore.so.4
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/RTlib/libQtGui.so.4
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/RTlib/libQtNetwork.so.4
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/RTlib/libQtWebKit.so.4
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/TVGuiDelegate
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/TVGuiSlave.32
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/TVGuiSlave.64
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/TeamViewer
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/TeamViewer_Desktop
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/desktop/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/desktop/teamviewer-teamviewer10.desktop
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/desktop/teamviewer.png
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/fonts_portable.conf
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/fontsmooth_rgb.reg
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/libdepend
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/no_fileassocs.reg
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/no_xrandr.reg
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/no_xvidmodeext.reg
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/setwinver.reg
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/teamviewer
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/teamviewer_setup
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/teamviewerd.DEB.conf
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/teamviewerd.RPM.conf
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/teamviewerd.pp
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/teamviewerd.service
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/teamviewerd.sysv
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/tvw_aux
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/tvw_config
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/tvw_daemon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/tvw_exec
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/tvw_extra
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/tvw_main
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/tvw_profile
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/script/wait-console-kit.sh
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/teamviewerd
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/AUTHORS
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/COPYING.LIB
W: teamviewer: extra-license-file opt/teamviewer/tv_bin/wine/COPYING.LIB
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/LICENSE
W: teamviewer: extra-license-file opt/teamviewer/tv_bin/wine/LICENSE
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/README
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/VERSION
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/bin/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/bin/wine
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/bin/wine-preloader
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/bin/wineserver
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/License.txt
W: teamviewer: extra-license-file opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/License.txt
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/License_Full.txt
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/Lizenz.txt
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/Lizenz_Full.txt
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer.exe
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_bg.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_cs.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_da.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_de.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_en.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_es.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_fi.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_fr.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_hr.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_hu.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_id.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_it.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_lt.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_nl.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_no.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_pl.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_pt.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_ro.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_ru.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_sk.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_sr.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_sv.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_tr.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_Resource_uk.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/TeamViewer_StaticRes.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/TeamViewer/tvwine.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/windows/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/windows/system32/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/drive_c/windows/system32/winemenubuilder.exe
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/libwine.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/libwine.so.1
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/libwine.so.1.0
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/advapi32.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/atl100.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/avicap32.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/comctl32.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/comdlg32.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/crypt32.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/dbghelp.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/ddraw.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/devenum.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/dsound.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/explorer.exe.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/fakedlls/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/fakedlls/explorer.exe
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/fakedlls/rsabase.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/fakedlls/rsaenh.dll
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/gdi32.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/gdiplus.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/imagehlp.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/imm32.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/iphlpapi.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/kernel32.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/mapi32.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/midimap.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/mmdevapi.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/mpr.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/msacm32.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/msacm32.drv.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/msimg32.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/msvcrt.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/msvfw32.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/netapi32.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/ntdll.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/ole32.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/oleaut32.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/opengl32.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/psapi.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/quartz.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/regedit.exe.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/riched20.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/rpcrt4.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/rsaenh.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/rundll32.exe.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/secur32.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/sensapi.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/services.exe.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/setupapi.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/shell32.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/shlwapi.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/user32.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/userenv.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/usp10.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/uxtheme.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/version.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/windowscodecs.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/windowscodecsext.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/wineboot.exe.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/winecfg.exe.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/wined3d.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/winedbg.exe.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/winemapi.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/winex11.drv.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/winhttp.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/wininet.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/winmm.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/winspool.drv.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/winsta.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/wintrust.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/ws2_32.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/lib/wine/wtsapi32.dll.so
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/coue1255.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/coue1256.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/coue1257.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/coure.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/couree.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/coureg.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/courer.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/couret.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/cvgasys.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/hvgasys.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/jsmalle.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/jvgasys.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/marlett.ttf
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/smae1255.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/smae1256.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/smae1257.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/smalle.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/smallee.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/smalleg.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/smaller.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/smallet.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/ssee1255.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/ssee1256.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/ssee1257.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/ssee874.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/ssef1255.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/ssef1256.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/ssef1257.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/ssef874.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/sserife.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/sserifee.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/sserifeg.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/sserifer.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/sserifet.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/sseriff.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/sseriffe.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/sseriffg.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/sseriffr.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/sserifft.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/svgasys.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/symbol.ttf
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/tahoma.ttf
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/tahomabd.ttf
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/vgas1255.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/vgas1256.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/vgas1257.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/vgas874.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/vgasys.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/vgasyse.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/vgasysg.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/vgasysr.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/fonts/vgasyst.fon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/generic.ppd
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/l_intl.nls
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/wine/share/wine/wine.inf
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/xdg-utils/
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/xdg-utils/LICENSE
W: teamviewer: extra-license-file opt/teamviewer/tv_bin/xdg-utils/LICENSE
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/xdg-utils/README
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/xdg-utils/xdg-desktop-icon
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/xdg-utils/xdg-desktop-menu
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/xdg-utils/xdg-email
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/xdg-utils/xdg-icon-resource
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/xdg-utils/xdg-mime
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/xdg-utils/xdg-open
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/xdg-utils/xdg-screensaver
E: teamviewer: dir-or-file-in-opt opt/teamviewer/tv_bin/xdg-utils/xdg-settings
W: teamviewer: file-in-unusual-dir var/log/teamviewer
W: teamviewer: binary-without-manpage usr/bin/teamviewer
E: teamviewer: maintainer-script-does-not-check-for-existence-of-updatemenus postrm:22
W: teamviewer: postrm-has-useless-call-to-update-menus
W: teamviewer: script-not-executable opt/teamviewer/tv_bin/script/tvw_aux
W: teamviewer: script-not-executable opt/teamviewer/tv_bin/script/tvw_config
W: teamviewer: script-not-executable opt/teamviewer/tv_bin/script/tvw_daemon
W: teamviewer: script-not-executable opt/teamviewer/tv_bin/script/tvw_exec
W: teamviewer: script-not-executable opt/teamviewer/tv_bin/script/tvw_extra
W: teamviewer: script-not-executable opt/teamviewer/tv_bin/script/tvw_main
W: teamviewer: script-not-executable opt/teamviewer/tv_bin/script/tvw_profile
W: teamviewer: executable-not-elf-or-script opt/teamviewer/tv_bin/RTlib/doc/Qt4/TeamViewerNote.txt
W: teamviewer: executable-not-elf-or-script opt/teamviewer/tv_bin/RTlib/doc/Qt4/WEBKIT-LICENSE.LGPL
W: teamviewer: maintainer-script-ignores-errors postrm
W: teamviewer: maintainer-script-ignores-errors prerm
W: teamviewer: maintainer-script-ignores-errors preinst
W: teamviewer: maintainer-script-ignores-errors postinst
E: teamviewer: shlib-with-non-pic-code opt/teamviewer/tv_bin/RTlib/libQtNetwork.so.4
E: teamviewer: shlib-with-executable-bit opt/teamviewer/tv_bin/wine/lib/libwine.so.1.0 0755


Lintian mit folgendem Rückgabewert beendet: 1
```

Can somebody help me, what i do wrong? I get the same error, if i also make the installation over command line :(


Downloaded Teamviewer Version: [TABLE]
[TR]
[TD][**Download deb **v10.0.41499]("http://download.teamviewer.com/download/teamviewer_i386.deb")[/TD]
[TD][/TD]
[TD]32-Bit / 64-Bit Multiarch[/TD]
[/TR]
[/TABLE]

Looking forward for any tipps or hints

---

### Post by leunam12 on 2015-05-16
That's pretty strange, I just installed it and it worked. What Lubuntu version do you have? Do you have most recent updates? Do you have that library installed? Try this other version and see if it works: open terminal, cd to your download folder and type ```
wget http://www.teamviewer.com/download/teamviewer_linux.deb
```then double-click it.

---

### Post by David_Isler on 2015-05-16
Thanks for your answer.

Lubuntu Version 14.04 is installed. I tried your steps, but get the same error, as in the first post :(

All updates seems to be installed. When i understand linux correctly, he has some problems with libc6. I also entered "sudo apt-get install libc6". He answer on that, that already the newest version of libc6 is installed

Any other idea?

---

### Post by leunam12 on 2015-05-16
I have no idea, my only suggestion is this: ```
sudo apt-get install libc6-i386
``` and then try to install.

---

