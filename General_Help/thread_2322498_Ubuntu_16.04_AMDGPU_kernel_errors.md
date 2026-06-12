---
title: "Ubuntu 16.04 AMDGPU kernel errors"
date: 2016-04-28
forum: General Help
---

### Post by giannis_androulida on 2016-04-28
Hey,

yesterday i had a clean installation of Ubuntu 16.04 on a Dell 5547 Inspiron laptop with AMD R7 M265 gpu. Everything went ok, but after some hours the screen "freezed" so i had to tun off my laptop. From then on, during boot the kernel prints some errors, which can also be viewed with dmesg :

```

[   34.209198] [drm] PCIE GART of 2048M enabled (table at 0x0000000000040000).
[   34.496093] [drm:gfx_v8_0_ring_test_ring [amdgpu]] *ERROR* amdgpu: cp failed to lock ring 0 (-2).
[   34.496131] [drm:amdgpu_resume [amdgpu]] *ERROR* resume 4 failed -2
[   34.496158] [drm:amdgpu_resume_kms [amdgpu]] *ERROR* amdgpu_resume failed (-2).
[   34.496287] amdgpu 0000:03:00.0: couldn't schedule ib
[   34.496331] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[   34.496373] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   34.738034] amdgpu 0000:03:00.0: couldn't schedule ib
[   34.738071] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[   34.738093] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   34.738096] amdgpu 0000:03:00.0: couldn't schedule ib
[   34.738114] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[   34.738130] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   34.738281] amdgpu 0000:03:00.0: couldn't schedule ib
[   34.738307] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[   34.738328] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   35.645284] amdgpu 0000:03:00.0: couldn't schedule ib
[   35.645333] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[   35.645370] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   35.645405] amdgpu 0000:03:00.0: couldn't schedule ib
[   35.645439] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[   35.645468] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   35.645472] amdgpu 0000:03:00.0: couldn't schedule ib
[   35.645499] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[   35.645526] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   35.645529] amdgpu 0000:03:00.0: couldn't schedule ib
[   35.645546] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[   35.645564] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   35.645566] amdgpu 0000:03:00.0: couldn't schedule ib
[   35.645582] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[   35.645599] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   35.645927] amdgpu 0000:03:00.0: couldn't schedule ib
[   35.645958] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[   35.645988] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   35.645998] amdgpu 0000:03:00.0: couldn't schedule ib
[   35.646028] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[   35.646055] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   35.938788] amdgpu 0000:03:00.0: couldn't schedule ib
[   35.938831] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[   35.938857] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   35.938860] amdgpu 0000:03:00.0: couldn't schedule ib
[   35.938884] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[   35.938908] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   35.938910] amdgpu 0000:03:00.0: couldn't schedule ib
[   35.938928] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[   35.938946] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   35.938955] amdgpu 0000:03:00.0: couldn't schedule ib
[   35.938976] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[   35.938994] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   36.022590] amdgpu 0000:03:00.0: couldn't schedule ib
[   36.022626] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[   36.022651] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   36.042256] amdgpu 0000:03:00.0: couldn't schedule ib
[   36.042300] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[   36.042326] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   36.663527] amdgpu 0000:03:00.0: couldn't schedule ib
[   36.663570] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[   36.663598] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   36.663683] amdgpu 0000:03:00.0: couldn't schedule ib
[   36.663716] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[   36.663741] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   36.663745] amdgpu 0000:03:00.0: couldn't schedule ib
[   36.663767] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[   36.663787] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   45.054545] Bluetooth: RFCOMM TTY layer initialized
[   45.054563] Bluetooth: RFCOMM socket layer initialized
[   45.054632] Bluetooth: RFCOMM ver 1.11
[   59.286203] wlp2s0: authenticate with 00:14:c1:28:98:46
[   59.288456] wlp2s0: send auth to 00:14:c1:28:98:46 (try 1/3)
[   59.292239] wlp2s0: authenticated
[   59.292436] iwlwifi 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[   59.292443] iwlwifi 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
[   59.294357] wlp2s0: associate with 00:14:c1:28:98:46 (try 1/3)
[   59.296702] wlp2s0: RX AssocResp from 00:14:c1:28:98:46 (capab=0x411 status=0 aid=4)
[   59.297824] wlp2s0: associated
[   59.297868] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[ 8659.816306] [drm] PCIE GART of 2048M enabled (table at 0x0000000000040000).
[ 8660.107281] [drm:gfx_v8_0_hw_init [amdgpu]] *ERROR* amdgpu: cp failed to lock ring (-2).
[ 8660.107293] [drm] ring test on 0 succeeded in 2 usecs
[ 8660.107515] [drm:gfx_v8_0_ring_test_ring [amdgpu]] *ERROR* amdgpu: cp failed to lock ring 1 (-2).
[ 8660.107534] [drm:gfx_v8_0_ring_test_ring [amdgpu]] *ERROR* amdgpu: cp failed to lock ring 2 (-2).
[ 8660.107552] [drm:gfx_v8_0_ring_test_ring [amdgpu]] *ERROR* amdgpu: cp failed to lock ring 3 (-2).
[ 8660.107569] [drm:gfx_v8_0_ring_test_ring [amdgpu]] *ERROR* amdgpu: cp failed to lock ring 4 (-2).
[ 8660.107585] [drm:gfx_v8_0_ring_test_ring [amdgpu]] *ERROR* amdgpu: cp failed to lock ring 5 (-2).
[ 8660.107602] [drm:gfx_v8_0_ring_test_ring [amdgpu]] *ERROR* amdgpu: cp failed to lock ring 6 (-2).
[ 8660.107618] [drm:gfx_v8_0_ring_test_ring [amdgpu]] *ERROR* amdgpu: cp failed to lock ring 7 (-2).
[ 8660.107634] [drm:gfx_v8_0_ring_test_ring [amdgpu]] *ERROR* amdgpu: cp failed to lock ring 8 (-2).
[ 8660.107666] [drm] ring test on 9 succeeded in 7 usecs
[ 8660.107691] [drm:sdma_v2_4_ring_test_ring [amdgpu]] *ERROR* amdgpu: dma failed to lock ring 10 (-2).
[ 8660.107703] [drm:amdgpu_resume [amdgpu]] *ERROR* resume 5 failed -2
[ 8660.107716] [drm:amdgpu_resume_kms [amdgpu]] *ERROR* amdgpu_resume failed (-2).


```

Any ideas of what i can do ? From what i see the integrated graphics card is in use and the AMD chipset cannot be configured.

Thanks

---

### Post by El Zoido on 2016-04-29
I can't help you, sorry, but you might get more help when having this thread moved to hardware or general discussion.

---

### Post by yoshii on 2016-04-30
from what I understand, Ubuntu 16.04 is incompatible with AMD R7 video hardware and will be for about a year.  
There's no alternative except to avoid upgrading to 16.04 or use some other video hardware card maybe.  
You can still possibly use 16.04 if you boot with "nomodeset" which disables all hardware acceleration of video, but that's like not having a video card at all.  
Also, you have to put "nomodeset" into the grub configuration so that it stays there until you remove it manually.

---

### Post by El Zoido on 2016-05-01
I don't think that is right.
AMDGPU is incompatible with it, but the old RadeonSI open source driver should work just fine, shouldn't it?
It definitely supports GCN1 hardware.
No idea why the laptop even intends to use AMDGPU.

---

### Post by nasir8891 on 2016-05-27
I am facing the similar problem. For last one year or so i was using Ubuntu 14.04 and did not face such issue. After installing a fresh Ubuntu 16.04 this is happening.

---

### Post by yoshii on 2016-05-27
There is more info about the AMD/ATI/Radeon GPU issues in the Ubuntu v16 release notes which can be cross referenced to technical articles written on other websites about it.

---

### Post by m3asmi-gmail on 2016-07-18
I have the same problem :/

---

### Post by johnenglart on 2017-01-06
Aaaargh....same issue for my HP Pavillion notebook running AMD/ATI/Radeon R7 M260 graphics card. At some stage in 2016 I upgraded to 16.04 from 14.04, but then didn't need to use the Notebook (I bought a 2nd hand Mac Book Pro as I needed the longer battery capacity while travelling). Came to use my Notebook today, when I boot into Ubuntu I get the error message similar to the above, then the login screen comes up, I login and sometimes I get a system freeze immediately and sometimes after a few minutes.

I checked [COLOR=#333333][FONT=UbuntuMono]lspci | grep -E 'VGA|Display'
[/FONT][/COLOR]Result: VGA compatible controller AMD/ATI Radeon R4/R5 Graphics (rev 05)
Display controller: AMD/ATI Topaz XT Radeon R7 M260/M265

I know, I should have read this before upgrading to 16.04 LTS, but honestly I expected issues like this would have been resolved before LTS was rolled out.
[http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04](http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04)

Ubuntu Help on the Radeon driver doesn't even mention my Graphics card and what to do in my case
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Is there anyway to fix the driver problem in 16.04 from the recovery terminal? or do I just reinstall 14.04 again?

---

