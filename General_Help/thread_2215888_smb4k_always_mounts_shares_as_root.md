---
title: "smb4k always mounts shares as root"
date: 2014-04-08
forum: General Help
---

### Post by cesera on 2014-04-08
I am using smb4k to mount some samba shares from our linux server. Up to recently it worked fine, however no I cannot access any of the shares. A quick investigation shows that smb4k mounts all the shares as root instead of the userid specified in the settings (Preference -> Samba -> Mounting). As the server specifies the directory permissions as 750 and it is mounted as root:root that means I don't have access to the shares anymore (I can mount and unmount them, but don't even have read access).

Is this a recent bug in smb4k or am I doing something wrong?

---

### Post by fran5 on 2014-05-05
Formatting was all jacked and I guess you can't delete around here.

---

### Post by fran5 on 2014-05-05
Formatting was all jacked and I guess you can't delete around here.

---

### Post by fran5 on 2014-05-05
~/.kde/share/apps/smb4k/custom_options.xml  

Go in there and see if your mount point is in there with the wrong user, like this:

```

<options type="share" profile="">
        <workgroup>workgroup</workgroup>
        <unc>//SERVER/upload</unc>
        <ip>10.53.36.25</ip>
        <custom>
            <filesystem_port>445</filesystem_port>
            <gid>0</gid>
            <group>root</group>
            <owner>root</owner>
            <remount>false</remount>
            <smb_port>139</smb_port>
            <uid>0</uid>
        </custom>
    </options>

```

Take this out or rename the file.  Should work after that.

---

