---
title: "Do I need irqbalance service on my home laptop ?"
date: 2023-11-12
forum: General Help
---

### Post by nilovsergey on 2023-11-12
Do I need irqbalance service on my home laptop with kubuntu 2022.04 ?

What I see in hardinfo 
[IMG]https://img001.prntscr.com/file/img001/CtX96yJaQjSn5rragd-DDA.png[/IMG]

In net I found :

       ```
irqbalance - distribute hardware interrupts across processors on a multiprocessor system
```

I want to disable services I do not need...

I suppose I can disable this service, but not sure actually...

---

### Post by MAFoElffen on 2023-11-12
No. It needs to run at least once during the boot sequence...

Here is the service:
```

mafoelffen@Mikes-B460M:/data/ISO$ grep . /usr/lib/systemd/system/irqbalance.service
[Unit]
Description=irqbalance daemon
Documentation=man:irqbalance(1)
Documentation=https://github.com/Irqbalance/irqbalance
ConditionVirtualization=!container
[Service]
EnvironmentFile=-/usr/lib/irqbalance/defaults.env
EnvironmentFile=-/etc/default/irqbalance
ExecStart=/usr/sbin/irqbalance --foreground $IRQBALANCE_ARGS
CapabilityBoundingSet=
NoNewPrivileges=yes
ReadOnlyPaths=/
ReadWritePaths=/proc/irq
RestrictAddressFamilies=AF_UNIX
RuntimeDirectory=irqbalance/
[Install]
WantedBy=multi-user.target

```
Here is what RedHat says in their Doc's
RE: [https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/performance_tuning_guide/sect-red_hat_enterprise_linux-performance_tuning_guide-tool_reference-irqbalance](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/performance_tuning_guide/sect-red_hat_enterprise_linux-performance_tuning_guide-tool_reference-irqbalance)
> 
irqbalance is a command line tool that distributes hardware interrupts across processors to improve system performance. It runs as a daemon by default, but can be run once only with the --oneshot option. 

Which means it you add this line to the "[Service]" section, it will run on-demand, once, instead of being loaded as a daemon...
```

...
[Service]
Type=oneshot
...

```

---

