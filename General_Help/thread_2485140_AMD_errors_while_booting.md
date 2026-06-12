---
title: "AMD errors while booting"
date: 2023-03-21
forum: General Help
---

### Post by daanheuvelbeuk on 2023-03-21
Why am I seeing the following errors? 
```
mrt 21 10:29:12 Elfheim kernel: NVRM cpuidInfoAMD: Unrecognized AMD processor in cpuidInfoAMD
mrt 21 10:29:12 Elfheim kernel: [drm:nv_drm_load [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00002d00] Failed to allocate NvKmsKapiDevice
mrt 21 10:29:12 Elfheim kernel: [drm:nv_drm_probe_devices [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00002d00] Failed to register device
```

---

### Post by ActionParsnip on 2023-03-21
Does the system boot OK despite the errors?

---

### Post by daanheuvelbeuk on 2023-03-22
Yes. But I think I have issues with my sound and movies. My Bluetooth headphones does not work each time, I have to remove and add the headphones often. Movies do not always work. 

Did I install the wrong version drivers?

---

### Post by MAFoElffen on 2023-03-22
Please post the output of
```

uname -r
sudo dpkg -l | awk '/  nvidia-/ {print $0}'
grep -i 'model name' /proc/cpuinfo | head -n 1

```

---

