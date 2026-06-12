---
title: "Using f-spot for auto detected camera"
date: 2007-02-19
forum: General Help
---

### Post by mbeierl on 2007-02-19
Upon plugging in my digital camera I get a pop up asking me if I want to import the pictures.  Nice work!  I love it, 

BUT

(there's always gotta be something)

how can I change this to use f-spot instead?  My kids find f-spot to be a perfect replacement for Adobe's photo album.

---

### Post by mbeierl on 2007-03-12
/usr/bin/gnome-volume-manager-gthumb

I changed it to read as follows:
```

#!/bin/sh
MOUNT_POINT=$(hal-get-property --udi "$1" --key volume.mount_point)
if test -z "$MOUNT_POINT"; then
  # original:
  # gthumb --import-photos
  # new:
  f-spot --import "$MOUNT_POINT"
else
  ROOT=${MOUNT_POINT}
  dcim=$(ls "${ROOT}" | grep -i dcim)
  if [ $? -eq 0 ]; then
    ROOT="${ROOT}/$dcim"
    # if there is only one dir in the dcim directory, enter it
    if test $(/bin/ls -1 "${ROOT}" | wc -l)  -eq 1; then
      ROOT="${ROOT}/$(ls -1 "${ROOT}" | head -n 1)"
    fi
  fi
  # original:
  # exec /usr/bin/gthumb "${ROOT}"
  # new:
  exec /usr/bin/f-spot --import "${ROOT}"
fi

```
Works perfectly now.

---

### Post by mbeierl on 2007-03-12
Now how do I mark a thread as resolved? :confused:

---

### Post by SendDerek on 2007-03-30
I think this is a GREAT idea!!

I've taken your instructions, and double checked them, but when I click on "import", nothing happens.  It just sits there.

I don't know if it makes any difference, but here are my specs:
Edgy Eft
F-Spot v. 0.3.3

Would you be able to help me with this one?

(BTW:  In order to mark as solved, you do an advance edit on your original post and then check the "Solved" checkbox.)

---

### Post by SendDerek on 2007-03-30
Nevermind... I found a good soultion:

[http://ubuntuforums.org/showthread.php?t=257576](http://ubuntuforums.org/showthread.php?t=257576)

---

