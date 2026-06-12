---
title: "Wubi 8.04 installation error"
date: 2008-03-29
forum: General Help
---

### Post by Meriadok on 2008-03-29
I've tried to install KUbuntu 8.04 beta on my laptop Toshiba Satellite L40 (Vista Home Premium, two partitions - C: , E:). I installed it on drive E:. That was some freeze at the end of installation but there was message "done" and cd was ejected from cdrom.
After rebooting i choose "kubuntu-kde4" in boot menu but there is error "ntfs 5: no wubildr".
bcdedit /enum command types next:
> &#1044;&#1080;&#1089;&#1087;&#1077;&#1090;&#1095;&#1077;&#1088; &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080; Windows
--------------------
&#1080;&#1076;&#1077;&#1085;&#1090;&#1080;&#1092;&#1080;&#1082;&#1072;&#1090;&#1086;&#1088;           {bootmgr}
device                  partition=C:
description             Windows Boot Manager
locale                  ru-RU
inherit                 {globalsettings}
default                 {current}
resumeobject            {a61cb260-506c-11dc-ba21-001a92aadfd0}
displayorder            {current}
                        {03ba8ba1-fd8f-11dc-8baa-001d60f28766}
                        {03ba8ba2-fd8f-11dc-8baa-001d60f28766}
toolsdisplayorder       {memdiag}
timeout                 10

&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1072; Windows
-------------------
&#1080;&#1076;&#1077;&#1085;&#1090;&#1080;&#1092;&#1080;&#1082;&#1072;&#1090;&#1086;&#1088;           {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Microsoft Windows Vista
locale                  ru-RU
inherit                 {bootloadersettings}
recoverysequence        {572bcd56-ffa7-11d9-aae0-0007e994107d}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {a61cb260-506c-11dc-ba21-001a92aadfd0}
nx                      OptIn

&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1086;&#1095;&#1085;&#1099;&#1081; &#1089;&#1077;&#1082;&#1090;&#1086;&#1088; &#1088;&#1077;&#1072;&#1083;&#1100;&#1085;&#1086;&#1075;&#1086; &#1088;&#1077;&#1078;&#1080;&#1084;&#1072;
---------------------
&#1080;&#1076;&#1077;&#1085;&#1090;&#1080;&#1092;&#1080;&#1082;&#1072;&#1090;&#1086;&#1088;           {03ba8ba1-fd8f-11dc-8baa-001d60f28766}
device                  partition=E:
path                    \ubuntu\winboot\wubildr.mbr
description             Kubuntu-KDE4

&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1086;&#1095;&#1085;&#1099;&#1081; &#1089;&#1077;&#1082;&#1090;&#1086;&#1088; &#1088;&#1077;&#1072;&#1083;&#1100;&#1085;&#1086;&#1075;&#1086; &#1088;&#1077;&#1078;&#1080;&#1084;&#1072;
---------------------
&#1080;&#1076;&#1077;&#1085;&#1090;&#1080;&#1092;&#1080;&#1082;&#1072;&#1090;&#1086;&#1088;           {03ba8ba2-fd8f-11dc-8baa-001d60f28766}
device                  boot
path                    \grldr.mbr
description             KUbuntu1

Sorry for russian words in the log - you may compare it with your own log. The last intire was made as an experiment (advice from topic about wubi and vista). Trying to boot from it leads to error "ntfs 5: no grldr".

I installed wubi under administrator rights, all files (such as wubildr, menu.lst) exists in roots of each drive, folder E:\ubuntu\winboot\ exists, file wubildr.mbr is in it.

What can i do with it?

---

### Post by givver on 2008-03-29
I am having exactly the same problem.

---

### Post by Meriadok on 2008-03-29
Just now i've tried to add a NeoGRUB entire with EasyBCD. Have similar error. So i think it's not my mistake or wubi installing error. I have feeling that it's some vista security issue.

---

