---
title: "Boot time over a minute"
date: 2016-09-03
forum: General Help
---

### Post by c10h15n2 on 2016-09-03
Hello. I noticed that it takes a lot longer than before for Ubuntu to start up so I ran these two commands (that I found in another topic) to see what's going on:

```

systemd-analyze
systemd-analyze critical-chain

```

and I got this:

```

Startup finished in 4.126s (kernel) + 1min 2.964s (userspace) = 1min 7.090s

raphical.target @1min 2.942s
&#9492;&#9472;multi-user.target @1min 2.942s
  &#9492;&#9472;getty.target @1min 2.941s
    &#9492;&#9472;getty@tty1.service @1min 2.941s
      &#9492;&#9472;[COLOR=#ff0000]rc-local.service @51.778s +3ms[/COLOR]
        &#9492;&#9472;network-online.target @51.765s
          &#9492;&#9472;network.target @22.877s
            &#9492;&#9472;[COLOR=#ff0000]networking.service @12.797s +10.079s[/COLOR]
              &#9492;&#9472;a[COLOR=#ff0000]pparmor.service @8.078s +4.682s[/COLOR]
                &#9492;&#9472;local-fs.target @7.929s
                  &#9492;&#9472;run-user-120.mount @53.122s
                    &#9492;&#9472;local-fs-pre.target @7.929s
                      &#9492;&#9472;[COLOR=#ff0000]systemd-remount-fs.service @7.697s +164ms[/COLOR]
                        &#9492;&#9472;system.slice @2.329s
                          &#9492;&#9472;-.slice @2.299s


```

Is there something I can do in order to decrease the booting time ? 

**Specs:**

**Memory:** 7,4 GiB
**Processor:** Intel® Core&#8482; i5-3230M CPU @ 2.60GHz × 4
**Graphics: **NVIDIA: GeForce GT 740M
**OS**: Ubuntu 16.04.1 LTS 64-bit

Thanks.

---

