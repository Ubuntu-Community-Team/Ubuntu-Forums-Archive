---
title: "error: phablet-dev-bootstrap: error while trying to sync repository"
date: 2017-10-28
forum: General Help
---

### Post by 8t-narud on 2017-10-28
```
~$ phablet-dev-bootstrap phablet
INFO:phablet-dev-bootstrap:Changing to workdir /home/tiktikals/phablet
INFO:phablet-dev-bootstrap:Initializing repository
Get https://gerrit.googlesource.com/git-repo/clone.bundle
Get https://gerrit.googlesource.com/git-repo
remote: Finding sources: 100% (3/3)
remote: Total 3 (delta 1), reused 3 (delta 1)
Unpacking objects: 100% (3/3), done.
From https://gerrit.googlesource.com/git-repo
   788e962..c00d28b  master     -> origin/master

... A new repo command ( 1.23) is available.
... You should upgrade soon:

    cp /home/tiktikals/phablet/.repo/repo/repo /usr/bin/repo

Get https://code-review.phablet.ubuntu.com/p/aosp/platform/manifest.git
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:--  0:00:02 --:--:--     0
100  2399  100  2399    0     0    747      0  0:00:03  0:00:03 --:--:-- 1171k
Invalid clone.bundle file; ignoring.
remote: Counting objects: 1502, done        
remote: Finding sources: 100% (1498/1498)           
remote: Total 3112 (delta 489), reused 3057 (delta 489)          
Receiving objects: 100% (3112/3112), 2.04 MiB | 66.00 KiB/s, done.
Resolving deltas: 100% (881/881), done.
From https://code-review.phablet.ubuntu.com/p/aosp/platform/manifest
 * [new branch]      android-1.6_r1 -> origin/android-1.6_r1
 * [new branch]      android-1.6_r1.1 -> origin/android-1.6_r1.1
 * [new branch]      android-1.6_r1.2 -> origin/android-1.6_r1.2
 * [new branch]      android-1.6_r1.3 -> origin/android-1.6_r1.3
 * [new branch]      android-1.6_r1.4 -> origin/android-1.6_r1.4
 * [new branch]      android-1.6_r1.5 -> origin/android-1.6_r1.5
 * [new branch]      android-1.6_r2 -> origin/android-1.6_r2
 * [new branch]      android-2.0.1_r1 -> origin/android-2.0.1_r1
 * [new branch]      android-2.0_r1 -> origin/android-2.0_r1
 * [new branch]      android-2.1_r1 -> origin/android-2.1_r1
 * [new branch]      android-2.1_r2 -> origin/android-2.1_r2
 * [new branch]      android-2.1_r2.1p -> origin/android-2.1_r2.1p
 * [new branch]      android-2.1_r2.1p2 -> origin/android-2.1_r2.1p2
 * [new branch]      android-2.1_r2.1s -> origin/android-2.1_r2.1s
 * [new branch]      android-2.2.1_r1 -> origin/android-2.2.1_r1
 * [new branch]      android-2.2.1_r2 -> origin/android-2.2.1_r2
 * [new branch]      android-2.2.2_r1 -> origin/android-2.2.2_r1
 * [new branch]      android-2.2.3_r1 -> origin/android-2.2.3_r1
 * [new branch]      android-2.2.3_r2 -> origin/android-2.2.3_r2
 * [new branch]      android-2.2.3_r2.1 -> origin/android-2.2.3_r2.1
 * [new branch]      android-2.2_r1 -> origin/android-2.2_r1
 * [new branch]      android-2.2_r1.1 -> origin/android-2.2_r1.1
 * [new branch]      android-2.2_r1.2 -> origin/android-2.2_r1.2
 * [new branch]      android-2.2_r1.3 -> origin/android-2.2_r1.3
 * [new branch]      android-2.3.1_r1 -> origin/android-2.3.1_r1
 * [new branch]      android-2.3.2_r1 -> origin/android-2.3.2_r1
 * [new branch]      android-2.3.3_r1 -> origin/android-2.3.3_r1
 * [new branch]      android-2.3.3_r1.1 -> origin/android-2.3.3_r1.1
 * [new branch]      android-2.3.4_r0.9 -> origin/android-2.3.4_r0.9
 * [new branch]      android-2.3.4_r1 -> origin/android-2.3.4_r1
 * [new branch]      android-2.3.5_r1 -> origin/android-2.3.5_r1
 * [new branch]      android-2.3.6_r0.9 -> origin/android-2.3.6_r0.9
 * [new branch]      android-2.3.6_r1 -> origin/android-2.3.6_r1
 * [new branch]      android-2.3.7_r1 -> origin/android-2.3.7_r1
 * [new branch]      android-2.3_r1 -> origin/android-2.3_r1
 * [new branch]      android-4.0.1_r1 -> origin/android-4.0.1_r1
 * [new branch]      android-4.0.1_r1.1 -> origin/android-4.0.1_r1.1
 * [new branch]      android-4.0.1_r1.2 -> origin/android-4.0.1_r1.2
 * [new branch]      android-4.0.2_r1 -> origin/android-4.0.2_r1
 * [new branch]      android-4.0.3_r1 -> origin/android-4.0.3_r1
 * [new branch]      android-4.0.3_r1.1 -> origin/android-4.0.3_r1.1
 * [new branch]      android-4.0.4_r1 -> origin/android-4.0.4_r1
 * [new branch]      android-4.0.4_r1.1 -> origin/android-4.0.4_r1.1
 * [new branch]      android-4.0.4_r1.2 -> origin/android-4.0.4_r1.2
 * [new branch]      android-4.0.4_r2 -> origin/android-4.0.4_r2
 * [new branch]      android-4.0.4_r2.1 -> origin/android-4.0.4_r2.1
 * [new branch]      android-4.1.1_r1 -> origin/android-4.1.1_r1
 * [new branch]      android-4.1.1_r1.1 -> origin/android-4.1.1_r1.1
 * [new branch]      android-4.1.1_r2 -> origin/android-4.1.1_r2
 * [new branch]      android-4.1.1_r3 -> origin/android-4.1.1_r3
 * [new branch]      android-4.1.1_r4 -> origin/android-4.1.1_r4
 * [new branch]      android-4.1.1_r5 -> origin/android-4.1.1_r5
 * [new branch]      android-4.1.1_r6 -> origin/android-4.1.1_r6
 * [new branch]      android-4.1.1_r6.1 -> origin/android-4.1.1_r6.1
 * [new branch]      android-4.1.2_r1 -> origin/android-4.1.2_r1
 * [new branch]      android-4.1.2_r2 -> origin/android-4.1.2_r2
 * [new branch]      android-4.1.2_r2.1 -> origin/android-4.1.2_r2.1
 * [new branch]      android-4.2.1_r1 -> origin/android-4.2.1_r1
 * [new branch]      android-4.2.1_r1.1 -> origin/android-4.2.1_r1.1
 * [new branch]      android-4.2.1_r1.2 -> origin/android-4.2.1_r1.2
 * [new branch]      android-4.2.2_r1 -> origin/android-4.2.2_r1
 * [new branch]      android-4.2.2_r1.1 -> origin/android-4.2.2_r1.1
 * [new branch]      android-4.2.2_r1.2 -> origin/android-4.2.2_r1.2
 * [new branch]      android-4.2.2_r1.2b -> origin/android-4.2.2_r1.2b
 * [new branch]      android-4.2_r1 -> origin/android-4.2_r1
 * [new branch]      android-4.3.1_r1 -> origin/android-4.3.1_r1
 * [new branch]      android-4.3_r0.9 -> origin/android-4.3_r0.9
 * [new branch]      android-4.3_r0.9.1 -> origin/android-4.3_r0.9.1
 * [new branch]      android-4.3_r1 -> origin/android-4.3_r1
 * [new branch]      android-4.3_r1.1 -> origin/android-4.3_r1.1
 * [new branch]      android-4.3_r2 -> origin/android-4.3_r2
 * [new branch]      android-4.3_r2.1 -> origin/android-4.3_r2.1
 * [new branch]      android-4.3_r2.2 -> origin/android-4.3_r2.2
 * [new branch]      android-4.3_r2.2-cts -> origin/android-4.3_r2.2-cts
 * [new branch]      android-4.3_r2.3 -> origin/android-4.3_r2.3
 * [new branch]      android-4.3_r3 -> origin/android-4.3_r3
 * [new branch]      android-4.3_r3.1 -> origin/android-4.3_r3.1
 * [new branch]      android-4.4.1_r1 -> origin/android-4.4.1_r1
 * [new branch]      android-4.4.2_r1 -> origin/android-4.4.2_r1
 * [new branch]      android-4.4_r1 -> origin/android-4.4_r1
 * [new branch]      android-4.4_r1.1 -> origin/android-4.4_r1.1
 * [new branch]      android-4.4_r1.2 -> origin/android-4.4_r1.2
 * [new branch]      android-5.0.0_r1 -> origin/android-5.0.0_r1
 * [new branch]      android-5.0.0_r1.0.1 -> origin/android-5.0.0_r1.0.1
 * [new branch]      android-5.0.0_r2 -> origin/android-5.0.0_r2
 * [new branch]      android-5.0.0_r2.0.1 -> origin/android-5.0.0_r2.0.1
 * [new branch]      android-5.0.0_r3 -> origin/android-5.0.0_r3
 * [new branch]      android-5.0.0_r3.0.1 -> origin/android-5.0.0_r3.0.1
 * [new branch]      android-5.0.0_r4 -> origin/android-5.0.0_r4
 * [new branch]      android-5.0.0_r4.0.1 -> origin/android-5.0.0_r4.0.1
 * [new branch]      android-5.0.0_r5 -> origin/android-5.0.0_r5
 * [new branch]      android-5.0.0_r5.0.1 -> origin/android-5.0.0_r5.0.1
 * [new branch]      android-5.0.0_r5.1 -> origin/android-5.0.0_r5.1
 * [new branch]      android-5.0.0_r5.1.0.1 -> origin/android-5.0.0_r5.1.0.1
 * [new branch]      android-5.0.0_r6 -> origin/android-5.0.0_r6
 * [new branch]      android-5.0.0_r6.0.1 -> origin/android-5.0.0_r6.0.1
 * [new branch]      android-5.0.0_r7 -> origin/android-5.0.0_r7
 * [new branch]      android-5.0.0_r7.0.1 -> origin/android-5.0.0_r7.0.1
 * [new branch]      android-5.0.1_r1 -> origin/android-5.0.1_r1
 * [new branch]      android-5.0.2_r1 -> origin/android-5.0.2_r1
 * [new branch]      android-5.0.2_r3 -> origin/android-5.0.2_r3
 * [new branch]      android-5.1.0_r1 -> origin/android-5.1.0_r1
 * [new branch]      android-5.1.0_r3 -> origin/android-5.1.0_r3
 * [new branch]      android-5.1.0_r4 -> origin/android-5.1.0_r4
 * [new branch]      android-5.1.0_r5 -> origin/android-5.1.0_r5
 * [new branch]      android-5.1.1_r1 -> origin/android-5.1.1_r1
 * [new branch]      android-5.1.1_r10 -> origin/android-5.1.1_r10
 * [new branch]      android-5.1.1_r12 -> origin/android-5.1.1_r12
 * [new branch]      android-5.1.1_r13 -> origin/android-5.1.1_r13
 * [new branch]      android-5.1.1_r14 -> origin/android-5.1.1_r14
 * [new branch]      android-5.1.1_r15 -> origin/android-5.1.1_r15
 * [new branch]      android-5.1.1_r16 -> origin/android-5.1.1_r16
 * [new branch]      android-5.1.1_r17 -> origin/android-5.1.1_r17
 * [new branch]      android-5.1.1_r18 -> origin/android-5.1.1_r18
 * [new branch]      android-5.1.1_r19 -> origin/android-5.1.1_r19
 * [new branch]      android-5.1.1_r2 -> origin/android-5.1.1_r2
 * [new branch]      android-5.1.1_r20 -> origin/android-5.1.1_r20
 * [new branch]      android-5.1.1_r22 -> origin/android-5.1.1_r22
 * [new branch]      android-5.1.1_r23 -> origin/android-5.1.1_r23
 * [new branch]      android-5.1.1_r24 -> origin/android-5.1.1_r24
 * [new branch]      android-5.1.1_r25 -> origin/android-5.1.1_r25
 * [new branch]      android-5.1.1_r26 -> origin/android-5.1.1_r26
 * [new branch]      android-5.1.1_r28 -> origin/android-5.1.1_r28
 * [new branch]      android-5.1.1_r29 -> origin/android-5.1.1_r29
 * [new branch]      android-5.1.1_r3 -> origin/android-5.1.1_r3
 * [new branch]      android-5.1.1_r30 -> origin/android-5.1.1_r30
 * [new branch]      android-5.1.1_r33 -> origin/android-5.1.1_r33
 * [new branch]      android-5.1.1_r34 -> origin/android-5.1.1_r34
 * [new branch]      android-5.1.1_r35 -> origin/android-5.1.1_r35
 * [new branch]      android-5.1.1_r36 -> origin/android-5.1.1_r36
 * [new branch]      android-5.1.1_r37 -> origin/android-5.1.1_r37
 * [new branch]      android-5.1.1_r4 -> origin/android-5.1.1_r4
 * [new branch]      android-5.1.1_r5 -> origin/android-5.1.1_r5
 * [new branch]      android-5.1.1_r6 -> origin/android-5.1.1_r6
 * [new branch]      android-5.1.1_r7 -> origin/android-5.1.1_r7
 * [new branch]      android-5.1.1_r8 -> origin/android-5.1.1_r8
 * [new branch]      android-5.1.1_r9 -> origin/android-5.1.1_r9
 * [new branch]      android-6.0.0_r1 -> origin/android-6.0.0_r1
 * [new branch]      android-6.0.0_r11 -> origin/android-6.0.0_r11
 * [new branch]      android-6.0.0_r12 -> origin/android-6.0.0_r12
 * [new branch]      android-6.0.0_r13 -> origin/android-6.0.0_r13
 * [new branch]      android-6.0.0_r2 -> origin/android-6.0.0_r2
 * [new branch]      android-6.0.0_r23 -> origin/android-6.0.0_r23
 * [new branch]      android-6.0.0_r24 -> origin/android-6.0.0_r24
 * [new branch]      android-6.0.0_r25 -> origin/android-6.0.0_r25
 * [new branch]      android-6.0.0_r26 -> origin/android-6.0.0_r26
 * [new branch]      android-6.0.0_r3 -> origin/android-6.0.0_r3
 * [new branch]      android-6.0.0_r4 -> origin/android-6.0.0_r4
 * [new branch]      android-6.0.0_r41 -> origin/android-6.0.0_r41
 * [new branch]      android-6.0.0_r5 -> origin/android-6.0.0_r5
 * [new branch]      android-6.0.0_r6 -> origin/android-6.0.0_r6
 * [new branch]      android-6.0.0_r7 -> origin/android-6.0.0_r7
 * [new branch]      android-6.0.1_r1 -> origin/android-6.0.1_r1
 * [new branch]      android-6.0.1_r10 -> origin/android-6.0.1_r10
 * [new branch]      android-6.0.1_r11 -> origin/android-6.0.1_r11
 * [new branch]      android-6.0.1_r12 -> origin/android-6.0.1_r12
 * [new branch]      android-6.0.1_r13 -> origin/android-6.0.1_r13
 * [new branch]      android-6.0.1_r16 -> origin/android-6.0.1_r16
 * [new branch]      android-6.0.1_r17 -> origin/android-6.0.1_r17
 * [new branch]      android-6.0.1_r18 -> origin/android-6.0.1_r18
 * [new branch]      android-6.0.1_r20 -> origin/android-6.0.1_r20
 * [new branch]      android-6.0.1_r21 -> origin/android-6.0.1_r21
 * [new branch]      android-6.0.1_r22 -> origin/android-6.0.1_r22
 * [new branch]      android-6.0.1_r24 -> origin/android-6.0.1_r24
 * [new branch]      android-6.0.1_r3 -> origin/android-6.0.1_r3
 * [new branch]      android-6.0.1_r30 -> origin/android-6.0.1_r30
 * [new branch]      android-6.0.1_r31 -> origin/android-6.0.1_r31
 * [new branch]      android-6.0.1_r4 -> origin/android-6.0.1_r4
 * [new branch]      android-6.0.1_r5 -> origin/android-6.0.1_r5
 * [new branch]      android-6.0.1_r7 -> origin/android-6.0.1_r7
 * [new branch]      android-6.0.1_r8 -> origin/android-6.0.1_r8
 * [new branch]      android-6.0.1_r9 -> origin/android-6.0.1_r9
 * [new branch]      android-cts-2.2_r8 -> origin/android-cts-2.2_r8
 * [new branch]      android-cts-2.3_r10 -> origin/android-cts-2.3_r10
 * [new branch]      android-cts-2.3_r11 -> origin/android-cts-2.3_r11
 * [new branch]      android-cts-2.3_r12 -> origin/android-cts-2.3_r12
 * [new branch]      android-cts-4.0.3_r1 -> origin/android-cts-4.0.3_r1
 * [new branch]      android-cts-4.0.3_r2 -> origin/android-cts-4.0.3_r2
 * [new branch]      android-cts-4.0_r1 -> origin/android-cts-4.0_r1
 * [new branch]      android-cts-4.1_r1 -> origin/android-cts-4.1_r1
 * [new branch]      android-cts-4.1_r2 -> origin/android-cts-4.1_r2
 * [new branch]      android-cts-4.2_r2 -> origin/android-cts-4.2_r2
 * [new branch]      android-cts-verifier-4.0.3_r1 -> origin/android-cts-verifier-4.0.3_r1
 * [new branch]      android-cts-verifier-4.0_r1 -> origin/android-cts-verifier-4.0_r1
 * [new branch]      android-sdk-4.0.3-tools_r1 -> origin/android-sdk-4.0.3-tools_r1
 * [new branch]      android-sdk-4.0.3_r1 -> origin/android-sdk-4.0.3_r1
 * [new branch]      android-sdk-adt_r16.0.1 -> origin/android-sdk-adt_r16.0.1
 * [new branch]      android-sdk-adt_r20 -> origin/android-sdk-adt_r20
 * [new branch]      android-sdk-support_r11 -> origin/android-sdk-support_r11
 * [new branch]      default    -> origin/default
 * [new branch]      froyo      -> origin/froyo
 * [new branch]      gingerbread -> origin/gingerbread
 * [new branch]      gingerbread-release -> origin/gingerbread-release
 * [new branch]      ics-mr0    -> origin/ics-mr0
 * [new branch]      ics-mr1    -> origin/ics-mr1
 * [new branch]      ics-plus-aosp -> origin/ics-plus-aosp
 * [new branch]      idea133    -> origin/idea133
 * [new branch]      jb-dev     -> origin/jb-dev
 * [new branch]      jb-mr1-dev -> origin/jb-mr1-dev
 * [new branch]      jb-mr1-dev-plus-aosp -> origin/jb-mr1-dev-plus-aosp
 * [new branch]      jb-mr1.1-dev -> origin/jb-mr1.1-dev
 * [new branch]      jb-mr1.1-dev-plus-aosp -> origin/jb-mr1.1-dev-plus-aosp
 * [new branch]      jb-mr2-dev -> origin/jb-mr2-dev
 * [new branch]      jumper-stable -> origin/jumper-stable
 * [new branch]      kitkat-cts-dev -> origin/kitkat-cts-dev
 * [new branch]      kitkat-dev -> origin/kitkat-dev
 * [new branch]      master     -> origin/master
 * [new branch]      master-dalvik -> origin/master-dalvik
 * [new branch]      master-dalvik-host -> origin/master-dalvik-host
 * [new branch]      oneplusx_5.1.1_r5 -> origin/oneplusx_5.1.1_r5
 * [new branch]      personal/chihchun/phablet-6.0.0_r1 -> origin/personal/chihchun/phablet-6.0.0_r1
 * [new branch]      personal/chihchun/phablet-mirror -> origin/personal/chihchun/phablet-mirror
 * [new branch]      personal/w-ondra/mirror-manifest -> origin/personal/w-ondra/mirror-manifest
 * [new branch]      personal/w-ondra/phablet-5.0.2_r3 -> origin/personal/w-ondra/phablet-5.0.2_r3
 * [new branch]      personal/w-ondra/phablet-5.1.1_r36 -> origin/personal/w-ondra/phablet-5.1.1_r36
 * [new branch]      personal/w-ondra/phablet-5.1.1_r5 -> origin/personal/w-ondra/phablet-5.1.1_r5
 * [new branch]      personal/w-ondra/phablet-6.0.0_r1 -> origin/personal/w-ondra/phablet-6.0.0_r1
 * [new branch]      personal/w-ondra/phablet-6.0.1_r22 -> origin/personal/w-ondra/phablet-6.0.1_r22
 * [new branch]      personal/w-ondra/phablet-6.0.1_r42 -> origin/personal/w-ondra/phablet-6.0.1_r42
 * [new branch]      personal/w-ondra/xperia-5.1.1_r36 -> origin/personal/w-ondra/xperia-5.1.1_r36
 * [new branch]      personal/w-ondra/xperia-5.1.1_r5 -> origin/personal/w-ondra/xperia-5.1.1_r5
 * [new branch]      personal/w-ondra/xperia-6.0.1_r42 -> origin/personal/w-ondra/xperia-6.0.1_r42
 * [new branch]      personal/w-ondra/xperia_5.1.1_r5 -> origin/personal/w-ondra/xperia_5.1.1_r5
 * [new branch]      phablet-4.2.2_r1 -> origin/phablet-4.2.2_r1
 * [new branch]      phablet-4.3.1_r1 -> origin/phablet-4.3.1_r1
 * [new branch]      phablet-4.4.1_r1 -> origin/phablet-4.4.1_r1
 * [new branch]      phablet-4.4.2_r1 -> origin/phablet-4.4.2_r1
 * [new branch]      phablet-4.4_r1 -> origin/phablet-4.4_r1
 * [new branch]      phablet-5.1.1_r36 -> origin/phablet-5.1.1_r36
 * [new branch]      phablet-6.0.0_r1 -> origin/phablet-6.0.0_r1
 * [new branch]      phablet-6.x -> origin/phablet-6.x
 * [new branch]      tools_r20  -> origin/tools_r20
 * [new branch]      tools_r21  -> origin/tools_r21
 * [new branch]      tools_r21.1 -> origin/tools_r21.1
 * [new branch]      tools_r22  -> origin/tools_r22
 * [new branch]      tools_r22.2 -> origin/tools_r22.2
 * [new branch]      tradefed   -> origin/tradefed
 * [new branch]      xperia-5.1.1_r36 -> origin/xperia-5.1.1_r36
 * [new tag]         adt_23.0.3 -> adt_23.0.3
 * [new tag]         android-1.6_r1.1_ -> android-1.6_r1.1_
 * [new tag]         android-1.6_r1.2_ -> android-1.6_r1.2_
 * [new tag]         android-1.6_r1.3_ -> android-1.6_r1.3_
 * [new tag]         android-1.6_r1.4_ -> android-1.6_r1.4_
 * [new tag]         android-1.6_r1.5_ -> android-1.6_r1.5_
 * [new tag]         android-1.6_r1_ -> android-1.6_r1_
 * [new tag]         android-1.6_r2_ -> android-1.6_r2_
 * [new tag]         android-2.0.1_r1_ -> android-2.0.1_r1_
 * [new tag]         android-2.0_r1_ -> android-2.0_r1_
 * [new tag]         android-2.1_r1_ -> android-2.1_r1_
 * [new tag]         android-2.1_r2.1p2_ -> android-2.1_r2.1p2_
 * [new tag]         android-2.1_r2.1p_ -> android-2.1_r2.1p_
 * [new tag]         android-2.1_r2.1s_ -> android-2.1_r2.1s_
 * [new tag]         android-2.1_r2_ -> android-2.1_r2_
 * [new tag]         android-2.2.1_r1_ -> android-2.2.1_r1_
 * [new tag]         android-2.2.1_r2_ -> android-2.2.1_r2_
 * [new tag]         android-2.2.2_r1_ -> android-2.2.2_r1_
 * [new tag]         android-2.2.3_r1 -> android-2.2.3_r1
 * [new tag]         android-2.2.3_r2 -> android-2.2.3_r2
 * [new tag]         android-2.2.3_r2.1 -> android-2.2.3_r2.1
 * [new tag]         android-2.2_r1.1_ -> android-2.2_r1.1_
 * [new tag]         android-2.2_r1.2_ -> android-2.2_r1.2_
 * [new tag]         android-2.2_r1.3_ -> android-2.2_r1.3_
 * [new tag]         android-2.2_r1_ -> android-2.2_r1_
 * [new tag]         android-2.3.1_r1_ -> android-2.3.1_r1_
 * [new tag]         android-2.3.2_r1_ -> android-2.3.2_r1_
 * [new tag]         android-2.3.3_r1.1_ -> android-2.3.3_r1.1_
 * [new tag]         android-2.3.3_r1_ -> android-2.3.3_r1_
 * [new tag]         android-2.3.4_r0.9_ -> android-2.3.4_r0.9_
 * [new tag]         android-2.3.4_r1_ -> android-2.3.4_r1_
 * [new tag]         android-2.3.5_r1_ -> android-2.3.5_r1_
 * [new tag]         android-2.3.6_r0.9 -> android-2.3.6_r0.9
 * [new tag]         android-2.3.6_r1 -> android-2.3.6_r1
 * [new tag]         android-2.3.7_r1 -> android-2.3.7_r1
 * [new tag]         android-2.3_r1_ -> android-2.3_r1_
 * [new tag]         android-4.0.1_r1 -> android-4.0.1_r1
 * [new tag]         android-4.0.1_r1.1 -> android-4.0.1_r1.1
 * [new tag]         android-4.0.1_r1.2 -> android-4.0.1_r1.2
 * [new tag]         android-4.0.2_r1 -> android-4.0.2_r1
 * [new tag]         android-4.0.3_r1 -> android-4.0.3_r1
 * [new tag]         android-4.0.3_r1.1 -> android-4.0.3_r1.1
 * [new tag]         android-4.0.4_r1 -> android-4.0.4_r1
 * [new tag]         android-4.0.4_r1.1 -> android-4.0.4_r1.1
 * [new tag]         android-4.0.4_r1.2 -> android-4.0.4_r1.2
 * [new tag]         android-4.0.4_r2 -> android-4.0.4_r2
 * [new tag]         android-4.0.4_r2.1 -> android-4.0.4_r2.1
 * [new tag]         android-4.1.1_r1 -> android-4.1.1_r1
 * [new tag]         android-4.1.1_r1.1 -> android-4.1.1_r1.1
 * [new tag]         android-4.1.1_r1_ -> android-4.1.1_r1_
 * [new tag]         android-4.1.1_r2 -> android-4.1.1_r2
 * [new tag]         android-4.1.1_r3 -> android-4.1.1_r3
 * [new tag]         android-4.1.1_r4 -> android-4.1.1_r4
 * [new tag]         android-4.1.1_r5 -> android-4.1.1_r5
 * [new tag]         android-4.1.1_r6 -> android-4.1.1_r6
 * [new tag]         android-4.1.1_r6.1 -> android-4.1.1_r6.1
 * [new tag]         android-4.1.2_r1 -> android-4.1.2_r1
 * [new tag]         android-4.1.2_r2 -> android-4.1.2_r2
 * [new tag]         android-4.1.2_r2.1 -> android-4.1.2_r2.1
 * [new tag]         android-4.2.1_r1.1 -> android-4.2.1_r1.1
 * [new tag]         android-4.2.1_r1.2 -> android-4.2.1_r1.2
 * [new tag]         android-4.2.1_r1__ -> android-4.2.1_r1__
 * [new tag]         android-4.2.2_r1.1 -> android-4.2.2_r1.1
 * [new tag]         android-4.2.2_r1.2 -> android-4.2.2_r1.2
 * [new tag]         android-4.2.2_r1_ -> android-4.2.2_r1_
 * [new tag]         android-4.2_r1___ -> android-4.2_r1___
 * [new tag]         android-4.3.1_r1 -> android-4.3.1_r1
 * [new tag]         android-4.3_r0.9 -> android-4.3_r0.9
 * [new tag]         android-4.3_r0.9.1 -> android-4.3_r0.9.1
 * [new tag]         android-4.3_r0.9.1_ -> android-4.3_r0.9.1_
 * [new tag]         android-4.3_r0.9_ -> android-4.3_r0.9_
 * [new tag]         android-4.3_r1 -> android-4.3_r1
 * [new tag]         android-4.3_r1.1 -> android-4.3_r1.1
 * [new tag]         android-4.3_r1_ -> android-4.3_r1_
 * [new tag]         android-4.3_r2 -> android-4.3_r2
 * [new tag]         android-4.3_r2.1_ -> android-4.3_r2.1_
 * [new tag]         android-4.3_r2.1__ -> android-4.3_r2.1__
 * [new tag]         android-4.3_r2.2 -> android-4.3_r2.2
 * [new tag]         android-4.3_r2.3 -> android-4.3_r2.3
 * [new tag]         android-4.3_r2_ -> android-4.3_r2_
 * [new tag]         android-4.3_r3 -> android-4.3_r3
 * [new tag]         android-4.3_r3.1 -> android-4.3_r3.1
 * [new tag]         android-4.4.1_r1 -> android-4.4.1_r1
 * [new tag]         android-4.4.1_r1.0.1 -> android-4.4.1_r1.0.1
 * [new tag]         android-4.4.2_r1 -> android-4.4.2_r1
 * [new tag]         android-4.4.2_r1.0.1 -> android-4.4.2_r1.0.1
 * [new tag]         android-4.4.2_r2 -> android-4.4.2_r2
 * [new tag]         android-4.4.2_r2.0.1 -> android-4.4.2_r2.0.1
 * [new tag]         android-4.4.3_r1 -> android-4.4.3_r1
 * [new tag]         android-4.4.3_r1.0.1 -> android-4.4.3_r1.0.1
 * [new tag]         android-4.4.3_r1.1 -> android-4.4.3_r1.1
 * [new tag]         android-4.4.3_r1.1.0.1 -> android-4.4.3_r1.1.0.1
 * [new tag]         android-4.4.4_r1 -> android-4.4.4_r1
 * [new tag]         android-4.4.4_r1.0.1 -> android-4.4.4_r1.0.1
 * [new tag]         android-4.4.4_r2 -> android-4.4.4_r2
 * [new tag]         android-4.4.4_r2.0.1 -> android-4.4.4_r2.0.1
 * [new tag]         android-4.4_r1 -> android-4.4_r1
 * [new tag]         android-4.4_r1.0.1 -> android-4.4_r1.0.1
 * [new tag]         android-4.4_r1.1 -> android-4.4_r1.1
 * [new tag]         android-4.4_r1.1.0.1 -> android-4.4_r1.1.0.1
 * [new tag]         android-4.4_r1.2 -> android-4.4_r1.2
 * [new tag]         android-4.4_r1.2.0.1 -> android-4.4_r1.2.0.1
 * [new tag]         android-4.4w_r1 -> android-4.4w_r1
 * [new tag]         android-5.0.0_r1 -> android-5.0.0_r1
 * [new tag]         android-5.0.0_r1.0.1 -> android-5.0.0_r1.0.1
 * [new tag]         android-5.0.0_r2 -> android-5.0.0_r2
 * [new tag]         android-5.0.0_r2.0.1 -> android-5.0.0_r2.0.1
 * [new tag]         android-5.0.0_r3 -> android-5.0.0_r3
 * [new tag]         android-5.0.0_r3.0.1 -> android-5.0.0_r3.0.1
 * [new tag]         android-5.0.0_r4 -> android-5.0.0_r4
 * [new tag]         android-5.0.0_r4.0.1 -> android-5.0.0_r4.0.1
 * [new tag]         android-5.0.0_r5 -> android-5.0.0_r5
 * [new tag]         android-5.0.0_r5.0.1 -> android-5.0.0_r5.0.1
 * [new tag]         android-5.0.0_r5.1 -> android-5.0.0_r5.1
 * [new tag]         android-5.0.0_r5.1.0.1 -> android-5.0.0_r5.1.0.1
 * [new tag]         android-5.0.0_r6 -> android-5.0.0_r6
 * [new tag]         android-5.0.0_r6.0.1 -> android-5.0.0_r6.0.1
 * [new tag]         android-5.0.0_r7 -> android-5.0.0_r7
 * [new tag]         android-5.0.0_r7.0.1 -> android-5.0.0_r7.0.1
 * [new tag]         android-5.0.1_r1 -> android-5.0.1_r1
 * [new tag]         android-5.0.2_r1 -> android-5.0.2_r1
 * [new tag]         android-5.0.2_r3 -> android-5.0.2_r3
 * [new tag]         android-5.1.0_r1 -> android-5.1.0_r1
 * [new tag]         android-5.1.0_r3 -> android-5.1.0_r3
 * [new tag]         android-5.1.0_r4 -> android-5.1.0_r4
 * [new tag]         android-5.1.0_r5 -> android-5.1.0_r5
 * [new tag]         android-5.1.1_r1 -> android-5.1.1_r1
 * [new tag]         android-5.1.1_r10 -> android-5.1.1_r10
 * [new tag]         android-5.1.1_r12 -> android-5.1.1_r12
 * [new tag]         android-5.1.1_r13 -> android-5.1.1_r13
 * [new tag]         android-5.1.1_r14 -> android-5.1.1_r14
 * [new tag]         android-5.1.1_r15 -> android-5.1.1_r15
 * [new tag]         android-5.1.1_r16 -> android-5.1.1_r16
 * [new tag]         android-5.1.1_r17 -> android-5.1.1_r17
 * [new tag]         android-5.1.1_r18 -> android-5.1.1_r18
 * [new tag]         android-5.1.1_r19 -> android-5.1.1_r19
 * [new tag]         android-5.1.1_r2 -> android-5.1.1_r2
 * [new tag]         android-5.1.1_r20 -> android-5.1.1_r20
 * [new tag]         android-5.1.1_r22 -> android-5.1.1_r22
 * [new tag]         android-5.1.1_r23 -> android-5.1.1_r23
 * [new tag]         android-5.1.1_r24 -> android-5.1.1_r24
 * [new tag]         android-5.1.1_r25 -> android-5.1.1_r25
 * [new tag]         android-5.1.1_r26 -> android-5.1.1_r26
 * [new tag]         android-5.1.1_r28 -> android-5.1.1_r28
 * [new tag]         android-5.1.1_r29 -> android-5.1.1_r29
 * [new tag]         android-5.1.1_r3 -> android-5.1.1_r3
 * [new tag]         android-5.1.1_r30 -> android-5.1.1_r30
 * [new tag]         android-5.1.1_r33 -> android-5.1.1_r33
 * [new tag]         android-5.1.1_r34 -> android-5.1.1_r34
 * [new tag]         android-5.1.1_r35 -> android-5.1.1_r35
 * [new tag]         android-5.1.1_r36 -> android-5.1.1_r36
 * [new tag]         android-5.1.1_r37 -> android-5.1.1_r37
 * [new tag]         android-5.1.1_r4 -> android-5.1.1_r4
 * [new tag]         android-5.1.1_r5 -> android-5.1.1_r5
 * [new tag]         android-5.1.1_r6 -> android-5.1.1_r6
 * [new tag]         android-5.1.1_r7 -> android-5.1.1_r7
 * [new tag]         android-5.1.1_r8 -> android-5.1.1_r8
 * [new tag]         android-5.1.1_r9 -> android-5.1.1_r9
 * [new tag]         android-6.0.0_r1 -> android-6.0.0_r1
 * [new tag]         android-6.0.0_r11 -> android-6.0.0_r11
 * [new tag]         android-6.0.0_r12 -> android-6.0.0_r12
 * [new tag]         android-6.0.0_r13 -> android-6.0.0_r13
 * [new tag]         android-6.0.0_r2 -> android-6.0.0_r2
 * [new tag]         android-6.0.0_r23 -> android-6.0.0_r23
 * [new tag]         android-6.0.0_r24 -> android-6.0.0_r24
 * [new tag]         android-6.0.0_r25 -> android-6.0.0_r25
 * [new tag]         android-6.0.0_r26 -> android-6.0.0_r26
 * [new tag]         android-6.0.0_r3 -> android-6.0.0_r3
 * [new tag]         android-6.0.0_r4 -> android-6.0.0_r4
 * [new tag]         android-6.0.0_r41 -> android-6.0.0_r41
 * [new tag]         android-6.0.0_r5 -> android-6.0.0_r5
 * [new tag]         android-6.0.0_r6 -> android-6.0.0_r6
 * [new tag]         android-6.0.0_r7 -> android-6.0.0_r7
 * [new tag]         android-6.0.1_r1 -> android-6.0.1_r1
 * [new tag]         android-6.0.1_r10 -> android-6.0.1_r10
 * [new tag]         android-6.0.1_r11 -> android-6.0.1_r11
 * [new tag]         android-6.0.1_r12 -> android-6.0.1_r12
 * [new tag]         android-6.0.1_r13 -> android-6.0.1_r13
 * [new tag]         android-6.0.1_r16 -> android-6.0.1_r16
 * [new tag]         android-6.0.1_r17 -> android-6.0.1_r17
 * [new tag]         android-6.0.1_r18 -> android-6.0.1_r18
 * [new tag]         android-6.0.1_r20 -> android-6.0.1_r20
 * [new tag]         android-6.0.1_r21 -> android-6.0.1_r21
 * [new tag]         android-6.0.1_r22 -> android-6.0.1_r22
 * [new tag]         android-6.0.1_r24 -> android-6.0.1_r24
 * [new tag]         android-6.0.1_r3 -> android-6.0.1_r3
 * [new tag]         android-6.0.1_r30 -> android-6.0.1_r30
 * [new tag]         android-6.0.1_r31 -> android-6.0.1_r31
 * [new tag]         android-6.0.1_r4 -> android-6.0.1_r4
 * [new tag]         android-6.0.1_r5 -> android-6.0.1_r5
 * [new tag]         android-6.0.1_r7 -> android-6.0.1_r7
 * [new tag]         android-6.0.1_r8 -> android-6.0.1_r8
 * [new tag]         android-6.0.1_r9 -> android-6.0.1_r9
 * [new tag]         android-cts-2.2_r8 -> android-cts-2.2_r8
 * [new tag]         android-cts-2.3_r10 -> android-cts-2.3_r10
 * [new tag]         android-cts-2.3_r11 -> android-cts-2.3_r11
 * [new tag]         android-cts-2.3_r12 -> android-cts-2.3_r12
 * [new tag]         android-cts-4.0.3_r1 -> android-cts-4.0.3_r1
 * [new tag]         android-cts-4.0.3_r2 -> android-cts-4.0.3_r2
 * [new tag]         android-cts-4.0_r1 -> android-cts-4.0_r1
 * [new tag]         android-cts-4.1_r1 -> android-cts-4.1_r1
 * [new tag]         android-cts-4.1_r2 -> android-cts-4.1_r2
 * [new tag]         android-cts-4.1_r4 -> android-cts-4.1_r4
 * [new tag]         android-cts-4.2_r2 -> android-cts-4.2_r2
 * [new tag]         android-cts-4.4_r1 -> android-cts-4.4_r1
 * [new tag]         android-cts-4.4_r4 -> android-cts-4.4_r4
 * [new tag]         android-cts-5.0_r2 -> android-cts-5.0_r2
 * [new tag]         android-cts-5.0_r3 -> android-cts-5.0_r3
 * [new tag]         android-cts-5.0_r5 -> android-cts-5.0_r5
 * [new tag]         android-cts-5.1_r1 -> android-cts-5.1_r1
 * [new tag]         android-cts-5.1_r2 -> android-cts-5.1_r2
 * [new tag]         android-cts-5.1_r3 -> android-cts-5.1_r3
 * [new tag]         android-cts-5.1_r6 -> android-cts-5.1_r6
 * [new tag]         android-cts-6.0_r1 -> android-cts-6.0_r1
 * [new tag]         android-cts-6.0_r2 -> android-cts-6.0_r2
 * [new tag]         android-cts-6.0_r4 -> android-cts-6.0_r4
 * [new tag]         android-cts-6.0_r5 -> android-cts-6.0_r5
 * [new tag]         android-cts-verifier-4.0.3_r1 -> android-cts-verifier-4.0.3_r1
 * [new tag]         android-cts-verifier-4.0_r1 -> android-cts-verifier-4.0_r1
 * [new tag]         android-l-preview_r2 -> android-l-preview_r2
 * [new tag]         android-m-preview -> android-m-preview
 * [new tag]         android-m-preview-1 -> android-m-preview-1
 * [new tag]         android-m-preview-2 -> android-m-preview-2
 * [new tag]         android-n-preview-1 -> android-n-preview-1
 * [new tag]         android-sdk-4.0.3-tools_r1 -> android-sdk-4.0.3-tools_r1
 * [new tag]         android-sdk-4.0.3_r1 -> android-sdk-4.0.3_r1
 * [new tag]         android-sdk-4.4.2_r1 -> android-sdk-4.4.2_r1
 * [new tag]         android-sdk-4.4.2_r1.0.1 -> android-sdk-4.4.2_r1.0.1
 * [new tag]         android-sdk-adt_r16.0.1 -> android-sdk-adt_r16.0.1
 * [new tag]         android-sdk-adt_r20 -> android-sdk-adt_r20
 * [new tag]         android-sdk-support_r11 -> android-sdk-support_r11
 * [new tag]         android-tsl-2.0 -> android-tsl-2.0
 * [new tag]         android-tsl-3.0 -> android-tsl-3.0
 * [new tag]         android-tsl-4.0 -> android-tsl-4.0
 * [new tag]         android-wear-5.0.0_r1 -> android-wear-5.0.0_r1
 * [new tag]         android-wear-5.1.0_r1 -> android-wear-5.1.0_r1
 * [new tag]         android-wear-5.1.1_r1 -> android-wear-5.1.1_r1
 * [new tag]         gradle_0.12.2 -> gradle_0.12.2
 * [new tag]         gradle_0.13.0 -> gradle_0.13.0
 * [new tag]         gradle_0.13.1 -> gradle_0.13.1
 * [new tag]         gradle_0.13.2 -> gradle_0.13.2
 * [new tag]         gradle_0.13.3 -> gradle_0.13.3
 * [new tag]         gradle_0.14.0 -> gradle_0.14.0
 * [new tag]         gradle_0.14.1 -> gradle_0.14.1
 * [new tag]         gradle_0.14.2 -> gradle_0.14.2
 * [new tag]         gradle_0.14.3 -> gradle_0.14.3
 * [new tag]         gradle_0.14.4 -> gradle_0.14.4
 * [new tag]         gradle_1.0.0 -> gradle_1.0.0
 * [new tag]         gradle_1.0.0-rc1 -> gradle_1.0.0-rc1
 * [new tag]         gradle_1.0.0-rc2 -> gradle_1.0.0-rc2
 * [new tag]         gradle_1.0.0-rc3 -> gradle_1.0.0-rc3
 * [new tag]         gradle_1.0.0-rc4 -> gradle_1.0.0-rc4
 * [new tag]         gradle_1.0.1 -> gradle_1.0.1
 * [new tag]         gradle_1.1.0 -> gradle_1.1.0
 * [new tag]         gradle_1.1.0-rc1 -> gradle_1.1.0-rc1
 * [new tag]         gradle_1.1.0-rc2 -> gradle_1.1.0-rc2
 * [new tag]         gradle_1.1.0-rc3 -> gradle_1.1.0-rc3
 * [new tag]         gradle_1.1.1 -> gradle_1.1.1
 * [new tag]         gradle_1.1.2 -> gradle_1.1.2
 * [new tag]         gradle_1.1.3 -> gradle_1.1.3
 * [new tag]         gradle_1.2.0 -> gradle_1.2.0
 * [new tag]         gradle_1.2.0-beta1 -> gradle_1.2.0-beta1
 * [new tag]         gradle_1.2.0-rc1 -> gradle_1.2.0-rc1
 * [new tag]         gradle_1.2.1 -> gradle_1.2.1
 * [new tag]         gradle_1.2.2 -> gradle_1.2.2
 * [new tag]         gradle_1.2.3 -> gradle_1.2.3
 * [new tag]         gradle_1.3.0-beta1 -> gradle_1.3.0-beta1
 * [new tag]         gradle_1.3.0-beta2 -> gradle_1.3.0-beta2
 * [new tag]         gradle_1.3.0-beta3 -> gradle_1.3.0-beta3
 * [new tag]         gradle_1.3.0-beta4 -> gradle_1.3.0-beta4
 * [new tag]         gradle_1.3.1 -> gradle_1.3.1
 * [new tag]         gradle_1.5.0 -> gradle_1.5.0
 * [new tag]         gradle_2.0.0 -> gradle_2.0.0
 * [new tag]         ndk-r11    -> ndk-r11
 * [new tag]         ndk-r11b   -> ndk-r11b
 * [new tag]         ndk-r11c   -> ndk-r11c
 * [new tag]         studio-1.4 -> studio-1.4
 * [new tag]         studio-1.5 -> studio-1.5
 * [new tag]         studio-2.0 -> studio-2.0
 * [new tag]         studio-2.0-rc1 -> studio-2.0-rc1
 * [new tag]         studio_0.8.6 -> studio_0.8.6
 * [new tag]         studio_1.0.0 -> studio_1.0.0
 * [new tag]         studio_1.0.1 -> studio_1.0.1
 * [new tag]         ub-jack-arzon-mr2 -> ub-jack-arzon-mr2
 * [new tag]         webview-m40_r1 -> webview-m40_r1
 * [new tag]         webview-m40_r2 -> webview-m40_r2
 * [new tag]         webview-m40_r3 -> webview-m40_r3
 * [new tag]         webview-m40_r4 -> webview-m40_r4

Traceback (most recent call last):
  File "/home/tiktikals/phablet/.repo/repo/main.py", line 531, in <module>
    _Main(sys.argv[1:])
  File "/home/tiktikals/phablet/.repo/repo/main.py", line 507, in _Main
    result = repo._Run(argv) or 0
  File "/home/tiktikals/phablet/.repo/repo/main.py", line 180, in _Run
    result = cmd.Execute(copts, cargs)
  File "/home/tiktikals/phablet/.repo/repo/subcmds/init.py", line 404, in Execute
    self._ConfigureUser()
  File "/home/tiktikals/phablet/.repo/repo/subcmds/init.py", line 298, in _ConfigureUser
    name  = self._Prompt('Your Name', mp.UserName)
  File "/home/tiktikals/phablet/.repo/repo/project.py", line 784, in UserName
    self._LoadUserIdentity()
  File "/home/tiktikals/phablet/.repo/repo/project.py", line 797, in _LoadUserIdentity
    u = self.bare_git.var('GIT_COMMITTER_IDENT')
  File "/home/tiktikals/phablet/.repo/repo/project.py", line 2747, in runner
    (self._project.name, name, p.stderr))
error.GitError: manifests var: 
*** Please tell me who you are.

Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: unable to auto-detect email address (got 'tiktikals@masangkay-tiktikals.(none)')

ERROR:phablet-dev-bootstrap:Error while trying to sync repository

```
i'm new to ubuntu and want to port ubuntu touch to a new device 
i'm using 16.04 LTS

can anyone help me please
thanks in advance

---

