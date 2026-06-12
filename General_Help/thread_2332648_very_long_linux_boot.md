---
title: "very long linux boot"
date: 2016-08-02
forum: General Help
---

### Post by psijic on 2016-08-02
Hello. My Linux loads more than 1.5 minutes now. Can you help me with that? 
[http://imgh.us/filename2.svg](http://imgh.us/filename2.svg)

---

### Post by psijic on 2016-08-02
made some tricks, the final situation is here:
[http://imgh.us/filename5.svg](http://imgh.us/filename5.svg)

Desktop: Cinnamon 3.0.6 (Gtk 3.18.9-1ubuntu3.1)
           Distro: Linux Mint 18 Sarah
CPU:       Dual core Intel Core i3-2100 (-HT-MCP-) cache: 3072 KB
Graphics:  Card-1: Intel 2nd Generation Core Processor Family Integrated Graphics Controller
           Card-2: NVIDIA GF104 [GeForce GTX 460] bus-ID: 01:00.0
           Display Server: X.Org 1.18.3 drivers: nvidia,intel (unloaded: fbdev,vesa,nouveau)


graphical.target @1min 30.679s
&#9492;&#9472;ntp.service @1min 34.882s +35ms
  &#9492;&#9472;basic.target @1min 30.190s
    &#9492;&#9472;paths.target @1min 30.190s
      &#9492;&#9472;cups.path @1min 30.190s
        &#9492;&#9472;sysinit.target @1min 30.171s
          &#9492;&#9472;systemd-update-utmp.service @639ms +23ms
            &#9492;&#9472;systemd-tmpfiles-setup.service @576ms +27ms
              &#9492;&#9472;local-fs.target @549ms
                &#9492;&#9472;run-user-1000-gvfs.mount @1min 32.238s
                  &#9492;&#9472;run-user-1000.mount @1min 31.615s
                    &#9492;&#9472;local-fs-pre.target @549ms
                      &#9492;&#9472;lvm2-monitor.service @152ms +396ms
                        &#9492;&#9472;lvm2-lvmetad.service @198ms
                          &#9492;&#9472;lvm2-lvmetad.socket @152ms
                            &#9492;&#9472;-.mount @118ms
                              &#9492;&#9472;system.slice @120ms
                                &#9492;&#9472;-.slice @118ms

---

