---
title: "just upgraded 18.04.5 and rebooted and fewer than half as many processes ran"
date: 2020-09-02
forum: General Help
---

### Post by Skaperen on 2020-09-02
i just upgraded 18.04.5 and rebooted and fewer than half as many processes ran to boot up and run my setup script.  usually i end up at around process 23000+.  now i'm at around 11000+.  is it actually running fewer processes or is the kernel counting them in a different way?

```

lt2a/forums /home/forums 1> uname -a
Linux lt2a 5.4.0-42-generic #46~18.04.1-Ubuntu SMP Fri Jul 10 07:21:24 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
lt2a/forums /home/forums 2> 

```

---

### Post by VMC on 2020-09-02
How did you check the number of processes at startup? 
I was always concerned with services, which has about 50-60, while an Arch install had 9 !
```
$ systemctl list-unit-files --state=enabled --no-pager|wc -l
58
``` What does pstree show? mine kubuntu:```
$ pstree root
systemd&#9472;&#9516;&#9472;DiscoverNotifie&#9472;&#9472;&#9472;3*[{DiscoverNotifie}]
        &#9500;&#9472;NetworkManager&#9472;&#9472;&#9472;2*[{NetworkManager}]
        &#9500;&#9472;accounts-daemon&#9472;&#9472;&#9472;2*[{accounts-daemon}]
        &#9500;&#9472;acpid
        &#9500;&#9472;agent&#9472;&#9472;&#9472;2*[{agent}]
        &#9500;&#9472;at-spi-bus-laun&#9472;&#9516;&#9472;dbus-daemon
        &#9474;                 &#9492;&#9472;3*[{at-spi-bus-laun}]
        &#9500;&#9472;avahi-daemon&#9472;&#9472;&#9472;avahi-daemon
        &#9500;&#9472;baloo_file&#9472;&#9472;&#9472;2*[{baloo_file}]
        &#9500;&#9472;bluetoothd
        &#9500;&#9472;cron
        &#9500;&#9472;cups-browsed&#9472;&#9472;&#9472;2*[{cups-browsed}]
        &#9500;&#9472;cupsd&#9472;&#9472;&#9472;9*[dbus]
        &#9500;&#9472;dbus-daemon
        &#9500;&#9472;gmenudbusmenupr&#9472;&#9472;&#9472;2*[{gmenudbusmenupr}]
        &#9500;&#9472;haveged
        &#9500;&#9472;irqbalance&#9472;&#9472;&#9472;{irqbalance}
        &#9500;&#9472;kaccess&#9472;&#9472;&#9472;2*[{kaccess}]
        &#9500;&#9472;kdeconnectd&#9472;&#9472;&#9472;3*[{kdeconnectd}]
        &#9500;&#9472;kded5&#9472;&#9472;&#9472;6*[{kded5}]
        &#9500;&#9472;kdeinit5&#9472;&#9516;&#9472;4*[file.so]
        &#9474;          &#9500;&#9472;klauncher&#9472;&#9472;&#9472;2*[{klauncher}]
        &#9474;          &#9500;&#9472;2*[tags.so]
        &#9474;          &#9500;&#9472;2*[thumbnail.so&#9472;&#9472;&#9472;6*[{thumbnail.so}]]
        &#9474;          &#9492;&#9472;trash.so&#9472;&#9472;&#9472;{trash.so}
        &#9500;&#9472;2*[kerneloops]
        &#9500;&#9472;ksmserver&#9472;&#9472;&#9472;2*[{ksmserver}]
        &#9500;&#9472;kwalletd5&#9472;&#9472;&#9472;2*[{kwalletd5}]
        &#9500;&#9472;kwin_x11&#9472;&#9472;&#9472;9*[{kwin_x11}]
        &#9500;&#9472;mount.ntfs
        &#9500;&#9472;networkd-dispat
        &#9500;&#9472;org_kde_powerde&#9472;&#9472;&#9472;4*[{org_kde_powerde}]
        &#9500;&#9472;packagekitd&#9472;&#9472;&#9472;2*[{packagekitd}]
        &#9500;&#9472;plasmashell&#9472;&#9516;&#9472;dolphin&#9472;&#9516;&#9472;kate&#9472;&#9472;&#9472;6*[{kate}]
        &#9474;             &#9474;         &#9492;&#9472;7*[{dolphin}]
        &#9474;             &#9500;&#9472;firefox&#9472;&#9516;&#9472;Privileged Cont&#9472;&#9472;&#9472;26*[{Privileged Cont}]
        &#9474;             &#9474;         &#9500;&#9472;Web Content&#9472;&#9472;&#9472;36*[{Web Content}]
        &#9474;             &#9474;         &#9500;&#9472;Web Content&#9472;&#9472;&#9472;29*[{Web Content}]
        &#9474;             &#9474;         &#9500;&#9472;Web Content&#9472;&#9472;&#9472;19*[{Web Content}]
        &#9474;             &#9474;         &#9500;&#9472;WebExtensions&#9472;&#9472;&#9472;28*[{WebExtensions}]
        &#9474;             &#9474;         &#9492;&#9472;76*[{firefox}]
        &#9474;             &#9500;&#9472;konsole&#9472;&#9516;&#9472;bash
        &#9474;             &#9474;         &#9492;&#9472;6*[{konsole}]
        &#9474;             &#9500;&#9472;konsole&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;pstree
        &#9474;             &#9474;         &#9492;&#9472;6*[{konsole}]
        &#9474;             &#9492;&#9472;13*[{plasmashell}]
        &#9500;&#9472;polkit-kde-auth&#9472;&#9472;&#9472;4*[{polkit-kde-auth}]
        &#9500;&#9472;polkitd&#9472;&#9472;&#9472;2*[{polkitd}]
        &#9500;&#9472;rsyslogd&#9472;&#9472;&#9472;3*[{rsyslogd}]
        &#9500;&#9472;rtkit-daemon&#9472;&#9472;&#9472;2*[{rtkit-daemon}]
        &#9500;&#9472;sddm&#9472;&#9516;&#9472;Xorg&#9472;&#9472;&#9472;9*[{Xorg}]
        &#9474;      &#9500;&#9472;sddm-helper&#9472;&#9472;&#9472;startplasma-x11&#9472;&#9516;&#9472;ssh-agent
        &#9474;      &#9474;                               &#9492;&#9472;{startplasma-x11}
        &#9474;      &#9492;&#9472;{sddm}
        &#9500;&#9472;start_kdeinit
        &#9500;&#9472;systemd&#9472;&#9516;&#9472;(sd-pam)
        &#9474;         &#9500;&#9472;dbus-daemon
        &#9474;         &#9500;&#9472;dconf-service&#9472;&#9472;&#9472;2*[{dconf-*********]
        &#9474;         &#9500;&#9472;kactivitymanage&#9472;&#9472;&#9472;5*[{kactivitymanage}]
        &#9474;         &#9500;&#9472;kglobalaccel5&#9472;&#9472;&#9472;2*[{kglobalaccel5}]
        &#9474;         &#9500;&#9472;kscreen_backend&#9472;&#9472;&#9472;2*[{kscreen_backend}]
        &#9474;         &#9492;&#9472;pulseaudio&#9472;&#9472;&#9472;2*[{pulseaudio}]
        &#9500;&#9472;systemd-journal
        &#9500;&#9472;systemd-logind
        &#9500;&#9472;systemd-resolve
        &#9500;&#9472;systemd-timesyn&#9472;&#9472;&#9472;{systemd-timesyn}
        &#9500;&#9472;systemd-udevd
        &#9500;&#9472;thermald&#9472;&#9472;&#9472;{thermald}
        &#9500;&#9472;udisksd&#9472;&#9472;&#9472;4*[{udisksd}]
        &#9500;&#9472;unattended-upgr&#9472;&#9472;&#9472;{unattended-upgr}
        &#9500;&#9472;upowerd&#9472;&#9472;&#9472;2*[{upowerd}]
        &#9500;&#9472;whoopsie&#9472;&#9472;&#9472;2*[{whoopsie}]
        &#9500;&#9472;wpa_supplicant
        &#9500;&#9472;xembedsniproxy&#9472;&#9472;&#9472;2*[{xembedsniproxy}]
        &#9492;&#9472;xsettingsd
```

---

### Post by Skaperen on 2020-09-03
my setup script reports its PID and the last step it does starts 12 background sessions under username "phil"and lists them.  that list has their PIDs.  the last session was PID 11712.  the first shell (username "admin") got PID 2064.  the setup script got PID 2212 (has exited).  usually the last session would get a PID above 22000, often above 23000.

---

### Post by Skaperen on 2020-09-03
maybe threads no longer get a unique PID?

---

### Post by Skaperen on 2020-09-08
just upgraded, again, and it's back to 22000+ PIDs.

---

