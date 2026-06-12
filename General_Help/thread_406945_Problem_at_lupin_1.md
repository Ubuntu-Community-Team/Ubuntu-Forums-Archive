---
title: "Problem at lupin 1"
date: 2007-04-11
forum: General Help
---

### Post by Bobberb on 2007-04-11
Ok so I let the thing sit and boot, but it couldn't find the necessary items needed to boot or something, I will get the log

---

### Post by Bobberb on 2007-04-11
here:


+ PREREQ=
+ . /scripts/lupin-functions
+ . /scripts/functions
+ ERR_MNT_ROOT=1
+ ERR_NO_INIT=2
+ ERR_RUN_INIT=3
+ ERR_MNT_HOST=4
+ ERR_NO_HOST=5
+ ERR_LOOP_ROOT=6
+ ERR_LOOP_HOME=7
+ ERR_LOOP_SWAP=8
+ ERR_LOOP_EXTRA=9
+ ERR_MNT_ISO=10
+ ERR_NO_ISO=11
+ ERR_INVALID_ISO=12
+ ERR_LOOP_ISO=13
+ ERR_NO_PRESEED=14
+ ERR_FAIL=15
+ ERR_MNT=16
+ ERR_LIVE_ISO=17
+ ERR_ALTERNATE_ISO=18
+ ERR_NO_FILESYSTEM=19
+ ERR_WRONG_FILESYSTEM=20
+ . /conf/param.conf
+ ROOT=/dev/loop7
+ ROOTFSTYPE=ext3
+ ROOTDEV=/dev/loop7
+ ISOMNT=/cdrom
+ ROOTMNT=/root
+ HOSTFOLDER=/host/wubi
+ SUITE=
+ SETUPISO=
+ HOSTMNT=/host
+ ROOTDEV=/dev/loop7
+ HOMEDEV=/dev/loop6
+ SWAPDEV=/dev/loop5
+ EXTRADEV=/dev/loop4
+ PAUSEFORDEBUG=n
+ pause_for_debug
+ cd /
+ cp_logs
+ [ -e /logs ]
+ mkdir /logs
+ cp /tmp/lupin.log /tmp/zenigata.log /logs/
+ [ -e /host/wubi ]
+ [ -e /host/wubi/logs ]
+ mkdir /host/wubi/logs
+ cp /tmp/lupin.log /tmp/zenigata.log /host/wubi/logs
+ [ n = y ]
+ return 0
+ grep -q /dev/loop7 /proc/mounts
+ check_fs /dev/loop7
+ dev=/dev/loop7
+ get_fs /dev/loop7
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ get_iso
+ [ -n  ]
+ log_warning_msg No Setup-ISO specified, looking for one
+ _log_msg Warning: No Setup-ISO specified, looking for one
+ echo Warning: No Setup-ISO specified, looking for one
Warning: No Setup-ISO specified, looking for one
+ [ -f /host/wubi/install/* ]
+ continue
+ [ -f /host/wubi/install/*/* ]
+ continue
+ [ -f /host/wubi/Uninstall.exe ]
+ [ -f /host/wubi/WUBI-README.txt ]
+ [ -f /host/wubi/boot ]
+ continue
+ [ -f /host/wubi/config.ini ]
+ [ -f /host/wubi/disks ]
+ continue
+ [ -f /host/wubi/docs ]
+ continue
+ [ -f /host/wubi/initrd.gz ]
+ [ -f /host/wubi/install ]
+ continue
+ [ -f /host/wubi/license.txt ]
+ [ -f /host/wubi/linux ]
+ [ -f /host/wubi/logs ]
+ continue
+ [ -f /host/wubi/tools ]
+ continue
+ [ -f /host/wubi/wubi.ini ]
+ [ -f /host/wubi/boot/menu.lst ]
+ [ -f /host/wubi/boot/wingrub ]
+ continue
+ [ -f /host/wubi/disks/home.img ]
+ [ -f /host/wubi/disks/root.img ]
+ [ -f /host/wubi/disks/swap.img ]
+ [ -f /host/wubi/logs/lupin.log ]
+ [ -f /host/wubi/logs/zenigata.log ]
+ [ -f /host/AUTOEXEC.BAT ]
+ [ -f /host/CD Images ]
[: Images: unknown operand
+ continue
+ [ -f /host/CONFIG.SYS ]
+ [ -f /host/Documents and Settings ]
[: and: unknown operand
+ continue
+ [ -f /host/IO.SYS ]
+ [ -f /host/IPH.PH ]
+ [ -f /host/MSDOS.SYS ]
+ [ -f /host/MSOCache ]
+ continue
+ [ -f /host/NTDETECT.COM ]
+ [ -f /host/Program Files ]
[: Files: unknown operand
+ continue
+ [ -f /host/RECYCLER ]
+ continue
+ [ -f /host/RHDSetup.log ]
+ [ -f /host/Sega ]
+ continue
+ [ -f /host/System Volume Information ]
[: Volume: unknown operand
+ continue
+ [ -f /host/WINDOWS ]
+ continue
+ [ -f /host/boot.ini ]
+ [ -f /host/games ]
+ continue
+ [ -f /host/grldr ]
+ [ -f /host/hiberfil.sys ]
+ [ -f /host/menu.lst ]
+ [ -f /host/ntldr ]
+ [ -f /host/pagefile.sys ]
+ [ -f /host/temp ]
+ continue
+ [ -f /host/utorrent.exe ]
+ [ -f /host/wubi ]
+ continue
+ [ -f /host/CD Images/Sega Smash Pach II.ccd ]
[: Images/Sega: unknown operand
+ continue
+ [ -f /host/CD Images/Sega Smash Pach II.cue ]
[: Images/Sega: unknown operand
+ continue
+ [ -f /host/CD Images/Sega Smash Pach II.img ]
[: Images/Sega: unknown operand
+ continue
+ [ -f /host/CD Images/Sega Smash Pach II.sub ]
[: Images/Sega: unknown operand
+ continue
+ [ -f /host/CD Images/WarCraftIII Reign of Chaos.ccd ]
[: Images/WarCraftIII: unknown operand
+ continue
+ [ -f /host/CD Images/WarCraftIII Reign of Chaos.cue ]
[: Images/WarCraftIII: unknown operand
+ continue
+ [ -f /host/CD Images/WarCraftIII Reign of Chaos.img ]
[: Images/WarCraftIII: unknown operand
+ continue
+ [ -f /host/CD Images/WarCraftIII Reign of Chaos.sub ]
[: Images/WarCraftIII: unknown operand
+ continue
+ [ -f /host/Documents and Settings/All Users ]
[: and: unknown operand
+ continue
+ [ -f /host/Documents and Settings/Default User ]
[: and: unknown operand
+ continue
+ [ -f /host/Documents and Settings/Joshizzle ]
[: and: unknown operand
+ continue
+ [ -f /host/Documents and Settings/LocalService ]
[: and: unknown operand
+ continue
+ [ -f /host/Documents and Settings/NetworkService ]
[: and: unknown operand
+ continue
+ [ -f /host/MSOCache/All Users ]
[: Users: unknown operand
+ continue
+ [ -f /host/Program Files/7-Zip ]
[: Files/7-Zip: unknown operand
+ continue
+ [ -f /host/Program Files/AIM6 ]
[: Files/AIM6: unknown operand
+ continue
+ [ -f /host/Program Files/Alcohol Soft ]
[: Files/Alcohol: unknown operand
+ continue
+ [ -f /host/Program Files/Apple Keyboard Support ]
[: Files/Apple: unknown operand
+ continue
+ [ -f /host/Program Files/Apple Software Update ]
[: Files/Apple: unknown operand
+ continue
+ [ -f /host/Program Files/ComPlus Applications ]
[: Files/ComPlus: unknown operand
+ continue
+ [ -f /host/Program Files/Common Files ]
[: Files/Common: unknown operand
+ continue
+ [ -f /host/Program Files/DIFX ]
[: Files/DIFX: unknown operand
+ continue
+ [ -f /host/Program Files/ESTsoft ]
[: Files/ESTsoft: unknown operand
+ continue
+ [ -f /host/Program Files/Elaborate Bytes ]
[: Files/Elaborate: unknown operand
+ continue
+ [ -f /host/Program Files/Eraser ]
[: Files/Eraser: unknown operand
+ continue
+ [ -f /host/Program Files/Foxit Software ]
[: Files/Foxit: unknown operand
+ continue
+ [ -f /host/Program Files/Gaim ]
[: Files/Gaim: unknown operand
+ continue
+ [ -f /host/Program Files/Google ]
[: Files/Google: unknown operand
+ continue
+ [ -f /host/Program Files/HIP ]
[: Files/HIP: unknown operand
+ continue
+ [ -f /host/Program Files/Handbrake ]
[: Files/Handbrake: unknown operand
+ continue
+ [ -f /host/Program Files/Illustrate ]
[: Files/Illustrate: unknown operand
+ continue
+ [ -f /host/Program Files/Infinite Interactive ]
[: Files/Infinite: unknown operand
+ continue
+ [ -f /host/Program Files/Infogrames ]
[: Files/Infogrames: unknown operand
+ continue
+ [ -f /host/Program Files/InstallShield Installation Information ]
[: Files/InstallShield: unknown operand
+ continue
+ [ -f /host/Program Files/Intel ]
[: Files/Intel: unknown operand
+ continue
+ [ -f /host/Program Files/Internet Explorer ]
[: Files/Internet: unknown operand
+ continue
+ [ -f /host/Program Files/Ipod Video Converter ]
[: Files/Ipod: unknown operand
+ continue
+ [ -f /host/Program Files/Java ]
[: Files/Java: unknown operand
+ continue
+ [ -f /host/Program Files/K-Lite Codec Pack ]
[: Files/K-Lite: unknown operand
+ continue
+ [ -f /host/Program Files/Launchy ]
[: Files/Launchy: unknown operand
+ continue
+ [ -f /host/Program Files/Lugaru ]
[: Files/Lugaru: unknown operand
+ continue
+ [ -f /host/Program Files/MSN ]
[: Files/MSN: unknown operand
+ continue
+ [ -f /host/Program Files/MSN Gaming Zone ]
[: Files/MSN: unknown operand
+ continue
+ [ -f /host/Program Files/MediaMonkey ]
[: Files/MediaMonkey: unknown operand
+ continue
+ [ -f /host/Program Files/Messenger ]
[: Files/Messenger: unknown operand
+ continue
+ [ -f /host/Program Files/Microsoft Office ]
[: Files/Microsoft: unknown operand
+ continue
+ [ -f /host/Program Files/Microsoft Visual Studio ]
[: Files/Microsoft: unknown operand
+ continue
+ [ -f /host/Program Files/Microsoft Works ]
[: Files/Microsoft: unknown operand
+ continue
+ [ -f /host/Program Files/Motorola ]
[: Files/Motorola: unknown operand
+ continue
+ [ -f /host/Program Files/Movie Maker ]
[: Files/Movie: unknown operand
+ continue
+ [ -f /host/Program Files/Mozilla Firefox ]
[: Files/Mozilla: unknown operand
+ continue
+ [ -f /host/Program Files/NetMeeting ]
[: Files/NetMeeting: unknown operand
+ continue
+ [ -f /host/Program Files/Notepad++ ]
[: Files/Notepad++: unknown operand
+ continue
+ [ -f /host/Program Files/Online Services ]
[: Files/Online: unknown operand
+ continue
+ [ -f /host/Program Files/OpenAL ]
[: Files/OpenAL: unknown operand
+ continue
+ [ -f /host/Program Files/Outlook Express ]
[: Files/Outlook: unknown operand
+ continue
+ [ -f /host/Program Files/Paint.NET ]
[: Files/Paint.NET: unknown operand
+ continue
+ [ -f /host/Program Files/Power Defragmenter ]
[: Files/Power: unknown operand
+ continue
+ [ -f /host/Program Files/QuickTime ]
[: Files/QuickTime: unknown operand
+ continue
+ [ -f /host/Program Files/Realtek ]
[: Files/Realtek: unknown operand
+ continue
+ [ -f /host/Program Files/SigmaTel ]
[: Files/SigmaTel: unknown operand
+ continue
+ [ -f /host/Program Files/SlySoft ]
[: Files/SlySoft: unknown operand
+ continue
+ [ -f /host/Program Files/TrueCrypt ]
[: Files/TrueCrypt: unknown operand
+ continue
+ [ -f /host/Program Files/TryMedia ]
[: Files/TryMedia: unknown operand
+ continue
+ [ -f /host/Program Files/Uninstall Information ]
[: Files/Uninstall: unknown operand
+ continue
+ [ -f /host/Program Files/VideoLAN ]
[: Files/VideoLAN: unknown operand
+ continue
+ [ -f /host/Program Files/Viewpoint ]
[: Files/Viewpoint: unknown operand
+ continue
+ [ -f /host/Program Files/WC3Banlist ]
[: Files/WC3Banlist: unknown operand
+ continue
+ [ -f /host/Program Files/Warcraft III ]
[: Files/Warcraft: unknown operand
+ continue
+ [ -f /host/Program Files/WinPcap ]
[: Files/WinPcap: unknown operand
+ continue
+ [ -f /host/Program Files/WinZip ]
[: Files/WinZip: unknown operand
+ continue
+ [ -f /host/Program Files/Windows Media Player ]
[: Files/Windows: unknown operand
+ continue
+ [ -f /host/Program Files/Windows NT ]
[: Files/Windows: unknown operand
+ continue
+ [ -f /host/Program Files/WindowsUpdate ]
[: Files/WindowsUpdate: unknown operand
+ continue
+ [ -f /host/Program Files/ffdshow ]
[: Files/ffdshow: unknown operand
+ continue
+ [ -f /host/Program Files/iPod ]
[: Files/iPod: unknown operand
+ continue
+ [ -f /host/Program Files/iTunes ]
[: Files/iTunes: unknown operand
+ continue
+ [ -f /host/Program Files/microsoft frontpage ]
[: Files/microsoft: unknown operand
+ continue
+ [ -f /host/Program Files/xerox ]
[: Files/xerox: unknown operand
+ continue
+ [ -f /host/RECYCLER/S-1-5-21-776561741-492894223-839522115-1003 ]
+ continue
+ [ -f /host/Sega/Smash Pack II ]
[: Pack: unknown operand
+ continue
+ [ -f /host/System Volume Information/MountPointManagerRemoteDatabase ]
[: Volume: unknown operand
+ continue
+ [ -f /host/System Volume Information/_restore{CF32CD6A-C0A5-4B4C-9DB4-54AA62DF4075} ]
[: Volume: unknown operand
+ continue
+ [ -f /host/System Volume Information/catalog.wci ]
[: Volume: unknown operand
+ continue
+ [ -f /host/System Volume Information/tracking.log ]
[: Volume: unknown operand
+ continue
+ [ -f /host/WINDOWS/$MSI31Uninstall_KB893803v2$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB873339$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB885835$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB885836$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB886185$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB887472$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB888111WXPSP2$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB888302$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB890859$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB891781$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB893756$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB894391$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB896358$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB896423$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB896424$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB896428$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB898461$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB899587$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB899591$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB900485$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB900725$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB901017$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB901214$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB902400$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB904706$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB905414$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB905749$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB908519$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB908531$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB910437$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB911280$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB911562$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB911564$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB911927$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB912919$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB913580$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB914388$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB914389$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB916595$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB917344$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB917422$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB917734_WMP9$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB917953$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB918118$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB918439$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB919007$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB920213$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB920670$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB920683$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB920685$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB920872$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB922582$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB922819$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB923191$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB923414$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB923689$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB923694$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB923980$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB924191$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB924270$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB924496$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB924667$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB925398_WMP64$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB925902$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB926255$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB926436$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB927779$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB927802$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB928090$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB928255$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB928843$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB929338$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB929969$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB931836$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallWdf01001$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallWdf01005$ ]
+ continue
+ [ -f /host/WINDOWS/$hf_mig$ ]
+ continue
+ [ -f /host/WINDOWS/0.log ]
+ [ -f /host/WINDOWS/AppPatch ]
+ continue
+ [ -f /host/WINDOWS/Blue Lace 16.bmp ]
[: Lace: unknown operand
+ continue
+ [ -f /host/WINDOWS/CIV.INI ]
+ [ -f /host/WINDOWS/Coffee Bean.bmp ]
[: Bean.bmp: unknown operand
+ continue
+ [ -f /host/WINDOWS/Config ]
+ continue
+ [ -f /host/WINDOWS/Connection Wizard ]
[: Wizard: unknown operand
+ continue
+ [ -f /host/WINDOWS/Cursors ]
+ continue
+ [ -f /host/WINDOWS/DPINST.LOG ]
+ [ -f /host/WINDOWS/Debug ]
+ continue
+ [ -f /host/WINDOWS/Downloaded Program Files ]
[: Program: unknown operand
+ continue
+ [ -f /host/WINDOWS/Driver Cache ]
[: Cache: unknown operand
+ continue
+ [ -f /host/WINDOWS/DtcInstall.log ]
+ [ -f /host/WINDOWS/FaxSetup.log ]
+ [ -f /host/WINDOWS/FeatherTexture.bmp ]
+ [ -f /host/WINDOWS/Fonts ]
+ continue
+ [ -f /host/WINDOWS/Gone Fishing.bmp ]
[: Fishing.bmp: unknown operand
+ continue
+ [ -f /host/WINDOWS/Greenstone.bmp ]
+ [ -f /host/WINDOWS/Help ]
+ continue
+ [ -f /host/WINDOWS/Installer ]
+ continue
+ [ -f /host/WINDOWS/IsUninst.exe ]
+ [ -f /host/WINDOWS/KB873339.log ]
+ [ -f /host/WINDOWS/KB885835.log ]
+ [ -f /host/WINDOWS/KB885836.log ]
+ [ -f /host/WINDOWS/KB886185.log ]
+ [ -f /host/WINDOWS/KB887472.log ]
+ [ -f /host/WINDOWS/KB888111.log ]
+ [ -f /host/WINDOWS/KB888302.log ]
+ [ -f /host/WINDOWS/KB890859.log ]
+ [ -f /host/WINDOWS/KB891781.log ]
+ [ -f /host/WINDOWS/KB893756.log ]
+ [ -f /host/WINDOWS/KB893803v2.log ]
+ [ -f /host/WINDOWS/KB894391.log ]
+ [ -f /host/WINDOWS/KB896358.log ]
+ [ -f /host/WINDOWS/KB896423.log ]
+ [ -f /host/WINDOWS/KB896424.log ]
+ [ -f /host/WINDOWS/KB896428.log ]
+ [ -f /host/WINDOWS/KB898461.log ]
+ [ -f /host/WINDOWS/KB899587.log ]
+ [ -f /host/WINDOWS/KB899591.log ]
+ [ -f /host/WINDOWS/KB900485.log ]
+ [ -f /host/WINDOWS/KB900725.log ]
+ [ -f /host/WINDOWS/KB901017.log ]
+ [ -f /host/WINDOWS/KB901214.log ]
+ [ -f /host/WINDOWS/KB902400.log ]
+ [ -f /host/WINDOWS/KB904706.log ]
+ [ -f /host/WINDOWS/KB905414.log ]
+ [ -f /host/WINDOWS/KB905749.log ]
+ [ -f /host/WINDOWS/KB908519.log ]
+ [ -f /host/WINDOWS/KB908531.log ]
+ [ -f /host/WINDOWS/KB910437.log ]
+ [ -f /host/WINDOWS/KB911280.log ]
+ [ -f /host/WINDOWS/KB911562.log ]
+ [ -f /host/WINDOWS/KB911564.log ]
+ [ -f /host/WINDOWS/KB911927.log ]
+ [ -f /host/WINDOWS/KB912919.log ]
+ [ -f /host/WINDOWS/KB913580.log ]
+ [ -f /host/WINDOWS/KB914388.log ]
+ [ -f /host/WINDOWS/KB914389.log ]
+ [ -f /host/WINDOWS/KB916595.log ]
+ [ -f /host/WINDOWS/KB917344.log ]
+ [ -f /host/WINDOWS/KB917422.log ]
+ [ -f /host/WINDOWS/KB917734.log ]
+ [ -f /host/WINDOWS/KB917953.log ]
+ [ -f /host/WINDOWS/KB918118.log ]
+ [ -f /host/WINDOWS/KB918439.log ]
+ [ -f /host/WINDOWS/KB919007.log ]
+ [ -f /host/WINDOWS/KB920213.log ]
+ [ -f /host/WINDOWS/KB920670.log ]
+ [ -f /host/WINDOWS/KB920683.log ]
+ [ -f /host/WINDOWS/KB920685.log ]
+ [ -f /host/WINDOWS/KB920872.log ]
+ [ -f /host/WINDOWS/KB922582.log ]
+ [ -f /host/WINDOWS/KB922819.log ]
+ [ -f /host/WINDOWS/KB923191.log ]
+ [ -f /host/WINDOWS/KB923414.log ]
+ [ -f /host/WINDOWS/KB923689.log ]
+ [ -f /host/WINDOWS/KB923694.log ]
+ [ -f /host/WINDOWS/KB923980.log ]
+ [ -f /host/WINDOWS/KB924191.log ]
+ [ -f /host/WINDOWS/KB924270.log ]
+ [ -f /host/WINDOWS/KB924496.log ]
+ [ -f /host/WINDOWS/KB924667.log ]
+ [ -f /host/WINDOWS/KB925398.log ]
+ [ -f /host/WINDOWS/KB925902.log ]
+ [ -f /host/WINDOWS/KB926255.log ]
+ [ -f /host/WINDOWS/KB926436.log ]
+ [ -f /host/WINDOWS/KB927779.log ]
+ [ -f /host/WINDOWS/KB927802.log ]
+ [ -f /host/WINDOWS/KB928090.log ]
+ [ -f /host/WINDOWS/KB928255.log ]
+ [ -f /host/WINDOWS/KB928843.log ]
+ [ -f /host/WINDOWS/KB929338.log ]
+ [ -f /host/WINDOWS/KB929969.log ]
+ [ -f /host/WINDOWS/KB931836.log ]
+ [ -f /host/WINDOWS/MedCtrOC.log ]
+ [ -f /host/WINDOWS/Media ]
+ continue
+ [ -f /host/WINDOWS/MicCal.exe ]
+ [ -f /host/WINDOWS/Microsoft.NET ]
+ continue
+ [ -f /host/WINDOWS/Minidump ]
+ continue
+ [ -f /host/WINDOWS/NOTEPAD.EXE ]
+ [ -f /host/WINDOWS/ODBC.INI ]
+ [ -f /host/WINDOWS/ODBCINST.INI ]
+ [ -f /host/WINDOWS/OEWABLog.txt ]
+ [ -f /host/WINDOWS/Offline Web Pages ]
[: Web: unknown operand
+ continue
+ [ -f /host/WINDOWS/PeerNet ]
+ continue
+ [ -f /host/WINDOWS/Prairie Wind.bmp ]
[: Wind.bmp: unknown operand
+ continue
+ [ -f /host/WINDOWS/Prefetch ]
+ continue
+ [ -f /host/WINDOWS/Provisioning ]
+ continue
+ [ -f /host/WINDOWS/REGLOCS.OLD ]
+ [ -f /host/WINDOWS/RTHDCPL.exe ]
+ [ -f /host/WINDOWS/Registration ]
+ continue
+ [ -f /host/WINDOWS/Resources ]
+ continue
+ [ -f /host/WINDOWS/Rhododendron.bmp ]
+ [ -f /host/WINDOWS/River Sumida.bmp ]
[: Sumida.bmp: unknown operand
+ continue
+ [ -f /host/WINDOWS/RtlExUpd.dll ]
+ [ -f /host/WINDOWS/RtlUpd.exe ]
+ [ -f /host/WINDOWS/SET3.tmp ]
+ [ -f /host/WINDOWS/SET4.tmp ]
+ [ -f /host/WINDOWS/SET8.tmp ]
+ [ -f /host/WINDOWS/SHELLNEW ]
+ continue
+ [ -f /host/WINDOWS/Santa Fe Stucco.bmp ]
[: Fe: unknown operand
+ continue
+ [ -f /host/WINDOWS/SchedLgU.Txt ]
+ [ -f /host/WINDOWS/Soap Bubbles.bmp ]
[: Bubbles.bmp: unknown operand
+ continue
+ [ -f /host/WINDOWS/SoftwareDistribution ]
+ continue
+ [ -f /host/WINDOWS/Sti_Trace.log ]
+ [ -f /host/WINDOWS/Sun ]
+ continue
+ [ -f /host/WINDOWS/SxsCaPendDel ]
+ continue
+ [ -f /host/WINDOWS/TASKMAN.EXE ]
+ [ -f /host/WINDOWS/Tasks ]
+ continue
+ [ -f /host/WINDOWS/Temp ]
+ continue
+ [ -f /host/WINDOWS/Thumbs.db ]
+ [ -f /host/WINDOWS/WGA.log ]
+ [ -f /host/WINDOWS/WMSysPr9.prx ]
+ [ -f /host/WINDOWS/War3Unin.dat ]
+ [ -f /host/WINDOWS/War3Unin.exe ]
+ [ -f /host/WINDOWS/War3Unin.pif ]
+ [ -f /host/WINDOWS/Wdf01001Inst.log ]
+ [ -f /host/WINDOWS/Wdf01005Inst.log ]
+ [ -f /host/WINDOWS/Web ]
+ continue
+ [ -f /host/WINDOWS/WgaNotify.log ]
+ [ -f /host/WINDOWS/WinSxS ]
+ continue
+ [ -f /host/WINDOWS/WindowsShell.Manifest ]
+ [ -f /host/WINDOWS/WindowsUpdate.log ]
+ [ -f /host/WINDOWS/Zapotec.bmp ]
+ [ -f /host/WINDOWS/_default.pif ]
+ [ -f /host/WINDOWS/addins ]
+ continue
+ [ -f /host/WINDOWS/assembly ]
+ continue
+ [ -f /host/WINDOWS/atid.ini ]
+ [ -f /host/WINDOWS/bootstat.dat ]
+ [ -f /host/WINDOWS/clock.avi ]
+ [ -f /host/WINDOWS/cmsetacl.log ]
+ [ -f /host/WINDOWS/comsetup.log ]
+ [ -f /host/WINDOWS/control.ini ]
+ [ -f /host/WINDOWS/desktop.ini ]
+ [ -f /host/WINDOWS/ehome ]
+ continue
+ [ -f /host/WINDOWS/explorer.exe ]
+ [ -f /host/WINDOWS/explorer.scf ]
+ [ -f /host/WINDOWS/hh.exe ]
+ [ -f /host/WINDOWS/iis6.log ]
+ [ -f /host/WINDOWS/ime ]
+ continue
+ [ -f /host/WINDOWS/imsins.BAK ]
+ [ -f /host/WINDOWS/imsins.log ]
+ [ -f /host/WINDOWS/inf ]
+ continue
+ [ -f /host/WINDOWS/java ]
+ continue
+ [ -f /host/WINDOWS/mozver.dat ]
+ [ -f /host/WINDOWS/msagent ]
+ continue
+ [ -f /host/WINDOWS/msapps ]
+ continue
+ [ -f /host/WINDOWS/msdfmap.ini ]
+ [ -f /host/WINDOWS/msgsocm.log ]
+ [ -f /host/WINDOWS/msmqinst.log ]
+ [ -f /host/WINDOWS/mui ]
+ continue
+ [ -f /host/WINDOWS/netfxocm.log ]
+ [ -f /host/WINDOWS/nsreg.dat ]
+ [ -f /host/WINDOWS/ntdtcsetup.log ]
+ [ -f /host/WINDOWS/ocgen.log ]
+ [ -f /host/WINDOWS/ocmsn.log ]
+ [ -f /host/WINDOWS/pchealth ]
+ continue
+ [ -f /host/WINDOWS/regedit.exe ]
+ [ -f /host/WINDOWS/regopt.log ]
+ [ -f /host/WINDOWS/repair ]
+ continue
+ [ -f /host/WINDOWS/security ]
+ continue
+ [ -f /host/WINDOWS/sessmgr.setup.log ]
+ [ -f /host/WINDOWS/setupact.log ]
+ [ -f /host/WINDOWS/setupapi.log ]
+ [ -f /host/WINDOWS/setuperr.log ]
+ [ -f /host/WINDOWS/setuplog.txt ]
+ [ -f /host/WINDOWS/spupdsvc.log ]
+ [ -f /host/WINDOWS/srchasst ]
+ continue
+ [ -f /host/WINDOWS/system ]
+ continue
+ [ -f /host/WINDOWS/system.ini ]
+ [ -f /host/WINDOWS/system32 ]
+ continue
+ [ -f /host/WINDOWS/tabletoc.log ]
+ [ -f /host/WINDOWS/tsoc.log ]
+ [ -f /host/WINDOWS/twain.dll ]
+ [ -f /host/WINDOWS/twain_32 ]
+ continue
+ [ -f /host/WINDOWS/twain_32.dll ]
+ [ -f /host/WINDOWS/twunk_16.exe ]
+ [ -f /host/WINDOWS/twunk_32.exe ]
+ [ -f /host/WINDOWS/updspapi.log ]
+ [ -f /host/WINDOWS/vb.ini ]
+ [ -f /host/WINDOWS/vbaddin.ini ]
+ [ -f /host/WINDOWS/vmmreg32.dll ]
+ [ -f /host/WINDOWS/wiadebug.log ]
+ [ -f /host/WINDOWS/wiaservc.log ]
+ [ -f /host/WINDOWS/win.ini ]
+ [ -f /host/WINDOWS/winhelp.exe ]
+ [ -f /host/WINDOWS/winhlp32.exe ]
+ [ -f /host/WINDOWS/winnt.bmp ]
+ [ -f /host/WINDOWS/winnt256.bmp ]
+ [ -f /host/WINDOWS/wmsetup.log ]
+ [ -f /host/wubi/Uninstall.exe ]
+ [ -f /host/wubi/WUBI-README.txt ]
+ [ -f /host/wubi/boot ]
+ continue
+ [ -f /host/wubi/config.ini ]
+ [ -f /host/wubi/disks ]
+ continue
+ [ -f /host/wubi/docs ]
+ continue
+ [ -f /host/wubi/initrd.gz ]
+ [ -f /host/wubi/install ]
+ continue
+ [ -f /host/wubi/license.txt ]
+ [ -f /host/wubi/linux ]
+ [ -f /host/wubi/logs ]
+ continue
+ [ -f /host/wubi/tools ]
+ continue
+ [ -f /host/wubi/wubi.ini ]
+ log_warning_msg Could not find any ISO
+ _log_msg Warning: Could not find any ISO
+ echo Warning: Could not find any ISO
Warning: Could not find any ISO
+ return 11
+ fail 
Could not find any file needed to boot...
The bootlader is probably pointing to the wrong file/folder
Please check that the 'find' kernel parameter in menu.lst
points to the correct location
+ quit_usplash
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write PROGRESS 100
+ /sbin/usplash_write SUCCESS ok
+ /sbin/usplash_write QUIT
+ log_failure_msg 
Could not find any file needed to boot...
The bootlader is probably pointing to the wrong file/folder
Please check that the 'find' kernel parameter in menu.lst
points to the correct location
+ _log_msg Failure: 
Could not find any file needed to boot...
The bootlader is probably pointing to the wrong file/folder
Please check that the 'find' kernel parameter in menu.lst
points to the correct location
+ echo Failure: 
Could not find any file needed to boot...
The bootlader is probably pointing to the wrong file/folder
Please check that the 'find' kernel parameter in menu.lst
points to the correct location
Failure: 
Could not find any file needed to boot...
The bootlader is probably pointing to the wrong file/folder
Please check that the 'find' kernel parameter in menu.lst
points to the correct location
+ echo -------------------------------------------
+ echo ERROR:
+ echo
+ echo 
Could not find any file needed to boot...
The bootlader is probably pointing to the wrong file/folder
Please check that the 'find' kernel parameter in menu.lst
points to the correct location
+ echo -------------------------------------------
+ cp_logs
+ [ -e /logs ]
+ cp /tmp/lupin.log /tmp/zenigata.log /logs/
+ [ -e /host/wubi ]
+ [ -e /host/wubi/logs ]
+ cp /tmp/lupin.log /tmp/zenigata.log /host/wubi/logs

---

### Post by ago on 2007-04-11
You are trying to install but there is no ISO in c:\wubi\install. There should be a 700MB iso file

---

### Post by Bobberb on 2007-04-11
no...did not work, I think the log file is even the same:
+ PREREQ=
+ . /scripts/lupin-functions
+ . /scripts/functions
+ ERR_MNT_ROOT=1
+ ERR_NO_INIT=2
+ ERR_RUN_INIT=3
+ ERR_MNT_HOST=4
+ ERR_NO_HOST=5
+ ERR_LOOP_ROOT=6
+ ERR_LOOP_HOME=7
+ ERR_LOOP_SWAP=8
+ ERR_LOOP_EXTRA=9
+ ERR_MNT_ISO=10
+ ERR_NO_ISO=11
+ ERR_INVALID_ISO=12
+ ERR_LOOP_ISO=13
+ ERR_NO_PRESEED=14
+ ERR_FAIL=15
+ ERR_MNT=16
+ ERR_LIVE_ISO=17
+ ERR_ALTERNATE_ISO=18
+ ERR_NO_FILESYSTEM=19
+ ERR_WRONG_FILESYSTEM=20
+ . /conf/param.conf
+ ROOT=/dev/loop7
+ ROOTFSTYPE=ext3
+ ROOTDEV=/dev/loop7
+ ISOMNT=/cdrom
+ ROOTMNT=/root
+ HOSTFOLDER=/host/wubi
+ SUITE=
+ SETUPISO=
+ HOSTMNT=/host
+ ROOTDEV=/dev/loop7
+ HOMEDEV=/dev/loop6
+ SWAPDEV=/dev/loop5
+ EXTRADEV=/dev/loop4
+ PAUSEFORDEBUG=n
+ pause_for_debug
+ cd /
+ cp_logs
+ [ -e /logs ]
+ mkdir /logs
+ cp /tmp/lupin.log /tmp/zenigata.log /logs/
+ [ -e /host/wubi ]
+ [ -e /host/wubi/logs ]
+ cp /tmp/lupin.log /tmp/zenigata.log /host/wubi/logs
+ [ n = y ]
+ return 0
+ grep -q /dev/loop7 /proc/mounts
+ check_fs /dev/loop7
+ dev=/dev/loop7
+ get_fs /dev/loop7
+ [ -n  ]
+ [ unknown = unknown ]
+ return 19
+ get_iso
+ [ -n  ]
+ log_warning_msg No Setup-ISO specified, looking for one
+ _log_msg Warning: No Setup-ISO specified, looking for one
+ echo Warning: No Setup-ISO specified, looking for one
Warning: No Setup-ISO specified, looking for one
+ [ -f /host/wubi/install/ubuntu-7.04-beta-alternate-i386.iso ]
+ is_setup_iso /host/wubi/install/ubuntu-7.04-beta-alternate-i386.iso
+ isodev=/host/wubi/install/ubuntu-7.04-beta-alternate-i386.iso
+ safe_mount /host/wubi/install/ubuntu-7.04-beta-alternate-i386.iso /cdrom
+ dev=/host/wubi/install/ubuntu-7.04-beta-alternate-i386.iso
+ mntpoint=/cdrom
+ options=
+ [ -n  ]
+ check_mountpoint /cdrom
+ mntpoint=/cdrom
+ [ -d /cdrom ]
+ mkdir -p /cdrom
+ umount /cdrom
+ get_fs /host/wubi/install/ubuntu-7.04-beta-alternate-i386.iso
+ dev=/host/wubi/install/ubuntu-7.04-beta-alternate-i386.iso
+ FSTYPE=
+ FSSIZE=
+ [ ! -b /host/wubi/install/ubuntu-7.04-beta-alternate-i386.iso ]
+ [ ! -f /host/wubi/install/ubuntu-7.04-beta-alternate-i386.iso ]
+ fstype
+ eval FSTYPE=iso9660 FSSIZE=0
+ FSTYPE=iso9660 FSSIZE=0
+ [ -z iso9660 ]
+ [ iso9660 = unknown ]
+ [ -z iso9660 ]
+ [ iso9660 = unknown ]
+ [ -z iso9660 ]
+ mount -t iso9660 /host/wubi/install/ubuntu-7.04-beta-alternate-i386.iso /cdrom
+ [ -e /cdrom/.disk/info ]
+ uname -r
+ [ -e /cdrom/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-12-generic_2.6.20-12.20_i386.deb ]
+ get_allowed_suites
+ [ ! -n  ]
+ [ -f /host/wubi/install/preseed.cfg ]
+ [ -n  ]
+ SUITE=
+ umount /cdrom
+ return 12
+ [ -f /host/wubi/install/*/* ]
+ continue
+ [ -f /host/wubi/Uninstall.exe ]
+ [ -f /host/wubi/WUBI-README.txt ]
+ [ -f /host/wubi/boot ]
+ continue
+ [ -f /host/wubi/config.ini ]
+ [ -f /host/wubi/disks ]
+ continue
+ [ -f /host/wubi/docs ]
+ continue
+ [ -f /host/wubi/initrd.gz ]
+ [ -f /host/wubi/install ]
+ continue
+ [ -f /host/wubi/license.txt ]
+ [ -f /host/wubi/linux ]
+ [ -f /host/wubi/logs ]
+ continue
+ [ -f /host/wubi/tools ]
+ continue
+ [ -f /host/wubi/wubi-7.04-beta-v3.exe ]
+ [ -f /host/wubi/wubi.ini ]
+ [ -f /host/wubi/boot/menu.lst ]
+ [ -f /host/wubi/boot/wingrub ]
+ continue
+ [ -f /host/wubi/disks/home.img ]
+ [ -f /host/wubi/disks/root.img ]
+ [ -f /host/wubi/disks/swap.img ]
+ [ -f /host/wubi/install/ubuntu-7.04-beta-alternate-i386.iso ]
+ is_setup_iso /host/wubi/install/ubuntu-7.04-beta-alternate-i386.iso
+ isodev=/host/wubi/install/ubuntu-7.04-beta-alternate-i386.iso
+ safe_mount /host/wubi/install/ubuntu-7.04-beta-alternate-i386.iso /cdrom
+ dev=/host/wubi/install/ubuntu-7.04-beta-alternate-i386.iso
+ mntpoint=/cdrom
+ options=
+ [ -n  ]
+ check_mountpoint /cdrom
+ mntpoint=/cdrom
+ [ -d /cdrom ]
+ umount /cdrom
+ get_fs /host/wubi/install/ubuntu-7.04-beta-alternate-i386.iso
+ dev=/host/wubi/install/ubuntu-7.04-beta-alternate-i386.iso
+ FSTYPE=
+ FSSIZE=
+ [ ! -b /host/wubi/install/ubuntu-7.04-beta-alternate-i386.iso ]
+ [ ! -f /host/wubi/install/ubuntu-7.04-beta-alternate-i386.iso ]
+ fstype
+ eval FSTYPE=iso9660 FSSIZE=0
+ FSTYPE=iso9660 FSSIZE=0
+ [ -z iso9660 ]
+ [ iso9660 = unknown ]
+ [ -z iso9660 ]
+ [ iso9660 = unknown ]
+ [ -z iso9660 ]
+ mount -t iso9660 /host/wubi/install/ubuntu-7.04-beta-alternate-i386.iso /cdrom
+ [ -e /cdrom/.disk/info ]
+ uname -r
+ [ -e /cdrom/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-12-generic_2.6.20-12.20_i386.deb ]
+ get_allowed_suites
+ [ ! -n  ]
+ [ -f /host/wubi/install/preseed.cfg ]
+ [ -n  ]
+ SUITE=
+ umount /cdrom
+ return 12
+ [ -f /host/wubi/logs/lupin.log ]
+ [ -f /host/wubi/logs/zenigata.log ]
+ [ -f /host/AUTOEXEC.BAT ]
+ [ -f /host/CD Images ]
[: Images: unknown operand
+ continue
+ [ -f /host/CONFIG.SYS ]
+ [ -f /host/Documents and Settings ]
[: and: unknown operand
+ continue
+ [ -f /host/IO.SYS ]
+ [ -f /host/IPH.PH ]
+ [ -f /host/MSDOS.SYS ]
+ [ -f /host/MSOCache ]
+ continue
+ [ -f /host/NTDETECT.COM ]
+ [ -f /host/Program Files ]
[: Files: unknown operand
+ continue
+ [ -f /host/RECYCLER ]
+ continue
+ [ -f /host/RHDSetup.log ]
+ [ -f /host/Sega ]
+ continue
+ [ -f /host/System Volume Information ]
[: Volume: unknown operand
+ continue
+ [ -f /host/WINDOWS ]
+ continue
+ [ -f /host/boot.ini ]
+ [ -f /host/games ]
+ continue
+ [ -f /host/grldr ]
+ [ -f /host/hiberfil.sys ]
+ [ -f /host/menu.lst ]
+ [ -f /host/ntldr ]
+ [ -f /host/pagefile.sys ]
+ [ -f /host/temp ]
+ continue
+ [ -f /host/utorrent.exe ]
+ [ -f /host/wubi ]
+ continue
+ [ -f /host/CD Images/Sega Smash Pach II.ccd ]
[: Images/Sega: unknown operand
+ continue
+ [ -f /host/CD Images/Sega Smash Pach II.cue ]
[: Images/Sega: unknown operand
+ continue
+ [ -f /host/CD Images/Sega Smash Pach II.img ]
[: Images/Sega: unknown operand
+ continue
+ [ -f /host/CD Images/Sega Smash Pach II.sub ]
[: Images/Sega: unknown operand
+ continue
+ [ -f /host/CD Images/WarCraftIII Reign of Chaos.ccd ]
[: Images/WarCraftIII: unknown operand
+ continue
+ [ -f /host/CD Images/WarCraftIII Reign of Chaos.cue ]
[: Images/WarCraftIII: unknown operand
+ continue
+ [ -f /host/CD Images/WarCraftIII Reign of Chaos.img ]
[: Images/WarCraftIII: unknown operand
+ continue
+ [ -f /host/CD Images/WarCraftIII Reign of Chaos.sub ]
[: Images/WarCraftIII: unknown operand
+ continue
+ [ -f /host/Documents and Settings/All Users ]
[: and: unknown operand
+ continue
+ [ -f /host/Documents and Settings/Default User ]
[: and: unknown operand
+ continue
+ [ -f /host/Documents and Settings/Joshizzle ]
[: and: unknown operand
+ continue
+ [ -f /host/Documents and Settings/LocalService ]
[: and: unknown operand
+ continue
+ [ -f /host/Documents and Settings/NetworkService ]
[: and: unknown operand
+ continue
+ [ -f /host/MSOCache/All Users ]
[: Users: unknown operand
+ continue
+ [ -f /host/Program Files/7-Zip ]
[: Files/7-Zip: unknown operand
+ continue
+ [ -f /host/Program Files/AIM6 ]
[: Files/AIM6: unknown operand
+ continue
+ [ -f /host/Program Files/Alcohol Soft ]
[: Files/Alcohol: unknown operand
+ continue
+ [ -f /host/Program Files/Apple Keyboard Support ]
[: Files/Apple: unknown operand
+ continue
+ [ -f /host/Program Files/Apple Software Update ]
[: Files/Apple: unknown operand
+ continue
+ [ -f /host/Program Files/ComPlus Applications ]
[: Files/ComPlus: unknown operand
+ continue
+ [ -f /host/Program Files/Common Files ]
[: Files/Common: unknown operand
+ continue
+ [ -f /host/Program Files/DIFX ]
[: Files/DIFX: unknown operand
+ continue
+ [ -f /host/Program Files/ESTsoft ]
[: Files/ESTsoft: unknown operand
+ continue
+ [ -f /host/Program Files/Elaborate Bytes ]
[: Files/Elaborate: unknown operand
+ continue
+ [ -f /host/Program Files/Eraser ]
[: Files/Eraser: unknown operand
+ continue
+ [ -f /host/Program Files/Foxit Software ]
[: Files/Foxit: unknown operand
+ continue
+ [ -f /host/Program Files/Gaim ]
[: Files/Gaim: unknown operand
+ continue
+ [ -f /host/Program Files/Google ]
[: Files/Google: unknown operand
+ continue
+ [ -f /host/Program Files/HIP ]
[: Files/HIP: unknown operand
+ continue
+ [ -f /host/Program Files/Handbrake ]
[: Files/Handbrake: unknown operand
+ continue
+ [ -f /host/Program Files/Illustrate ]
[: Files/Illustrate: unknown operand
+ continue
+ [ -f /host/Program Files/Infinite Interactive ]
[: Files/Infinite: unknown operand
+ continue
+ [ -f /host/Program Files/Infogrames ]
[: Files/Infogrames: unknown operand
+ continue
+ [ -f /host/Program Files/InstallShield Installation Information ]
[: Files/InstallShield: unknown operand
+ continue
+ [ -f /host/Program Files/Intel ]
[: Files/Intel: unknown operand
+ continue
+ [ -f /host/Program Files/Internet Explorer ]
[: Files/Internet: unknown operand
+ continue
+ [ -f /host/Program Files/Ipod Video Converter ]
[: Files/Ipod: unknown operand
+ continue
+ [ -f /host/Program Files/Java ]
[: Files/Java: unknown operand
+ continue
+ [ -f /host/Program Files/K-Lite Codec Pack ]
[: Files/K-Lite: unknown operand
+ continue
+ [ -f /host/Program Files/Launchy ]
[: Files/Launchy: unknown operand
+ continue
+ [ -f /host/Program Files/Lugaru ]
[: Files/Lugaru: unknown operand
+ continue
+ [ -f /host/Program Files/MSN ]
[: Files/MSN: unknown operand
+ continue
+ [ -f /host/Program Files/MSN Gaming Zone ]
[: Files/MSN: unknown operand
+ continue
+ [ -f /host/Program Files/MediaMonkey ]
[: Files/MediaMonkey: unknown operand
+ continue
+ [ -f /host/Program Files/Messenger ]
[: Files/Messenger: unknown operand
+ continue
+ [ -f /host/Program Files/Microsoft Office ]
[: Files/Microsoft: unknown operand
+ continue
+ [ -f /host/Program Files/Microsoft Visual Studio ]
[: Files/Microsoft: unknown operand
+ continue
+ [ -f /host/Program Files/Microsoft Works ]
[: Files/Microsoft: unknown operand
+ continue
+ [ -f /host/Program Files/Motorola ]
[: Files/Motorola: unknown operand
+ continue
+ [ -f /host/Program Files/Movie Maker ]
[: Files/Movie: unknown operand
+ continue
+ [ -f /host/Program Files/Mozilla Firefox ]
[: Files/Mozilla: unknown operand
+ continue
+ [ -f /host/Program Files/NetMeeting ]
[: Files/NetMeeting: unknown operand
+ continue
+ [ -f /host/Program Files/Notepad++ ]
[: Files/Notepad++: unknown operand
+ continue
+ [ -f /host/Program Files/Online Services ]
[: Files/Online: unknown operand
+ continue
+ [ -f /host/Program Files/OpenAL ]
[: Files/OpenAL: unknown operand
+ continue
+ [ -f /host/Program Files/Outlook Express ]
[: Files/Outlook: unknown operand
+ continue
+ [ -f /host/Program Files/Paint.NET ]
[: Files/Paint.NET: unknown operand
+ continue
+ [ -f /host/Program Files/Power Defragmenter ]
[: Files/Power: unknown operand
+ continue
+ [ -f /host/Program Files/QuickTime ]
[: Files/QuickTime: unknown operand
+ continue
+ [ -f /host/Program Files/Realtek ]
[: Files/Realtek: unknown operand
+ continue
+ [ -f /host/Program Files/SigmaTel ]
[: Files/SigmaTel: unknown operand
+ continue
+ [ -f /host/Program Files/SlySoft ]
[: Files/SlySoft: unknown operand
+ continue
+ [ -f /host/Program Files/TrueCrypt ]
[: Files/TrueCrypt: unknown operand
+ continue
+ [ -f /host/Program Files/TryMedia ]
[: Files/TryMedia: unknown operand
+ continue
+ [ -f /host/Program Files/Uninstall Information ]
[: Files/Uninstall: unknown operand
+ continue
+ [ -f /host/Program Files/VideoLAN ]
[: Files/VideoLAN: unknown operand
+ continue
+ [ -f /host/Program Files/Viewpoint ]
[: Files/Viewpoint: unknown operand
+ continue
+ [ -f /host/Program Files/WC3Banlist ]
[: Files/WC3Banlist: unknown operand
+ continue
+ [ -f /host/Program Files/Warcraft III ]
[: Files/Warcraft: unknown operand
+ continue
+ [ -f /host/Program Files/WinPcap ]
[: Files/WinPcap: unknown operand
+ continue
+ [ -f /host/Program Files/WinZip ]
[: Files/WinZip: unknown operand
+ continue
+ [ -f /host/Program Files/Windows Media Player ]
[: Files/Windows: unknown operand
+ continue
+ [ -f /host/Program Files/Windows NT ]
[: Files/Windows: unknown operand
+ continue
+ [ -f /host/Program Files/WindowsUpdate ]
[: Files/WindowsUpdate: unknown operand
+ continue
+ [ -f /host/Program Files/ffdshow ]
[: Files/ffdshow: unknown operand
+ continue
+ [ -f /host/Program Files/iPod ]
[: Files/iPod: unknown operand
+ continue
+ [ -f /host/Program Files/iTunes ]
[: Files/iTunes: unknown operand
+ continue
+ [ -f /host/Program Files/microsoft frontpage ]
[: Files/microsoft: unknown operand
+ continue
+ [ -f /host/Program Files/xerox ]
[: Files/xerox: unknown operand
+ continue
+ [ -f /host/RECYCLER/S-1-5-21-776561741-492894223-839522115-1003 ]
+ continue
+ [ -f /host/Sega/Smash Pack II ]
[: Pack: unknown operand
+ continue
+ [ -f /host/System Volume Information/MountPointManagerRemoteDatabase ]
[: Volume: unknown operand
+ continue
+ [ -f /host/System Volume Information/_restore{CF32CD6A-C0A5-4B4C-9DB4-54AA62DF4075} ]
[: Volume: unknown operand
+ continue
+ [ -f /host/System Volume Information/catalog.wci ]
[: Volume: unknown operand
+ continue
+ [ -f /host/System Volume Information/tracking.log ]
[: Volume: unknown operand
+ continue
+ [ -f /host/WINDOWS/$MSI31Uninstall_KB893803v2$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB873339$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB885835$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB885836$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB886185$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB887472$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB888111WXPSP2$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB888302$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB890859$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB891781$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB893756$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB894391$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB896358$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB896423$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB896424$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB896428$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB898461$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB899587$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB899591$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB900485$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB900725$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB901017$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB901214$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB902400$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB904706$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB905414$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB905749$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB908519$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB908531$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB910437$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB911280$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB911562$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB911564$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB911927$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB912919$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB913580$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB914388$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB914389$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB916595$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB917344$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB917422$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB917734_WMP9$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB917953$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB918118$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB918439$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB919007$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB920213$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB920670$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB920683$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB920685$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB920872$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB922582$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB922819$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB923191$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB923414$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB923689$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB923694$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB923980$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB924191$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB924270$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB924496$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB924667$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB925398_WMP64$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB925902$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB926255$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB926436$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB927779$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB927802$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB928090$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB928255$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB928843$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB929338$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB929969$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallKB931836$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallWdf01001$ ]
+ continue
+ [ -f /host/WINDOWS/$NtUninstallWdf01005$ ]
+ continue
+ [ -f /host/WINDOWS/$hf_mig$ ]
+ continue
+ [ -f /host/WINDOWS/0.log ]
+ [ -f /host/WINDOWS/AppPatch ]
+ continue
+ [ -f /host/WINDOWS/Blue Lace 16.bmp ]
[: Lace: unknown operand
+ continue
+ [ -f /host/WINDOWS/CIV.INI ]
+ [ -f /host/WINDOWS/Coffee Bean.bmp ]
[: Bean.bmp: unknown operand
+ continue
+ [ -f /host/WINDOWS/Config ]
+ continue
+ [ -f /host/WINDOWS/Connection Wizard ]
[: Wizard: unknown operand
+ continue
+ [ -f /host/WINDOWS/Cursors ]
+ continue
+ [ -f /host/WINDOWS/DPINST.LOG ]
+ [ -f /host/WINDOWS/Debug ]
+ continue
+ [ -f /host/WINDOWS/Downloaded Program Files ]
[: Program: unknown operand
+ continue
+ [ -f /host/WINDOWS/Driver Cache ]
[: Cache: unknown operand
+ continue
+ [ -f /host/WINDOWS/DtcInstall.log ]
+ [ -f /host/WINDOWS/FaxSetup.log ]
+ [ -f /host/WINDOWS/FeatherTexture.bmp ]
+ [ -f /host/WINDOWS/Fonts ]
+ continue
+ [ -f /host/WINDOWS/Gone Fishing.bmp ]
[: Fishing.bmp: unknown operand
+ continue
+ [ -f /host/WINDOWS/Greenstone.bmp ]
+ [ -f /host/WINDOWS/Help ]
+ continue
+ [ -f /host/WINDOWS/Installer ]
+ continue
+ [ -f /host/WINDOWS/IsUninst.exe ]
+ [ -f /host/WINDOWS/KB873339.log ]
+ [ -f /host/WINDOWS/KB885835.log ]
+ [ -f /host/WINDOWS/KB885836.log ]
+ [ -f /host/WINDOWS/KB886185.log ]
+ [ -f /host/WINDOWS/KB887472.log ]
+ [ -f /host/WINDOWS/KB888111.log ]
+ [ -f /host/WINDOWS/KB888302.log ]
+ [ -f /host/WINDOWS/KB890859.log ]
+ [ -f /host/WINDOWS/KB891781.log ]
+ [ -f /host/WINDOWS/KB893756.log ]
+ [ -f /host/WINDOWS/KB893803v2.log ]
+ [ -f /host/WINDOWS/KB894391.log ]
+ [ -f /host/WINDOWS/KB896358.log ]
+ [ -f /host/WINDOWS/KB896423.log ]
+ [ -f /host/WINDOWS/KB896424.log ]
+ [ -f /host/WINDOWS/KB896428.log ]
+ [ -f /host/WINDOWS/KB898461.log ]
+ [ -f /host/WINDOWS/KB899587.log ]
+ [ -f /host/WINDOWS/KB899591.log ]
+ [ -f /host/WINDOWS/KB900485.log ]
+ [ -f /host/WINDOWS/KB900725.log ]
+ [ -f /host/WINDOWS/KB901017.log ]
+ [ -f /host/WINDOWS/KB901214.log ]
+ [ -f /host/WINDOWS/KB902400.log ]
+ [ -f /host/WINDOWS/KB904706.log ]
+ [ -f /host/WINDOWS/KB905414.log ]
+ [ -f /host/WINDOWS/KB905749.log ]
+ [ -f /host/WINDOWS/KB908519.log ]
+ [ -f /host/WINDOWS/KB908531.log ]
+ [ -f /host/WINDOWS/KB910437.log ]
+ [ -f /host/WINDOWS/KB911280.log ]
+ [ -f /host/WINDOWS/KB911562.log ]
+ [ -f /host/WINDOWS/KB911564.log ]
+ [ -f /host/WINDOWS/KB911927.log ]
+ [ -f /host/WINDOWS/KB912919.log ]
+ [ -f /host/WINDOWS/KB913580.log ]
+ [ -f /host/WINDOWS/KB914388.log ]
+ [ -f /host/WINDOWS/KB914389.log ]
+ [ -f /host/WINDOWS/KB916595.log ]
+ [ -f /host/WINDOWS/KB917344.log ]
+ [ -f /host/WINDOWS/KB917422.log ]
+ [ -f /host/WINDOWS/KB917734.log ]
+ [ -f /host/WINDOWS/KB917953.log ]
+ [ -f /host/WINDOWS/KB918118.log ]
+ [ -f /host/WINDOWS/KB918439.log ]
+ [ -f /host/WINDOWS/KB919007.log ]
+ [ -f /host/WINDOWS/KB920213.log ]
+ [ -f /host/WINDOWS/KB920670.log ]
+ [ -f /host/WINDOWS/KB920683.log ]
+ [ -f /host/WINDOWS/KB920685.log ]
+ [ -f /host/WINDOWS/KB920872.log ]
+ [ -f /host/WINDOWS/KB922582.log ]
+ [ -f /host/WINDOWS/KB922819.log ]
+ [ -f /host/WINDOWS/KB923191.log ]
+ [ -f /host/WINDOWS/KB923414.log ]
+ [ -f /host/WINDOWS/KB923689.log ]
+ [ -f /host/WINDOWS/KB923694.log ]
+ [ -f /host/WINDOWS/KB923980.log ]
+ [ -f /host/WINDOWS/KB924191.log ]
+ [ -f /host/WINDOWS/KB924270.log ]
+ [ -f /host/WINDOWS/KB924496.log ]
+ [ -f /host/WINDOWS/KB924667.log ]
+ [ -f /host/WINDOWS/KB925398.log ]
+ [ -f /host/WINDOWS/KB925902.log ]
+ [ -f /host/WINDOWS/KB926255.log ]
+ [ -f /host/WINDOWS/KB926436.log ]
+ [ -f /host/WINDOWS/KB927779.log ]
+ [ -f /host/WINDOWS/KB927802.log ]
+ [ -f /host/WINDOWS/KB928090.log ]
+ [ -f /host/WINDOWS/KB928255.log ]
+ [ -f /host/WINDOWS/KB928843.log ]
+ [ -f /host/WINDOWS/KB929338.log ]
+ [ -f /host/WINDOWS/KB929969.log ]
+ [ -f /host/WINDOWS/KB931836.log ]
+ [ -f /host/WINDOWS/MedCtrOC.log ]
+ [ -f /host/WINDOWS/Media ]
+ continue
+ [ -f /host/WINDOWS/MicCal.exe ]
+ [ -f /host/WINDOWS/Microsoft.NET ]
+ continue
+ [ -f /host/WINDOWS/Minidump ]
+ continue
+ [ -f /host/WINDOWS/NOTEPAD.EXE ]
+ [ -f /host/WINDOWS/ODBC.INI ]
+ [ -f /host/WINDOWS/ODBCINST.INI ]
+ [ -f /host/WINDOWS/OEWABLog.txt ]
+ [ -f /host/WINDOWS/Offline Web Pages ]
[: Web: unknown operand
+ continue
+ [ -f /host/WINDOWS/PeerNet ]
+ continue
+ [ -f /host/WINDOWS/Prairie Wind.bmp ]
[: Wind.bmp: unknown operand
+ continue
+ [ -f /host/WINDOWS/Prefetch ]
+ continue
+ [ -f /host/WINDOWS/Provisioning ]
+ continue
+ [ -f /host/WINDOWS/REGLOCS.OLD ]
+ [ -f /host/WINDOWS/RTHDCPL.exe ]
+ [ -f /host/WINDOWS/Registration ]
+ continue
+ [ -f /host/WINDOWS/Resources ]
+ continue
+ [ -f /host/WINDOWS/Rhododendron.bmp ]
+ [ -f /host/WINDOWS/River Sumida.bmp ]
[: Sumida.bmp: unknown operand
+ continue
+ [ -f /host/WINDOWS/RtlExUpd.dll ]
+ [ -f /host/WINDOWS/RtlUpd.exe ]
+ [ -f /host/WINDOWS/SET3.tmp ]
+ [ -f /host/WINDOWS/SET4.tmp ]
+ [ -f /host/WINDOWS/SET8.tmp ]
+ [ -f /host/WINDOWS/SHELLNEW ]
+ continue
+ [ -f /host/WINDOWS/Santa Fe Stucco.bmp ]
[: Fe: unknown operand
+ continue
+ [ -f /host/WINDOWS/SchedLgU.Txt ]
+ [ -f /host/WINDOWS/Soap Bubbles.bmp ]
[: Bubbles.bmp: unknown operand
+ continue
+ [ -f /host/WINDOWS/SoftwareDistribution ]
+ continue
+ [ -f /host/WINDOWS/Sti_Trace.log ]
+ [ -f /host/WINDOWS/Sun ]
+ continue
+ [ -f /host/WINDOWS/SxsCaPendDel ]
+ continue
+ [ -f /host/WINDOWS/TASKMAN.EXE ]
+ [ -f /host/WINDOWS/Tasks ]
+ continue
+ [ -f /host/WINDOWS/Temp ]
+ continue
+ [ -f /host/WINDOWS/Thumbs.db ]
+ [ -f /host/WINDOWS/WGA.log ]
+ [ -f /host/WINDOWS/WMSysPr9.prx ]
+ [ -f /host/WINDOWS/War3Unin.dat ]
+ [ -f /host/WINDOWS/War3Unin.exe ]
+ [ -f /host/WINDOWS/War3Unin.pif ]
+ [ -f /host/WINDOWS/Wdf01001Inst.log ]
+ [ -f /host/WINDOWS/Wdf01005Inst.log ]
+ [ -f /host/WINDOWS/Web ]
+ continue
+ [ -f /host/WINDOWS/WgaNotify.log ]
+ [ -f /host/WINDOWS/WinSxS ]
+ continue
+ [ -f /host/WINDOWS/WindowsShell.Manifest ]
+ [ -f /host/WINDOWS/WindowsUpdate.log ]
+ [ -f /host/WINDOWS/Zapotec.bmp ]
+ [ -f /host/WINDOWS/_default.pif ]
+ [ -f /host/WINDOWS/addins ]
+ continue
+ [ -f /host/WINDOWS/assembly ]
+ continue
+ [ -f /host/WINDOWS/atid.ini ]
+ [ -f /host/WINDOWS/bootstat.dat ]
+ [ -f /host/WINDOWS/clock.avi ]
+ [ -f /host/WINDOWS/cmsetacl.log ]
+ [ -f /host/WINDOWS/comsetup.log ]
+ [ -f /host/WINDOWS/control.ini ]
+ [ -f /host/WINDOWS/desktop.ini ]
+ [ -f /host/WINDOWS/ehome ]
+ continue
+ [ -f /host/WINDOWS/explorer.exe ]
+ [ -f /host/WINDOWS/explorer.scf ]
+ [ -f /host/WINDOWS/hh.exe ]
+ [ -f /host/WINDOWS/iis6.log ]
+ [ -f /host/WINDOWS/ime ]
+ continue
+ [ -f /host/WINDOWS/imsins.BAK ]
+ [ -f /host/WINDOWS/imsins.log ]
+ [ -f /host/WINDOWS/inf ]
+ continue
+ [ -f /host/WINDOWS/java ]
+ continue
+ [ -f /host/WINDOWS/mozver.dat ]
+ [ -f /host/WINDOWS/msagent ]
+ continue
+ [ -f /host/WINDOWS/msapps ]
+ continue
+ [ -f /host/WINDOWS/msdfmap.ini ]
+ [ -f /host/WINDOWS/msgsocm.log ]
+ [ -f /host/WINDOWS/msmqinst.log ]
+ [ -f /host/WINDOWS/mui ]
+ continue
+ [ -f /host/WINDOWS/netfxocm.log ]
+ [ -f /host/WINDOWS/nsreg.dat ]
+ [ -f /host/WINDOWS/ntdtcsetup.log ]
+ [ -f /host/WINDOWS/ocgen.log ]
+ [ -f /host/WINDOWS/ocmsn.log ]
+ [ -f /host/WINDOWS/pchealth ]
+ continue
+ [ -f /host/WINDOWS/regedit.exe ]
+ [ -f /host/WINDOWS/regopt.log ]
+ [ -f /host/WINDOWS/repair ]
+ continue
+ [ -f /host/WINDOWS/security ]
+ continue
+ [ -f /host/WINDOWS/sessmgr.setup.log ]
+ [ -f /host/WINDOWS/setupact.log ]
+ [ -f /host/WINDOWS/setupapi.log ]
+ [ -f /host/WINDOWS/setuperr.log ]
+ [ -f /host/WINDOWS/setuplog.txt ]
+ [ -f /host/WINDOWS/spupdsvc.log ]
+ [ -f /host/WINDOWS/srchasst ]
+ continue
+ [ -f /host/WINDOWS/system ]
+ continue
+ [ -f /host/WINDOWS/system.ini ]
+ [ -f /host/WINDOWS/system32 ]
+ continue
+ [ -f /host/WINDOWS/tabletoc.log ]
+ [ -f /host/WINDOWS/tsoc.log ]
+ [ -f /host/WINDOWS/twain.dll ]
+ [ -f /host/WINDOWS/twain_32 ]
+ continue
+ [ -f /host/WINDOWS/twain_32.dll ]
+ [ -f /host/WINDOWS/twunk_16.exe ]
+ [ -f /host/WINDOWS/twunk_32.exe ]
+ [ -f /host/WINDOWS/updspapi.log ]
+ [ -f /host/WINDOWS/vb.ini ]
+ [ -f /host/WINDOWS/vbaddin.ini ]
+ [ -f /host/WINDOWS/vmmreg32.dll ]
+ [ -f /host/WINDOWS/wiadebug.log ]
+ [ -f /host/WINDOWS/wiaservc.log ]
+ [ -f /host/WINDOWS/win.ini ]
+ [ -f /host/WINDOWS/winhelp.exe ]
+ [ -f /host/WINDOWS/winhlp32.exe ]
+ [ -f /host/WINDOWS/winnt.bmp ]
+ [ -f /host/WINDOWS/winnt256.bmp ]
+ [ -f /host/WINDOWS/wmsetup.log ]
+ [ -f /host/wubi/Uninstall.exe ]
+ [ -f /host/wubi/WUBI-README.txt ]
+ [ -f /host/wubi/boot ]
+ continue
+ [ -f /host/wubi/config.ini ]
+ [ -f /host/wubi/disks ]
+ continue
+ [ -f /host/wubi/docs ]
+ continue
+ [ -f /host/wubi/initrd.gz ]
+ [ -f /host/wubi/install ]
+ continue
+ [ -f /host/wubi/license.txt ]
+ [ -f /host/wubi/linux ]
+ [ -f /host/wubi/logs ]
+ continue
+ [ -f /host/wubi/tools ]
+ continue
+ [ -f /host/wubi/wubi-7.04-beta-v3.exe ]
+ [ -f /host/wubi/wubi.ini ]
+ log_warning_msg Could not find any ISO
+ _log_msg Warning: Could not find any ISO
+ echo Warning: Could not find any ISO
Warning: Could not find any ISO
+ return 11
+ fail 
Could not find any file needed to boot...
The bootlader is probably pointing to the wrong file/folder
Please check that the 'find' kernel parameter in menu.lst
points to the correct location
+ quit_usplash
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write PROGRESS 100
+ /sbin/usplash_write SUCCESS ok
+ /sbin/usplash_write QUIT
+ log_failure_msg 
Could not find any file needed to boot...
The bootlader is probably pointing to the wrong file/folder
Please check that the 'find' kernel parameter in menu.lst
points to the correct location
+ _log_msg Failure: 
Could not find any file needed to boot...
The bootlader is probably pointing to the wrong file/folder
Please check that the 'find' kernel parameter in menu.lst
points to the correct location
+ echo Failure: 
Could not find any file needed to boot...
The bootlader is probably pointing to the wrong file/folder
Please check that the 'find' kernel parameter in menu.lst
points to the correct location
Failure: 
Could not find any file needed to boot...
The bootlader is probably pointing to the wrong file/folder
Please check that the 'find' kernel parameter in menu.lst
points to the correct location
+ echo -------------------------------------------
+ echo ERROR:
+ echo
+ echo 
Could not find any file needed to boot...
The bootlader is probably pointing to the wrong file/folder
Please check that the 'find' kernel parameter in menu.lst
points to the correct location
+ echo -------------------------------------------
+ cp_logs
+ [ -e /logs ]
+ cp /tmp/lupin.log /tmp/zenigata.log /logs/
+ [ -e /host/wubi ]
+ [ -e /host/wubi/logs ]
+ cp /tmp/lupin.log /tmp/zenigata.log /host/wubi/logs

---

### Post by ago on 2007-04-11
> **Bobberb said:**
> no...did not work, I think the log file is even the sae

Do you have an ISO file in c:\wubi\install? What's its name? What's its size?

---

### Post by Bobberb on 2007-04-11
> **ago said:**
> Do you have an ISO file in c:\wubi\install? What's its name? What's its size?

ubuntu-7.04-beta-alternate-i386.iso

---

### Post by ago on 2007-04-11
do you have C:/wubi/install/preseed.cfg?
If not you have to run wubi again and choose "reinstall"

---

### Post by Bobberb on 2007-04-11
> **ago said:**
> do you have C:/wubi/install/preseed.cfg?
If not you have to run wubi again and choose "reinstall"

preseed is not around either, I will reinstall and keep you posted

---

### Post by Bobberb on 2007-04-11
ok, well, that does not work either...will kinda:

something about:
IO-APIC not connected to timer! Timer doesnt work! reboot with apic=debug and send bug report! then boot with noapic

---

### Post by ago on 2007-04-11
run wubi again, choose to reinstall, but before rebooting edit c:\menu.lst and add 

noapic 

to the kernel line, then reboot

---

### Post by Bobberb on 2007-04-11
what does apic mean?

---

### Post by Bobberb on 2007-04-11
where is the kernel line I have this:
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        1

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

## Pretty colours
#color cyan/blue white/blue

#### MENU ITEMS BELOW HERE ####

title Ubuntu
find --set-root /wubi/boot/menu.lst
configfile /wubi/boot/menu.lst

---

### Post by ago on 2007-04-11
edit c:\wubi\boot\menu.lst

---

### Post by Bobberb on 2007-04-11
no dice:
the first time I did it I managed to get a blue screen with what appeared to be drivers being loaded, that ended and I was left with a blue screen with a line of back...another command line

second time I got my origininal error message

---

### Post by Bobberb on 2007-04-11
preseed got wiped for some reason...

---

### Post by ago on 2007-04-11
preseed gets deleted every time you install since it contains the password. If you interrupt the installation you must run wubi again.

If you see the blue screen that is good. Just wait. You can press Alt+F4 to see the progress.

---

### Post by Bobberb on 2007-04-11
yes...but after it loads a few things it goes blank blue and I can flood the screen with black...I guess I have to reinstall again - then what?

---

### Post by Bobberb on 2007-04-13
still happening, any advice?

---

### Post by ago on 2007-04-13
Did you try to press alt+f4?

---

### Post by Bobberb on 2007-04-14
during what part?

---

### Post by ago on 2007-04-14
when you see the blue screen

---

### Post by Bobberb on 2007-04-15
it wont let me, should I take a picture or something?

---

### Post by ago on 2007-04-15
Do you get to the blue screen with the red progressbars?

---

### Post by Bobberb on 2007-04-15
what do u mean by red?
its blue grey and red....with a black line at the bottom

---

