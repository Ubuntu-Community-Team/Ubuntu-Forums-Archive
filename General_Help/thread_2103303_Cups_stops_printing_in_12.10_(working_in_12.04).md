---
title: "Cups stops printing in 12.10 (working in 12.04)"
date: 2013-01-09
forum: General Help
---

### Post by vortex-5 on 2013-01-09
I used to print fine in Ubuntu 12.04 but since the upgrade to Ubuntu 12.10 now I can no longer print from the raw print queues over the network the job arrives fine and CUPS accepts it but it just stays there with the printer light blinking forever.

I can print if I use the Poscript print driver. Unfortunately I need the raw printer queue working.

Can anyone help?

mime.convs 

```

application/octet-stream	application/vnd.cups-raw	0	-

```

mime.types 

```

application/octet-stream

```


Here is /var/log/cups/error_log

```

W [09/Jan/2013:20:22:33 -0500] No limit for Cancel-Jobs defined in policy default - using Pause-Printer's policy.
W [09/Jan/2013:20:22:33 -0500] No limit for Cancel-My-Jobs defined in policy default - using Send-Document's policy.
W [09/Jan/2013:20:22:33 -0500] No limit for Close-Job defined in policy default - using Send-Document's policy.
W [09/Jan/2013:20:22:33 -0500] No JobPrivateAccess defined in policy default - using defaults.
W [09/Jan/2013:20:22:33 -0500] No JobPrivateValues defined in policy default - using defaults.
W [09/Jan/2013:20:22:33 -0500] No SubscriptionPrivateAccess defined in policy default - using defaults.
W [09/Jan/2013:20:22:33 -0500] No SubscriptionPrivateValues defined in policy default - using defaults.
W [09/Jan/2013:20:22:33 -0500] No limit for Cancel-Jobs defined in policy authenticated - using Pause-Printer's policy.
W [09/Jan/2013:20:22:33 -0500] No limit for Cancel-My-Jobs defined in policy authenticated - using Send-Document's policy.
W [09/Jan/2013:20:22:33 -0500] No limit for Close-Job defined in policy authenticated - using Send-Document's policy.
W [09/Jan/2013:20:22:33 -0500] No JobPrivateAccess defined in policy authenticated - using defaults.
W [09/Jan/2013:20:22:33 -0500] No JobPrivateValues defined in policy authenticated - using defaults.
W [09/Jan/2013:20:22:33 -0500] No SubscriptionPrivateAccess defined in policy authenticated - using defaults.
W [09/Jan/2013:20:22:33 -0500] No SubscriptionPrivateValues defined in policy authenticated - using defaults.
E [09/Jan/2013:20:22:33 -0500] Filter "oopstops" not found.
E [09/Jan/2013:20:22:33 -0500] Filter "hpgltops" not found.
E [09/Jan/2013:20:22:33 -0500] Filter "pstoraster" not found.
W [09/Jan/2013:20:22:33 -0500] AddProfile failed: org.freedesktop.DBus.Error.UnknownMethod:No such interface `org.freedesktop.ColorManager' on object at path /org/freedesktop/ColorManager/devices/cups_SCX_4200_PostScript
W [09/Jan/2013:20:23:07 -0500] Unexpected 'document-format' operation attribute in a Create-Job request

```

Can anyone suggest anything?

---

