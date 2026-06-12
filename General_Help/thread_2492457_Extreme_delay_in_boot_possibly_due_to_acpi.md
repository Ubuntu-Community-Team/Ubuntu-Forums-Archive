---
title: "Extreme delay in boot possibly due to acpi?"
date: 2023-11-11
forum: General Help
---

### Post by ozialien on 2023-11-11
dmsg:

 
  13.340883] Bluetooth: hci0: AOSP extensions version v1.00
[   13.340890] Bluetooth: hci0: AOSP quality report is supported
[   13.512617] workqueue: acpi_ec_event_processor hogged CPU for >10000us 4 times, consider switching to WQ_UNBOUND
[  100.231342] audit: type=1400 audit(1699740324.115:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="adbd" pid=2279 comm="apparmor_parser"
[  100.231388] audit: type=1400 audit(1699740324.115:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="android_app" pid=2280 comm="apparmor_parser"
[
.....

 124.657155] wlp2s0: associate with 34:98:b5:50:4e:48 (try 1/3)
[  124.666776] wlp2s0: RX ReassocResp from 34:98:b5:50:4e:48 (capab=0x1011 status=0 aid=15)
[  124.704811] wlp2s0: associated
[  124.704884] wlp2s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 34:98:b5:50:4e:48
[  130.633442] systemd-journald[1226]: Time jumped backwards, rotating.
[  288.146798] warning: `ThreadPoolForeg' uses wireless extensions which will stop working for Wi-Fi 7 hardware; use nl80211
[  288.267130] workqueue: acpi_ec_event_processor hogged CPU for >10000us 16 times, consider switching to WQ_UNBOUND
[  569.589813] usb 9-1: new high-speed USB device number 2 using xhci_hcd
[  569.649825] ACPI Error: No handler for Region [ECSI] (000000007ed630c1) [EmbeddedControl] (20230331/evregion-130)
[  569.649849] ACPI Error: Region EmbeddedControl (ID=3) has no handler (20230331/exfldio-261)


[  569.649879] No Local Variables are initialized for Method [ECRD]


[  569.649887] No Arguments are initialized for method [ECRD]


[  569.649898] ACPI Error: Aborting method \_SB.UBTC.ECRD due to previous error (AE_NOT_EXIST) (20230331/psparse-529)
[  569.649925] ACPI Error: Aborting method \_SB.UBTC.NTFY due to previous error (AE_NOT_EXIST) (20230331/psparse-529)
[  569.649949] ACPI Error: Aborting method \_SB.PCI0.LPC0.EC0._Q4F due to previous error (AE_NOT_EXIST) (20230331/psparse-529)

---

### Post by Rubi1200 on 2023-11-12
When you say "extreme delay in boot" what exactly does that mean? To reach the graphical login?

What does this show:
```
sudo systemd-analyze blame

```

When replying please click on Go Advanced >> paste the terminal output in the field >> highlight all the text and wrap with the # tag.

Will make it much easier to analyze.

Thanks.

---

