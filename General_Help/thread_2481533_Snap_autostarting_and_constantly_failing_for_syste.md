---
title: "Snap autostarting and constantly failing for system users on Ubuntu 22.04"
date: 2022-12-02
forum: General Help
---

### Post by mjd80 on 2022-12-02
Hi,

I observe big trouble with system user created only for running simple service.
This is user with ID<1000, with systemd enable-linger set.
After lingering, full session is being created like for ordinary user including snap directory being created automatically (/var/lib/myservice/snap).
After that, some snap modules start heavily flooding into the logs:

> 
Dec  2 09:47:59 ubuntu systemd[808]: snap.snapd-desktop-integration.snapd-desktop-integration.service: Scheduled restart job, restart counter is at 30725.
Dec  2 09:47:59 ubuntu systemd[808]: Stopped Service for snap application snapd-desktop-integration.snapd-desktop-integration.
Dec  2 09:47:59 ubuntu systemd[808]: Started Service for snap application snapd-desktop-integration.snapd-desktop-integration.
Dec  2 09:47:59 ubuntu snapd-desktop-integration.snapd-desktop-integration[1676118]: Sorry, home directories outside of /home are not currently supported.
Dec  2 09:47:59 ubuntu snapd-desktop-integration.snapd-desktop-integration[1676118]: See [https://forum.snapcraft.io/t/11209](https://forum.snapcraft.io/t/11209) for details.
Dec  2 09:47:59 ubuntu systemd[808]: snap.snapd-desktop-integration.snapd-desktop-integration.service: Main process exited, code=exited, status=1/FAILURE
Dec  2 09:47:59 ubuntu systemd[808]: snap.snapd-desktop-integration.snapd-desktop-integration.service: Failed with result 'exit-code'.
Dec  2 09:47:59 ubuntu systemd[1604571]: snap.snapd-desktop-integration.snapd-desktop-integration.service: Scheduled restart job, restart counter is at 645.
Dec  2 09:47:59 ubuntu systemd[1604571]: Stopped Service for snap application snapd-desktop-integration.snapd-desktop-integration.
Dec  2 09:47:59 ubuntu systemd[1604571]: Started Service for snap application snapd-desktop-integration.snapd-desktop-integration.
Dec  2 09:48:00 ubuntu snapd-desktop-i[1676143]: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.


Actually snap is fully unwelcome for such user. I observe that errors happen against pid of gdm user as well - not only for my service user. On two machines.
How could I cleanly avoid all the services running for the user, especially snap which is going into the madness as could be seen in logs? But maybe even tracker-miner, gvfs, gstreamer and others creating their .caches and .config directories?

Surely, I would like to stop using linger for running my service, but it's another dependency on systemd-run to run unprivileged LXC containers on cgroupv2.

---

### Post by mjd80 on 2022-12-06
I ended up creating the sub-directory ".config/systemd/user" and there the list of symlinks to /dev/null before enabling linger.
But it's not solution, it's ugly workaround.
At least on minimal Ubuntu the following list prevents from doing mess in system user dir:


```

add_user_lingering() {
    harmful_services="snap.snapd-desktop-integration.snapd-desktop-integration.service"
    harmful_services="${harmful_********** gvfs-daemon.service"
    harmful_services="${harmful_********** gvfs-goa-volume-monitor.service"
    harmful_services="${harmful_********** gvfs-metadata.service"
    harmful_services="${harmful_********** gvfs-udisks2-volume-monitor.service"
    harmful_services="${harmful_********** pipewire.service"
    harmful_services="${harmful_********** pipewire-media-session.service"
    harmful_services="${harmful_********** pulseaudio.service"
    harmful_services="${harmful_********** tracker-miner-fs-3.service"
    harmful_services="${harmful_********** tracker-extract-3.service"
    harmful_services="${harmful_********** xdg-document-portal.service"
    harmful_services="${harmful_********** xdg-permission-store.service"

    user_config_path="${HOMEDIR}/.config"
    if [ ! -d "${user_config_path}" ]; then
        su -l "${USERNAME}" -s /bin/sh -c "mkdir ${user_config_path} -m 700"
    fi
    systemd_path="${user_config_path}/systemd/user"
    if [ ! -d "${systemd_path}" ]; then
        su -l "${USERNAME}" -s /bin/sh -c "mkdir -p ${systemd_path}"
    fi

    for service in ${harmful_**********; do
        service_path="${systemd_path}/${*********"
        if [ ! -e "$service_path" ]; then
            su -l "${USERNAME}" -s /bin/sh -c "ln -s /dev/null '${service_path}'"
        fi
    done

    loginctl enable-linger "${USERNAME}"
}

```

---

