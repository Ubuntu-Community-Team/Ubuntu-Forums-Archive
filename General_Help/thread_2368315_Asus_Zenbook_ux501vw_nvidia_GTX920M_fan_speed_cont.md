---
title: "Asus Zenbook ux501vw nvidia GTX920M fan speed control"
date: 2017-08-09
forum: General Help
---

### Post by hdaemon on 2017-08-09
Diver is nvidia-384

nvidia-settings -q all

```
Attribute 'PCIEMaxLinkSpeed' (GSLM:0.0): 8000.
    'PCIEMaxLinkSpeed' is an integer attribute.
    'PCIEMaxLinkSpeed' is a read-only attribute.
    'PCIEMaxLinkSpeed' can use the following target types: X Screen, GPU, SDI Input Device.
  Attribute 'PCIECurrentLinkSpeed' (GSLM:0.0): 8000.
    'PCIECurrentLinkSpeed' is an integer attribute.
    'PCIECurrentLinkSpeed' is a read-only attribute.
    'PCIECurrentLinkSpeed' can use the following target types: X Screen, GPU, SDI Input Device.
  Attribute 'PCIEMaxLinkSpeed' (GSLM:0[gpu:0]): 8000.
    'PCIEMaxLinkSpeed' is an integer attribute.
    'PCIEMaxLinkSpeed' is a read-only attribute.
    'PCIEMaxLinkSpeed' can use the following target types: X Screen, GPU, SDI Input Device.
  Attribute 'PCIECurrentLinkSpeed' (GSLM:0[gpu:0]): 8000.
    'PCIECurrentLinkSpeed' is an integer attribute.
    'PCIECurrentLinkSpeed' is a read-only attribute.
    'PCIECurrentLinkSpeed' can use the following target types: X Screen, GPU, SDI Input Device.
gsl@GSLM:~$ NO_AT_BRIDGE=1 nvidia-settings -q all


Attributes queryable via GSLM:0.0:


  Attribute 'OperatingSystem' (GSLM:0.0): 0.
    The valid values for 'OperatingSystem' are in the range 0 - 2 (inclusive).
    'OperatingSystem' is a read-only attribute.
    'OperatingSystem' can use the following target types: X Screen, GPU.


  Attribute 'NvidiaDriverVersion' (GSLM:0.0): 384.59 
    'NvidiaDriverVersion' is a string attribute.
    'NvidiaDriverVersion' is a read-only attribute.
    'NvidiaDriverVersion' can use the following target types: X Screen, GPU.


  Attribute 'NvControlVersion' (GSLM:0.0): 1.29 
    'NvControlVersion' is a string attribute.
    'NvControlVersion' is a read-only attribute.
    'NvControlVersion' can use the following target types: X Screen.


  Attribute 'GLXServerVersion' (GSLM:0.0): 1.4 
    'GLXServerVersion' is a string attribute.
    'GLXServerVersion' is a read-only attribute.
    'GLXServerVersion' can use the following target types: X Screen.


  Attribute 'GLXClientVersion' (GSLM:0.0): 1.4 
    'GLXClientVersion' is a string attribute.
    'GLXClientVersion' is a read-only attribute.
    'GLXClientVersion' can use the following target types: X Screen.


  Attribute 'OpenGLVersion' (GSLM:0.0): 4.5.0 NVIDIA 384.59 
    'OpenGLVersion' is a string attribute.
    'OpenGLVersion' is a read-only attribute.
    'OpenGLVersion' can use the following target types: X Screen.


  Attribute 'XRandRVersion' (GSLM:0.0): 1.5 
    'XRandRVersion' is a string attribute.
    'XRandRVersion' is a read-only attribute.
    'XRandRVersion' can use the following target types: X Screen.


  Attribute 'XF86VidModeVersion' (GSLM:0.0): 2.2 
    'XF86VidModeVersion' is a string attribute.
    'XF86VidModeVersion' is a read-only attribute.
    'XF86VidModeVersion' can use the following target types: X Screen.


  Attribute 'XvVersion' (GSLM:0.0): 2.2 
    'XvVersion' is a string attribute.
    'XvVersion' is a read-only attribute.
    'XvVersion' can use the following target types: X Screen.


  Attribute 'TwinView' (GSLM:0.0): 0.
    'TwinView' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'TwinView' is a read-only attribute.
    'TwinView' can use the following target types: X Screen.


  Attribute 'ConnectedDisplays' (GSLM:0.0): 0x00000000.
    'ConnectedDisplays' is a bitmask attribute.
    'ConnectedDisplays' is a read-only attribute.
    'ConnectedDisplays' can use the following target types: X Screen, GPU.


  Attribute 'EnabledDisplays' (GSLM:0.0): 0x00000000.
    'EnabledDisplays' is a bitmask attribute.
    'EnabledDisplays' is a read-only attribute.
    'EnabledDisplays' can use the following target types: X Screen, GPU.


  Attribute 'AssociatedDisplays' (GSLM:0.0): 0x00000000.
    'AssociatedDisplays' is a bitmask attribute.
    'AssociatedDisplays' can use the following target types: X Screen.


  Attribute 'InitialPixmapPlacement' (GSLM:0.0): 2.
    The valid values for 'InitialPixmapPlacement' are in the range 0 - 4 (inclusive).
    'InitialPixmapPlacement' can use the following target types: X Screen.


  Attribute 'MultiGpuDisplayOwner' (GSLM:0.0): 0.
    'MultiGpuDisplayOwner' is an integer attribute.
    'MultiGpuDisplayOwner' is a read-only attribute.
    'MultiGpuDisplayOwner' can use the following target types: X Screen.


  Attribute 'GlyphCache' (GSLM:0.0): 1.
    'GlyphCache' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'GlyphCache' can use the following target types: X Screen.


  Attribute 'Depth30Allowed' (GSLM:0.0): 1.
    'Depth30Allowed' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'Depth30Allowed' is a read-only attribute.
    'Depth30Allowed' can use the following target types: X Screen, GPU.


  Attribute 'NoScanout' (GSLM:0.0): 1.
    'NoScanout' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'NoScanout' is a read-only attribute.
    'NoScanout' can use the following target types: X Screen, GPU.


  Attribute 'XServerUniqueId' (GSLM:0.0): 732716171.
    'XServerUniqueId' is an integer attribute.
    'XServerUniqueId' is a read-only attribute.
    'XServerUniqueId' can use the following target types: X Screen.


  Attribute 'PixmapCache' (GSLM:0.0): 1.
    'PixmapCache' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'PixmapCache' can use the following target types: X Screen.


  Attribute 'PixmapCacheRoundSizeKB' (GSLM:0.0): 1024.
    The valid values for 'PixmapCacheRoundSizeKB' are in the range 4 - 1048576 (inclusive).
    'PixmapCacheRoundSizeKB' can use the following target types: X Screen.


  Attribute 'AccelerateTrapezoids' (GSLM:0.0): 1.
    'AccelerateTrapezoids' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'AccelerateTrapezoids' can use the following target types: X Screen.


  Attribute 'ScreenPosition' (GSLM:0.0): x=0, y=0, width=3840, height=2160 
    'ScreenPosition' is a string attribute.
    'ScreenPosition' is a read-only attribute.
    'ScreenPosition' can use the following target types: X Screen.


  Attribute 'LogAniso' (GSLM:0.0): 0.
    The valid values for 'LogAniso' are in the range 0 - 4 (inclusive).
    'LogAniso' can use the following target types: X Screen.


  Attribute 'FSAA' (GSLM:0.0): 0.
    Valid values for 'FSAA' are: 0, 1, 5, 9, 10 and 11.
    'FSAA' can use the following target types: X Screen.


  Attribute 'TextureClamping' (GSLM:0.0): 1.
    'TextureClamping' is an integer attribute.
    'TextureClamping' can use the following target types: X Screen.


  Attribute 'FXAA' (GSLM:0.0): 0.
    'FXAA' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'FXAA' can use the following target types: X Screen.


  Attribute 'FSAAAppControlled' (GSLM:0.0): 1.
    'FSAAAppControlled' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'FSAAAppControlled' can use the following target types: X Screen.


  Attribute 'LogAnisoAppControlled' (GSLM:0.0): 1.
    'LogAnisoAppControlled' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'LogAnisoAppControlled' can use the following target types: X Screen.


  Attribute 'OpenGLImageSettings' (GSLM:0.0): 1.
    The valid values for 'OpenGLImageSettings' are in the range 0 - 3 (inclusive).
    'OpenGLImageSettings' can use the following target types: X Screen.


  Attribute 'FSAAAppEnhanced' (GSLM:0.0): 0.
    'FSAAAppEnhanced' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'FSAAAppEnhanced' can use the following target types: X Screen.


  Attribute 'SliMosaicModeAvailable' (GSLM:0.0): 0.
    'SliMosaicModeAvailable' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'SliMosaicModeAvailable' is a read-only attribute.
    'SliMosaicModeAvailable' can use the following target types: X Screen, GPU, VCS.


  Attribute 'BusType' (GSLM:0.0): 2.
    The valid values for 'BusType' are in the range 0 - 3 (inclusive).
    'BusType' is a read-only attribute.
    'BusType' can use the following target types: X Screen, GPU, SDI Input Device.


  Attribute 'PCIEMaxLinkSpeed' (GSLM:0.0): 8000.
    'PCIEMaxLinkSpeed' is an integer attribute.
    'PCIEMaxLinkSpeed' is a read-only attribute.
    'PCIEMaxLinkSpeed' can use the following target types: X Screen, GPU, SDI Input Device.


  Attribute 'PCIEMaxLinkWidth' (GSLM:0.0): 16.
    The valid values for 'PCIEMaxLinkWidth' are in the range 1 - 16 (inclusive).
    'PCIEMaxLinkWidth' is a read-only attribute.
    'PCIEMaxLinkWidth' can use the following target types: X Screen, GPU, SDI Input Device.


  Attribute 'PCIECurrentLinkSpeed' (GSLM:0.0): 8000.
    'PCIECurrentLinkSpeed' is an integer attribute.
    'PCIECurrentLinkSpeed' is a read-only attribute.
    'PCIECurrentLinkSpeed' can use the following target types: X Screen, GPU, SDI Input Device.


  Attribute 'PCIECurrentLinkWidth' (GSLM:0.0): 8.
    'PCIECurrentLinkWidth' is an integer attribute.
    'PCIECurrentLinkWidth' is a read-only attribute.
    'PCIECurrentLinkWidth' can use the following target types: X Screen, GPU, SDI Input Device.


  Attribute 'VideoRam' (GSLM:0.0): 2097152.
    'VideoRam' is an integer attribute.
    'VideoRam' is a read-only attribute.
    'VideoRam' can use the following target types: X Screen, GPU.


  Attribute 'Irq' (GSLM:0.0): 136.
    'Irq' is an integer attribute.
    'Irq' is a read-only attribute.
    'Irq' can use the following target types: X Screen, GPU, SDI Input Device.


  Attribute 'CUDACores' (GSLM:0.0): 640.
    'CUDACores' is an integer attribute.
    'CUDACores' is a read-only attribute.
    'CUDACores' can use the following target types: X Screen, GPU.


  Attribute 'GPUMemoryInterface' (GSLM:0.0): 128.
    'GPUMemoryInterface' is an integer attribute.
    'GPUMemoryInterface' is a read-only attribute.
    'GPUMemoryInterface' can use the following target types: X Screen, GPU.


  Attribute 'GPUCoreTemp' (GSLM:0.0): 49.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.


  Attribute 'GPUCurrentCoreVoltage' (GSLM:0.0): 0.
    'GPUCurrentCoreVoltage' is an integer attribute.
    'GPUCurrentCoreVoltage' is a read-only attribute.
    'GPUCurrentCoreVoltage' can use the following target types: X Screen, GPU.


  Attribute 'GPUCurrentClockFreqs' (GSLM:0.0): 1097,2505.
    'GPUCurrentClockFreqs' is a packed integer attribute.
    'GPUCurrentClockFreqs' is a read-only attribute.
    'GPUCurrentClockFreqs' can use the following target types: X Screen, GPU.


  Attribute 'BusRate' (GSLM:0.0): 16.
    The valid values for 'BusRate' are in the range 1 - 16 (inclusive).
    'BusRate' is a read-only attribute.
    'BusRate' can use the following target types: X Screen, GPU, SDI Input Device.


  Attribute 'PCIEGen' (GSLM:0.0): 3.
    'PCIEGen' is an integer attribute.
    'PCIEGen' is a read-only attribute.
    'PCIEGen' can use the following target types: X Screen, GPU, SDI Input Device.


  Attribute 'GPUErrors' (GSLM:0.0): 0.
    'GPUErrors' is an integer attribute.
    'GPUErrors' is a read-only attribute.
    'GPUErrors' can use the following target types: X Screen.


  Attribute 'GPUPowerSource' (GSLM:0.0): 0.
    'GPUPowerSource' is an integer attribute.
    'GPUPowerSource' is a read-only attribute.
    'GPUPowerSource' can use the following target types: X Screen, GPU.


  Attribute 'GPUCurrentPerfLevel' (GSLM:0.0): 2.
    'GPUCurrentPerfLevel' is an integer attribute.
    'GPUCurrentPerfLevel' is a read-only attribute.
    'GPUCurrentPerfLevel' can use the following target types: X Screen, GPU.


  Attribute 'GPUAdaptiveClockState' (GSLM:0.0): 1.
    'GPUAdaptiveClockState' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'GPUAdaptiveClockState' is a read-only attribute.
    'GPUAdaptiveClockState' can use the following target types: X Screen, GPU.


  Attribute 'ECCConfigurationSupported' (GSLM:0.0): 0.
    'ECCConfigurationSupported' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'ECCConfigurationSupported' is a read-only attribute.
    'ECCConfigurationSupported' can use the following target types: X Screen, GPU.


  Attribute 'GPUCurrentClockFreqsString' (GSLM:0.0): nvclock=1097, nvclockmin=135, nvclockmax=1202, nvclockeditable=0, memclock=2505,
  memclockmin=2505, memclockmax=2505, memclockeditable=0, memTransferRate=5010, memTransferRatemin=5010, memTransferRatemax=5010,
  memTransferRateeditable=0 
    'GPUCurrentClockFreqsString' is a string attribute.
    'GPUCurrentClockFreqsString' can use the following target types: X Screen, GPU.


  Attribute 'GPUPerfModes' (GSLM:0.0): perf=0, nvclock=135, nvclockmin=135, nvclockmax=405, nvclockeditable=0, memclock=405, memclockmin=405,
  memclockmax=405, memclockeditable=0, memTransferRate=810, memTransferRatemin=810, memTransferRatemax=810, memTransferRateeditable=0 ; perf=1,
  nvclock=135, nvclockmin=135, nvclockmax=1202, nvclockeditable=0, memclock=800, memclockmin=800, memclockmax=800, memclockeditable=0,
  memTransferRate=1600, memTransferRatemin=1600, memTransferRatemax=1600, memTransferRateeditable=0 ; perf=2, nvclock=135, nvclockmin=135,
  nvclockmax=1202, nvclockeditable=0, memclock=2505, memclockmin=2505, memclockmax=2505, memclockeditable=0, memTransferRate=5010,
  memTransferRatemin=5010, memTransferRatemax=5010, memTransferRateeditable=0 
    'GPUPerfModes' is a string attribute.
    'GPUPerfModes' is a read-only attribute.
    'GPUPerfModes' can use the following target types: X Screen, GPU.


  Attribute 'GvoSupported' (GSLM:0.0): 0.
    'GvoSupported' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'GvoSupported' is a read-only attribute.
    'GvoSupported' can use the following target types: X Screen.


  Attribute 'CurrentMetaModeID' (GSLM:0.0): 50.
    'CurrentMetaModeID' is an integer attribute.
    'CurrentMetaModeID' can use the following target types: X Screen.


  Attribute 'CurrentMetaMode' (GSLM:0.0): id=50, switchable=yes, source=xconfig :: NULL 
    'CurrentMetaMode' is a string attribute.
    'CurrentMetaMode' can use the following target types: X Screen.


  Attribute 'XVideoSyncToDisplayID' (GSLM:0.0): 0.
    'XVideoSyncToDisplayID' is an integer attribute.
    'XVideoSyncToDisplayID' can use the following target types: X Screen.


  Attribute 'CurrentXVideoSyncToDisplayID' (GSLM:0.0): -1.
    'CurrentXVideoSyncToDisplayID' is an integer attribute.
    'CurrentXVideoSyncToDisplayID' is a read-only attribute.
    'CurrentXVideoSyncToDisplayID' can use the following target types: X Screen.


Attributes queryable via GSLM:0[gpu:0]:


  Attribute 'OperatingSystem' (GSLM:0[gpu:0]): 0.
    The valid values for 'OperatingSystem' are in the range 0 - 2 (inclusive).
    'OperatingSystem' is a read-only attribute.
    'OperatingSystem' can use the following target types: X Screen, GPU.


  Attribute 'NvidiaDriverVersion' (GSLM:0[gpu:0]): 384.59 
    'NvidiaDriverVersion' is a string attribute.
    'NvidiaDriverVersion' is a read-only attribute.
    'NvidiaDriverVersion' can use the following target types: X Screen, GPU.


  Attribute 'ConnectedDisplays' (GSLM:0[gpu:0]): 0x00000000.
    'ConnectedDisplays' is a bitmask attribute.
    'ConnectedDisplays' is a read-only attribute.
    'ConnectedDisplays' can use the following target types: X Screen, GPU.


  Attribute 'EnabledDisplays' (GSLM:0[gpu:0]): 0x00000000.
    'EnabledDisplays' is a bitmask attribute.
    'EnabledDisplays' is a read-only attribute.
    'EnabledDisplays' can use the following target types: X Screen, GPU.


  Attribute 'Depth30Allowed' (GSLM:0[gpu:0]): 1.
    'Depth30Allowed' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'Depth30Allowed' is a read-only attribute.
    'Depth30Allowed' can use the following target types: X Screen, GPU.


  Attribute 'NoScanout' (GSLM:0[gpu:0]): 1.
    'NoScanout' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'NoScanout' is a read-only attribute.
    'NoScanout' can use the following target types: X Screen, GPU.


  Attribute 'SliMosaicModeAvailable' (GSLM:0[gpu:0]): 0.
    'SliMosaicModeAvailable' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'SliMosaicModeAvailable' is a read-only attribute.
    'SliMosaicModeAvailable' can use the following target types: X Screen, GPU, VCS.


  Attribute 'BusType' (GSLM:0[gpu:0]): 2.
    The valid values for 'BusType' are in the range 0 - 3 (inclusive).
    'BusType' is a read-only attribute.
    'BusType' can use the following target types: X Screen, GPU, SDI Input Device.


  Attribute 'PCIEMaxLinkSpeed' (GSLM:0[gpu:0]): 8000.
    'PCIEMaxLinkSpeed' is an integer attribute.
    'PCIEMaxLinkSpeed' is a read-only attribute.
    'PCIEMaxLinkSpeed' can use the following target types: X Screen, GPU, SDI Input Device.


  Attribute 'PCIEMaxLinkWidth' (GSLM:0[gpu:0]): 16.
    The valid values for 'PCIEMaxLinkWidth' are in the range 1 - 16 (inclusive).
    'PCIEMaxLinkWidth' is a read-only attribute.
    'PCIEMaxLinkWidth' can use the following target types: X Screen, GPU, SDI Input Device.


  Attribute 'PCIECurrentLinkSpeed' (GSLM:0[gpu:0]): 8000.
    'PCIECurrentLinkSpeed' is an integer attribute.
    'PCIECurrentLinkSpeed' is a read-only attribute.
    'PCIECurrentLinkSpeed' can use the following target types: X Screen, GPU, SDI Input Device.


  Attribute 'PCIECurrentLinkWidth' (GSLM:0[gpu:0]): 8.
    'PCIECurrentLinkWidth' is an integer attribute.
    'PCIECurrentLinkWidth' is a read-only attribute.
    'PCIECurrentLinkWidth' can use the following target types: X Screen, GPU, SDI Input Device.


  Attribute 'VideoRam' (GSLM:0[gpu:0]): 2097152.
    'VideoRam' is an integer attribute.
    'VideoRam' is a read-only attribute.
    'VideoRam' can use the following target types: X Screen, GPU.


  Attribute 'TotalDedicatedGPUMemory' (GSLM:0[gpu:0]): 2002.
    'TotalDedicatedGPUMemory' is an integer attribute.
    'TotalDedicatedGPUMemory' is a read-only attribute.
    'TotalDedicatedGPUMemory' can use the following target types: GPU.


  Attribute 'UsedDedicatedGPUMemory' (GSLM:0[gpu:0]): 499.
    'UsedDedicatedGPUMemory' is an integer attribute.
    'UsedDedicatedGPUMemory' is a read-only attribute.
    'UsedDedicatedGPUMemory' can use the following target types: GPU.


  Attribute 'Irq' (GSLM:0[gpu:0]): 136.
    'Irq' is an integer attribute.
    'Irq' is a read-only attribute.
    'Irq' can use the following target types: X Screen, GPU, SDI Input Device.


  Attribute 'CUDACores' (GSLM:0[gpu:0]): 640.
    'CUDACores' is an integer attribute.
    'CUDACores' is a read-only attribute.
    'CUDACores' can use the following target types: X Screen, GPU.


  Attribute 'GPUMemoryInterface' (GSLM:0[gpu:0]): 128.
    'GPUMemoryInterface' is an integer attribute.
    'GPUMemoryInterface' is a read-only attribute.
    'GPUMemoryInterface' can use the following target types: X Screen, GPU.


  Attribute 'GPUCoreTemp' (GSLM:0[gpu:0]): 50.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.


  Attribute 'GPUCurrentCoreVoltage' (GSLM:0[gpu:0]): 0.
    'GPUCurrentCoreVoltage' is an integer attribute.
    'GPUCurrentCoreVoltage' is a read-only attribute.
    'GPUCurrentCoreVoltage' can use the following target types: X Screen, GPU.


  Attribute 'GPUCurrentClockFreqs' (GSLM:0[gpu:0]): 1097,2505.
    'GPUCurrentClockFreqs' is a packed integer attribute.
    'GPUCurrentClockFreqs' is a read-only attribute.
    'GPUCurrentClockFreqs' can use the following target types: X Screen, GPU.


  Attribute 'BusRate' (GSLM:0[gpu:0]): 16.
    The valid values for 'BusRate' are in the range 1 - 16 (inclusive).
    'BusRate' is a read-only attribute.
    'BusRate' can use the following target types: X Screen, GPU, SDI Input Device.


  Attribute 'PCIDomain' (GSLM:0[gpu:0]): 0.
    'PCIDomain' is an integer attribute.
    'PCIDomain' is a read-only attribute.
    'PCIDomain' can use the following target types: GPU, SDI Input Device.


  Attribute 'PCIBus' (GSLM:0[gpu:0]): 1.
    'PCIBus' is an integer attribute.
    'PCIBus' is a read-only attribute.
    'PCIBus' can use the following target types: GPU, SDI Input Device.


  Attribute 'PCIDevice' (GSLM:0[gpu:0]): 0.
    'PCIDevice' is an integer attribute.
    'PCIDevice' is a read-only attribute.
    'PCIDevice' can use the following target types: GPU, SDI Input Device.


  Attribute 'PCIFunc' (GSLM:0[gpu:0]): 0.
    'PCIFunc' is an integer attribute.
    'PCIFunc' is a read-only attribute.
    'PCIFunc' can use the following target types: GPU, SDI Input Device.


  Attribute 'PCIID' (GSLM:0[gpu:0]): 4318,5019.
    'PCIID' is a packed integer attribute.
    'PCIID' is a read-only attribute.
    'PCIID' can use the following target types: GPU, SDI Input Device.


  Attribute 'PCIEGen' (GSLM:0[gpu:0]): 3.
    'PCIEGen' is an integer attribute.
    'PCIEGen' is a read-only attribute.
    'PCIEGen' can use the following target types: X Screen, GPU, SDI Input Device.


  Attribute 'GPUPowerSource' (GSLM:0[gpu:0]): 0.
    'GPUPowerSource' is an integer attribute.
    'GPUPowerSource' is a read-only attribute.
    'GPUPowerSource' can use the following target types: X Screen, GPU.


  Attribute 'GPUCurrentPerfLevel' (GSLM:0[gpu:0]): 2.
    'GPUCurrentPerfLevel' is an integer attribute.
    'GPUCurrentPerfLevel' is a read-only attribute.
    'GPUCurrentPerfLevel' can use the following target types: X Screen, GPU.


  Attribute 'GPUAdaptiveClockState' (GSLM:0[gpu:0]): 1.
    'GPUAdaptiveClockState' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'GPUAdaptiveClockState' is a read-only attribute.
    'GPUAdaptiveClockState' can use the following target types: X Screen, GPU.


  Attribute 'GPUPowerMizerMode' (GSLM:0[gpu:0]): 2.
    Valid values for 'GPUPowerMizerMode' are: 0, 1 and 2.
    'GPUPowerMizerMode' can use the following target types: GPU.


  Attribute 'GPUPowerMizerDefaultMode' (GSLM:0[gpu:0]): 0.
    'GPUPowerMizerDefaultMode' is an integer attribute.
    'GPUPowerMizerDefaultMode' is a read-only attribute.
    'GPUPowerMizerDefaultMode' can use the following target types: GPU.


  Attribute 'ECCSupported' (GSLM:0[gpu:0]): 0.
    'ECCSupported' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'ECCSupported' is a read-only attribute.
    'ECCSupported' can use the following target types: GPU.


  Attribute 'ECCConfigurationSupported' (GSLM:0[gpu:0]): 0.
    'ECCConfigurationSupported' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'ECCConfigurationSupported' is a read-only attribute.
    'ECCConfigurationSupported' can use the following target types: X Screen, GPU.


  Attribute 'BaseMosaic' (GSLM:0[gpu:0]): 0.
    Valid values for 'BaseMosaic' are: 0.
    'BaseMosaic' is a read-only attribute.
    'BaseMosaic' can use the following target types: GPU.


  Attribute 'MultiGpuMasterPossible' (GSLM:0[gpu:0]): 0.
    'MultiGpuMasterPossible' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'MultiGpuMasterPossible' is a read-only attribute.
    'MultiGpuMasterPossible' can use the following target types: GPU.


  Attribute 'VideoEncoderUtilization' (GSLM:0[gpu:0]): 0.
    'VideoEncoderUtilization' is an integer attribute.
    'VideoEncoderUtilization' is a read-only attribute.
    'VideoEncoderUtilization' can use the following target types: GPU.


  Attribute 'VideoDecoderUtilization' (GSLM:0[gpu:0]): 0.
    'VideoDecoderUtilization' is an integer attribute.
    'VideoDecoderUtilization' is a read-only attribute.
    'VideoDecoderUtilization' can use the following target types: GPU.


  Attribute 'GPUCurrentClockFreqsString' (GSLM:0[gpu:0]): nvclock=1097, nvclockmin=135, nvclockmax=1202, nvclockeditable=0, memclock=2505,
  memclockmin=2505, memclockmax=2505, memclockeditable=0, memTransferRate=5010, memTransferRatemin=5010, memTransferRatemax=5010,
  memTransferRateeditable=0 
    'GPUCurrentClockFreqsString' is a string attribute.
    'GPUCurrentClockFreqsString' can use the following target types: X Screen, GPU.


  Attribute 'GPUPerfModes' (GSLM:0[gpu:0]): perf=0, nvclock=135, nvclockmin=135, nvclockmax=405, nvclockeditable=0, memclock=405, memclockmin=405,
  memclockmax=405, memclockeditable=0, memTransferRate=810, memTransferRatemin=810, memTransferRatemax=810, memTransferRateeditable=0 ; perf=1,
  nvclock=135, nvclockmin=135, nvclockmax=1202, nvclockeditable=0, memclock=800, memclockmin=800, memclockmax=800, memclockeditable=0,
  memTransferRate=1600, memTransferRatemin=1600, memTransferRatemax=1600, memTransferRateeditable=0 ; perf=2, nvclock=135, nvclockmin=135,
  nvclockmax=1202, nvclockeditable=0, memclock=2505, memclockmin=2505, memclockmax=2505, memclockeditable=0, memTransferRate=5010,
  memTransferRatemin=5010, memTransferRatemax=5010, memTransferRateeditable=0 
    'GPUPerfModes' is a string attribute.
    'GPUPerfModes' is a read-only attribute.
    'GPUPerfModes' can use the following target types: X Screen, GPU.


  Attribute 'GpuUUID' (GSLM:0[gpu:0]): GPU-a23356f9-937a-4843-a3cc-da12769e0681 
    'GpuUUID' is a string attribute.
    'GpuUUID' is a read-only attribute.
    'GpuUUID' can use the following target types: GPU.


  Attribute 'GPUUtilization' (GSLM:0[gpu:0]): graphics=0, memory=0, video=0, PCIe=0 
    'GPUUtilization' is a string attribute.
    'GPUUtilization' is a read-only attribute.
    'GPUUtilization' can use the following target types: GPU.


Attributes queryable via GSLM:0[thermalsensor:0]:


  Attribute 'ThermalSensorReading' (GSLM:0[thermalsensor:0]): 50.
    The valid values for 'ThermalSensorReading' are in the range 0 - 127 (inclusive).
    'ThermalSensorReading' is a read-only attribute.
    'ThermalSensorReading' can use the following target types: Thermal Sensor.


  Attribute 'ThermalSensorProvider' (GSLM:0[thermalsensor:0]): 1.
    'ThermalSensorProvider' is an integer attribute.
    'ThermalSensorProvider' is a read-only attribute.
    'ThermalSensorProvider' can use the following target types: Thermal Sensor.


  Attribute 'ThermalSensorTarget' (GSLM:0[thermalsensor:0]): 1.
    'ThermalSensorTarget' is an integer attribute.
    'ThermalSensorTarget' is a read-only attribute.
    'ThermalSensorTarget' can use the following target types: Thermal Sensor.

```

No fan control attrs found.  Any idea?

---

