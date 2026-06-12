---
title: "System keeps crashing and then GPU fans go into overspeed."
date: 2024-03-27
forum: General Help
---

### Post by amos-burton12 on 2024-03-27
My monitor will go black and then my GPU will go into over-speed.  Any ideas what is going on? 

RTX4080 - Driver Version: 550.54.14
Ubuntu 22.04.4 LTS 
Linux 6.5.0-26-generic 

Here is a snippet from the logs file after logging back in. 

```

Mar 27 19:52:25 scott-linux-main kernel: nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000c67e:6:0:0x0000000f
Mar 27 19:52:25 scott-linux-main kernel: NVRM: _issueRpcAndWait: rpcSendMessage failed with status 0x0000000f for fn 76!
Mar 27 19:52:25 scott-linux-main kernel: NVRM: _issueRpcAndWait: rpcSendMessage failed with status 0x0000000f for fn 10!
Mar 27 19:52:25 scott-linux-main kernel: NVRM: rpcRmApiFree_GSP: GspRmFree failed: hClient=0xc1d0003b; hObject=0xbeef0310; paramsStatus=0x00000000; status=0x0000000f
Mar 27 19:52:25 scott-linux-main kernel: NVRM: nvAssertFailedNoLog: Assertion failed: status == NV_OK @ rs_client.c:834
Mar 27 19:52:25 scott-linux-main kernel: NVRM: nvAssertFailedNoLog: Assertion failed: status == NV_OK @ rs_server.c:167
Mar 27 19:52:25 scott-linux-main kernel: NVRM: _issueRpcAndWait: rpcSendMessage failed with status 0x0000000f for fn 10!
Mar 27 19:52:25 scott-linux-main kernel: NVRM: rpcRmApiFree_GSP: GspRmFree failed: hClient=0xc1d0003b; hObject=0xbeef00f0; paramsStatus=0x00000000; status=0x0000000f
Mar 27 19:52:25 scott-linux-main kernel: NVRM: nvAssertFailedNoLog: Assertion failed: status == NV_OK @ rs_client.c:834
Mar 27 19:52:25 scott-linux-main kernel: NVRM: nvAssertFailedNoLog: Assertion failed: status == NV_OK @ rs_server.c:167
Mar 27 19:52:25 scott-linux-main systemd[1]: systemd-timedated.service: Deactivated successfully.
Mar 27 19:52:33 scott-linux-main kernel: nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000c77d:0:0:0x0000000f
Mar 27 19:52:33 scott-linux-main kernel: nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000c67e:0:0:0x0000000f
Mar 27 19:52:33 scott-linux-main kernel: nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000c67e:1:0:0x0000000f
Mar 27 19:52:33 scott-linux-main kernel: nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000c67e:2:0:0x0000000f
Mar 27 19:52:33 scott-linux-main kernel: nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000c67e:3:0:0x0000000f
Mar 27 19:52:33 scott-linux-main kernel: nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000c67e:4:0:0x0000000f
Mar 27 19:52:33 scott-linux-main kernel: nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000c67e:5:0:0x0000000f
Mar 27 19:52:33 scott-linux-main kernel: nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000c67e:6:0:0x0000000f
Mar 27 19:52:33 scott-linux-main kernel: nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000c67e:7:0:0x0000000f
Mar 27 19:52:33 scott-linux-main kernel: nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000c77d:0:0:0x0000000f
Mar 27 19:52:33 scott-linux-main kernel: nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000c67e:0:0:0x0000000f
Mar 27 19:52:33 scott-linux-main kernel: nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000c67e:1:0:0x0000000f
Mar 27 19:52:33 scott-linux-main kernel: nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000c67e:2:0:0x0000000f
Mar 27 19:52:33 scott-linux-main kernel: nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000c67e:3:0:0x0000000f
Mar 27 19:52:33 scott-linux-main kernel: nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000c67e:4:0:0x0000000f
Mar 27 19:52:33 scott-linux-main kernel: nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000c67e:5:0:0x0000000f
Mar 27 19:52:33 scott-linux-main kernel: nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000c67e:6:0:0x0000000f
Mar 27 19:52:33 scott-linux-main kernel: nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000c67e:7:0:0x0000000f
Mar 27 19:52:36 scott-linux-main /usr/libexec/gdm-x-session[1964]: (EE) NVIDIA(GPU-0): WAIT (2, 8, 0x8000, 0x0003e728, 0x0003e7a8)
Mar 27 19:52:43 scott-linux-main /usr/libexec/gdm-x-session[1964]: (EE) NVIDIA(GPU-0): WAIT (1, 8, 0x8000, 0x0003e728, 0x0003e7a8)
Mar 27 19:52:43 scott-linux-main kernel: nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000c67e:6:0:0x0000000f
Mar 27 19:52:43 scott-linux-main kernel: nvidia-modeset: ERROR: GPU:0: Failed to query display engine channel state: 0x0000c67e:6:0:0x0000000f
Mar 27 19:52:43 scott-linux-main kernel: NVRM: nvAssertOkFailedNoLog: Assertion failed: Current device is not valid [NV_ERR_INVALID_DEVICE] (0x00000026) returned from rmDeviceGpuLocksAcquire(pGpu, GPUS_LOCK_FLAGS_NONE, RM_LOCK_MODULES_MEM_PMA) @ virtual_mem.c:115
Mar 27 19:52:43 scott-linux-main kernel: NVRM: _issueRpcAndWait: rpcSendMessage failed with status 0x0000000f for fn 76!
Mar 27 19:52:43 scott-linux-main kernel: NVRM: _issueRpcAndWait: rpcSendMessage failed with status 0x0000000f for fn 76!
Mar 27 19:52:43 scott-linux-main kernel: NVRM: _issueRpcAndWait: rpcSendMessage failed with status 0x0000000f for fn 76!
Mar 27 19:52:43 scott-linux-main kernel: NVRM: nvAssertFailedNoLog: Assertion failed: NV_OK == rmStatus @ video_mem.c:656
Mar 27 19:52:43 scott-linux-main kernel: NVRM: _issueRpcAndWait: rpcSendMessage failed with status 0x0000000f for fn 76!
Mar 27 19:52:43 scott-linux-main kernel: NVRM: _issueRpcAndWait: rpcSendMessage failed with status 0x0000000f for fn 76!


```

```

Mar 27 21:20:34 scott-linux-main /usr/libexec/gdm-x-session[1944]: (--) NVIDIA(GPU-0): DFP-5: Internal DisplayPort
Mar 27 21:20:34 scott-linux-main /usr/libexec/gdm-x-session[1944]: (--) NVIDIA(GPU-0): DFP-5: 2670.0 MHz maximum pixel clock
Mar 27 21:20:34 scott-linux-main /usr/libexec/gdm-x-session[1944]: (--) NVIDIA(GPU-0):
Mar 27 21:20:34 scott-linux-main /usr/libexec/gdm-x-session[1944]: (--) NVIDIA(GPU-0): DFP-6: disconnected
Mar 27 21:20:34 scott-linux-main /usr/libexec/gdm-x-session[1944]: (--) NVIDIA(GPU-0): DFP-6: Internal TMDS
Mar 27 21:20:34 scott-linux-main /usr/libexec/gdm-x-session[1944]: (--) NVIDIA(GPU-0): DFP-6: 165.0 MHz maximum pixel clock
Mar 27 21:20:34 scott-linux-main /usr/libexec/gdm-x-session[1944]: (--) NVIDIA(GPU-0):
Mar 27 21:20:34 scott-linux-main kernel: [drm:nv_drm_master_set [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00000100] Failed to grab modeset ownership

```

---

### Post by weberan2 on 2024-04-12
What troubleshooting steps can be taken to resolve the issue of system crashes, GPU fans going into overspeed, and black monitor screen with an RTX4080 GPU running on Ubuntu 22.04.4 LTS with Linux 6.5.0-26-generic? [[size=1][color=#F3F3F3]battleship game[/color][/size]](https://battleshipgame.io)

---

