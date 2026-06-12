---
title: "rkhunter: 58 warnings"
date: 2012-10-22
forum: General Help
---

### Post by slonchek on 2012-10-22
Hey!

I'm beginner in Ubuntu and I have some problems with Rootkit warnings. I've been using it a few days before, but I didnt have any warnings. Today I've checked again, updated, checked again and it was ok. A few hours later I've checked again and found this 58 warnings, but none possible rootkits. I've checked system with chkrootkit as well, but didnt found any infections.

This is rkhunter's report:
```
[21:02:01] Performing file properties checks
[21:02:01]   Checking for prerequisites                      [ OK ]
[21:02:04]   /usr/sbin/adduser                               [ OK ]
[21:02:04] Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
[21:02:04]   /usr/sbin/chroot                                [ Warning ]
[21:02:04] Warning: The file properties have changed:
[21:02:04]          File: /usr/sbin/chroot
[21:02:04]          Current hash: d1cd7bc7229c0b5771085f3c332da1385e443093
[21:02:04]          Stored hash : 7de0337f009a286a18d2653ebcb3af2aa8e73c74
[21:02:04]          Current inode: 4341142    Stored inode: 4333326
[21:02:04]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:04]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:04]   /usr/sbin/cron                                  [ OK ]
[21:02:05]   /usr/sbin/groupadd                              [ Warning ]
[21:02:05] Warning: The file properties have changed:
[21:02:05]          File: /usr/sbin/groupadd
[21:02:05]          Current hash: 880474304c42fd70dd691efe32ecbfb722e60805
[21:02:05]          Stored hash : de9c017539c00713fdbdbcee818a7efb0fc1b985
[21:02:05]          Current inode: 4327610    Stored inode: 4333370
[21:02:05]          Current file modification time: 1347488949 (13-Sep-2012 00:29:09)
[21:02:05]          Stored file modification time : 1333938724 (09-Apr-2012 04:32:04)
[21:02:05]   /usr/sbin/groupdel                              [ Warning ]
[21:02:05] Warning: The file properties have changed:
[21:02:05]          File: /usr/sbin/groupdel
[21:02:05]          Current hash: ddbd11b3e8b6ff73710aa224af39b82bdd6bbf6b
[21:02:05]          Stored hash : cb7e84dfe7dd56c688d355c0a14a5f3f536a8847
[21:02:05]          Current inode: 4327602    Stored inode: 4333371
[21:02:05]          Current file modification time: 1347488949 (13-Sep-2012 00:29:09)
[21:02:05]          Stored file modification time : 1333938724 (09-Apr-2012 04:32:04)
[21:02:05]   /usr/sbin/groupmod                              [ Warning ]
[21:02:05] Warning: The file properties have changed:
[21:02:05]          File: /usr/sbin/groupmod
[21:02:05]          Current hash: eb4fdfc0a38c8567c9b1385874cd1f60acdae094
[21:02:05]          Stored hash : 444a5d0e994b5b7b53e12d2cae94df7d97a5345f
[21:02:05]          Current inode: 4327605    Stored inode: 4333372
[21:02:05]          Current file modification time: 1347488949 (13-Sep-2012 00:29:09)
[21:02:05]          Stored file modification time : 1333938724 (09-Apr-2012 04:32:04)
[21:02:05]   /usr/sbin/grpck                                 [ Warning ]
[21:02:05] Warning: The file properties have changed:
[21:02:05]          File: /usr/sbin/grpck
[21:02:05]          Current hash: 00d541f79ff2475fc08b0de7655665901556dcd1
[21:02:05]          Stored hash : c887dc208d5fa018a79543cece0e8f9e9d825327
[21:02:05]          Current inode: 4326784    Stored inode: 4333373
[21:02:05]          Current file modification time: 1347488949 (13-Sep-2012 00:29:09)
[21:02:05]          Stored file modification time : 1333938724 (09-Apr-2012 04:32:04)
[21:02:06]   /usr/sbin/nologin                               [ Warning ]
[21:02:06] Warning: The file properties have changed:
[21:02:06]          File: /usr/sbin/nologin
[21:02:06]          Current hash: 8b00dca8879f2fd09a79bae8c9d74b8078925654
[21:02:06]          Stored hash : a0c9f7effec1d4060c75c9a5805e7089c00bf0c5
[21:02:06]          Current inode: 4325391    Stored inode: 4333427
[21:02:06]          Current file modification time: 1347488951 (13-Sep-2012 00:29:11)
[21:02:06]          Stored file modification time : 1333938726 (09-Apr-2012 04:32:06)
[21:02:06]   /usr/sbin/pwck                                  [ Warning ]
[21:02:06] Warning: The file properties have changed:
[21:02:06]          File: /usr/sbin/pwck
[21:02:06]          Current hash: e8b1bd6384ee46ac1582ce09ee9d179542183cdb
[21:02:06]          Stored hash : eb8fd45108118aadd67443b018204751a63f6083
[21:02:06]          Current inode: 4327604    Stored inode: 4333448
[21:02:06]          Current file modification time: 1347488949 (13-Sep-2012 00:29:09)
[21:02:06]          Stored file modification time : 1333938724 (09-Apr-2012 04:32:04)
[21:02:06]   /usr/sbin/rsyslogd                              [ OK ]
[21:02:07]   /usr/sbin/tcpd                                  [ OK ]
[21:02:07]   /usr/sbin/useradd                               [ Warning ]
[21:02:07] Warning: The file properties have changed:
[21:02:07]          File: /usr/sbin/useradd
[21:02:07]          Current hash: 8d9e2297473c6899f32b5dd670e1aaacc0a7550a
[21:02:07]          Stored hash : 2324043d20848109fbc637235c494ad375f0ca60
[21:02:07]          Current inode: 4327612    Stored inode: 4333513
[21:02:07]          Current file modification time: 1347488949 (13-Sep-2012 00:29:09)
[21:02:07]          Stored file modification time : 1333938724 (09-Apr-2012 04:32:04)
[21:02:07]   /usr/sbin/userdel                               [ Warning ]
[21:02:07] Warning: The file properties have changed:
[21:02:07]          File: /usr/sbin/userdel
[21:02:07]          Current hash: ea3019ed522dc32f1d329ff87523ffc1265ebd94
[21:02:07]          Stored hash : 8d54b21726b7de55470a693610c417d353c1fc42
[21:02:07]          Current inode: 4327609    Stored inode: 4333514
[21:02:07]          Current file modification time: 1347488949 (13-Sep-2012 00:29:09)
[21:02:07]          Stored file modification time : 1333938724 (09-Apr-2012 04:32:04)
[21:02:07]   /usr/sbin/usermod                               [ Warning ]
[21:02:07] Warning: The file properties have changed:
[21:02:07]          File: /usr/sbin/usermod
[21:02:07]          Current hash: 3bf5ac8c13b0d88f19ea7f0e89110a40fe23f4c8
[21:02:07]          Stored hash : d5203179672cb9ca34121dc57865d74c18b3e60d
[21:02:07]          Current inode: 4327614    Stored inode: 4333515
[21:02:07]          Current file modification time: 1347488949 (13-Sep-2012 00:29:09)
[21:02:07]          Stored file modification time : 1333938724 (09-Apr-2012 04:32:04)
[21:02:07]   /usr/sbin/vipw                                  [ Warning ]
[21:02:07] Warning: The file properties have changed:
[21:02:07]          File: /usr/sbin/vipw
[21:02:07]          Current hash: 02849e88d85e47c539d63aa5972f11fd7791d288
[21:02:07]          Stored hash : 286404a96f9b8d12040c3941f84711ba8ee9a273
[21:02:07]          Current inode: 4327607    Stored inode: 4333521
[21:02:07]          Current file modification time: 1347488949 (13-Sep-2012 00:29:09)
[21:02:07]          Stored file modification time : 1333938724 (09-Apr-2012 04:32:04)
[21:02:08]   /usr/bin/awk                                    [ OK ]
[21:02:08]   /usr/bin/basename                               [ Warning ]
[21:02:08] Warning: The file properties have changed:
[21:02:08]          File: /usr/bin/basename
[21:02:08]          Current hash: f7716a9c9f610152457db38cacb5e6d3bab4ec4d
[21:02:08]          Stored hash : 53087059bf09ef398a027e64831d7039a01ad1f5
[21:02:08]          Current inode: 4341154    Stored inode: 4325459
[21:02:08]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:08]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:08]   /usr/bin/chattr                                 [ OK ]
[21:02:08]   /usr/bin/cut                                    [ Warning ]
[21:02:08] Warning: The file properties have changed:
[21:02:08]          File: /usr/bin/cut
[21:02:08]          Current hash: 83360e34d7becfe9cafafbeddc8ef06fe59d80f6
[21:02:08]          Stored hash : a0010b3bc407564931e977e79d179b8316dc373b
[21:02:08]          Current inode: 4341149    Stored inode: 4325554
[21:02:08]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:08]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:08]   /usr/bin/diff                                   [ OK ]
[21:02:08]   /usr/bin/dirname                                [ Warning ]
[21:02:09] Warning: The file properties have changed:
[21:02:09]          File: /usr/bin/dirname
[21:02:09]          Current hash: bcce69d1120951327a05501a03bb483baafc8ae9
[21:02:09]          Stored hash : 835449d89300e652dc5580bc815f0bf609b4b2b3
[21:02:09]          Current inode: 4341184    Stored inode: 4325584
[21:02:09]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:09]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:09]   /usr/bin/dpkg                                   [ OK ]
[21:02:09]   /usr/bin/dpkg-query                             [ OK ]
[21:02:09]   /usr/bin/du                                     [ Warning ]
[21:02:09] Warning: The file properties have changed:
[21:02:09]          File: /usr/bin/du
[21:02:09]          Current hash: 940f486901405bae065622915e7f9c2388868a6a
[21:02:09]          Stored hash : 62f65e38ab921d5c252f9245d2187120857fbbce
[21:02:09]          Current inode: 4341211    Stored inode: 4325600
[21:02:09]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:09]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:09]   /usr/bin/env                                    [ Warning ]
[21:02:09] Warning: The file properties have changed:
[21:02:09]          File: /usr/bin/env
[21:02:09]          Current hash: 50d3eff8d490e2112281a26be51a607740c6376f
[21:02:09]          Stored hash : 54da14e742bc93dcd6e8366dcc768b27246e1ea2
[21:02:09]          Current inode: 4341161    Stored inode: 4325637
[21:02:09]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:09]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:09]   /usr/bin/file                                   [ OK ]
[21:02:09]   /usr/bin/find                                   [ OK ]
[21:02:09]   /usr/bin/GET                                    [ OK ]
[21:02:10]   /usr/bin/groups                                 [ Warning ]
[21:02:10] Warning: The file properties have changed:
[21:02:10]          File: /usr/bin/groups
[21:02:10]          Current hash: c2228a348eafba090e9c70c549acb5a8b0d87a56
[21:02:10]          Stored hash : 89a549acaa45400fdb10cf3667a77297bc779ab2
[21:02:10]          Current inode: 4341213    Stored inode: 4325790
[21:02:10]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:10]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:10] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
[21:02:10]   /usr/bin/head                                   [ Warning ]
[21:02:10] Warning: The file properties have changed:
[21:02:10]          File: /usr/bin/head
[21:02:10]          Current hash: 658415dc414f8f35c1b1d2db9378f7e5670b112f
[21:02:10]          Stored hash : 308c721477024ff91514fbbe1b3122792dce63fa
[21:02:10]          Current inode: 4341212    Stored inode: 4325862
[21:02:10]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:10]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:10]   /usr/bin/id                                     [ Warning ]
[21:02:10] Warning: The file properties have changed:
[21:02:10]          File: /usr/bin/id
[21:02:10]          Current hash: 34a8635b750d6e534772bc2167984fd9ea27238f
[21:02:10]          Stored hash : 4a4916e8ce9889615baeae68c402a328b760d521
[21:02:10]          Current inode: 4341172    Stored inode: 4325897
[21:02:10]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:10]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:10]   /usr/bin/killall                                [ OK ]
[21:02:10]   /usr/bin/last                                   [ OK ]
[21:02:10]   /usr/bin/lastlog                                [ Warning ]
[21:02:10] Warning: The file properties have changed:
[21:02:11]          File: /usr/bin/lastlog
[21:02:11]          Current hash: 26744886a3482331718d772b88d0a0a9b847bc78
[21:02:11]          Stored hash : c71eb2553681b79f6e1e8f8cfd680545f8c39de9
[21:02:11]          Current inode: 4325431    Stored inode: 4325960
[21:02:11]          Current file modification time: 1347488951 (13-Sep-2012 00:29:11)
[21:02:11]          Stored file modification time : 1333938726 (09-Apr-2012 04:32:06)
[21:02:11]   /usr/bin/ldd                                    [ Warning ]
[21:02:11] Warning: The file properties have changed:
[21:02:11]          File: /usr/bin/ldd
[21:02:11]          Current hash: e226c150d9f04a30f768b1cdadcc6d071044a238
[21:02:11]          Stored hash : 7e693353e3a8b0de66beca176bd840d024cd6a5f
[21:02:11]          Current inode: 4325651    Stored inode: 4326719
[21:02:11]          Current file modification time: 1349467568 (05-Oct-2012 22:06:08)
[21:02:11]          Stored file modification time : 1348912147 (29-Sep-2012 11:49:07)
[21:02:11] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
[21:02:11]   /usr/bin/less                                   [ OK ]
[21:02:11]   /usr/bin/locate                                 [ OK ]
[21:02:11]   /usr/bin/logger                                 [ OK ]
[21:02:11]   /usr/bin/lsattr                                 [ OK ]
[21:02:11]   /usr/bin/lsof                                   [ OK ]
[21:02:11]   /usr/bin/md5sum                                 [ Warning ]
[21:02:11] Warning: The file properties have changed:
[21:02:11]          File: /usr/bin/md5sum
[21:02:11]          Current hash: f83e9ff5ca9381764e48e6182d6da9fe04df8a05
[21:02:11]          Stored hash : a24f754ab57aae41a9e51377453f12bbab84941d
[21:02:11]          Current inode: 4341193    Stored inode: 4326057
[21:02:11]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:11]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:12]   /usr/bin/mlocate                                [ OK ]
[21:02:12]   /usr/bin/newgrp                                 [ Warning ]
[21:02:12] Warning: The file properties have changed:
[21:02:12]          File: /usr/bin/newgrp
[21:02:12]          Current hash: a1ad75bc512e3a05e946507c10ec006e0cca22ab
[21:02:12]          Stored hash : 6939fec8e0e35e197c1e9fabb0b8421e95af476c
[21:02:12]          Current inode: 4325458    Stored inode: 4326118
[21:02:12]          Current file modification time: 1347488951 (13-Sep-2012 00:29:11)
[21:02:12]          Stored file modification time : 1333938726 (09-Apr-2012 04:32:06)
[21:02:12]   /usr/bin/passwd                                 [ Warning ]
[21:02:12] Warning: The file properties have changed:
[21:02:12]          File: /usr/bin/passwd
[21:02:12]          Current hash: 0b77ef7d59230b825d38759c78f28371c4f2428c
[21:02:12]          Stored hash : 52c14f88ffe3f7d7269363707685cd7233d8ddef
[21:02:12]          Current inode: 4327616    Stored inode: 4326167
[21:02:12]          Current file modification time: 1347488949 (13-Sep-2012 00:29:09)
[21:02:12]          Stored file modification time : 1333938724 (09-Apr-2012 04:32:04)
[21:02:12]   /usr/bin/perl                                   [ OK ]
[21:02:12]   /usr/bin/pgrep                                  [ OK ]
[21:02:12]   /usr/bin/pstree                                 [ OK ]
[21:02:12]   /usr/bin/rkhunter                               [ OK ]
[21:02:13]   /usr/bin/runcon                                 [ Warning ]
[21:02:13] Warning: The file properties have changed:
[21:02:13]          File: /usr/bin/runcon
[21:02:13]          Current hash: d0cb24d573a66ac9c83b6b9a305e6919c021098c
[21:02:13]          Stored hash : 211a353e19cdd0f1e6842fa3202cde27f5c8d641
[21:02:13]          Current inode: 4341187    Stored inode: 4326328
[21:02:13]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:13]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:13]   /usr/bin/sha1sum                                [ Warning ]
[21:02:13] Warning: The file properties have changed:
[21:02:13]          File: /usr/bin/sha1sum
[21:02:13]          Current hash: ca65318feec16ab541ea3d75dee4270fddcf817e
[21:02:13]          Stored hash : 0340802bbc0caa06ccab25e54155af34cce9d7c7
[21:02:13]          Current inode: 4341201    Stored inode: 4326365
[21:02:13]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:13]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:13]   /usr/bin/sha224sum                              [ Warning ]
[21:02:13] Warning: The file properties have changed:
[21:02:13]          File: /usr/bin/sha224sum
[21:02:13]          Current hash: e6ac98619869e1aa2772e2e0605b129f42471672
[21:02:13]          Stored hash : 5acd5168cd46d12b98f6ce210e4d6dcf6a333cd1
[21:02:13]          Current inode: 4341199    Stored inode: 4326366
[21:02:13]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:13]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:13]   /usr/bin/sha256sum                              [ Warning ]
[21:02:13] Warning: The file properties have changed:
[21:02:13]          File: /usr/bin/sha256sum
[21:02:13]          Current hash: 722a69975299224766a87e77022d26ba4fe564c8
[21:02:13]          Stored hash : a51088e97cd4284ce9f4e224bbd0ffedba42e673
[21:02:13]          Current inode: 4341200    Stored inode: 4326367
[21:02:13]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:13]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:13]   /usr/bin/sha384sum                              [ Warning ]
[21:02:13] Warning: The file properties have changed:
[21:02:13]          File: /usr/bin/sha384sum
[21:02:13]          Current hash: fd0da9f1487cee2f33b0a23cf7243431651ffc40
[21:02:14]          Stored hash : a577b494cf2cd70a90f47227002ea07db12008cb
[21:02:14]          Current inode: 4341197    Stored inode: 4326368
[21:02:14]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:14]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:14]   /usr/bin/sha512sum                              [ Warning ]
[21:02:14] Warning: The file properties have changed:
[21:02:14]          File: /usr/bin/sha512sum
[21:02:14]          Current hash: 14ef345a9e89987b8c4d914fd669d8ba669470b7
[21:02:14]          Stored hash : 016152e8c34d463b026bf82302a41189631abb6b
[21:02:14]          Current inode: 4341204    Stored inode: 4326369
[21:02:14]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:14]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:14]   /usr/bin/size                                   [ OK ]
[21:02:14]   /usr/bin/sort                                   [ Warning ]
[21:02:14] Warning: The file properties have changed:
[21:02:14]          File: /usr/bin/sort
[21:02:14]          Current hash: d919ff6a7c50759ad97abbceca592624d8668692
[21:02:14]          Stored hash : 701dcba1db11b2b4a773be4ee480c0f76f0b38cc
[21:02:14]          Current inode: 4341183    Stored inode: 4326400
[21:02:14]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:14]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:14]   /usr/bin/stat                                   [ Warning ]
[21:02:14] Warning: The file properties have changed:
[21:02:14]          File: /usr/bin/stat
[21:02:14]          Current hash: 9d108d7d1888684b6f18e8b994599aef806c99a0
[21:02:14]          Stored hash : 08837463d2c5382c42c761af0cc0de1b0aae425a
[21:02:14]          Current inode: 4341194    Stored inode: 4326422
[21:02:14]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:14]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:14]   /usr/bin/strace                                 [ OK ]
[21:02:14]   /usr/bin/strings                                [ OK ]
[21:02:15]   /usr/bin/sudo                                   [ OK ]
[21:02:15]   /usr/bin/tail                                   [ Warning ]
[21:02:15] Warning: The file properties have changed:
[21:02:15]          File: /usr/bin/tail
[21:02:15]          Current hash: 2c3b9c159d67ab5711cd9f982189174a9a1b299e
[21:02:15]          Stored hash : 6e98afbb598b9f6b5c9fb42896f118cdf5c3772d
[21:02:15]          Current inode: 4341167    Stored inode: 4326440
[21:02:15]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:15]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:15]   /usr/bin/test                                   [ Warning ]
[21:02:15] Warning: The file properties have changed:
[21:02:15]          File: /usr/bin/test
[21:02:15]          Current hash: 356bbd7f1071cb5e4ac52aa5b98a2ffd9a680387
[21:02:15]          Stored hash : 6befefa27055597b14a5cf77279baf6f88598029
[21:02:15]          Current inode: 4341162    Stored inode: 4326450
[21:02:15]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:15]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:15]   /usr/bin/top                                    [ OK ]
[21:02:15]   /usr/bin/touch                                  [ Warning ]
[21:02:15] Warning: The file properties have changed:
[21:02:15]          File: /usr/bin/touch
[21:02:15]          Current hash: 81a10179d68850e05dab82a11b7113e576ffe5aa
[21:02:15]          Stored hash : cb071621835604ef603704f5453348ee9bfd5a60
[21:02:15]          Current inode: 4341214    Stored inode: 4326466
[21:02:15]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:15]          Stored file modification time : 1349104354 (01-Oct-2012 17:12:34)
[21:02:15]   /usr/bin/tr                                     [ Warning ]
[21:02:15] Warning: The file properties have changed:
[21:02:15]          File: /usr/bin/tr
[21:02:15]          Current hash: 242e7a6e4423d810f89e307985b5a27461b6aeca
[21:02:15]          Stored hash : 26ad4e5e3d506841b93c57e7bd0ef7da3a32b6be
[21:02:15]          Current inode: 4341207    Stored inode: 4326468
[21:02:15]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:15]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:16]   /usr/bin/uniq                                   [ Warning ]
[21:02:16] Warning: The file properties have changed:
[21:02:16]          File: /usr/bin/uniq
[21:02:16]          Current hash: 3547e2df40740899cbaeb6ea8c4f03894b82406f
[21:02:16]          Stored hash : a7fb03a026cd945b86788e0f6c477032ccd34ef8
[21:02:16]          Current inode: 4341176    Stored inode: 4326504
[21:02:16]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:16]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:16]   /usr/bin/users                                  [ Warning ]
[21:02:16] Warning: The file properties have changed:
[21:02:16]          File: /usr/bin/users
[21:02:16]          Current hash: 0bbc098570b0a90802360c8ba33cadde4f703227
[21:02:16]          Stored hash : dd036e4ef7b3c1df9d7281871d7c42819e1f3441
[21:02:16]          Current inode: 4341178    Stored inode: 4326531
[21:02:16]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:16]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:16]   /usr/bin/vmstat                                 [ OK ]
[21:02:16]   /usr/bin/w                                      [ OK ]
[21:02:16]   /usr/bin/watch                                  [ OK ]
[21:02:16]   /usr/bin/wc                                     [ Warning ]
[21:02:16] Warning: The file properties have changed:
[21:02:16]          File: /usr/bin/wc
[21:02:16]          Current hash: 84d9c358442a55b4b408b995745a1f9d177c2888
[21:02:16]          Stored hash : e7e50359ffc65fb669fce11fd43c512d20b9ad38
[21:02:16]          Current inode: 4341190    Stored inode: 4326548
[21:02:16]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:16]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:17]   /usr/bin/wget                                   [ OK ]
[21:02:17]   /usr/bin/whatis                                 [ OK ]
[21:02:17]   /usr/bin/whereis                                [ OK ]
[21:02:17]   /usr/bin/which                                  [ OK ]
[21:02:17]   /usr/bin/who                                    [ Warning ]
[21:02:17] Warning: The file properties have changed:
[21:02:17]          File: /usr/bin/who
[21:02:17]          Current hash: 8f334855c3de471c7fd23c3a64f32367fa250c05
[21:02:17]          Stored hash : 66c5e98c0a4dbb416796721feadc354417bdadd2
[21:02:17]          Current inode: 4341195    Stored inode: 4326554
[21:02:17]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:17]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:17]   /usr/bin/whoami                                 [ Warning ]
[21:02:17] Warning: The file properties have changed:
[21:02:17]          File: /usr/bin/whoami
[21:02:17]          Current hash: a45849feb34edc41c51df1aa7197ba09660cd886
[21:02:17]          Stored hash : c9bcebdcf70c960e5e33a286467526c332522f34
[21:02:17]          Current inode: 4341205    Stored inode: 4326555
[21:02:17]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:17]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:17]   /usr/bin/unhide.rb                              [ Warning ]
[21:02:17] Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: Ruby script, ASCII text
[21:02:17]   /usr/bin/mawk                                   [ OK ]
[21:02:17]   /usr/bin/lwp-request                            [ OK ]
[21:02:18] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[21:02:18]   /usr/bin/w.procps                               [ OK ]
[21:02:18]   /sbin/depmod                                    [ OK ]
[21:02:18]   /sbin/fsck                                      [ OK ]
[21:02:18]   /sbin/ifconfig                                  [ OK ]
[21:02:18]   /sbin/ifdown                                    [ OK ]
[21:02:18]   /sbin/ifup                                      [ OK ]
[21:02:18]   /sbin/init                                      [ OK ]
[21:02:19]   /sbin/insmod                                    [ OK ]
[21:02:19]   /sbin/ip                                        [ OK ]
[21:02:19]   /sbin/lsmod                                     [ OK ]
[21:02:19]   /sbin/modinfo                                   [ OK ]
[21:02:19]   /sbin/modprobe                                  [ OK ]
[21:02:19]   /sbin/rmmod                                     [ OK ]
[21:02:19]   /sbin/route                                     [ OK ]
[21:02:19]   /sbin/runlevel                                  [ OK ]
[21:02:20]   /sbin/sulogin                                   [ OK ]
[21:02:20]   /sbin/sysctl                                    [ OK ]
[21:02:20]   /bin/bash                                       [ OK ]
[21:02:20]   /bin/cat                                        [ Warning ]
[21:02:20] Warning: The file properties have changed:
[21:02:20]          File: /bin/cat
[21:02:20]          Current hash: 082a4a918aeb5d071cc4c3c0aa2963a8a4c08db5
[21:02:20]          Stored hash : e906615fca6df5b87baa76d7edc0a29159f0325f
[21:02:20]          Current inode: 131253    Stored inode: 131091
[21:02:20]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:20]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:21]   /bin/chmod                                      [ Warning ]
[21:02:21] Warning: The file properties have changed:
[21:02:21]          File: /bin/chmod
[21:02:21]          Current hash: 59b00623b55d3af4141ca5877640e6583cbccd23
[21:02:21]          Stored hash : 8bbd40048c98c9960bbe15c2a43405a6889ed0c9
[21:02:21]          Current inode: 131171    Stored inode: 131095
[21:02:21]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:21]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:21]   /bin/chown                                      [ Warning ]
[21:02:21] Warning: The file properties have changed:
[21:02:21]          File: /bin/chown
[21:02:21]          Current hash: 025775eab00690c3e31ce00260e4f86699213f67
[21:02:21]          Stored hash : 52cf4c2cbc30c5696e7fe754005300ab1e0c443a
[21:02:21]          Current inode: 131235    Stored inode: 131096
[21:02:21]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:21]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:21]   /bin/cp                                         [ Warning ]
[21:02:21] Warning: The file properties have changed:
[21:02:21]          File: /bin/cp
[21:02:21]          Current hash: 457961d56a959b95e88154ffc9c7fbeb3ba6b0f2
[21:02:21]          Stored hash : a0e4a7e22e13eb4bb11ee4475bf1646f36967e22
[21:02:21]          Current inode: 131172    Stored inode: 131098
[21:02:21]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:21]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:21]   /bin/date                                       [ Warning ]
[21:02:21] Warning: The file properties have changed:
[21:02:21]          File: /bin/date
[21:02:21]          Current hash: eefca61100bba27bbdde5fcc81f284e0aa4af054
[21:02:21]          Stored hash : 65e244abe4808af0dad954615422c2e066336234
[21:02:21]          Current inode: 131178    Stored inode: 131101
[21:02:21]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:21]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:21]   /bin/df                                         [ Warning ]
[21:02:21] Warning: The file properties have changed:
[21:02:22]          File: /bin/df
[21:02:22]          Current hash: a7a43406cc7b7d5c820547f30b50c010c5492b8b
[21:02:22]          Stored hash : 86d059ded5ac0756fdeaa35bb2ef48635d372aaa
[21:02:22]          Current inode: 131224    Stored inode: 131107
[21:02:22]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:22]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:22]   /bin/dmesg                                      [ OK ]
[21:02:22]   /bin/echo                                       [ Warning ]
[21:02:22] Warning: The file properties have changed:
[21:02:22]          File: /bin/echo
[21:02:22]          Current hash: d2cb44bc7d6a8fc4fd53247e39de705362c5dd6f
[21:02:22]          Stored hash : 8431e220bfd1f6c44a201a734b09743b17f5b163
[21:02:22]          Current inode: 131238    Stored inode: 131113
[21:02:22]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:22]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:22]   /bin/ed                                         [ OK ]
[21:02:22]   /bin/egrep                                      [ OK ]
[21:02:22] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[21:02:22]   /bin/fgrep                                      [ OK ]
[21:02:22] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
[21:02:22]   /bin/fuser                                      [ OK ]
[21:02:22]   /bin/grep                                       [ OK ]
[21:02:23]   /bin/ip                                         [ OK ]
[21:02:23]   /bin/kill                                       [ OK ]
[21:02:23]   /bin/less                                       [ OK ]
[21:02:23]   /bin/login                                      [ Warning ]
[21:02:23] Warning: The file properties have changed:
[21:02:23]          File: /bin/login
[21:02:23]          Current hash: a06b47d02d9e327fede7f1de5aafdfe1e2d507d6
[21:02:23]          Stored hash : 7cb604055d991dc05d045ccb72a747437843c8bd
[21:02:23]          Current inode: 131095    Stored inode: 131146
[21:02:23]          Current file modification time: 1347488951 (13-Sep-2012 00:29:11)
[21:02:23]          Stored file modification time : 1333938726 (09-Apr-2012 04:32:06)
[21:02:23]   /bin/ls                                         [ Warning ]
[21:02:23] Warning: The file properties have changed:
[21:02:23]          File: /bin/ls
[21:02:23]          Current hash: 86603190e1fa93af608bbcd96e658118b6a5391f
[21:02:23]          Stored hash : 8800fee57584ed1c44b638225c2f1eec818a27c2
[21:02:23]          Current inode: 131173    Stored inode: 131148
[21:02:23]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:23]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:23]   /bin/lsmod                                      [ OK ]
[21:02:23]   /bin/mktemp                                     [ Warning ]
[21:02:23] Warning: The file properties have changed:
[21:02:23]          File: /bin/mktemp
[21:02:23]          Current hash: 6627f49741e725970d04effd6c11b2142ff89027
[21:02:24]          Stored hash : 6f254da61961fcb54076ab0692db4782d90b9b37
[21:02:24]          Current inode: 131183    Stored inode: 131154
[21:02:24]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:24]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:24]   /bin/more                                       [ OK ]
[21:02:24]   /bin/mount                                      [ OK ]
[21:02:24]   /bin/mv                                         [ Warning ]
[21:02:24] Warning: The file properties have changed:
[21:02:24]          File: /bin/mv
[21:02:24]          Current hash: 87db8e4429ec5341d5ab278e4c193e224a92e9d5
[21:02:24]          Stored hash : 3c7e7e951ed27a510eec15d08071bad4d3ec82d4
[21:02:24]          Current inode: 131174    Stored inode: 131160
[21:02:24]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:24]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:24]   /bin/netstat                                    [ OK ]
[21:02:24]   /bin/ps                                         [ OK ]
[21:02:24]   /bin/pwd                                        [ Warning ]
[21:02:24] Warning: The file properties have changed:
[21:02:24]          File: /bin/pwd
[21:02:24]          Current hash: b2c65b677371ae1bad054209ca37c7241187dcba
[21:02:24]          Stored hash : c468d4992a1ae4bb50f620cb3053403f139137b7
[21:02:24]          Current inode: 131180    Stored inode: 131200
[21:02:25]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:25]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:25]   /bin/readlink                                   [ Warning ]
[21:02:25] Warning: The file properties have changed:
[21:02:25]          File: /bin/readlink
[21:02:25]          Current hash: 09240973b0b0f5061c809752c1857a8abc37b297
[21:02:25]          Stored hash : 377619f025aea2e4cad36f553c4801dc4842474e
[21:02:25]          Current inode: 131179    Stored inode: 131202
[21:02:25]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:25]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:25]   /bin/sed                                        [ OK ]
[21:02:25]   /bin/sh                                         [ OK ]
[21:02:25]   /bin/su                                         [ Warning ]
[21:02:25] Warning: The file properties have changed:
[21:02:25]          File: /bin/su
[21:02:25]          Current hash: 994d630b6f8e007ac5226f583f3808b8223cebde
[21:02:25]          Stored hash : 8eb46037e39f5c4931c195f25d23a4d62cb56236
[21:02:25]          Current inode: 131094    Stored inode: 131222
[21:02:26]          Current file modification time: 1347488951 (13-Sep-2012 00:29:11)
[21:02:26]          Stored file modification time : 1333938726 (09-Apr-2012 04:32:06)
[21:02:26]   /bin/touch                                      [ Warning ]
[21:02:26] Warning: The file properties have changed:
[21:02:26]          File: /bin/touch
[21:02:26]          Current hash: 81a10179d68850e05dab82a11b7113e576ffe5aa
[21:02:26]          Stored hash : cb071621835604ef603704f5453348ee9bfd5a60
[21:02:26]          Current inode: 131176    Stored inode: 131228
[21:02:26]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:26]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:26]   /bin/uname                                      [ Warning ]
[21:02:26] Warning: The file properties have changed:
[21:02:26]          File: /bin/uname
[21:02:26]          Current hash: fd668a5ef494985edd6e0346619c6232eadab71a
[21:02:26]          Stored hash : 9573190b2c6c3236fef40c147d3e03176a44451e
[21:02:26]          Current inode: 131212    Stored inode: 131232
[21:02:26]          Current file modification time: 1349148219 (02-Oct-2012 05:23:39)
[21:02:26]          Stored file modification time : 1333249752 (01-Apr-2012 05:09:12)
[21:02:26]   /bin/which                                      [ OK ]
[21:02:26] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
[21:02:27]   /bin/dash                                       [ OK ]
...
[21:04:07]   Checking for hidden files and directories       [ Warning ]
[21:04:07] Warning: Hidden directory found: /dev/.udev
[21:04:07] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'
[21:04:09]
[21:04:09] Info: Test 'apps' disabled at users request.
[21:04:09]
[21:04:09] System checks summary
[21:04:09] =====================
[21:04:09]
[21:04:09] File properties checks...
[21:04:09] Files checked: 132
[21:04:09] Suspect files: 58
[21:04:09]
[21:04:09] Rootkit checks...
[21:04:09] Rootkits checked : 242
[21:04:09] Possible rootkits: 0
[21:04:09]
[21:04:09] Applications checks...
[21:04:09] All checks skipped
[21:04:09]
[21:04:09] The system checks took: 2 minutes and 12 seconds
[21:04:09]
[21:04:09] Info: End date is Mon Oct 22 21:04:09 CEST 2012
```Can anybody please check this and tell me how to fix that?
Would deleting these files do a lot of damage? (plz dont get angry if it's a stupid question)

Also I've checked a system with ClamTk virus scanner, but didnt found any problems. That info might not be related to this problem, but still...

Please let me know if you need any additional data to solve the problem.

Thanks :)

---

### Post by Karlchen on 2012-10-22
Hello, slonchek,

have experienced this situation in the past few days on several systems. On my machines, it had been caused by the installation of software updates. Software updates do change the file properties (timestamps, filesizes, inodes etc) of executable files.
This has happend on your system as well. I bet that all of the warnings can be explained by recent software updates.
So the solution is **definitely not** deleting the modified files blindly.
Rather ```
sudo rkhunter --propupd
``` run after each  software update should prevent further panic attacks in the future.

Kind regards,
Karl

---

### Post by slonchek on 2012-10-23
Thank, Karl :)

---

