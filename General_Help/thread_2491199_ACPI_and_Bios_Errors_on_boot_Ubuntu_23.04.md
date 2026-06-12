---
title: "ACPI and Bios Errors on boot Ubuntu 23.04"
date: 2023-09-29
forum: General Help
---

### Post by heyashy on 2023-09-29
Hi Everyone,

I was wondering if anyone could help me. I have been getting errors on boot (ACPI, BIOS). I have run a grub repair and the problem still percists. I am running Ubuntu 23.04 on:

**HOST**: ROG Zephyrus M16 GU603ZX_GU603ZX 1.0.
**CPU**: 12th Gen Intel i9-12900H (20) @ 4.900GHz
**GPU**: NVIDIA GeForce RTX 3080 Ti Mobile
**GPU**: Intel Alder Lake-P 
**Memory**: 7430MiB / 31774MiB 



The errors from dmesg -l err,warn,emerg,alert,crit are as follows:

```

[COLOR=#BBBBBB][FONT=&amp][    [COLOR=#f09483]0[/COLOR].[COLOR=#f09483]000000[/COLOR]] [Firmware Bug]: TSC ADJUST: CPU0: -[COLOR=#f09483]1279980203[/COLOR] force to [COLOR=#f09483]0[/COLOR]
[    [COLOR=#f09483]0[/COLOR].[COLOR=#f09483]010413[/COLOR]] [Firmware Bug]: TSC ADJUST differs within socket(s), fixing all errors
[    [COLOR=#f09483]0[/COLOR].[COLOR=#f09483]121816[/COLOR]]   #[COLOR=#f09483]2[/COLOR]  #[COLOR=#f09483]3[/COLOR]  #[COLOR=#f09483]4[/COLOR]  #[COLOR=#f09483]5[/COLOR]  #[COLOR=#f09483]6[/COLOR]  #[COLOR=#f09483]7[/COLOR]  #[COLOR=#f09483]8[/COLOR]  #[COLOR=#f09483]9[/COLOR] #[COLOR=#f09483]10[/COLOR] #[COLOR=#f09483]11[/COLOR] #[COLOR=#f09483]12[/COLOR]
[    [COLOR=#f09483]0[/COLOR].[COLOR=#f09483]325755[/COLOR]]  #[COLOR=#f09483]13[/COLOR] #[COLOR=#f09483]14[/COLOR] #[COLOR=#f09483]15[/COLOR] #[COLOR=#f09483]16[/COLOR] #[COLOR=#f09483]17[/COLOR] #[COLOR=#f09483]18[/COLOR] #[COLOR=#f09483]19[/COLOR]
[    [COLOR=#f09483]0[/COLOR].[COLOR=#f09483]429949[/COLOR]] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]264075[/COLOR]] pnp [COLOR=#d5d8da]*00:03*[/COLOR]: disabling [mem [COLOR=#f09483]0xc0000000[/COLOR]-[COLOR=#f09483]0xcfffffff[/COLOR]] because it overlaps [COLOR=#f09483]0000:00:02[/COLOR].[COLOR=#f09483]0[/COLOR] BAR [COLOR=#f09483]9[/COLOR] [mem [COLOR=#f09483]0x00000000[/COLOR]-[COLOR=#f09483]0xdfffffff[/COLOR] 64bit pref]
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]290805[/COLOR]] hpet_acpi_add: no address or irqs in _CRS
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]301510[/COLOR]] i8042: PNP: PS/[COLOR=#f09483]2[/COLOR] appears to have AUX port disabled, if this is incorrect please boot with [COLOR=#f09483]i8042.nopnp[/COLOR]
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]305635[/COLOR]] device-mapper: core: CONFIG_IMA_DISABLE_HTABLE is disabled. Duplicate IMA measurements will not be recorded in the IMA log.
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]305696[/COLOR]] platform [COLOR=#f09483]eisa.0[/COLOR]: EISA: Cannot allocate resource for mainboard
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]305696[/COLOR]] platform [COLOR=#f09483]eisa.0[/COLOR]: Cannot allocate resource for EISA slot [COLOR=#f09483]1[/COLOR]
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]305697[/COLOR]] platform [COLOR=#f09483]eisa.0[/COLOR]: Cannot allocate resource for EISA slot [COLOR=#f09483]2[/COLOR]
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]305697[/COLOR]] platform [COLOR=#f09483]eisa.0[/COLOR]: Cannot allocate resource for EISA slot [COLOR=#f09483]3[/COLOR]
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]305698[/COLOR]] platform [COLOR=#f09483]eisa.0[/COLOR]: Cannot allocate resource for EISA slot [COLOR=#f09483]4[/COLOR]
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]305698[/COLOR]] platform [COLOR=#f09483]eisa.0[/COLOR]: Cannot allocate resource for EISA slot [COLOR=#f09483]5[/COLOR]
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]305699[/COLOR]] platform [COLOR=#f09483]eisa.0[/COLOR]: Cannot allocate resource for EISA slot [COLOR=#f09483]6[/COLOR]
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]305699[/COLOR]] platform [COLOR=#f09483]eisa.0[/COLOR]: Cannot allocate resource for EISA slot [COLOR=#f09483]7[/COLOR]
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]305700[/COLOR]] platform [COLOR=#f09483]eisa.0[/COLOR]: Cannot allocate resource for EISA slot [COLOR=#f09483]8[/COLOR]
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]624276[/COLOR]] pci [COLOR=#f09483]10000:e0:06[/COLOR].[COLOR=#f09483]0[/COLOR]: Primary bus is hard wired to [COLOR=#f09483]0[/COLOR]
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]625025[/COLOR]] pci [COLOR=#f09483]10000:e0:06[/COLOR].[COLOR=#f09483]2[/COLOR]: Primary bus is hard wired to [COLOR=#f09483]0[/COLOR]
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]625576[/COLOR]] pci [COLOR=#f09483]10000:e0:06[/COLOR].[COLOR=#f09483]0[/COLOR]: Primary bus is hard wired to [COLOR=#f09483]0[/COLOR]
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]625582[/COLOR]] pci [COLOR=#f09483]10000:e0:06[/COLOR].[COLOR=#f09483]2[/COLOR]: Primary bus is hard wired to [COLOR=#f09483]0[/COLOR]
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]826681[/COLOR]] pcieport [COLOR=#f09483]10000:e0:06[/COLOR].[COLOR=#f09483]0[/COLOR]: can't derive routing for PCI INT D
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]826684[/COLOR]] pcieport [COLOR=#f09483]10000:e0:06[/COLOR].[COLOR=#f09483]0[/COLOR]: PCI INT D: no GSI
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]826907[/COLOR]] pcieport [COLOR=#f09483]10000:e0:06[/COLOR].[COLOR=#f09483]2[/COLOR]: can't derive routing for PCI INT B
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]826909[/COLOR]] pcieport [COLOR=#f09483]10000:e0:06[/COLOR].[COLOR=#f09483]2[/COLOR]: PCI INT B: no GSI
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]840352[/COLOR]] pcieport [COLOR=#f09483]10000:e0:06[/COLOR].[COLOR=#f09483]0[/COLOR]: can't derive routing for PCI INT A
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]840353[/COLOR]] nvme [COLOR=#f09483]10000:e1:00[/COLOR].[COLOR=#f09483]0[/COLOR]: PCI INT A: not connected
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]840366[/COLOR]] pcieport [COLOR=#f09483]10000:e0:06[/COLOR].[COLOR=#f09483]2[/COLOR]: can't derive routing for PCI INT A
[    [COLOR=#f09483]3[/COLOR].[COLOR=#f09483]840368[/COLOR]] nvme [COLOR=#f09483]10000:e2:00[/COLOR].[COLOR=#f09483]0[/COLOR]: PCI INT A: no GSI
[    [COLOR=#f09483]5[/COLOR].[COLOR=#f09483]564872[/COLOR]] asus [COLOR=#f09483]0003:0B05:19B6[/COLOR].[COLOR=#f09483]0003[/COLOR]: Asus input not registered
[    [COLOR=#f09483]5[/COLOR].[COLOR=#f09483]565870[/COLOR]] asus: probe of [COLOR=#f09483]0003:0B05:19B6[/COLOR].[COLOR=#f09483]0003[/COLOR] failed with error -[COLOR=#f09483]12[/COLOR]
[    [COLOR=#f09483]8[/COLOR].[COLOR=#f09483]725227[/COLOR]] systemd[[COLOR=#f09483]1[/COLOR]]: Configuration file /etc/systemd/system/darktrace-[COLOR=#f09483]ebpf.service[/COLOR] is marked world-inaccessible. This has no effect as configuration data is accessible via APIs without restrictions. Proceeding anyway.
[    [COLOR=#f09483]8[/COLOR].[COLOR=#f09483]725383[/COLOR]] systemd[[COLOR=#f09483]1[/COLOR]]: Configuration file /etc/systemd/system/darktrace-[COLOR=#f09483]csensor.service[/COLOR] is marked world-inaccessible. This has no effect as configuration data is accessible via APIs without restrictions. Proceeding anyway.
[    [COLOR=#f09483]8[/COLOR].[COLOR=#f09483]926089[/COLOR]] systemd-journald[[COLOR=#f09483]1706[/COLOR]]: File /var/log/journal/[COLOR=#f09483]7711048590d64226a834a0919c0619ca[/COLOR]/system.journal corrupted or uncleanly shut down, renaming and replacing.
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]024503[/COLOR]] ACPI BIOS Error (bug): Could not resolve symbol [\CTDP], AE_NOT_FOUND ([COLOR=#f09483]20221020[/COLOR]/psargs-[COLOR=#f09483]330[/COLOR])

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]024561[/COLOR]] No Local Variables are initialized for Method [IDSP]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]024563[/COLOR]] No Arguments are initialized for method [IDSP]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]024565[/COLOR]] ACPI Error: Aborting method \_SB.[COLOR=#f09483]IETM.IDSP[/COLOR] due to previous error (AE_NOT_FOUND) ([COLOR=#f09483]20221020[/COLOR]/psparse-[COLOR=#f09483]529[/COLOR])
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]024630[/COLOR]] ACPI Warning: \_SB.[COLOR=#f09483]IETM._TRT[/COLOR]: Return Package has no elements (empty) ([COLOR=#f09483]20221020[/COLOR]/nsprepkg-[COLOR=#f09483]94[/COLOR])
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]038939[/COLOR]] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN1._CRT.S1CT[/COLOR]], AE_NOT_FOUND ([COLOR=#f09483]20221020[/COLOR]/psargs-[COLOR=#f09483]330[/COLOR])

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]039009[/COLOR]] No Local Variables are initialized for Method [_CRT]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]039011[/COLOR]] No Arguments are initialized for method [_CRT]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]039013[/COLOR]] ACPI Error: Aborting method \_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN1._CRT[/COLOR] due to previous error (AE_NOT_FOUND) ([COLOR=#f09483]20221020[/COLOR]/psparse-[COLOR=#f09483]529[/COLOR])
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]039103[/COLOR]] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN1._HOT.S1HT[/COLOR]], AE_NOT_FOUND ([COLOR=#f09483]20221020[/COLOR]/psargs-[COLOR=#f09483]330[/COLOR])

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]039167[/COLOR]] No Local Variables are initialized for Method [_HOT]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]039169[/COLOR]] No Arguments are initialized for method [_HOT]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]039171[/COLOR]] ACPI Error: Aborting method \_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN1._HOT[/COLOR] due to previous error (AE_NOT_FOUND) ([COLOR=#f09483]20221020[/COLOR]/psparse-[COLOR=#f09483]529[/COLOR])
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]039257[/COLOR]] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN1._PSV.S1PT[/COLOR]], AE_NOT_FOUND ([COLOR=#f09483]20221020[/COLOR]/psargs-[COLOR=#f09483]330[/COLOR])

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]039318[/COLOR]] No Local Variables are initialized for Method [_PSV]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]039320[/COLOR]] No Arguments are initialized for method [_PSV]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]039322[/COLOR]] ACPI Error: Aborting method \_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN1._PSV[/COLOR] due to previous error (AE_NOT_FOUND) ([COLOR=#f09483]20221020[/COLOR]/psparse-[COLOR=#f09483]529[/COLOR])
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]039419[/COLOR]] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN1._AC0.S1AT[/COLOR]], AE_NOT_FOUND ([COLOR=#f09483]20221020[/COLOR]/psargs-[COLOR=#f09483]330[/COLOR])

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]039480[/COLOR]] No Local Variables are initialized for Method [_AC0]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]039481[/COLOR]] No Arguments are initialized for method [_AC0]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]039483[/COLOR]] ACPI Error: Aborting method \_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN1._AC0[/COLOR] due to previous error (AE_NOT_FOUND) ([COLOR=#f09483]20221020[/COLOR]/psparse-[COLOR=#f09483]529[/COLOR])
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]045316[/COLOR]] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN2._CRT.S2CT[/COLOR]], AE_NOT_FOUND ([COLOR=#f09483]20221020[/COLOR]/psargs-[COLOR=#f09483]330[/COLOR])

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]045393[/COLOR]] No Local Variables are initialized for Method [_CRT]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]045395[/COLOR]] No Arguments are initialized for method [_CRT]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]045397[/COLOR]] ACPI Error: Aborting method \_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN2._CRT[/COLOR] due to previous error (AE_NOT_FOUND) ([COLOR=#f09483]20221020[/COLOR]/psparse-[COLOR=#f09483]529[/COLOR])
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]046986[/COLOR]] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN2._HOT.S2HT[/COLOR]], AE_NOT_FOUND ([COLOR=#f09483]20221020[/COLOR]/psargs-[COLOR=#f09483]330[/COLOR])

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]047060[/COLOR]] No Local Variables are initialized for Method [_HOT]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]047062[/COLOR]] No Arguments are initialized for method [_HOT]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]047064[/COLOR]] ACPI Error: Aborting method \_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN2._HOT[/COLOR] due to previous error (AE_NOT_FOUND) ([COLOR=#f09483]20221020[/COLOR]/psparse-[COLOR=#f09483]529[/COLOR])
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]047172[/COLOR]] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN2._PSV.S2PT[/COLOR]], AE_NOT_FOUND ([COLOR=#f09483]20221020[/COLOR]/psargs-[COLOR=#f09483]330[/COLOR])

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]047239[/COLOR]] No Local Variables are initialized for Method [_PSV]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]047240[/COLOR]] No Arguments are initialized for method [_PSV]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]047242[/COLOR]] ACPI Error: Aborting method \_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN2._PSV[/COLOR] due to previous error (AE_NOT_FOUND) ([COLOR=#f09483]20221020[/COLOR]/psparse-[COLOR=#f09483]529[/COLOR])
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]047346[/COLOR]] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN2._AC0.S2AT[/COLOR]], AE_NOT_FOUND ([COLOR=#f09483]20221020[/COLOR]/psargs-[COLOR=#f09483]330[/COLOR])

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]047413[/COLOR]] No Local Variables are initialized for Method [_AC0]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]047415[/COLOR]] No Arguments are initialized for method [_AC0]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]047417[/COLOR]] ACPI Error: Aborting method \_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN2._AC0[/COLOR] due to previous error (AE_NOT_FOUND) ([COLOR=#f09483]20221020[/COLOR]/psparse-[COLOR=#f09483]529[/COLOR])
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]050952[/COLOR]] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN3._CRT.S3CT[/COLOR]], AE_NOT_FOUND ([COLOR=#f09483]20221020[/COLOR]/psargs-[COLOR=#f09483]330[/COLOR])

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]051005[/COLOR]] No Local Variables are initialized for Method [_CRT]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]051006[/COLOR]] No Arguments are initialized for method [_CRT]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]051008[/COLOR]] ACPI Error: Aborting method \_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN3._CRT[/COLOR] due to previous error (AE_NOT_FOUND) ([COLOR=#f09483]20221020[/COLOR]/psparse-[COLOR=#f09483]529[/COLOR])
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]051077[/COLOR]] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN3._HOT.S3HT[/COLOR]], AE_NOT_FOUND ([COLOR=#f09483]20221020[/COLOR]/psargs-[COLOR=#f09483]330[/COLOR])

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]051133[/COLOR]] No Local Variables are initialized for Method [_HOT]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]051135[/COLOR]] No Arguments are initialized for method [_HOT]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]051136[/COLOR]] ACPI Error: Aborting method \_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN3._HOT[/COLOR] due to previous error (AE_NOT_FOUND) ([COLOR=#f09483]20221020[/COLOR]/psparse-[COLOR=#f09483]529[/COLOR])
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]051200[/COLOR]] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN3._PSV.S3PT[/COLOR]], AE_NOT_FOUND ([COLOR=#f09483]20221020[/COLOR]/psargs-[COLOR=#f09483]330[/COLOR])

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]051256[/COLOR]] No Local Variables are initialized for Method [_PSV]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]051258[/COLOR]] No Arguments are initialized for method [_PSV]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]051259[/COLOR]] ACPI Error: Aborting method \_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN3._PSV[/COLOR] due to previous error (AE_NOT_FOUND) ([COLOR=#f09483]20221020[/COLOR]/psparse-[COLOR=#f09483]529[/COLOR])
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]051291[/COLOR]] resource: resource sanity check: requesting [mem [COLOR=#f09483]0x00000000fedc0000[/COLOR]-[COLOR=#f09483]0x00000000fedcffff[/COLOR]], which spans more than pnp [COLOR=#d5d8da]*00:03*[/COLOR] [mem [COLOR=#f09483]0xfedc0000[/COLOR]-[COLOR=#f09483]0xfedc7fff[/COLOR]]
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]051308[/COLOR]] caller igen6_probe+[COLOR=#f09483]0x1c4[/COLOR]/[COLOR=#f09483]0x610[/COLOR] [igen6_edac] mapping multiple BARs
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]053606[/COLOR]] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN4._CRT.S4CT[/COLOR]], AE_NOT_FOUND ([COLOR=#f09483]20221020[/COLOR]/psargs-[COLOR=#f09483]330[/COLOR])

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]053679[/COLOR]] No Local Variables are initialized for Method [_CRT]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]053681[/COLOR]] No Arguments are initialized for method [_CRT]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]053683[/COLOR]] ACPI Error: Aborting method \_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN4._CRT[/COLOR] due to previous error (AE_NOT_FOUND) ([COLOR=#f09483]20221020[/COLOR]/psparse-[COLOR=#f09483]529[/COLOR])
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]053780[/COLOR]] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN4._HOT.S4HT[/COLOR]], AE_NOT_FOUND ([COLOR=#f09483]20221020[/COLOR]/psargs-[COLOR=#f09483]330[/COLOR])

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]053844[/COLOR]] No Local Variables are initialized for Method [_HOT]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]053846[/COLOR]] No Arguments are initialized for method [_HOT]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]053847[/COLOR]] ACPI Error: Aborting method \_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN4._HOT[/COLOR] due to previous error (AE_NOT_FOUND) ([COLOR=#f09483]20221020[/COLOR]/psparse-[COLOR=#f09483]529[/COLOR])
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]053943[/COLOR]] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN4._PSV.S4PT[/COLOR]], AE_NOT_FOUND ([COLOR=#f09483]20221020[/COLOR]/psargs-[COLOR=#f09483]330[/COLOR])

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]054008[/COLOR]] No Local Variables are initialized for Method [_PSV]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]054010[/COLOR]] No Arguments are initialized for method [_PSV]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]054012[/COLOR]] ACPI Error: Aborting method \_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN4._PSV[/COLOR] due to previous error (AE_NOT_FOUND) ([COLOR=#f09483]20221020[/COLOR]/psparse-[COLOR=#f09483]529[/COLOR])
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]054109[/COLOR]] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN4._AC0.S4AT[/COLOR]], AE_NOT_FOUND ([COLOR=#f09483]20221020[/COLOR]/psargs-[COLOR=#f09483]330[/COLOR])

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]054173[/COLOR]] No Local Variables are initialized for Method [_AC0]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]054174[/COLOR]] No Arguments are initialized for method [_AC0]

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]054176[/COLOR]] ACPI Error: Aborting method \_SB.[COLOR=#f09483]PC00.LPCB.EC0.SEN4._AC0[/COLOR] due to previous error (AE_NOT_FOUND) ([COLOR=#f09483]20221020[/COLOR]/psparse-[COLOR=#f09483]529[/COLOR])
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]194327[/COLOR]] iwlwifi [COLOR=#f09483]0000:00:14[/COLOR].[COLOR=#f09483]3[/COLOR]: api flags index [COLOR=#f09483]2[/COLOR] larger than supported by driver
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]292828[/COLOR]] nvidia: loading out-of-tree module taints kernel.
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]292836[/COLOR]] nvidia: module license 'NVIDIA' taints kernel.
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]292836[/COLOR]] Disabling lock debugging due to kernel taint

[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]455279[/COLOR]] thermal thermal_zone8: failed to read out thermal zone (-[COLOR=#f09483]61[/COLOR])
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]487367[/COLOR]] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  [COLOR=#f09483]535[/COLOR].[COLOR=#f09483]113[/COLOR].[COLOR=#f09483]01[/COLOR]  Tue Sep [COLOR=#f09483]12[/COLOR] [COLOR=#d5d8da]*19:41:24*[/COLOR] UTC [COLOR=#f09483]2023[/COLOR]
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]534922[/COLOR]] ACPI Warning: \_SB.[COLOR=#f09483]NPCF._DSM[/COLOR]: Argument #[COLOR=#f09483]4[/COLOR] type mismatch - Found [Buffer], ACPI requires [Package] ([COLOR=#f09483]20221020[/COLOR]/nsarguments-[COLOR=#f09483]61[/COLOR])
[    [COLOR=#f09483]9[/COLOR].[COLOR=#f09483]534966[/COLOR]] ACPI Warning: \_SB.[COLOR=#f09483]PC00.PEG1.PEGP._DSM[/COLOR]: Argument #[COLOR=#f09483]4[/COLOR] type mismatch - Found [Buffer], ACPI requires [Package] ([COLOR=#f09483]20221020[/COLOR]/nsarguments-[COLOR=#f09483]61[/COLOR])
[   [COLOR=#f09483]10[/COLOR].[COLOR=#f09483]536149[/COLOR]] nvidia_uvm: module uses symbols nvUvmInterfaceDisableAccessCntr from proprietary module nvidia, inheriting taint.
[   [COLOR=#f09483]10[/COLOR].[COLOR=#f09483]699275[/COLOR]] Bluetooth: hci0: Malformed MSFT vendor event: [COLOR=#f09483]0x02[/COLOR]
[   [COLOR=#f09483]11[/COLOR].[COLOR=#f09483]093603[/COLOR]] systemd-journald[[COLOR=#f09483]1706[/COLOR]]: File /var/log/journal/[COLOR=#f09483]7711048590d64226a834a0919c0619ca[/COLOR]/user-[COLOR=#f09483]1000[/COLOR].journal corrupted or uncleanly shut down, renaming and replacing.
[   [COLOR=#f09483]11[/COLOR].[COLOR=#f09483]712758[/COLOR]] ACPI BIOS Error (bug): Could not resolve symbol [\CTDP], AE_NOT_FOUND ([COLOR=#f09483]20221020[/COLOR]/psargs-[COLOR=#f09483]330[/COLOR])

[   [COLOR=#f09483]11[/COLOR].[COLOR=#f09483]712814[/COLOR]] No Local Variables are initialized for Method [IDSP]

[   [COLOR=#f09483]11[/COLOR].[COLOR=#f09483]712815[/COLOR]] No Arguments are initialized for method [IDSP]

[   [COLOR=#f09483]11[/COLOR].[COLOR=#f09483]712816[/COLOR]] ACPI Error: Aborting method \_SB.[COLOR=#f09483]IETM.IDSP[/COLOR] due to previous error (AE_NOT_FOUND) ([COLOR=#f09483]20221020[/COLOR]/psparse-[COLOR=#f09483]529[/COLOR])
[   [COLOR=#f09483]11[/COLOR].[COLOR=#f09483]712854[/COLOR]] ACPI Error: Aborting method \_SB.[COLOR=#f09483]IETM._OSC[/COLOR] due to previous error (AE_NOT_FOUND) ([COLOR=#f09483]20221020[/COLOR]/psparse-[COLOR=#f09483]529[/COLOR])
[   [COLOR=#f09483]16[/COLOR].[COLOR=#f09483]167276[/COLOR]] kauditd_printk_skb: [COLOR=#f09483]100[/COLOR] callbacks suppressed
[   [COLOR=#f09483]25[/COLOR].[COLOR=#f09483]893365[/COLOR]] kauditd_printk_skb: [COLOR=#f09483]12[/COLOR] callbacks suppressed
[  [COLOR=#f09483]367[/COLOR].[COLOR=#f09483]430992[/COLOR]] i915 [COLOR=#f09483]0000:00:02[/COLOR].[COLOR=#f09483]0[/COLOR]: [drm] *ERROR* GuC engine reset request failed on [COLOR=#f09483]0[/COLOR]:[COLOR=#f09483]0[/COLOR] (rcs0) because [COLOR=#f09483]0x00000000[/COLOR]
[  [COLOR=#f09483]367[/COLOR].[COLOR=#f09483]543368[/COLOR]] i915 [COLOR=#f09483]0000:00:02[/COLOR].[COLOR=#f09483]0[/COLOR]: [drm] *ERROR* rcs0 reset request timed out: {request: [COLOR=#f09483]00000001[/COLOR], RESET_CTL: [COLOR=#f09483]00000001[/COLOR]}
[  [COLOR=#f09483]367[/COLOR].[COLOR=#f09483]544074[/COLOR]] i915 [COLOR=#f09483]0000:00:02[/COLOR].[COLOR=#f09483]0[/COLOR]: [drm] *ERROR* rcs0 reset request timed out: {request: [COLOR=#f09483]00000001[/COLOR], RESET_CTL: [COLOR=#f09483]00000001[/COLOR]}
[  [COLOR=#f09483]376[/COLOR].[COLOR=#f09483]866527[/COLOR]] i915 [COLOR=#f09483]0000:00:02[/COLOR].[COLOR=#f09483]0[/COLOR]: [drm] *ERROR* GuC engine reset request failed on [COLOR=#f09483]0[/COLOR]:[COLOR=#f09483]0[/COLOR] (rcs0) because [COLOR=#f09483]0x00000000[/COLOR]
[  [COLOR=#f09483]376[/COLOR].[COLOR=#f09483]979177[/COLOR]] i915 [COLOR=#f09483]0000:00:02[/COLOR].[COLOR=#f09483]0[/COLOR]: [drm] *ERROR* rcs0 reset request timed out: {request: [COLOR=#f09483]00000001[/COLOR], RESET_CTL: [COLOR=#f09483]00000001[/COLOR]}
[  [COLOR=#f09483]376[/COLOR].[COLOR=#f09483]979883[/COLOR]] i915 [COLOR=#f09483]0000:00:02[/COLOR].[COLOR=#f09483]0[/COLOR]: [drm] *ERROR* rcs0 reset request timed out: {request: [COLOR=#f09483]00000001[/COLOR], RESET_CTL: [COLOR=#f09483]00000001[/COLOR]}
[  [COLOR=#f09483]388[/COLOR].[COLOR=#f09483]418950[/COLOR]] i915 [COLOR=#f09483]0000:00:02[/COLOR].[COLOR=#f09483]0[/COLOR]: [drm] *ERROR* GuC engine reset request failed on [COLOR=#f09483]0[/COLOR]:[COLOR=#f09483]0[/COLOR] (rcs0) because [COLOR=#f09483]0x00000000[/COLOR]
[  [COLOR=#f09483]388[/COLOR].[COLOR=#f09483]531116[/COLOR]] i915 [COLOR=#f09483]0000:00:02[/COLOR].[COLOR=#f09483]0[/COLOR]: [drm] *ERROR* rcs0 reset request timed out: {request: [COLOR=#f09483]00000001[/COLOR], RESET_CTL: [COLOR=#f09483]00000001[/COLOR]}
[  [COLOR=#f09483]388[/COLOR].[COLOR=#f09483]531825[/COLOR]] i915 [COLOR=#f09483]0000:00:02[/COLOR].[COLOR=#f09483]0[/COLOR]: [drm] *ERROR* rcs0 reset request timed out: {request: [COLOR=#f09483]00000001[/COLOR], RESET_CTL: [COLOR=#f09483]00000001[/COLOR]}
[  [COLOR=#f09483]503[/COLOR].[COLOR=#f09483]449228[/COLOR]] i915 [COLOR=#f09483]0000:00:02[/COLOR].[COLOR=#f09483]0[/COLOR]: [drm] *ERROR* GuC engine reset request failed on [COLOR=#f09483]0[/COLOR]:[COLOR=#f09483]0[/COLOR] (rcs0) because [COLOR=#f09483]0x00000000[/COLOR]
[  [COLOR=#f09483]503[/COLOR].[COLOR=#f09483]561446[/COLOR]] i915 [COLOR=#f09483]0000:00:02[/COLOR].[COLOR=#f09483]0[/COLOR]: [drm] *ERROR* rcs0 reset request timed out: {request: [COLOR=#f09483]00000001[/COLOR], RESET_CTL: [COLOR=#f09483]00000001[/COLOR]}
[  [COLOR=#f09483]503[/COLOR].[COLOR=#f09483]562153[/COLOR]] i915 [COLOR=#f09483]0000:00:02[/COLOR].[COLOR=#f09483]0[/COLOR]: [drm] *ERROR* rcs0 reset request timed out: {request: [COLOR=#f09483]00000001[/COLOR], RESET_CTL: [COLOR=#f09483]00000001[/COLOR]}
[  [COLOR=#f09483]514[/COLOR].[COLOR=#f09483]603632[/COLOR]] i915 [COLOR=#f09483]0000:00:02[/COLOR].[COLOR=#f09483]0[/COLOR]: [drm] *ERROR* GuC engine reset request failed on [COLOR=#f09483]0[/COLOR]:[COLOR=#f09483]0[/COLOR] (rcs0) because [COLOR=#f09483]0x00000000[/COLOR]
[  [COLOR=#f09483]514[/COLOR].[COLOR=#f09483]721392[/COLOR]] i915 [COLOR=#f09483]0000:00:02[/COLOR].[COLOR=#f09483]0[/COLOR]: [drm] *ERROR* rcs0 reset request timed out: {request: [COLOR=#f09483]00000001[/COLOR], RESET_CTL: [COLOR=#f09483]00000001[/COLOR]}
[  [COLOR=#f09483]514[/COLOR].[COLOR=#f09483]722110[/COLOR]] i915 [COLOR=#f09483]0000:00:02[/COLOR].[COLOR=#f09483]0[/COLOR]: [drm] *ERROR* rcs0 reset request timed out: {request: [COLOR=#f09483]00000001[/COLOR], RESET_CTL: [COLOR=#f09483]00000001[/COLOR]}
[  [COLOR=#f09483]523[/COLOR].[COLOR=#f09483]616947[/COLOR]] i915 [COLOR=#f09483]0000:00:02[/COLOR].[COLOR=#f09483]0[/COLOR]: [drm] *ERROR* GuC engine reset request failed on [COLOR=#f09483]0[/COLOR]:[COLOR=#f09483]0[/COLOR] (rcs0) because [COLOR=#f09483]0x00000000[/COLOR]
[  [COLOR=#f09483]523[/COLOR].[COLOR=#f09483]733127[/COLOR]] i915 [COLOR=#f09483]0000:00:02[/COLOR].[COLOR=#f09483]0[/COLOR]: [drm] *ERROR* rcs0 reset request timed out: {request: [COLOR=#f09483]00000001[/COLOR], RESET_CTL: [COLOR=#f09483]00000001[/COLOR]}
[  [COLOR=#f09483]523[/COLOR].[COLOR=#f09483]733838[/COLOR]] i915 [COLOR=#f09483]0000:00:02[/COLOR].[COLOR=#f09483]0[/COLOR]: [drm] *ERROR* rcs0 reset request timed out: {request: [COLOR=#f09483]00000001[/COLOR], RESET_CTL: [COLOR=#f09483]00000001[/COLOR]}

[/FONT][/COLOR]

```

---

### Post by MAFoElffen on 2023-09-29
Besides the errors messages, does everything seem to work okay? Or do some things not work? (Like the sound?)

I don't want to tell you to disable something in ACPI, if the 'loglevel' of your boot messages default is just being set wrong...

---

