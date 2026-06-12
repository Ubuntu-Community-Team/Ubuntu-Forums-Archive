---
title: "Unable to update Time, Power and some other settings in Ubuntu 14.04.3"
date: 2015-12-16
forum: General Help
---

### Post by Flacon on 2015-12-16
I did some recommended tweaks within Live environment after installing by mounting the installed system. When finally booted into the OS, it works fine except that I can't change (options are not greyed out but if try unchecking items, they check themselves again instantly). Here are the recommended tweaks (from *above*) that I performed:
```

  # Update /etc/fstab
  echo "none     /tmp     tmpfs     rw,noexec,nosuid,nodev     0     0" >> /mnt/etc/fstab
  sed -ie '/\s\/home\s/ s/defaults/defaults,noexec,nosuid,nodev/' /mnt/etc/fstab
  echo "none     /run/shm     tmpfs     rw,noexec,nosuid,nodev     0     0" >> /mnt/etc/fstab

  # Prevent standard user executing su
  chroot /mnt dpkg-statoverride --update --add root adm 4750 /bin/su

  # Disable apport (error reporting)
  sed -ie '/^enabled=1$/ s/1/0/' /mnt/etc/default/apport

  # Protect user home directories
  sed -ie '/^DIR_MODE=/ s/=[0-9]*\+/=0750/' /mnt/etc/adduser.conf
  sed -ie '/^UMASK\s\+/ s/022/027/' /mnt/etc/login.defs
  chmod 750 /mnt/home/"$ADMINUSER"

  # Disable shell access for new users (not affecting the existing admin user)
  sed -ie '/^SHELL=/ s/=.*\+/=\/usr\/sbin\/nologin/' /mnt/etc/default/useradd
  sed -ie '/^DSHELL=/ s/=.*\+/=\/usr\/sbin\/nologin/' /mnt/etc/adduser.conf

  # Disable guest login
  mkdir /mnt/etc/lightdm/lightdm.conf.d
  echo "[SeatDefaults]
allow-guest=false
" > /mnt/etc/lightdm/lightdm.conf.d/50-no-guest.conf# A hook to disable online scopes in dash on login
  echo '#!/bin/bash' > /mnt/usr/local/bin/unity-privacy-hook.sh
  echo "gsettings set com.canonical.Unity.Lenses remote-content-search 'none'
gsettings set com.canonical.Unity.Lenses disabled-scopes \"['more_suggestions-amazon.scope', 'more_suggestions-u1ms.scope', 'more_suggestions-populartracks.scope', 'music-musicstore.scope', 'more_suggestions-ebay.scope', 'more_suggestions-ubuntushop.scope', 'more_suggestions-skimlinks.scope']\"
for USER in \`ls -1 /home\`; do
  chown \"\$USER\":\"\$USER\" /home/\"\$USER\"/.*
done
exit 0
" >> /mnt/usr/local/bin/unity-privacy-hook.sh
  chmod 755 /mnt/usr/local/bin/unity-privacy-hook.sh
  echo "[SeatDefaults]
session-setup-script=/usr/local/bin/unity-privacy-hook.sh" > /mnt/etc/lightdm/lightdm.conf.d/20privacy-hook.conf

# Create /etc/crypttab
blkid | grep "$DISK"3 | awk -F"\"" '{print "lvm UUID=" $2, "none luks,discard"}' > /mnt/etc/crypttab
chmod 664 /mnt/etc/crypttab

# Update initramfs
chroot /mnt update-initramfs -u -k all
```

Updating fstab shouldn't be issue, I guess. After that I restarted and boot into the installed OS, everything works fine except the mentioned issues. I haven't checked the system thoughly except installing updates and Language packs.

---

### Post by Flacon on 2015-12-16
I just removed (back it up first) /home/user/.config/dconf & rebooted, problem solved

Maybe follwing created the problem which I did immediately at first boot:

# Turn off privacy-leaking aspects of Unity
echo "user-db:user" > /etc/dconf/profile/user
echo "system-db:local" >> /etc/dconf/profile/user

mkdir -p /etc/dconf/db/local.d

echo "[com/canonical/unity/lenses]" > /etc/dconf/db/local.d/unity
echo "remote-content-search=false" >> /etc/dconf/db/local.d/unity

mkdir -p /etc/dconf/db/local.d/locks

echo "/com/canonical/unity/lenses/remote-content-search" > /etc/dconf/db/local.d/locks/unity

dconf update

---

