---
title: "Sudden drop in battery life, huge number of wakeups/sec"
date: 2016-09-30
forum: General Help
---

### Post by Blnd2Spll on 2016-09-30
I've been running 16.04 on my Dell XPS 15 9550 for a few weeks now. I've typically been getting about 6-8 hrs on battery using TLP. However, as of yesterday, I'm averaging more like 2-3 hrs on full charge, and I cannot figure out what's changed. Here's the output from powertop. I'm averaging between 1000 and 1500 wakeups/sec, and >40 GPU ops/second. This is much higher than I've seen elsewhere. Is there anything out of the ordinary here? Any ideas of how to troubleshoot this?


```


The battery reports a discharge rate of 14.0 W
The estimated remaining time is 3 hours, 16 minutes

Summary: 1309.5 wakeups/second,  51.0 GPU ops/seconds, 0.0 VFS ops/sec and 22.6% CPU use

                Usage       Events/s    Category       Description
              9.8 pkts/s                Device         Network interface: wlp2s0 (brcmfmac)
             71.4 ms/s     309.5        Process        /usr/lib/x86_64-linux-gnu/opera/opera
             42.7 ms/s     267.5        Process        /usr/lib/x86_64-linux-gnu/opera/opera --type=renderer --alt-high-dpi-setting=73 --system-dpi-setting=73 --primordial-pipe-token
            100.0%                      Device         USB device: USB Receiver (Logitech)
              1.8 ms/s     146.7        Timer          tick_sched_timer
             18.8 ms/s     147.6        Process        /usr/lib/x86_64-linux-gnu/opera/opera --type=gpu-process --channel=2550.0.258183796 --mojo-application-channel-token=16E98127F0
             28.7 ms/s     107.8        Process        compiz
             25.3 ms/s      41.9        Process        /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
            651.0 µs/s      41.0        Interrupt      [6] tasklet(softirq)
              1.0 ms/s      38.4        Timer          hrtimer_wakeup
            327.5 µs/s      37.3        Process        [rcu_sched]
            150.2 µs/s      37.1        Timer          intel_uncore_fw_release_timer
              3.2 ms/s      35.0        Interrupt      [123] xhci_hcd
              2.1 ms/s      26.9        Interrupt      [127] i915_bpo
            132.1 µs/s      15.7        kWork          intel_unpin_work_fn
              6.1 ms/s      12.5        kWork          intel_mmio_flip_work_func
              1.7 ms/s      10.2        Process        nm-applet
              2.3 ms/s       9.4        Process        /usr/lib/libreoffice/program/soffice.bin --calc file:///home/dsm/power.results.csv --splash-pipe=5
            109.1 µs/s       8.7        kWork          gen6_pm_rps_work
              1.3 ms/s       8.6        Process        /usr/sbin/NetworkManager --no-daemon
              1.5 ms/s       7.7        Process        /usr/lib/gnome-terminal/gnome-terminal-server
            266.1 µs/s       6.3        Process        [irq/136-brcmf_p]
             25.5 µs/s       4.3        kWork          brcmf_msgbuf_txflow_worker
            185.3 µs/s       4.1        Process        /usr/lib/telepathy/mission-control-5
            117.1 µs/s       4.0        Process        upstart-dbus-bridge --daemon --system --user --bus-name system
             11.0 µs/s       3.6        kWork          blk_mq_run_work_fn
            401.8 µs/s       2.3        Process        /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
              1.2 ms/s       2.2        Process        /usr/lib/x86_64-linux-gnu/opera/opera --type=renderer --alt-high-dpi-setting=73 --system-dpi-setting=73 --primordial-pipe-token
              2.3 ms/s       2.1        Process        /usr/lib/x86_64-linux-gnu/opera/opera --type=renderer --alt-high-dpi-setting=73 --system-dpi-setting=73 --primordial-pipe-token
              1.2 ms/s       1.7        Process        /usr/lib/x86_64-linux-gnu/opera/opera --type=renderer --alt-high-dpi-setting=73 --system-dpi-setting=73 --primordial-pipe-token
            328.9 µs/s       1.6        Process        /usr/lib/snapd/snapd
            137.0 µs/s       1.4        Process        nautilus -n
            467.6 µs/s       1.3        Process        /usr/lib/x86_64-linux-gnu/unity/unity-panel-service
             19.1 µs/s       1.0        kWork          pci_pme_list_scan
             19.3 µs/s       0.9        kWork          blk_mq_requeue_work
              7.8 µs/s       0.9        kWork          vmstat_shepherd
            101.7 µs/s       0.9        Interrupt      [3] net_rx(softirq)
            125.3 µs/s       0.8        Interrupt      [136] brcmf_pcie_intr
             18.3 µs/s       0.6        Timer          watchdog_timer_fn
              6.6 µs/s       0.6        kWork          brcmf_fweh_event_worker
            114.8 µs/s       0.5        Process        /usr/lib/x86_64-linux-gnu/opera/opera --type=renderer --alt-high-dpi-setting=73 --system-dpi-setting=73 --primordial-pipe-token
             91.2 µs/s       0.5        Process        /usr/lib/x86_64-linux-gnu/opera/opera --type=renderer --alt-high-dpi-setting=73 --system-dpi-setting=73 --primordial-pipe-token
             97.1 µs/s       0.5        kWork          i915_hangcheck_elapsed
              1.9 µs/s       0.5        kWork          mei_timer
             55.3 µs/s       0.4        Process        /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/NetworkManager/dnsmasq.pid
             30.6 µs/s       0.4        kWork          i915_gem_idle_work_handler
              2.9 µs/s       0.4        Process        [ksoftirqd/1]
            107.1 µs/s       0.4        kWork          i915_gem_retire_work_handler
             22.7 µs/s       0.4        Process        /usr/lib/x86_64-linux-gnu/indicator-application/indicator-application-service
             32.6 µs/s       0.3        Process        /usr/lib/x86_64-linux-gnu/bamf/bamfdaemon
            174.4 µs/s      0.30        Process        /sbin/wpa_supplicant -u -s -O /run/wpa_supplicant
              9.4 µs/s      0.30        Interrupt      [130] nvme0q4
              8.4 µs/s      0.30        Process        gpg-agent --homedir /home/dsm/.gnupg --use-standard-socket --daemon
            138.5 µs/s      0.25        Process        /usr/lib/upower/upowerd
              3.2 µs/s      0.25        Timer          sched_rt_period_timer
            330.7 µs/s      0.20        Process        WorkerPool/27
              4.5 µs/s      0.20        Process        [watchdog/5]
              3.8 ms/s      0.15        Interrupt      [7] sched(softirq)
             30.1 µs/s      0.15        Process        upstart-dbus-bridge --daemon --session --user --bus-name session
             20.3 µs/s      0.15        Interrupt      [132] nvme0q6
             18.3 µs/s      0.15        Process        /opt/sublime_text/sublime_text htmlfile.html
             13.8 µs/s      0.15        Process        pool
             11.6 µs/s      0.15        Process        /usr/bin/unity-scope-loader applications/applications.scope applications/scopes.scope commands.scope
              2.7 µs/s      0.15        Process        [watchdog/7]

```

And the device stats:

```


             13.9%        CPU misc
            100.0%        USB device: USB Receiver (Logitech)
             13.9%        DRAM
             13.9%        CPU core
              1.9 pkts/s  Network interface: wlp2s0 (brcmfmac)
             11.6 ops/s   GPU core
            100.0%        USB device: xHCI Host Controller
            100.0%        Radio device: brcmfmac
             11.6 ops/s   GPU misc

```

The only item listed as "Bad" under the Tunables tab is "VM writeback timeout"

---

### Post by paulms on 2016-11-06
I have the same laptop, did you find a workaround to the problem?

---

