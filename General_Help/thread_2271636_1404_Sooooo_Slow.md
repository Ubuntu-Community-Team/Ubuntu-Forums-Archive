---
title: "14:04 Sooooo Slow"
date: 2015-03-31
forum: General Help
---

### Post by wolfie52 on 2015-03-31
Please can anyone help

I am currently using a Packard Bell. It has Microsoft Vista installed as a standard and Ubuntu 14:04. There is no dual operating, I do not have access or wish to use MS Vista.

Up until quite recently my PC was fast and slick. Now it is terribly slow. Im not sure how much disk space there is but trust me, I have a mass of capacity. I tried to load Ubuntu Tweak but it just will not run on this machine.

I can download but then it wont actually run.

Please can someone help me tidy the disc space and get this old bird to start performing again. 

Many thanks


Geoff

---

### Post by egeezer on 2015-03-31
Not sure what you mean by "It has Microsoft Vista installed as a standard and Ubuntu 14:04. There is no dual operating" Are you running it as Wubi?  You might try opening a terminal and running: ```
sudo parted /dev/sda print
``` and showing the output in your next post.  That will show the setup you have.

---

### Post by wolfie52 on 2015-04-01
Hello: Appreciate your response. Here is the set up:

Look forward to hearing from you.

Geoff

I'm not sure the machine was set-up using WUBI. The installation of Ubuntu was pre loaded when I bought this machine. I like Ubuntu so much I have no use for Windows and would happily take that off the drive if it helped my concern.


```
Model: ATA ST3250820AS (scsi)Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  8192MB  8191MB  primary   ext4            boot
 3      8193MB  246GB   238GB   primary   ext4
 2      246GB   250GB   4096MB  extended
 5      246GB   250GB   4096MB  logical   linux-swap(v1)
```

---

### Post by Bucky Ball on 2015-04-01
Unsure where Vista is as you appear to have no NTFS partition on that disk (sda). You have two EXT4 partitions, an extended (which is like a container, not like a regular partition) with /swap (unecessarily) inside that.

Vista can't live on any of the partitions you have here. It can live inside an extended partition ... on an NTFS logical partition.

Do you have the disk sdb hiding somewhere?

PS: Please use [code] tags for terminal output. See last link in my signature. ;)

---

### Post by wolfie52 on 2015-04-03
Thank you for your responses Bucky and Egeezer. I now do appreciate the need to use [code] tags and why it obviously clarifies the content of communication.

The above said, my PC is still very slow. Can I take Windows off? Would that help I wonder. As for disk sdb hiding I am not familiar with this but will endeavour to try to establish an answer.

Thank you for your help, and any other forthcoming help would really be appreciated.

Geoff

---

### Post by dino99 on 2015-04-03
i understand your system is slow ;) i'm also surprised you can still use it:

****
Number  Start   End     Size    Type      File system     Flags
 1      1049kB  8192MB  8191MB  primary   ext4            boot
 3      8193MB  246GB   238GB   primary   ext4
 2      246GB   250GB   4096MB  extended
 5      246GB   250GB   4096MB  logical   linux-swap(v1)
*****
that installation has been badly set (not what a genuine one looks like)
you need 3 partitions:
1- ext4 about 10000/12000MB for ubuntu installation (OS & apps)
2- a swap partition about 4000MB
3- ext4 /home partition for your data 

actually you seems sharing the first partition between OS/apps & your own data; which means that 8191MB is way too narrow, so the slowness as the system may waste its full time swaping.
if you does not care about vista then save your data on an exteral usb stick (or else) then do a fresh install from the mini.iso
boot from a usb/cd iso to format and install ubuntu.
 [http://cdimage.ubuntu.com/netboot/](http://cdimage.ubuntu.com/netboot/)

---

### Post by wolfie52 on 2015-04-04
really appreciate the time you have taken to help. I will look at your comments and try to act. Thank you again.

Geoff

---

### Post by Impavidus on 2015-04-04
From where is the assumtion that root and /home are both on sda1? I see an 8GB ext4 partition (root?), a 238GB ext4 partition (/home?) and a 4GB swap partition. There is no Windows present on this hard drive. To find the details, use```
[s]du -h[/s]
df -h
```It's possible that the root partition is almost full and causes the slowdown as fragmentation sets in. 8GB is rather small for a root partition.

There is no Windows installed (at least not on sda), so it can't be taken off. Maybe there are multiple hard drives? Windows could be hiding on sdb (=drive #2), as Bucky Ball suggested. This command should tell:```
sudo parted -l
```

---

### Post by wolfie52 on 2015-04-05
hello Impavidus and 9d9

Here, I hope is the information you suggest. And also I (really) hope the presentation is correct for the forum with code tags.


```

ization/3.0.0.0__b77a5c561934e089
432K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Runtime.Serialization
48K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.CompilerServices.SymbolWriter/2.0.0.0__0738eb9f132ed756
48K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.CompilerServices.SymbolWriter/4.0.0.0__0738eb9f132ed756
100K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.CompilerServices.SymbolWriter
40K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Parallel/4.0.0.0__0738eb9f132ed756
44K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Parallel
116K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Xml.Linq/4.0.0.0__b77a5c561934e089
112K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Xml.Linq/3.5.0.0__b77a5c561934e089
232K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Xml.Linq
44K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.WebPages.Deployment/2.0.0.0__31bf3856ad364e35
48K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.WebPages.Deployment
88K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Threading.Tasks.Dataflow/4.0.0.0__b77a5c561934e089
92K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Threading.Tasks.Dataflow
52K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Management/4.0.0.0__b03f5f7f11d50a3a
52K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Management/2.0.0.0__b03f5f7f11d50a3a
108K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Management
20K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Management/2.0.0.0__0738eb9f132ed756
20K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Management/4.0.0.0__0738eb9f132ed756
44K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Management
684K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.CodeContracts/4.0.0.0__0738eb9f132ed756
688K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.CodeContracts
20K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Security.Win32/2.0.0.0__0738eb9f132ed756
24K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Security.Win32/4.0.0.0__0738eb9f132ed756
48K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Security.Win32
24K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/WebMatrix.Data/4.0.0.0__0738eb9f132ed756
28K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/WebMatrix.Data
12K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.Xna.Framework.Graphics/4.0.0.0__842cf8be1de50553
16K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.Xna.Framework.Graphics
524K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Data.Linq/4.0.0.0__b77a5c561934e089
520K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Data.Linq/3.5.0.0__b77a5c561934e089
1.1M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Data.Linq
788K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Core/4.0.0.0__b77a5c561934e089
292K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Core/3.5.0.0__b77a5c561934e089
1.1M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Core
180K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.Build.Tasks.v3.5/3.5.0.0__b03f5f7f11d50a3a
184K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.Build.Tasks.v3.5
80K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.Build/4.0.0.0__b03f5f7f11d50a3a
84K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.Build
44K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Runtime.Serialization.Formatters.Soap/4.0.0.0__b03f5f7f11d50a3a
40K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Runtime.Serialization.Formatters.Soap/2.0.0.0__b03f5f7f11d50a3a
88K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Runtime.Serialization.Formatters.Soap
20K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.Web.Infrastructure/1.0.0.0__31bf3856ad364e35
24K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.Web.Infrastructure
36K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Transactions/4.0.0.0__b77a5c561934e089
36K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Transactions/2.0.0.0__b77a5c561934e089
76K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Transactions
40K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/I18N/2.0.0.0__0738eb9f132ed756
40K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/I18N/4.0.0.0__0738eb9f132ed756
84K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/I18N
456K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/MonoGame.Framework.Wine/4.0.0.0__0738eb9f132ed756
460K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/MonoGame.Framework.Wine
40K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Messaging.RabbitMQ/2.0.0.0__0738eb9f132ed756
40K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Messaging.RabbitMQ/4.0.0.0__0738eb9f132ed756
84K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Messaging.RabbitMQ
4.5M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/EntityFramework/6.0.0.0__b77a5c561934e089
4.5M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/EntityFramework
112K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Net.Http/4.0.0.0__b03f5f7f11d50a3a
116K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Net.Http
308K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Cecil.VB/0.9.3.0__0738eb9f132ed756
312K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Cecil.VB
472K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/RabbitMQ.Client/4.0.0.0__b03f5f7f11d50a3a
468K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/RabbitMQ.Client/2.0.0.0__b03f5f7f11d50a3a
944K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/RabbitMQ.Client
288K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Security/2.0.0.0__0738eb9f132ed756
292K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Security/4.0.0.0__0738eb9f132ed756
584K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Security
16K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.VisualC/8.0.0.0__b03f5f7f11d50a3a
16K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.VisualC/0.0.0.0__b03f5f7f11d50a3a
36K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.VisualC
16K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Net/3.5.0.0__7cec85d7bea7798e
16K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Net/4.0.0.0__7cec85d7bea7798e
36K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Net
148K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.ServiceModel.Discovery/4.0.0.0__31bf3856ad364e35
152K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.ServiceModel.Discovery
188K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.Build.Tasks.v4.0/4.0.0.0__b03f5f7f11d50a3a
192K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.Build.Tasks.v4.0
172K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/I18N.Rare/2.0.0.0__0738eb9f132ed756
172K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/I18N.Rare/4.0.0.0__0738eb9f132ed756
348K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/I18N.Rare
84K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Messaging/4.0.0.0__b03f5f7f11d50a3a
80K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Messaging/2.0.0.0__b03f5f7f11d50a3a
168K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Messaging
60K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Data.Services/4.0.0.0__b77a5c561934e089
28K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Data.Services/3.5.0.0__b77a5c561934e089
92K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Data.Services
1.2M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/monodoc/1.0.0.0__0738eb9f132ed756
1.2M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/monodoc
260K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Novell.Directory.Ldap/2.0.0.0__0738eb9f132ed756
260K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Novell.Directory.Ldap/4.0.0.0__0738eb9f132ed756
524K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Novell.Directory.Ldap
16K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Tasklets/2.0.0.0__0738eb9f132ed756
16K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Tasklets/4.0.0.0__0738eb9f132ed756
36K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Tasklets
36K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/I18N.Other/2.0.0.0__0738eb9f132ed756
40K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/I18N.Other/4.0.0.0__0738eb9f132ed756
80K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/I18N.Other
284K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.ComponentModel.Composition/4.0.0.0__b77a5c561934e089
288K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.ComponentModel.Composition
64K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Json/4.0.0.0__31bf3856ad364e35
68K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Json
96K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Dynamic/4.0.0.0__b77a5c561934e089
100K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Dynamic
288K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Design/4.0.0.0__b03f5f7f11d50a3a
284K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Design/2.0.0.0__b03f5f7f11d50a3a
576K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Design
2.7M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Wine.OpenTK/4.0.0.0__bad199fe84eb3df4
2.7M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Wine.OpenTK
104K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/nunit.util/2.4.8.0__96d09a1eb7f44a77
108K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/nunit.util
68K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/I18N.West/2.0.0.0__0738eb9f132ed756
72K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/I18N.West/4.0.0.0__0738eb9f132ed756
144K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/I18N.West
840K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Data/4.0.0.0__b77a5c561934e089
836K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Data/2.0.0.0__b77a5c561934e089
1.7M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Data
40K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Numerics/4.0.0.0__b77a5c561934e089
44K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Numerics
8.0K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.Xna.Framework.Xact/4.0.0.0__842cf8be1de50553
12K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.Xna.Framework.Xact
1.3M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Xml/4.0.0.0__b77a5c561934e089
1.3M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Xml/2.0.0.0__b77a5c561934e089
2.5M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Xml
36K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.CSharp/4.0.0.0__b03f5f7f11d50a3a
40K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.CSharp
56K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.Build.Utilities/2.0.0.0__b03f5f7f11d50a3a
60K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.Build.Utilities
240K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Commons.Xml.Relaxng/2.0.0.0__0738eb9f132ed756
240K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Commons.Xml.Relaxng/4.0.0.0__0738eb9f132ed756
484K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Commons.Xml.Relaxng
40K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Messaging/2.0.0.0__0738eb9f132ed756
40K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Messaging/4.0.0.0__0738eb9f132ed756
84K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Messaging
2.4M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web/4.0.0.0__b03f5f7f11d50a3a
2.2M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web/2.0.0.0__b03f5f7f11d50a3a
4.6M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web
32K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Data.DataSetExtensions/4.0.0.0__b77a5c561934e089
32K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Data.DataSetExtensions/3.5.0.0__b77a5c561934e089
68K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Data.DataSetExtensions
752K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.Extensions/3.5.0.0__31bf3856ad364e35
604K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.Extensions/1.0.61025.0__31bf3856ad364e35
756K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.Extensions/4.0.0.0__31bf3856ad364e35
2.1M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.Extensions
32K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Http/2.0.0.0__0738eb9f132ed756
32K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Http/4.0.0.0__0738eb9f132ed756
68K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Http
40K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.Routing/3.5.0.0__31bf3856ad364e35
16K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.Routing/4.0.0.0__31bf3856ad364e35
60K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.Routing
48K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.ServiceProcess/4.0.0.0__b03f5f7f11d50a3a
48K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.ServiceProcess/2.0.0.0__b03f5f7f11d50a3a
100K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.ServiceProcess
76K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.DynamicData/3.5.0.0__31bf3856ad364e35
76K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.DynamicData/4.0.0.0__31bf3856ad364e35
156K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.DynamicData
12K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.Xna.Framework.Game/4.0.0.0__842cf8be1de50553
16K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.Xna.Framework.Game
32K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/nunit.core.interfaces/2.4.8.0__96d09a1eb7f44a77
36K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/nunit.core.interfaces
16K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Accessibility/4.0.0.0__b03f5f7f11d50a3a
16K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Accessibility/2.0.0.0__b03f5f7f11d50a3a
36K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Accessibility
20K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/cscompmgd/8.0.0.0__b03f5f7f11d50a3a
24K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/cscompmgd/0.0.0.0__b03f5f7f11d50a3a
48K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/cscompmgd
20K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/CustomMarshalers/4.0.0.0__b03f5f7f11d50a3a
16K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/CustomMarshalers/2.0.0.0__b03f5f7f11d50a3a
40K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/CustomMarshalers
172K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Data.Sqlite/2.0.0.0__0738eb9f132ed756
172K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Data.Sqlite/4.0.0.0__0738eb9f132ed756
348K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Data.Sqlite
1.2M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.CSharp/2.0.0.0__0738eb9f132ed756
1.2M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.CSharp/4.0.0.0__0738eb9f132ed756
2.3M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.CSharp
16K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/nunit.mocks/2.4.8.0__96d09a1eb7f44a77
20K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/nunit.mocks
348K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.Services/4.0.0.0__b03f5f7f11d50a3a
344K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.Services/2.0.0.0__b03f5f7f11d50a3a
696K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.Services
440K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Drawing/4.0.0.0__b03f5f7f11d50a3a
440K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Drawing/2.0.0.0__b03f5f7f11d50a3a
884K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Drawing
48K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Cecil.VB.Mdb/0.9.3.0__0738eb9f132ed756
52K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Cecil.VB.Mdb
20K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.Extensions.Design/3.5.0.0__31bf3856ad364e35
20K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.Extensions.Design/1.0.61025.0__31bf3856ad364e35
20K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.Extensions.Design/4.0.0.0__31bf3856ad364e35
64K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.Extensions.Design
500K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/EntityFramework.SqlServer/6.0.0.0__b77a5c561934e089
504K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/EntityFramework.SqlServer
136K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Lidgren.Network.Wine/2011.3.12.0__0738eb9f132ed756
140K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Lidgren.Network.Wine
200K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.ServiceModel.Web/3.5.0.0__31bf3856ad364e35
92K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.ServiceModel.Web/4.0.0.0__31bf3856ad364e35
296K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.ServiceModel.Web
180K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.Build.Tasks/2.0.0.0__b03f5f7f11d50a3a
184K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Microsoft.Build.Tasks
24K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/nunit-console-runner/2.4.8.0__96d09a1eb7f44a77
28K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/nunit-console-runner
88K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Cecil.VB.Pdb/0.9.3.0__0738eb9f132ed756
92K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Cecil.VB.Pdb
200K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Xaml/4.0.0.0__b77a5c561934e089
204K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Xaml
212K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.WebPages/2.0.0.0__31bf3856ad364e35
216K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.WebPages
76K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/nunit.core/2.4.8.0__96d09a1eb7f44a77
80K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/nunit.core
32K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.ApplicationServices/4.0.0.0__31bf3856ad364e35
36K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.ApplicationServices
108K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.IdentityModel/4.0.0.0__b77a5c561934e089
108K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.IdentityModel/3.0.0.0__b77a5c561934e089
220K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.IdentityModel
172K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.WebBrowser/2.0.0.0__0738eb9f132ed756
172K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.WebBrowser/4.0.0.0__0738eb9f132ed756
348K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.WebBrowser
1.8M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System/4.0.0.0__b77a5c561934e089
1.7M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System/2.0.0.0__b77a5c561934e089
3.5M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System
48K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Cecil.Mdb/0.9.5.0__0738eb9f132ed756
52K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Mono.Cecil.Mdb
64K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.Abstractions/3.5.0.0__31bf3856ad364e35
16K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.Abstractions/4.0.0.0__31bf3856ad364e35
84K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.Abstractions
180K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Npgsql/2.0.0.0__5d8b90d52f46fda7
180K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Npgsql/4.0.0.0__5d8b90d52f46fda7
364K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/Npgsql
280K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.Razor/2.0.0.0__31bf3856ad364e35
284K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Web.Razor
176K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Data.OracleClient/4.0.0.0__b77a5c561934e089
176K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Data.OracleClient/2.0.0.0__b77a5c561934e089
356K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/System.Data.OracleClient
36K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/I18N.MidEast/2.0.0.0__0738eb9f132ed756
36K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/I18N.MidEast/4.0.0.0__0738eb9f132ed756
76K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac/I18N.MidEast
60M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/gac
4.0K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/compat-2.0
4.0K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/monodoc
112K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/2.0/MSBuild
3.4M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/2.0
12M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/4.5
44K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/xbuild/Microsoft/Silverlight/v2.0
44K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/xbuild/Microsoft/Silverlight/v3.0
92K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/xbuild/Microsoft/Silverlight
8.0K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/xbuild/Microsoft/Portable/v4.0
12K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/xbuild/Microsoft/Portable
8.0K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/xbuild/Microsoft/VisualStudio/v9.0/WebApplications
12K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/xbuild/Microsoft/VisualStudio/v9.0
16K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/xbuild/Microsoft/VisualStudio
124K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/xbuild/Microsoft
128K    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono/xbuild
102M    ./.wine/drive_c/windows/mono/mono-2.0/lib/mono
102M    ./.wine/drive_c/windows/mono/mono-2.0/lib
128M    ./.wine/drive_c/windows/mono/mono-2.0
128M    ./.wine/drive_c/windows/mono
8.0K    ./.wine/drive_c/windows/winsxs/x86_microsoft.windows.gdiplus_6595b64144ccf1df_1.0.6000.16386_none_deadbeef
136K    ./.wine/drive_c/windows/winsxs/x86_microsoft-windows-msxml30_31bf3856ad364e35_6.0.6000.16386_none_deadbeef
112K    ./.wine/drive_c/windows/winsxs/x86_microsoft-windows-msxml60_31bf3856ad364e35_6.0.6000.16386_none_deadbeef
8.0K    ./.wine/drive_c/windows/winsxs/x86_microsoft.vc90.crt_1fc8b3b9a1e18e3b_9.0.30729.6161_none_deadbeef
48K    ./.wine/drive_c/windows/winsxs/manifests
16K    ./.wine/drive_c/windows/winsxs/Policies/x86_policy.8.0.Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_x-ww_77c24773
20K    ./.wine/drive_c/windows/winsxs/Policies
180K    ./.wine/drive_c/windows/winsxs/x86_microsoft.windows.common-controls_6595b64144ccf1df_6.0.2600.2982_none_deadbeef
8.0K    ./.wine/drive_c/windows/winsxs/x86_microsoft.vc80.crt_1fc8b3b9a1e18e3b_8.0.50727.4053_none_deadbeef
1.6M    ./.wine/drive_c/windows/winsxs/x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.6195_x-ww_44262b86
108K    ./.wine/drive_c/windows/winsxs/x86_microsoft.msxml2_6bd6b9abf345378f_4.1.0.0_none_deadbeef
8.0K    ./.wine/drive_c/windows/winsxs/x86_microsoft.vc90.crt_1fc8b3b9a1e18e3b_9.0.30729.4148_none_deadbeef
2.3M    ./.wine/drive_c/windows/winsxs
4.0K    ./.wine/drive_c/windows/logs
4.0K    ./.wine/drive_c/windows/temp
4.0K    ./.wine/drive_c/windows/help
92K    ./.wine/drive_c/windows/command
60K    ./.wine/drive_c/windows/Installer/{789A5B64-9DD9-4BA5-915A-F0FC0A1B7BFE}
8.0K    ./.wine/drive_c/windows/Installer/{46F044A5-CE8B-4196-984E-5BD6525E361D}
100K    ./.wine/drive_c/windows/Installer/{79155F2B-9895-49D7-8612-D92580E0DE5B}
288K    ./.wine/drive_c/windows/Installer/{0592EF96-69D8-4E4B-9CC9-88F58EA86F01}
460K    ./.wine/drive_c/windows/Installer/{C197BC08-3D82-4651-8886-E68C21578A38}
183M    ./.wine/drive_c/windows/Installer
36K    ./.wine/drive_c/windows/Microsoft.NET/Framework/v2.0.50727/CONFIG
52K    ./.wine/drive_c/windows/Microsoft.NET/Framework/v2.0.50727
8.0K    ./.wine/drive_c/windows/Microsoft.NET/Framework/v3.0/windows communication foundation
8.0K    ./.wine/drive_c/windows/Microsoft.NET/Framework/v3.0/wpf
20K    ./.wine/drive_c/windows/Microsoft.NET/Framework/v3.0
36K    ./.wine/drive_c/windows/Microsoft.NET/Framework/v1.1.4322/CONFIG
56K    ./.wine/drive_c/windows/Microsoft.NET/Framework/v1.1.4322
40K    ./.wine/drive_c/windows/Microsoft.NET/Framework/v4.0.30319/CONFIG
52K    ./.wine/drive_c/windows/Microsoft.NET/Framework/v4.0.30319
184K    ./.wine/drive_c/windows/Microsoft.NET/Framework
188K    ./.wine/drive_c/windows/Microsoft.NET
24K    ./.wine/drive_c/windows/system32/wbem
8.0K    ./.wine/drive_c/windows/system32/spool/drivers/color
24K    ./.wine/drive_c/windows/system32/spool/drivers/win40/0
28K    ./.wine/drive_c/windows/system32/spool/drivers/win40
24K    ./.wine/drive_c/windows/system32/spool/drivers/w32x86/3
28K    ./.wine/drive_c/windows/system32/spool/drivers/w32x86
68K    ./.wine/drive_c/windows/system32/spool/drivers
4.0K    ./.wine/drive_c/windows/system32/spool/printers
76K    ./.wine/drive_c/windows/system32/spool
8.0K    ./.wine/drive_c/windows/system32/drivers
32K    ./.wine/drive_c/windows/system32/catroot/{f750e6c3-38ee-11d1-85e5-00c04fc295ee}
36K    ./.wine/drive_c/windows/system32/catroot
1.5M    ./.wine/drive_c/windows/system32/DRVSTORE/netaapl_A04DD80CB60ABF2DD73AAE417B0A34E10C321346
6.0M    ./.wine/drive_c/windows/system32/DRVSTORE/usbaapl_2FC536FD6A680CFDA9FB2D577DA31924B96AB666
32K    ./.wine/drive_c/windows/system32/DRVSTORE/GEARAspiWD_1E13C24EB2F28CB6915317F7F17F180ECAA0DB1E/x86
48K    ./.wine/drive_c/windows/system32/DRVSTORE/GEARAspiWD_1E13C24EB2F28CB6915317F7F17F180ECAA0DB1E
7.4M    ./.wine/drive_c/windows/system32/DRVSTORE
4.0K    ./.wine/drive_c/windows/system32/mui
620K    ./.wine/drive_c/windows/system32/gecko/2.21/wine_gecko/dictionaries
44M    ./.wine/drive_c/windows/system32/gecko/2.21/wine_gecko
44M    ./.wine/drive_c/windows/system32/gecko/2.21
8.0K    ./.wine/drive_c/windows/system32/gecko/plugin
620K    ./.wine/drive_c/windows/system32/gecko/1.4/wine_gecko/dictionaries
2.0M    ./.wine/drive_c/windows/system32/gecko/1.4/wine_gecko/hyphenation
4.0K    ./.wine/drive_c/windows/system32/gecko/1.4/wine_gecko/components
31M    ./.wine/drive_c/windows/system32/gecko/1.4/wine_gecko
31M    ./.wine/drive_c/windows/system32/gecko/1.4
74M    ./.wine/drive_c/windows/system32/gecko
98M    ./.wine/drive_c/windows/system32
410M    ./.wine/drive_c/windows
825M    ./.wine/drive_c
4.0K    ./.wine/dosdevices
828M    ./.wine

```

```


Model: ATA ST3250820AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  8192MB  8191MB  primary   ext4            boot
 3      8193MB  246GB   238GB   primary   ext4
 2      246GB   250GB   4096MB  extended
 5      246GB   250GB   4096MB  logical   linux-swap(v1)


```

---

### Post by Impavidus on 2015-04-05
I'm sorry, I meant```
df -h
```instead of du -h. Fixing it above.

It seams there is only a single drive present, with no Windows.

---

### Post by wolfie52 on 2015-04-06
impavidus: 

Here is the response to your amended message and terminal input.

```

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       7.4G  5.9G  1.2G  84% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            491M  4.0K  491M   1% /dev
tmpfs           101M  1.6M   99M   2% /run
none            5.0M     0  5.0M   0% /run/lock
none            501M   19M  483M   4% /run/shm
none            100M   36K  100M   1% /run/user
/dev/sda3       218G  5.1G  202G   3% /home

```

Does this mean................?

Geoff

---

### Post by Kenneth_Benson on 2015-04-06
Could you run top and see what programs/daemons are running and approximate percentages? If what I suspect is true, wine is running in the background. If you are not using any windows programs, I would dump wine.

---

### Post by wolfie52 on 2015-04-07
Hello Kenneth. I don't run any windows programme so could dump wine. Also, Impavidus, I was told when I bought the machine that windows had not been taken off but sits aside Ubuntu though non functional. However I respect your view. 

I guess taking Wine off will help. I loaded it to try to run BTSport but to no real satisfactory outcome.

Again I appreciate your help and support

Geoff

---

### Post by Bucky Ball on 2015-04-07
Completely eradicating Wine from your install is a near impossibility in my experience. And there is NO Windows on that drive. I mentioned it way back on the first page. Win needs an NTFS partition. You don't have one. ;)

---

### Post by wolfie52 on 2015-04-07
OK thank you. I again appreciate your comments, though I feel scolded. 

Geoff

---

### Post by Bucky Ball on 2015-04-07
You shouldn't. ;)

---

### Post by wolfie52 on 2015-04-07
Thank you Bucky, I really appreciate that comment, it means a lot.


Geoff

---

### Post by Bucky Ball on 2015-04-07
All good. ;)

---

### Post by wolfie52 on 2015-05-02
Hello Dino99

You responded to a query of mine a little while ago, can I contact you again regarding this please?

Would really appreciate your help.

Geoff

---

### Post by wolfie52 on 2015-05-03
> **dino99 said:**
> i understand your system is slow ;) i'm also surprised you can still use it:

****
Number  Start   End     Size    Type      File system     Flags
 1      1049kB  8192MB  8191MB  primary   ext4            boot
 3      8193MB  246GB   238GB   primary   ext4
 2      246GB   250GB   4096MB  extended
 5      246GB   250GB   4096MB  logical   linux-swap(v1)
*****
that installation has been badly set (not what a genuine one looks like)
you need 3 partitions:
1- ext4 about 10000/12000MB for ubuntu installation (OS & apps)
2- a swap partition about 4000MB
3- ext4 /home partition for your data 

actually you seems sharing the first partition between OS/apps & your own data; which means that 8191MB is way too narrow, so the slowness as the system may waste its full time swaping.
if you does not care about vista then save your data on an exteral usb stick (or else) then do a fresh install from the mini.iso
boot from a usb/cd iso to format and install ubuntu.
 [http://cdimage.ubuntu.com/netboot/](http://cdimage.ubuntu.com/netboot/)


Hello Dino,

I realise you are busy but am really desperate to find a way forward whichever way that might be. I have loaded on my machine, GPartion but just need some guidance as to how I can now get to a place where I can resolve the crashing and slow running of my PC. I have two books, "The Linux Conmmand Line" and "Ubuntu Linux for non Geeks" and also looked at youtube for help but just cant get a grasp on what I actually need to do. Please are you able to point me in the right direction please. I really would appreciate.   Geoff

---

### Post by pmi2 on 2015-05-03
> **wolfie52 said:**
> ...find a way forward whichever way that might be...Do you want to try using GParted to increase the size of the partition where Ubuntu is installed?

You may first need to boot from a Live CD/DVD or USB stick, and only then run GParted.  I am sure the books will help a bit, but you can also look up how to make and boot from a Live CD, and then how to use GParted to change or move partitions on your disk, either here on this site, or just by doing a search.

For example:

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

and 

[http://howtoubuntu.org/how-to-resize-partitions-with-the-ubuntu-or-gparted-live-cd](http://howtoubuntu.org/how-to-resize-partitions-with-the-ubuntu-or-gparted-live-cd)

---

### Post by wolfie52 on 2015-05-03
Thank you pmi2 I will look up those two links. Appreciate the help

Geoff

---

### Post by wolfie52 on 2015-07-22
I must be a real dumb ass and perhaps this is the first time this type of request has ever been posted, but my problem still exists and I ask if any knowledgeable ubuntu user might be prepared to meet me to help resolve this face to face. i live in the west midlands. 

I look forward to hearing from any sympathetic and reasonably local ubuntuist!

geoff

---

### Post by howefield on 2015-07-22
Hi Geoff,

You might alleviate the issue by removing packages no longer required as well as the aforementioned wine if you haven't already done so.

```
sudo apt-get clean
```
```
sudo apt-get autoclean
```
```
sudo apt-get autoremove
```

Uninstall the wine application and then delete the hidden .wine folder in your /home folder.

That might buy you some time whilst you sort out the bigger issue of resizing the partition if that is what you want to do.

---

### Post by wolfie52 on 2015-07-23
Thank you Howefield, appreciate the help.

Geoff

---

### Post by Topsiho on 2015-07-23
+1 for howefield, I was about to give you the same advice :)

From the info that you gave, sda1, which contains the system files, is 84% full, which means that there is far too little room to move in. As a whale swimming in a cramped bath tub will not be able to come to speed.
Every time that you update the files are installed somewhere in your system partition, using up space. When the system partition is as small as yours, some day it will be filled, and the easiest way to get some space again is to remove all unnecessary, for already used, update files, using the methods that howefield mentioned.

And Bucky Ball is right saying there is no Windows installed, anyways not on sda. The only possibility is that you also have a second hard disk installed, but that doesn't seem to be the case.

Topsiho

---

### Post by wolfie52 on 2015-07-25
Again, thank you Topshio, I do really appreciate the help you all provide. Perhaps now I should focus on resolving my problem and its mnaybe easier than I think and I just need to bite the bullet, get my brain in gear and do it.

You have no idea how much I appreciate the help from you all...........sorry thats cheesy but what the heck!

Geoff

---

