---
title: "Mount action to allow content to display in uppercase"
date: 2022-10-08
forum: General Help
---

### Post by ddebevec on 2022-10-08
I have a DVD with its contents (i.e file and directory names) in mixed case.  I would like to be able to display the content in uppercase, but the "map=o" option doesn't seem to do it.  I think I've tried as many options that I could, but still I can't get the content to display in uppercase.  Anyone have any ideas?  Also Joliet is enabled.

Thanks in advance.
David

Running Ubuntu 20.04.5 LTS

---

### Post by TheFu on 2022-10-09
Unix is case sensitive and has been since the beginning.  Not being case sensitive is a hack, always.

 What, exactly, is the mount command being used?

The mount manpage has the following information on related options in the "Mount options for iso9660" section:
```
       norock Disable the use of Rock Ridge extensions, even if available.  Cf. map.

       nojoliet
              Disable the use of Microsoft Joliet extensions, even if available.  Cf. map.

       check={r[elaxed]|s[trict]}
              With check=relaxed, a filename is first converted to lower case before doing the lookup.  This is
              probably only meaningful together with norock and map=normal.  (Default: check=strict.)

       uid=value and gid=value
              Give all files in the filesystem the indicated user or group id, possibly overriding the informa&#8208;
              tion found in the Rock Ridge extensions.  (Default: uid=0,gid=0.)

       map={n[ormal]|o[ff]|a[corn]}
              For  non-Rock  Ridge  volumes,  normal  name  translation maps upper to lower case ASCII, drops a
              trailing `;1', and converts `;' to `.'.  With map=off no name translation is done.   See  norock.
              (Default: map=normal.)  map=acorn is like map=normal but also apply Acorn extensions if present.

```
Be certain to validate that the iso9660 has or doesn't have joliet and/or rock ridge extensions.  Also, check your kernel for that support (or not), as desired.

---

### Post by ddebevec on 2022-10-09
The mount command I was using is:

sudo mount -t isp9660 -o ro,map=o /dev/cdrom /cdrom

I ran the following command:

 grep -i joliet /boot/config-`uname -r`

which returned:

CONFIG_JOLIET=y

Not sure how to check for [COLOR=#000000]rock ridge extensions.[/COLOR]

---

### Post by TheFu on 2022-10-10
"isp9660" isn't a valid file system.  Try "iso9660" instead.  Details matter.

Did you read the "check" option and what it recommends?

---

### Post by ddebevec on 2022-10-10
I fat fingered the response.  I am using [COLOR=#000000]iso9660.  I tried all combinations and still no luck.[/COLOR]

---

### Post by Holger_Gehrke on 2022-10-10
If you only want to **display** the contents in upper case, then you can pipe the output of 'ls' through 'tr', like so:
```
ls | tr '[:lower:]' '[:upper:]'
```this will map all lower case letters in the output of ls to upper case.

Holger

---

### Post by TheFu on 2022-10-10
> **ddebevec said:**
> I fat fingered the response.  I am using [COLOR=#000000]iso9660.  I tried all combinations and still no luck.[/COLOR]

Did you really try over 100 combinations?

---

### Post by ddebevec on 2022-10-10
I tried combinations with and without norock and nojoliet and check and map options.

---

