---
title: "Random shutdown problem"
date: 2015-11-18
forum: General Help
---

### Post by steve202 on 2015-11-18
My system starting shutting down randomly recently the box pops up before asking if id like to lock suspend hibernate or shutdown, if i dont grab keyboard quickly and select suspend it shuts system off. I catured a log from last 20 minutes or so when it atempted to do it, let me know if it isnt enough log i can grab more. I went into bios and disabled cpu temp readings to rule that out, but i watched it before and never saw much over 50c. ```
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  device added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  end _init.
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  Loaded settings plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list. (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-settings-plugin-ifupdown.so)
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  Loaded settings plugin keyfile: (c) 2007 - 2015 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  SCPlugin-Ofono: init!
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <warn>  SCPlugin-Ofono: file doesn't exist: /var/lib/ofono
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  SCPlugin-Ofono: end _init.
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  Loaded settings plugin ofono: (C) 2013 Canonical Ltd.  To report bugs please use the NetworkManager mailing list. (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-settings-plugin-ofono.so)
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  (13947040) ... get_connections.
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  (13947040) ... get_connections (managed=false): return empty list.
Nov 18 19:43:07 nyokie-MIR-795HS avahi-daemon[705]: Found user 'avahi' (UID 107) and group 'avahi' (GID 116).
Nov 18 19:43:07 nyokie-MIR-795HS avahi-daemon[705]: Successfully dropped root privileges.
Nov 18 19:43:07 nyokie-MIR-795HS avahi-daemon[705]: avahi-daemon 0.6.31 starting up.
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  SCPlugin-Ofono: (13787584) ... get_connections.
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  SCPlugin-Ofono: (13787584) connections count: 0
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  get unmanaged devices count: 0
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  monitoring kernel firmware directory '/lib/firmware'.
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  monitoring ifupdown state file '/run/network/ifstate'.
Nov 18 19:43:07 nyokie-MIR-795HS systemd[1]: Started Avahi mDNS/DNS-SD Stack.
Nov 18 19:43:07 nyokie-MIR-795HS avahi-daemon[705]: Successfully called chroot().
Nov 18 19:43:07 nyokie-MIR-795HS avahi-daemon[705]: Successfully dropped remaining capabilities.
Nov 18 19:43:07 nyokie-MIR-795HS systemd[1]: Started Make remote CUPS printers available locally.
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Dumping parsed XML Data
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: *** Index 0 ***
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Name: GenericX86LaptopDevice
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: UUID:
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: type: 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Sensor 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Name: TSKN
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Path:
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Async Capable: 1
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Virtual: 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Zone 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Name: SKIN
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Trip Point 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: temp 55000
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: trip type 2
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: hyst id 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: sensor type TSKN
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: cdev index 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: type rapl_controller
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: influence 100
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: SamplingPeriod 16
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: cdev index 1
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: type intel_powerclamp
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: influence 100
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: SamplingPeriod 12
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: *** Index 1 ***
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Name: ExamplePlatformName
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: UUID: ExampleUUID
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: type: 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Sensor 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Name: TSKN
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Path:
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Async Capable: 1
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Virtual: 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Sensor 1
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Name: example_sensor_1
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Path: /some_path
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Async Capable: 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Virtual: 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Sensor 2
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Name: example_thermal_sysfs_sensor
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Path:
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Async Capable: 1
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Virtual: 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Sensor 3
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Name: example_virtual_sensor
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Path:
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Async Capable: 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Virtual: 1
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Link type: example_sensor_1
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Link mult: 0.500000
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Link offset: 10.000000
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Zone 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Name: ExampleZonetype
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Trip Point 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: temp 75000
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: trip type 1
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: hyst id 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: sensor type example_sensor_1
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: cdev index 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: type example_cooling_device
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: influence 100
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: SamplingPeriod 12
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Cooling Dev 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Type: example_cooling_device
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Path:
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Min: 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Max: 50
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Step: 10
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: AutoDownControl: 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: PID: Kp 0.001000
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: PID: Ki 0.000100
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: PID: Kd 0.000100
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Product Name matched [wildcard]
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: sensor id 1: No temp sysfs for reading raw temp
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: sensor index:0 hwmon /sys/class/hwmon/hwmon2/temp2_input Async:0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: thd_read_default_cooling devices loaded 5 cdevs
Nov 18 19:43:07 nyokie-MIR-795HS avahi-daemon[705]: No service file found in /etc/avahi/services.
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: powercap RAPL no long term time window
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Product Name matched [wildcard]
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: 0: Processor, C:0 MN: 0 MX:3 ST:1 pt:/sys/class/thermal/ rd_bk 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: 1: Processor, C:0 MN: 0 MX:3 ST:1 pt:/sys/class/thermal/ rd_bk 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: 2: Processor, C:0 MN: 0 MX:3 ST:1 pt:/sys/class/thermal/ rd_bk 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: 3: Processor, C:0 MN: 0 MX:3 ST:1 pt:/sys/class/thermal/ rd_bk 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: 4: intel_powerclamp, C:-1 MN: 0 MX:50 ST:5 pt:/sys/class/thermal/ rd_bk 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: 5: cpufreq, C:0 MN: 0 MX:0 ST:1 pt:/sys/devices/system/cpu/ rd_bk 1
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: thd_read_default_thermal_zones loaded 0 zones
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: zone cpu will be created
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: dts zone /sys/devices/platform/coretemp.0/name doesn't exist
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: /sys/class/hwmon/hwmon0/name->nouveau
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: /sys/class/hwmon/hwmon1/name->atk0110
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: /sys/class/hwmon/hwmon2/name->coretemp
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Core temp DTS :critical 105000, max 89000
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Read set point 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Trying to bind hwmon sensor
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Bind hwmon sensor
Nov 18 19:43:07 nyokie-MIR-795HS avahi-daemon[705]: Network interface enumeration completed.
Nov 18 19:43:07 nyokie-MIR-795HS avahi-daemon[705]: Registering HINFO record with values 'X86_64'/'LINUX'.
Nov 18 19:43:07 nyokie-MIR-795HS avahi-daemon[705]: Server startup complete. Host name is nyokie-MIR-795HS.local. Local service cookie is 3640806628.
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: node type: Element, name: CoolingDevice value: rapl_controller
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: node type: Element, name: CoolingDevice value: intel_pstate
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: node type: Element, name: CoolingDevice value: intel_powerclamp
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: node type: Element, name: CoolingDevice value: cpufreq
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: node type: Element, name: CoolingDevice value: Processor
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: CDEVS order specified in thermal-cpu-cdev-order.xml
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Sorted trip dump :
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: index 1: type:passive temp:89000 hyst:0 zone id:0 sensor id:65535 cdev size:3
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: cdev[0] intel_powerclamp
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: cdev[1] cpufreq
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: cdev[2] Processor
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: index 0: type:max temp:96000 hyst:0 zone id:0 sensor id:65535 cdev size:3
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: cdev[0] intel_powerclamp
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: cdev[1] cpufreq
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: cdev[2] Processor
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: trip type: 2 temp: 89000
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: trip type: 1 temp: 96000
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Read set point 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Product Name matched [wildcard]
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: XML zone: invalid sensor type TSKN
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Zone update failed: unable to bind
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Zone 0: cpu, Active:1 Bind:0 Sensor_cnt:1
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: ..sensors..
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: sensor index:0 hwmon /sys/class/hwmon/hwmon2/temp2_input Async:0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: ..trips..
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: index 1: type:passive temp:89000 hyst:0 zone id:0 sensor id:65535 cdev size:3
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: cdev[0] intel_powerclamp
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: cdev[1] cpufreq
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: cdev[2] Processor
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: index 0: type:max temp:96000 hyst:0 zone id:0 sensor id:65535 cdev size:3
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: cdev[0] intel_powerclamp
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: cdev[1] cpufreq
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: cdev[2] Processor
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: FD = 8
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: Current user preference is 0
Nov 18 19:43:07 nyokie-MIR-795HS thermald[621]: thd_engine_thread begin
Nov 18 19:43:07 nyokie-MIR-795HS polkitd[732]: started daemon version 0.105 using authority implementation `local' version `0.105'
Nov 18 19:43:07 nyokie-MIR-795HS dbus[633]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Nov 18 19:43:07 nyokie-MIR-795HS systemd[1]: Started Authenticate and Authorize Users to Run Privileged Tasks.
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  Loaded device plugin: NMVxlanFactory (internal)
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  Loaded device plugin: NMVlanFactory (internal)
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  Loaded device plugin: NMVethFactory (internal)
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  Loaded device plugin: NMTunFactory (internal)
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  Loaded device plugin: NMMacvlanFactory (internal)
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  Loaded device plugin: NMInfinibandFactory (internal)
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  Loaded device plugin: NMGreFactory (internal)
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  Loaded device plugin: NMEthernetFactory (internal)
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  Loaded device plugin: NMBridgeFactory (internal)
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  Loaded device plugin: NMBondFactory (internal)
Nov 18 19:43:07 nyokie-MIR-795HS systemd[1]: Started LSB: Record successful boot for GRUB.
Nov 18 19:43:07 nyokie-MIR-795HS accounts-daemon[614]: started daemon version 0.6.40
Nov 18 19:43:07 nyokie-MIR-795HS systemd[1]: Started Accounts Service.
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so)
Nov 18 19:43:07 nyokie-MIR-795HS NetworkManager[624]: <info>  Loaded device plugin: NMAtmManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-adsl.so)
Nov 18 19:43:08 nyokie-MIR-795HS NetworkManager[624]: <info>  Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wifi.so)
Nov 18 19:43:08 nyokie-MIR-795HS NetworkManager[624]: <info>  Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wwan.so)
Nov 18 19:43:08 nyokie-MIR-795HS NetworkManager[624]: <info>  WiFi enabled by radio killswitch; enabled by state file
Nov 18 19:43:08 nyokie-MIR-795HS NetworkManager[624]: <info>  WWAN enabled by radio killswitch; enabled by state file
Nov 18 19:43:08 nyokie-MIR-795HS NetworkManager[624]: <info>  WiMAX enabled by radio killswitch; enabled by state file
Nov 18 19:43:08 nyokie-MIR-795HS NetworkManager[624]: <info>  Networking is enabled by state file
Nov 18 19:43:08 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): new Ethernet device (carrier: OFF, driver: 'r8169', ifindex: 2)
Nov 18 19:43:08 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 18 19:43:08 nyokie-MIR-795HS kernel: [   31.225388] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 18 19:43:08 nyokie-MIR-795HS kernel: [   31.551585] r8169 0000:02:00.0 eth0: link down
Nov 18 19:43:08 nyokie-MIR-795HS kernel: [   31.551598] r8169 0000:02:00.0 eth0: link down
Nov 18 19:43:08 nyokie-MIR-795HS kernel: [   31.551628] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 18 19:43:08 nyokie-MIR-795HS NetworkManager[624]: <info>  keyfile: add connection in-memory (5ca04a42-297c-4a9f-8184-1855f9566371,"Wired connection 1")
Nov 18 19:43:08 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): created default wired connection 'Wired connection 1'
Nov 18 19:43:08 nyokie-MIR-795HS NetworkManager[624]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Nov 18 19:43:08 nyokie-MIR-795HS NetworkManager[624]: <info>  (lo): link connected
Nov 18 19:43:08 nyokie-MIR-795HS NetworkManager[624]: <info>  (lo): new Generic device (carrier: ON, driver: 'unknown', ifindex: 1)
Nov 18 19:43:08 nyokie-MIR-795HS NetworkManager[624]: <info>  urfkill disappeared from the bus
Nov 18 19:43:08 nyokie-MIR-795HS dbus[633]: [system] Activating via systemd: service name='fi.w1.wpa_supplicant1' unit='wpa_supplicant.service'
Nov 18 19:43:08 nyokie-MIR-795HS systemd[1]: Starting WPA supplicant...
Nov 18 19:43:08 nyokie-MIR-795HS whoopsie[630]: [19:43:08] offline
Nov 18 19:43:08 nyokie-MIR-795HS NetworkManager[624]: <info>  ofono is now available
Nov 18 19:43:08 nyokie-MIR-795HS NetworkManager[624]: <warn>  failed to enumerate oFono devices: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Nov 18 19:43:08 nyokie-MIR-795HS systemd[1]: Started Modem Manager.
Nov 18 19:43:08 nyokie-MIR-795HS NetworkManager[624]: <info>  ModemManager disappeared from bus
Nov 18 19:43:08 nyokie-MIR-795HS NetworkManager[624]: <info>  ModemManager available in the bus
Nov 18 19:43:08 nyokie-MIR-795HS dbus[633]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Nov 18 19:43:08 nyokie-MIR-795HS wpa_supplicant[745]: Successfully initialized wpa_supplicant
Nov 18 19:43:08 nyokie-MIR-795HS systemd[1]: Started WPA supplicant.
Nov 18 19:43:08 nyokie-MIR-795HS NetworkManager[624]: <info>  wpa_supplicant running
Nov 18 19:43:10 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): link connected
Nov 18 19:43:10 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Nov 18 19:43:10 nyokie-MIR-795HS kernel: [   33.262602] r8169 0000:02:00.0 eth0: link up
Nov 18 19:43:10 nyokie-MIR-795HS kernel: [   33.262620] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Nov 18 19:43:10 nyokie-MIR-795HS NetworkManager[624]: <info>  Device 'eth0' has no connection; scheduling activate_check in 0 seconds.
Nov 18 19:43:10 nyokie-MIR-795HS NetworkManager[624]: <info>  Auto-activating connection 'Wired connection 1'.
Nov 18 19:43:10 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): Activation: starting connection 'Wired connection 1' (5ca04a42-297c-4a9f-8184-1855f9566371)
Nov 18 19:43:10 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 18 19:43:10 nyokie-MIR-795HS NetworkManager[624]: <info>  NetworkManager state is now CONNECTING
Nov 18 19:43:10 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 18 19:43:10 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov 18 19:43:10 nyokie-MIR-795HS NetworkManager[624]: <info>  Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Nov 18 19:43:10 nyokie-MIR-795HS ModemManager[629]: <info>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.0': not supported by any plugin
Nov 18 19:43:13 nyokie-MIR-795HS NetworkManager[624]: <info>  dhclient started with pid 747
Nov 18 19:43:15 nyokie-MIR-795HS avahi-daemon[705]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::f66d:4ff:fe13:215.
Nov 18 19:43:15 nyokie-MIR-795HS avahi-daemon[705]: New relevant interface eth0.IPv6 for mDNS.
Nov 18 19:43:15 nyokie-MIR-795HS avahi-daemon[705]: Registering new address record for fe80::f66d:4ff:fe13:215 on eth0.*.
Nov 18 19:43:16 nyokie-MIR-795HS dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0xa14f7f61)
Nov 18 19:43:16 nyokie-MIR-795HS gpu-manager[617]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Nov 18 19:43:16 nyokie-MIR-795HS systemd[1]: Started Detect the available GPUs and deal with any system changes.
Nov 18 19:43:16 nyokie-MIR-795HS systemd[1]: Starting Light Display Manager...
Nov 18 19:43:16 nyokie-MIR-795HS dhclient: DHCPREQUEST of 192.168.1.7 on eth0 to 255.255.255.255 port 67 (xid=0x617f4fa1)
Nov 18 19:43:16 nyokie-MIR-795HS dhclient: DHCPOFFER of 192.168.1.7 from 192.168.1.1
Nov 18 19:43:16 nyokie-MIR-795HS dhclient: DHCPACK of 192.168.1.7 from 192.168.1.1
Nov 18 19:43:16 nyokie-MIR-795HS systemd[1]: Started Light Display Manager.
Nov 18 19:43:16 nyokie-MIR-795HS NetworkManager[624]: <info>    address 192.168.1.7
Nov 18 19:43:16 nyokie-MIR-795HS NetworkManager[624]: <info>    plen 24 (255.255.255.0)
Nov 18 19:43:16 nyokie-MIR-795HS NetworkManager[624]: <info>    gateway 192.168.1.1
Nov 18 19:43:16 nyokie-MIR-795HS NetworkManager[624]: <info>    server identifier 192.168.1.1
Nov 18 19:43:16 nyokie-MIR-795HS NetworkManager[624]: <info>    lease time 86400
Nov 18 19:43:16 nyokie-MIR-795HS NetworkManager[624]: <info>    nameserver '192.168.1.1'
Nov 18 19:43:16 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): DHCPv4 state changed unknown -> bound
Nov 18 19:43:16 nyokie-MIR-795HS avahi-daemon[705]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.7.
Nov 18 19:43:16 nyokie-MIR-795HS avahi-daemon[705]: New relevant interface eth0.IPv4 for mDNS.
Nov 18 19:43:16 nyokie-MIR-795HS avahi-daemon[705]: Registering new address record for 192.168.1.7 on eth0.IPv4.
Nov 18 19:43:16 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
Nov 18 19:43:16 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Nov 18 19:43:16 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Nov 18 19:43:16 nyokie-MIR-795HS NetworkManager[624]: <info>  NetworkManager state is now CONNECTED_LOCAL
Nov 18 19:43:16 nyokie-MIR-795HS whoopsie[630]: [19:43:16] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Nov 18 19:43:16 nyokie-MIR-795HS whoopsie[630]: [19:43:16] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Nov 18 19:43:16 nyokie-MIR-795HS dhclient: bound to 192.168.1.7 -- renewal in 39253 seconds.
Nov 18 19:43:16 nyokie-MIR-795HS NetworkManager[624]: <info>  NetworkManager state is now CONNECTED_GLOBAL
Nov 18 19:43:16 nyokie-MIR-795HS NetworkManager[624]: <info>  Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 18 19:43:16 nyokie-MIR-795HS NetworkManager[624]: <info>  DNS: starting dnsmasq...
Nov 18 19:43:16 nyokie-MIR-795HS NetworkManager[624]: <warn>  dnsmasq not available on the bus, can't update servers.
Nov 18 19:43:16 nyokie-MIR-795HS NetworkManager[624]: <error> [1447893796.925456] [dns-manager/nm-dns-dnsmasq.c:387] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Nov 18 19:43:16 nyokie-MIR-795HS NetworkManager[624]: <warn>  DNS: plugin dnsmasq update failed
Nov 18 19:43:16 nyokie-MIR-795HS NetworkManager[624]: <info>  Writing DNS information to /sbin/resolvconf
Nov 18 19:43:17 nyokie-MIR-795HS dnsmasq[787]: started, version 2.75 cache disabled
Nov 18 19:43:17 nyokie-MIR-795HS dnsmasq[787]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth DNSSEC loop-detect inotify
Nov 18 19:43:17 nyokie-MIR-795HS dnsmasq[787]: DBus support enabled: connected to system bus
Nov 18 19:43:17 nyokie-MIR-795HS dnsmasq[787]: warning: no upstream servers configured
Nov 18 19:43:17 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): Activation: successful, device activated.
Nov 18 19:43:17 nyokie-MIR-795HS NetworkManager[624]: <info>  startup complete
Nov 18 19:43:17 nyokie-MIR-795HS dbus[633]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Nov 18 19:43:17 nyokie-MIR-795HS NetworkManager[624]: <warn>  dnsmasq appeared on DBus: :1.23
Nov 18 19:43:17 nyokie-MIR-795HS dnsmasq[787]: setting upstream servers from DBus
Nov 18 19:43:17 nyokie-MIR-795HS dnsmasq[787]: using nameserver 192.168.1.1#53
Nov 18 19:43:17 nyokie-MIR-795HS systemd[1]: Starting Network Manager Script Dispatcher Service...
Nov 18 19:43:17 nyokie-MIR-795HS NetworkManager[624]: <info>  Writing DNS information to /sbin/resolvconf
Nov 18 19:43:17 nyokie-MIR-795HS whoopsie[630]: [19:43:17] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/0
Nov 18 19:43:17 nyokie-MIR-795HS systemd[1]: Started Network Manager Wait Online.
Nov 18 19:43:17 nyokie-MIR-795HS whoopsie[630]: [19:43:17] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/0
Nov 18 19:43:17 nyokie-MIR-795HS whoopsie[630]: [19:43:17] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/0
Nov 18 19:43:17 nyokie-MIR-795HS whoopsie[630]: [19:43:17] online
Nov 18 19:43:17 nyokie-MIR-795HS systemd[1]: Reached target Network is Online.
Nov 18 19:43:17 nyokie-MIR-795HS dbus[633]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Nov 18 19:43:17 nyokie-MIR-795HS nm-dispatcher: Dispatching action 'up' for eth0
Nov 18 19:43:17 nyokie-MIR-795HS systemd[1]: Starting LSB: Tool to automatically collect and submit kernel crash signatures...
Nov 18 19:43:17 nyokie-MIR-795HS systemd[1]: Starting /etc/rc.local Compatibility...
Nov 18 19:43:17 nyokie-MIR-795HS systemd[1]: Started Network Manager Script Dispatcher Service.
Nov 18 19:43:17 nyokie-MIR-795HS systemd[1]: Started /etc/rc.local Compatibility.
Nov 18 19:43:17 nyokie-MIR-795HS systemd[1]: Starting Wait for Plymouth Boot Screen to Quit...
Nov 18 19:43:17 nyokie-MIR-795HS systemd[1]: Started LSB: Tool to automatically collect and submit kernel crash signatures.
Nov 18 19:43:17 nyokie-MIR-795HS NetworkManager[624]: <info>  WiFi hardware radio set enabled
Nov 18 19:43:17 nyokie-MIR-795HS NetworkManager[624]: <info>  WWAN hardware radio set enabled
Nov 18 19:43:18 nyokie-MIR-795HS systemd[1]: Received SIGRTMIN+21 from PID 326 (plymouthd).
Nov 18 19:43:18 nyokie-MIR-795HS systemd[1]: Started Wait for Plymouth Boot Screen to Quit.
Nov 18 19:43:18 nyokie-MIR-795HS systemd[1]: Started Getty on tty1.
Nov 18 19:43:18 nyokie-MIR-795HS systemd[1]: Reached target Login Prompts.
Nov 18 19:43:18 nyokie-MIR-795HS systemd[1]: Reached target Multi-User System.
Nov 18 19:43:18 nyokie-MIR-795HS systemd[1]: Reached target Graphical Interface.
Nov 18 19:43:18 nyokie-MIR-795HS systemd[1]: Started Stop ureadahead data collection 45s after completed startup.
Nov 18 19:43:18 nyokie-MIR-795HS systemd[1]: Starting Update UTMP about System Runlevel Changes...
Nov 18 19:43:18 nyokie-MIR-795HS systemd[1]: Started Update UTMP about System Runlevel Changes.
Nov 18 19:43:18 nyokie-MIR-795HS systemd[1]: Startup finished in 5.993s (kernel) + 35.427s (userspace) = 41.420s.
Nov 18 19:43:18 nyokie-MIR-795HS systemd[1]: Created slice user-1000.slice.
Nov 18 19:43:18 nyokie-MIR-795HS systemd[1]: Starting User Manager for UID 1000...
Nov 18 19:43:18 nyokie-MIR-795HS systemd[1]: Started Session c1 of user nyokie.
Nov 18 19:43:18 nyokie-MIR-795HS systemd[1033]: Reached target Paths.
Nov 18 19:43:18 nyokie-MIR-795HS systemd[1033]: Reached target Timers.
Nov 18 19:43:18 nyokie-MIR-795HS systemd[1033]: Reached target Sockets.
Nov 18 19:43:18 nyokie-MIR-795HS systemd[1033]: Reached target Basic System.
Nov 18 19:43:18 nyokie-MIR-795HS systemd[1033]: Reached target Default.
Nov 18 19:43:18 nyokie-MIR-795HS systemd[1033]: Startup finished in 38ms.
Nov 18 19:43:18 nyokie-MIR-795HS systemd[1]: Started User Manager for UID 1000.
Nov 18 19:43:23 nyokie-MIR-795HS org.a11y.atspi.Registry[1212]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Nov 18 19:43:24 nyokie-MIR-795HS org.gnome.ScreenSaver[1131]: ** (gnome-screensaver:1287): WARNING **: Couldn't get presence status: The name org.gnome.SessionManager was not provided by any .service files
Nov 18 18:46:43 nyokie-MIR-795HS ntpdate[988]: step time server 91.189.94.4 offset -3400.998039 sec
Nov 18 18:46:43 nyokie-MIR-795HS systemd[1]: Time has been changed
Nov 18 18:46:43 nyokie-MIR-795HS systemd[1033]: Time has been changed
Nov 18 18:46:43 nyokie-MIR-795HS systemd-timesyncd[443]: Synchronized to time server 91.189.94.4:123 (ntp.ubuntu.com).
Nov 18 18:46:43 nyokie-MIR-795HS gnome-session[1206]: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Nov 18 18:46:43 nyokie-MIR-795HS gnome-session[1206]: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Nov 18 18:46:43 nyokie-MIR-795HS gnome-session[1206]: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Nov 18 18:46:43 nyokie-MIR-795HS dbus[633]: [system] Activating via systemd: service name='org.freedesktop.UPower' unit='upower.service'
Nov 18 18:46:43 nyokie-MIR-795HS systemd[1]: Starting Daemon for power management...
Nov 18 18:46:44 nyokie-MIR-795HS dbus[633]: [system] Activating via systemd: service name='org.freedesktop.RealtimeKit1' unit='rtkit-daemon.service'
Nov 18 18:46:44 nyokie-MIR-795HS systemd[1]: Starting RealtimeKit Scheduling Policy Service...
Nov 18 18:46:44 nyokie-MIR-795HS dbus[633]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Nov 18 18:46:44 nyokie-MIR-795HS systemd[1]: Started RealtimeKit Scheduling Policy Service.
Nov 18 18:46:44 nyokie-MIR-795HS rtkit-daemon[1334]: Successfully called chroot.
Nov 18 18:46:44 nyokie-MIR-795HS rtkit-daemon[1334]: Successfully dropped privileges.
Nov 18 18:46:44 nyokie-MIR-795HS rtkit-daemon[1334]: Successfully limited resources.
Nov 18 18:46:44 nyokie-MIR-795HS rtkit-daemon[1334]: Canary thread running.
Nov 18 18:46:44 nyokie-MIR-795HS rtkit-daemon[1334]: Running.
Nov 18 18:46:44 nyokie-MIR-795HS rtkit-daemon[1334]: Watchdog thread running.
Nov 18 18:46:44 nyokie-MIR-795HS dbus[633]: [system] Successfully activated service 'org.freedesktop.UPower'
Nov 18 18:46:44 nyokie-MIR-795HS systemd[1]: Started Daemon for power management.
Nov 18 18:46:44 nyokie-MIR-795HS rtkit-daemon[1334]: Successfully made thread 1333 of process 1333 (n/a) owned by '1000' high priority at nice level -11.
Nov 18 18:46:44 nyokie-MIR-795HS rtkit-daemon[1334]: Supervising 1 threads of 1 processes of 1 users.
Nov 18 18:46:44 nyokie-MIR-795HS dbus[633]: [system] Activating via systemd: service name='org.bluez' unit='dbus-org.bluez.service'
Nov 18 18:46:45 nyokie-MIR-795HS dbus[633]: [system] Activating via systemd: service name='org.freedesktop.ColorManager' unit='colord.service'
Nov 18 18:46:45 nyokie-MIR-795HS systemd[1]: Starting Manage, Install and Generate Color Profiles...
Nov 18 18:46:45 nyokie-MIR-795HS rtkit-daemon[1334]: Supervising 1 threads of 1 processes of 1 users.
Nov 18 18:46:45 nyokie-MIR-795HS rtkit-daemon[1334]: Successfully made thread 1426 of process 1333 (n/a) owned by '1000' RT at priority 5.
Nov 18 18:46:45 nyokie-MIR-795HS rtkit-daemon[1334]: Supervising 2 threads of 1 processes of 1 users.
Nov 18 18:46:45 nyokie-MIR-795HS rtkit-daemon[1334]: Supervising 2 threads of 1 processes of 1 users.
Nov 18 18:46:45 nyokie-MIR-795HS rtkit-daemon[1334]: Successfully made thread 1434 of process 1333 (n/a) owned by '1000' RT at priority 5.
Nov 18 18:46:45 nyokie-MIR-795HS rtkit-daemon[1334]: Supervising 3 threads of 1 processes of 1 users.
Nov 18 18:46:45 nyokie-MIR-795HS rtkit-daemon[1334]: Supervising 3 threads of 1 processes of 1 users.
Nov 18 18:46:45 nyokie-MIR-795HS rtkit-daemon[1334]: Successfully made thread 1435 of process 1333 (n/a) owned by '1000' RT at priority 5.
Nov 18 18:46:45 nyokie-MIR-795HS rtkit-daemon[1334]: Supervising 4 threads of 1 processes of 1 users.
Nov 18 18:46:46 nyokie-MIR-795HS rtkit-daemon[1334]: Successfully made thread 1445 of process 1445 (n/a) owned by '1000' high priority at nice level -11.
Nov 18 18:46:46 nyokie-MIR-795HS rtkit-daemon[1334]: Supervising 5 threads of 2 processes of 1 users.
Nov 18 18:46:46 nyokie-MIR-795HS pulseaudio[1445]: [pulseaudio] pid.c: Daemon already running.
Nov 18 18:46:46 nyokie-MIR-795HS rtkit-daemon[1334]: Successfully made thread 1448 of process 1448 (n/a) owned by '1000' high priority at nice level -11.
Nov 18 18:46:46 nyokie-MIR-795HS rtkit-daemon[1334]: Supervising 6 threads of 3 processes of 1 users.
Nov 18 18:46:46 nyokie-MIR-795HS pulseaudio[1448]: [pulseaudio] pid.c: Daemon already running.
Nov 18 18:46:46 nyokie-MIR-795HS dbus[633]: [system] Activating via systemd: service name='org.freedesktop.locale1' unit='dbus-org.freedesktop.locale1.service'
Nov 18 18:46:46 nyokie-MIR-795HS gnome-session[1206]: (process:1452): indicator-application-service-WARNING **: Unable to get watcher name 'org.kde.StatusNotifierWatcher'
Nov 18 18:46:46 nyokie-MIR-795HS gnome-session[1206]: (process:1452): indicator-application-service-WARNING **: Name Lost
Nov 18 18:46:46 nyokie-MIR-795HS dbus[633]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Nov 18 18:46:46 nyokie-MIR-795HS systemd[1]: Starting Locale Service...
Nov 18 18:46:46 nyokie-MIR-795HS systemd[1]: Started Manage, Install and Generate Color Profiles.
Nov 18 18:46:46 nyokie-MIR-795HS gnome-session[1206]: Entering running state
Nov 18 18:46:46 nyokie-MIR-795HS dbus[633]: [system] Successfully activated service 'org.freedesktop.locale1'
Nov 18 18:46:46 nyokie-MIR-795HS systemd[1]: Started Locale Service.
Nov 18 18:46:47 nyokie-MIR-795HS dbus[633]: [system] Activating via systemd: service name='org.freedesktop.UDisks2' unit='udisks2.service'
Nov 18 18:46:47 nyokie-MIR-795HS systemd[1]: Starting Disk Manager...
Nov 18 18:46:47 nyokie-MIR-795HS udisksd[1489]: udisks daemon version 2.1.6 starting
Nov 18 18:46:47 nyokie-MIR-795HS dbus[633]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Nov 18 18:46:47 nyokie-MIR-795HS systemd[1]: Started Disk Manager.
Nov 18 18:46:47 nyokie-MIR-795HS udisksd[1489]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Nov 18 18:46:47 nyokie-MIR-795HS org.gtk.Private.AfcVolumeMonitor[1131]: Volume monitor alive
Nov 18 18:46:52 nyokie-MIR-795HS org.gnome.keyring.SystemPrompter[1131]: Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Nov 18 18:46:58 nyokie-MIR-795HS ntpdate[1570]: adjust time server 91.189.94.4 offset 0.002507 sec
Nov 18 18:47:01 nyokie-MIR-795HS org.gnome.ScreenSaver[1131]: ** Message: Lost the name, shutting down.
Nov 18 18:47:03 nyokie-MIR-795HS org.freedesktop.Telepathy.AccountManager[1131]: (process:1634): mcd-WARNING **: Not sure what the type of 'mc-account-name' is, assuming string
Nov 18 18:47:06 nyokie-MIR-795HS colord-sane: io/hpmud/pp.c 627: unable to read device-id ret=-1
Nov 18 18:47:06 nyokie-MIR-795HS colord[1425]: (colord:1425): Cd-WARNING **: failed to get session [pid 1474]: No such device or address
Nov 18 18:47:09 nyokie-MIR-795HS pulseaudio[1333]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out
Nov 18 18:47:09 nyokie-MIR-795HS org.gnome.zeitgeist.Engine[1131]: ** (zeitgeist-datahub:1671): WARNING **: zeitgeist-datahub.vala:229: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
Nov 18 18:47:12 nyokie-MIR-795HS gnome-session[1206]: (nm-applet:1458): nm-applet-WARNING **: Could not find ShellVersion property on org.gnome.Shell after 5 tries
Nov 18 18:47:22 nyokie-MIR-795HS systemd[1]: Starting Stop ureadahead data collection...
Nov 18 18:47:22 nyokie-MIR-795HS systemd[1]: Stopped Read required files in advance.
Nov 18 18:47:22 nyokie-MIR-795HS systemd[1]: Started Stop ureadahead data collection.
Nov 18 18:47:29 nyokie-MIR-795HS org.gnome.evolution.dataserver.Sources4[1131]: (evolution-source-registry:1440): module-ubuntu-online-accounts-WARNING **: ubuntu_online_accounts_got_userinfo_cb: Failed to create ESource collection for AgAccount 'nyokie@gmail.com': GDBus.Error:com.google.code.AccountsSSO.SingleSignOn.Error.UserInteraction: userActionFinished error: 10
Nov 18 18:47:31 nyokie-MIR-795HS systemd[1]: Started Daemon for generating UUIDs.
Nov 18 18:53:46 nyokie-MIR-795HS gnome-session[1206]: Failed to open VDPAU backend libvdpau_nouveau.so: cannot open shared object file: No such file or directory
Nov 18 18:59:21 nyokie-MIR-795HS gnome-session[1206]: Failed to open VDPAU backend libvdpau_nouveau.so: cannot open shared object file: No such file or directory
Nov 18 19:01:22 nyokie-MIR-795HS systemd[1]: Starting Cleanup of Temporary Directories...
Nov 18 19:01:22 nyokie-MIR-795HS systemd-tmpfiles[2482]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Nov 18 19:01:22 nyokie-MIR-795HS systemd[1]: Started Cleanup of Temporary Directories.
Nov 18 19:13:57 nyokie-MIR-795HS kernel: [ 1682.522815] perf interrupt took too long (2501 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Nov 18 19:17:01 nyokie-MIR-795HS CRON[2642]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 18 19:28:22 nyokie-MIR-795HS kernel: [ 2548.132462] usb 1-1.3: USB disconnect, device number 4
Nov 18 19:28:23 nyokie-MIR-795HS kernel: [ 2549.101075] usb 1-1.3: new low-speed USB device number 6 using ehci-pci
Nov 18 19:28:23 nyokie-MIR-795HS kernel: [ 2549.197961] usb 1-1.3: New USB device found, idVendor=1d57, idProduct=0001
Nov 18 19:28:23 nyokie-MIR-795HS kernel: [ 2549.197965] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Nov 18 19:28:23 nyokie-MIR-795HS kernel: [ 2549.197967] usb 1-1.3: Product: 2.4G Mouse
Nov 18 19:28:23 nyokie-MIR-795HS kernel: [ 2549.197968] usb 1-1.3: Manufacturer: 2.4G KB
Nov 18 19:28:23 nyokie-MIR-795HS kernel: [ 2549.201278] input: 2.4G KB 2.4G Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/0003:1D57:0001.0008/input/input19
Nov 18 19:28:23 nyokie-MIR-795HS kernel: [ 2549.257531] hid-generic 0003:1D57:0001.0008: input,hidraw1: USB HID v1.10 Keyboard [2.4G KB 2.4G Mouse] on usb-0000:00:1a.0-1.3/input0
Nov 18 19:28:23 nyokie-MIR-795HS kernel: [ 2549.261885] input: 2.4G KB 2.4G Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.1/0003:1D57:0001.0009/input/input20
Nov 18 19:28:23 nyokie-MIR-795HS mtp-probe: checking bus 1, device 6: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3"
Nov 18 19:28:23 nyokie-MIR-795HS kernel: [ 2549.317680] hid-generic 0003:1D57:0001.0009: input,hidraw3: USB HID v1.10 Mouse [2.4G KB 2.4G Mouse] on usb-0000:00:1a.0-1.3/input1
Nov 18 19:28:23 nyokie-MIR-795HS mtp-probe: bus: 1, device: 6 was not an MTP device
Nov 18 19:28:26 nyokie-MIR-795HS colord-sane: io/hpmud/pp.c 627: unable to read device-id ret=-1
Nov 18 19:34:31 nyokie-MIR-795HS gnome-session[1206]: Failed to open VDPAU backend libvdpau_nouveau.so: cannot open shared object file: No such file or directory
Nov 18 19:37:47 nyokie-MIR-795HS gnome-session[1206]: gnome-session[1206]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Nov 18 19:37:47 nyokie-MIR-795HS gnome-session[1206]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Nov 18 19:37:47 nyokie-MIR-795HS gnome-session[1206]: message repeated 2 times: [ GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed]
Nov 18 19:37:47 nyokie-MIR-795HS gnome-session[1206]: gnome-session[1206]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Nov 18 19:37:47 nyokie-MIR-795HS gnome-session[1206]: gnome-session[1206]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Nov 18 19:37:48 nyokie-MIR-795HS gnome-session[1206]: WARNING: Client '/org/gnome/SessionManager/Client1' failed to reply before timeout
Nov 18 19:37:48 nyokie-MIR-795HS gnome-session[1206]: gnome-session[1206]: WARNING: Client '/org/gnome/SessionManager/Client1' failed to reply before timeout
Nov 18 19:38:05 nyokie-MIR-795HS gnome-session[1206]: Entering running state
Nov 18 19:38:05 nyokie-MIR-795HS gnome-session[1206]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Nov 18 19:38:05 nyokie-MIR-795HS gnome-session[1206]: gnome-session[1206]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Nov 18 19:38:05 nyokie-MIR-795HS NetworkManager[624]: <info>  sleep requested (sleeping: no  enabled: yes)
Nov 18 19:38:05 nyokie-MIR-795HS NetworkManager[624]: <info>  sleeping...
Nov 18 19:38:05 nyokie-MIR-795HS NetworkManager[624]: <info>  NetworkManager state is now ASLEEP
Nov 18 19:38:05 nyokie-MIR-795HS whoopsie[630]: [19:38:05] offline
Nov 18 19:38:06 nyokie-MIR-795HS systemd[1]: Reached target Sleep.
Nov 18 19:38:06 nyokie-MIR-795HS systemd[1]: Starting Suspend...
Nov 18 19:38:06 nyokie-MIR-795HS systemd-sleep[3091]: Suspending system...
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3132.705902] PM: Syncing filesystems ... done.
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3133.004324] PM: Preparing system for sleep (mem)
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3133.004554] Freezing user space processes ... (elapsed 0.002 seconds) done.
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3133.006715] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3133.007861] PM: Suspending system (mem)
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3133.007899] Suspending console(s) (use no_console_suspend to debug)
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3133.008884] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3133.119021] parport_pc 00:06: disabled
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3133.119208] serial 00:04: disabled
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3133.119215] serial 00:04: System wakeup disabled by ACPI
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3133.119351] nouveau  [     DRM] suspending console...
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3133.119356] nouveau  [     DRM] suspending display...
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3133.119393] nouveau  [     DRM] evicting buffers...
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3133.177116] sd 0:0:0:0: [sda] Stopping disk
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3134.834209] nouveau  [     DRM] waiting for kernel channels to go idle...
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3134.834251] nouveau  [     DRM] suspending client object trees...
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3134.834811] nouveau  [     DRM] suspending kernel object tree...
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.841717] PM: suspend of devices complete after 3830.873 msecs
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.842312] PM: late suspend of devices complete after 0.589 msecs
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.842772] pcieport 0000:00:1c.4: System wakeup enabled by ACPI
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.842801] ehci-pci 0000:00:1d.0: System wakeup enabled by ACPI
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.842920] ehci-pci 0000:00:1a.0: System wakeup enabled by ACPI
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.857515] PM: noirq suspend of devices complete after 15.190 msecs
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.857862] ACPI: Preparing to enter system sleep state S3
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.858156] PM: Saving platform NVS memory
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.858417] Disabling non-boot CPUs ...
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.858694] Broke affinity for irq 25
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.859712] smpboot: CPU 1 is now offline
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.874067] Broke affinity for irq 25
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.875082] smpboot: CPU 2 is now offline
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.890316] Broke affinity for irq 17
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.890321] Broke affinity for irq 21
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.890326] Broke affinity for irq 23
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.890329] Broke affinity for irq 25
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.891354] smpboot: CPU 3 is now offline
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.906848] ACPI: Low-level resume complete
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.906886] PM: Restoring platform NVS memory
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.907335] Enabling non-boot CPUs ...
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.907384] x86: Booting SMP configuration:
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.907385] smpboot: Booting Node 0 Processor 1 APIC 0x4
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.918917]  cache: parent cpu1 should not be sleeping
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.919093] CPU1 is up
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.919111] smpboot: Booting Node 0 Processor 2 APIC 0x1
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.926958]  cache: parent cpu2 should not be sleeping
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.927135] CPU2 is up
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.927156] smpboot: Booting Node 0 Processor 3 APIC 0x5
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.934989]  cache: parent cpu3 should not be sleeping
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.935173] CPU3 is up
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.937478] ACPI: Waking up from system sleep state S3
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.950930] ehci-pci 0000:00:1a.0: System wakeup disabled by ACPI
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.950990] ehci-pci 0000:00:1d.0: System wakeup disabled by ACPI
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.951088] PM: noirq resume of devices complete after 13.354 msecs
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.951413] PM: early resume of devices complete after 0.305 msecs
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.951640] nouveau  [     DRM] re-enabling device...
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.951657] nouveau  [     DRM] resuming kernel object tree...
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.951676] rtc_cmos 00:01: System wakeup disabled by ACPI
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.951676] nouveau  [   VBIOS][0000:01:00.0] running init tables
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.951681] pcieport 0000:00:1c.4: System wakeup disabled by ACPI
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.953917] sd 0:0:0:0: [sda] Starting disk
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.954815] serial 00:04: activated
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3136.955413] parport_pc 00:06: activated
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3137.281539] ata4: SATA link down (SStatus 0 SControl 300)
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3137.292101] ata3: SATA link down (SStatus 0 SControl 300)
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3137.297158] nouveau  [    VOLT][0000:01:00.0] GPU voltage: 900000uv
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3137.297196] nouveau  [  PTHERM][0000:01:00.0] fan management: automatic
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3137.297482] nouveau  [     CLK][0000:01:00.0] --: core 270 MHz memory 270 MHz 
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3137.298700] nouveau  [     DRM] resuming client object trees...
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3137.299384] r8169 0000:02:00.0 eth0: link down
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3137.299441] nouveau  [     DRM] resuming display...
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3137.351600] nouveau  [     DRM] resuming console...
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3137.351769] PM: resume of devices complete after 400.063 msecs
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3137.352028] PM: Finishing wakeup.
Nov 18 19:38:17 nyokie-MIR-795HS rtkit-daemon[1334]: The canary thread is apparently starving. Taking action.
Nov 18 19:38:17 nyokie-MIR-795HS systemd[1]: Time has been changed
Nov 18 19:38:17 nyokie-MIR-795HS rtkit-daemon[1334]: Demoting known real-time threads.
Nov 18 19:38:17 nyokie-MIR-795HS systemd[1033]: Time has been changed
Nov 18 19:38:17 nyokie-MIR-795HS rtkit-daemon[1334]: Successfully demoted thread 1435 of process 1333 (n/a).
Nov 18 19:38:17 nyokie-MIR-795HS rtkit-daemon[1334]: Successfully demoted thread 1434 of process 1333 (n/a).
Nov 18 19:38:17 nyokie-MIR-795HS rtkit-daemon[1334]: Successfully demoted thread 1426 of process 1333 (n/a).
Nov 18 19:38:17 nyokie-MIR-795HS rtkit-daemon[1334]: Successfully demoted thread 1333 of process 1333 (n/a).
Nov 18 19:38:17 nyokie-MIR-795HS rtkit-daemon[1334]: Demoted 4 threads.
Nov 18 19:38:17 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): link disconnected (deferring action for 4 seconds)
Nov 18 19:38:17 nyokie-MIR-795HS systemd-sleep[3091]: System resumed.
Nov 18 19:38:17 nyokie-MIR-795HS systemd[1]: Started Suspend.
Nov 18 19:38:17 nyokie-MIR-795HS systemd[1]: sleep.target: Unit not needed anymore. Stopping.
Nov 18 19:38:17 nyokie-MIR-795HS systemd[1]: Stopped target Sleep.
Nov 18 19:38:17 nyokie-MIR-795HS systemd[1]: Reached target Suspend.
Nov 18 19:38:17 nyokie-MIR-795HS kernel: [ 3137.352029] Restarting tasks ... done.
Nov 18 19:38:17 nyokie-MIR-795HS NetworkManager[624]: <info>  wake requested (sleeping: yes  enabled: yes)
Nov 18 19:38:17 nyokie-MIR-795HS systemd[1]: suspend.target: Unit is bound to inactive unit systemd-suspend.service. Stopping, too.
Nov 18 19:38:17 nyokie-MIR-795HS NetworkManager[624]: <info>  waking up...
Nov 18 19:38:17 nyokie-MIR-795HS systemd[1]: Stopped target Suspend.
Nov 18 19:38:17 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): device state change: activated -> unmanaged (reason 'sleeping') [100 10 37]
Nov 18 19:38:17 nyokie-MIR-795HS systemd[1]: Started Run anacron jobs at resume.
Nov 18 19:38:17 nyokie-MIR-795HS systemd[1]: Started Run anacron jobs.
Nov 18 19:38:17 nyokie-MIR-795HS anacron[3205]: Anacron 2.3 started on 2015-11-18
Nov 18 19:38:17 nyokie-MIR-795HS anacron[3205]: Normal exit (0 jobs run)
Nov 18 19:38:17 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): canceled DHCP transaction, DHCP client pid 747
Nov 18 19:38:17 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): DHCPv4 state changed bound -> done
Nov 18 19:38:17 nyokie-MIR-795HS avahi-daemon[705]: Withdrawing address record for 192.168.1.7 on eth0.
Nov 18 19:38:17 nyokie-MIR-795HS avahi-daemon[705]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.7.
Nov 18 19:38:17 nyokie-MIR-795HS avahi-daemon[705]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 18 19:38:17 nyokie-MIR-795HS avahi-daemon[705]: Withdrawing address record for fe80::f66d:4ff:fe13:215 on eth0.
Nov 18 19:38:17 nyokie-MIR-795HS avahi-daemon[705]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::f66d:4ff:fe13:215.
Nov 18 19:38:17 nyokie-MIR-795HS avahi-daemon[705]: Interface eth0.IPv6 no longer relevant for mDNS.
Nov 18 19:38:17 nyokie-MIR-795HS whoopsie[630]: [19:38:17] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Nov 18 19:38:17 nyokie-MIR-795HS NetworkManager[624]: <info>  Writing DNS information to /sbin/resolvconf
Nov 18 19:38:17 nyokie-MIR-795HS dnsmasq[787]: setting upstream servers from DBus
Nov 18 19:38:17 nyokie-MIR-795HS NetworkManager[624]: <info>  NetworkManager state is now CONNECTED_LOCAL
Nov 18 19:38:17 nyokie-MIR-795HS whoopsie[630]: [19:38:17] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Nov 18 19:38:17 nyokie-MIR-795HS NetworkManager[624]: <info>  NetworkManager state is now DISCONNECTED
Nov 18 19:38:18 nyokie-MIR-795HS kernel: [ 3137.807383] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 18 19:38:18 nyokie-MIR-795HS kernel: [ 3137.807396] ata2.01: SATA link down (SStatus 0 SControl 300)
Nov 18 19:38:18 nyokie-MIR-795HS kernel: [ 3137.807407] ata2.01: link offline, clearing class 3 to NONE
Nov 18 19:38:18 nyokie-MIR-795HS kernel: [ 3137.819513] ata2.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
Nov 18 19:38:18 nyokie-MIR-795HS kernel: [ 3137.819517] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
Nov 18 19:38:18 nyokie-MIR-795HS kernel: [ 3137.819519] ata2.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
Nov 18 19:38:18 nyokie-MIR-795HS kernel: [ 3138.023626] ata2.00: configured for UDMA/100
Nov 18 19:38:22 nyokie-MIR-795HS pulseaudio[1333]: [pulseaudio] sap.c: sendmsg() failed: Invalid argument
Nov 18 19:38:23 nyokie-MIR-795HS kernel: [ 3142.755010] ata1.00: link is slow to respond, please be patient (ready=0)
Nov 18 19:38:24 nyokie-MIR-795HS kernel: [ 3144.388192] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 18 19:38:24 nyokie-MIR-795HS kernel: [ 3144.388210] ata1.01: SATA link down (SStatus 0 SControl 300)
Nov 18 19:38:24 nyokie-MIR-795HS kernel: [ 3144.396290] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
Nov 18 19:38:24 nyokie-MIR-795HS kernel: [ 3144.396297] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
Nov 18 19:38:24 nyokie-MIR-795HS kernel: [ 3144.396486] ata1.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
Nov 18 19:38:24 nyokie-MIR-795HS kernel: [ 3144.396494] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
Nov 18 19:38:24 nyokie-MIR-795HS kernel: [ 3144.412460] ata1.00: configured for UDMA/133
Nov 18 19:38:26 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 18 19:38:26 nyokie-MIR-795HS dbus[633]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Nov 18 19:38:26 nyokie-MIR-795HS kernel: [ 3145.522603] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 18 19:38:26 nyokie-MIR-795HS systemd[1]: Starting Network Manager Script Dispatcher Service...
Nov 18 19:38:26 nyokie-MIR-795HS kernel: [ 3145.660808] r8169 0000:02:00.0 eth0: link down
Nov 18 19:38:26 nyokie-MIR-795HS kernel: [ 3145.660856] r8169 0000:02:00.0 eth0: link down
Nov 18 19:38:26 nyokie-MIR-795HS kernel: [ 3145.660871] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 18 19:38:26 nyokie-MIR-795HS dbus[633]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Nov 18 19:38:26 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): link disconnected (calling deferred action)
Nov 18 19:38:26 nyokie-MIR-795HS systemd[1]: Started Network Manager Script Dispatcher Service.
Nov 18 19:38:26 nyokie-MIR-795HS nm-dispatcher: Dispatching action 'down' for eth0
Nov 18 19:38:27 nyokie-MIR-795HS pulseaudio[1333]: [pulseaudio] sap.c: sendmsg() failed: Invalid argument
Nov 18 19:38:27 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): link connected
Nov 18 19:38:27 nyokie-MIR-795HS kernel: [ 3147.412990] r8169 0000:02:00.0 eth0: link up
Nov 18 19:38:27 nyokie-MIR-795HS kernel: [ 3147.413007] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Nov 18 19:38:27 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Nov 18 19:38:27 nyokie-MIR-795HS NetworkManager[624]: <info>  Device 'eth0' has no connection; scheduling activate_check in 0 seconds.
Nov 18 19:38:27 nyokie-MIR-795HS NetworkManager[624]: <info>  Auto-activating connection 'Wired connection 1'.
Nov 18 19:38:27 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): Activation: starting connection 'Wired connection 1' (5ca04a42-297c-4a9f-8184-1855f9566371)
Nov 18 19:38:27 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 18 19:38:27 nyokie-MIR-795HS NetworkManager[624]: <info>  NetworkManager state is now CONNECTING
Nov 18 19:38:27 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 18 19:38:27 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov 18 19:38:27 nyokie-MIR-795HS NetworkManager[624]: <info>  Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Nov 18 19:38:27 nyokie-MIR-795HS NetworkManager[624]: <info>  dhclient started with pid 3255
Nov 18 19:38:28 nyokie-MIR-795HS dhclient: DHCPREQUEST of 192.168.1.7 on eth0 to 255.255.255.255 port 67 (xid=0x41069ebe)
Nov 18 19:38:28 nyokie-MIR-795HS dhclient: DHCPACK of 192.168.1.7 from 192.168.1.1
Nov 18 19:38:28 nyokie-MIR-795HS NetworkManager[624]: <info>    address 192.168.1.7
Nov 18 19:38:28 nyokie-MIR-795HS NetworkManager[624]: <info>    plen 24 (255.255.255.0)
Nov 18 19:38:28 nyokie-MIR-795HS NetworkManager[624]: <info>    gateway 192.168.1.1
Nov 18 19:38:28 nyokie-MIR-795HS NetworkManager[624]: <info>    server identifier 192.168.1.1
Nov 18 19:38:28 nyokie-MIR-795HS NetworkManager[624]: <info>    lease time 86400
Nov 18 19:38:28 nyokie-MIR-795HS NetworkManager[624]: <info>    nameserver '192.168.1.1'
Nov 18 19:38:28 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): DHCPv4 state changed unknown -> bound
Nov 18 19:38:28 nyokie-MIR-795HS avahi-daemon[705]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.7.
Nov 18 19:38:28 nyokie-MIR-795HS avahi-daemon[705]: New relevant interface eth0.IPv4 for mDNS.
Nov 18 19:38:28 nyokie-MIR-795HS avahi-daemon[705]: Registering new address record for 192.168.1.7 on eth0.IPv4.
Nov 18 19:38:28 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
Nov 18 19:38:28 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Nov 18 19:38:28 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Nov 18 19:38:28 nyokie-MIR-795HS NetworkManager[624]: <info>  NetworkManager state is now CONNECTED_LOCAL
Nov 18 19:38:28 nyokie-MIR-795HS whoopsie[630]: [19:38:28] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Nov 18 19:38:28 nyokie-MIR-795HS whoopsie[630]: [19:38:28] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Nov 18 19:38:28 nyokie-MIR-795HS dhclient: bound to 192.168.1.7 -- renewal in 37503 seconds.
Nov 18 19:38:28 nyokie-MIR-795HS NetworkManager[624]: <info>  NetworkManager state is now CONNECTED_GLOBAL
Nov 18 19:38:28 nyokie-MIR-795HS NetworkManager[624]: <info>  Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 18 19:38:28 nyokie-MIR-795HS NetworkManager[624]: <info>  Writing DNS information to /sbin/resolvconf
Nov 18 19:38:28 nyokie-MIR-795HS dnsmasq[787]: setting upstream servers from DBus
Nov 18 19:38:28 nyokie-MIR-795HS dnsmasq[787]: using nameserver 192.168.1.1#53
Nov 18 19:38:28 nyokie-MIR-795HS NetworkManager[624]: <info>  (eth0): Activation: successful, device activated.
Nov 18 19:38:28 nyokie-MIR-795HS nm-dispatcher: Dispatching action 'up' for eth0
Nov 18 19:38:28 nyokie-MIR-795HS whoopsie[630]: [19:38:28] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/1
Nov 18 19:38:29 nyokie-MIR-795HS whoopsie[630]: [19:38:28] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/1
Nov 18 19:38:29 nyokie-MIR-795HS whoopsie[630]: [19:38:28] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/1
Nov 18 19:38:29 nyokie-MIR-795HS whoopsie[630]: [19:38:29] online
Nov 18 19:38:29 nyokie-MIR-795HS avahi-daemon[705]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::f66d:4ff:fe13:215.
Nov 18 19:38:29 nyokie-MIR-795HS avahi-daemon[705]: New relevant interface eth0.IPv6 for mDNS.
Nov 18 19:38:29 nyokie-MIR-795HS avahi-daemon[705]: Registering new address record for fe80::f66d:4ff:fe13:215 on eth0.*.
Nov 18 19:38:35 nyokie-MIR-795HS ntpdate[3367]: adjust time server 91.189.94.4 offset -0.140088 sec
Nov 18 19:38:40 nyokie-MIR-795HS kernel: [ 3160.266710] usb 1-1-port3: disabled by hub (EMI?), re-enabling...
Nov 18 19:38:40 nyokie-MIR-795HS kernel: [ 3160.266827] usb 1-1.3: USB disconnect, device number 6
Nov 18 19:38:41 nyokie-MIR-795HS kernel: [ 3160.602440] usb 1-1.3: new low-speed USB device number 7 using ehci-pci
Nov 18 19:38:41 nyokie-MIR-795HS kernel: [ 3160.699745] usb 1-1.3: New USB device found, idVendor=1d57, idProduct=0001
Nov 18 19:38:41 nyokie-MIR-795HS kernel: [ 3160.699749] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Nov 18 19:38:41 nyokie-MIR-795HS kernel: [ 3160.699751] usb 1-1.3: Product: 2.4G Mouse
Nov 18 19:38:41 nyokie-MIR-795HS kernel: [ 3160.699752] usb 1-1.3: Manufacturer: 2.4G KB
Nov 18 19:38:41 nyokie-MIR-795HS kernel: [ 3160.703167] input: 2.4G KB 2.4G Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/0003:1D57:0001.000A/input/input24
Nov 18 19:38:41 nyokie-MIR-795HS kernel: [ 3160.759147] hid-generic 0003:1D57:0001.000A: input,hidraw1: USB HID v1.10 Keyboard [2.4G KB 2.4G Mouse] on usb-0000:00:1a.0-1.3/input0
Nov 18 19:38:41 nyokie-MIR-795HS kernel: [ 3160.763253] input: 2.4G KB 2.4G Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.1/0003:1D57:0001.000B/input/input25
Nov 18 19:38:41 nyokie-MIR-795HS mtp-probe: checking bus 1, device 7: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3"
Nov 18 19:38:41 nyokie-MIR-795HS mtp-probe: bus: 1, device: 7 was not an MTP device
Nov 18 19:38:41 nyokie-MIR-795HS kernel: [ 3160.819027] hid-generic 0003:1D57:0001.000B: input,hidraw3: USB HID v1.10 Mouse [2.4G KB 2.4G Mouse] on usb-0000:00:1a.0-1.3/input1
Nov 18 19:38:45 nyokie-MIR-795HS colord-sane: io/hpmud/pp.c 627: unable to read device-id ret=-1
Nov 18 19:38:50 nyokie-MIR-795HS ntpdate[3487]: adjust time server 91.189.94.4 offset -0.135332 sec
Nov 18 19:46:56 nyokie-MIR-795HS org.gnome.evolution.dataserver.Sources4[1131]: ** (evolution-source-registry:1440): WARNING **: secret_service_search_sync: must specify at least one attribute to match
Nov 18 19:47:50 nyokie-MIR-795HS gnome-session[1206]: (nautilus:3678): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
Nov 18 19:47:50 nyokie-MIR-795HS gnome-session[1206]: (nautilus:3678): GLib-GObject-WARNING **: invalid (NULL) pointer instance
Nov 18 19:47:50 nyokie-MIR-795HS gnome-session[1206]: (nautilus:3678): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
Nov 18 19:47:50 nyokie-MIR-795HS dbus[633]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Nov 18 19:47:50 nyokie-MIR-795HS systemd[1]: Starting Hostname Service...
Nov 18 19:47:51 nyokie-MIR-795HS org.gtk.vfs.Daemon[1131]: ** (process:1574): WARNING **: send_done_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/2 (g-dbus-error-quark, 19)
Nov 18 19:47:51 nyokie-MIR-795HS dbus[633]: [system] Successfully activated service 'org.freedesktop.hostname1'
Nov 18 19:47:51 nyokie-MIR-795HS systemd[1]: Started Hostname Service.
Nov 18 19:47:54 nyokie-MIR-795HS gnome-session[1206]: Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Nov 18 19:47:54 nyokie-MIR-795HS gnome-session[1206]: Please ask your system administrator to enable user sharing.
Nov 18 19:49:59 nyokie-MIR-795HS org.gnome.zeitgeist.SimpleIndexer[1131]: ** (zeitgeist-fts:1669): WARNING **: Unable to get info on application://nautilus-autostart.desktop
```

---

### Post by steve202 on 2015-11-19
Not detailed enough?  Its 15.10 but was doing on older version too, upgraded to see if it would repair it but still doing it. Anyone see something in this log as to why its shutting down on me?

---

### Post by tgalati4 on 2015-11-19
Nothing really shows up in the log file.  What is the make and model of the computer?  How old is the computer?  Check the voltages of the PSU in BIOS or with a meter.  Try a Live USB stick of 14.04.

---

### Post by steve202 on 2015-11-19
It's a transource with 3gig i3 maybe 4 or 5 years old? Any setting in via bios to prevent voltage shutdown too rule that out? Like a acpi setting?

---

### Post by tgalati4 on 2015-11-19
Voltage values tend to be hard-coded for emergency shutdown.  Thermal shutdown can be tailored within limits.  Some BIOS support throttling at 1 temp and emergency thermal shutdown at a 2nd temp--typically 89C and 100C.

---

### Post by steve202 on 2015-11-19
Ok cause I've never seen over 57 must be voltage I'll check with a meter and report back later thanks

---

